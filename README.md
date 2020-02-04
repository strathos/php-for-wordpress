# PHP 7.2 php-fpm alpine with configurable UID and GID and configured for WordPress
Based on [wordpress:php7.2-fpm-alpine](https://github.com/docker-library/wordpress/blob/0df5de06a4f43f2790dfc3be92554a7e229115d9/php7.2/fpm-alpine/Dockerfile) from [official WordPress](https://hub.docker.com/_/wordpress/) but with configurable UID and GID for www-data. The container itself is still ran as root. WordPress installation is NOT included and should be installed separately with Composer. In addition the image includes wp-cli.

Dockerfile installs shadow for usermod and groupmod command and defaults for UID and GID 1000. Also docker-entrypoint.sh file has been modified to take new values on runtime. Use environment variables `PUID` and `PGID` to override the defaults.

```bash
docker run -it --rm -e PUID=1001 -e PGID=1234 strathos/php-for-wordpress:7.2-fpm-alpine-uid bash
```