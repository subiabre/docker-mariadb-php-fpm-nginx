ARG PHP_VERSION

FROM php:${PHP_VERSION}-fpm

# System dependencies
RUN apt update && apt install -y \
    curl

# PHP zip extension
RUN apt install -y \
    libzip-dev zip unzip \
    && docker-php-ext-install \
    zip

# PHP extensions, standalone
RUN docker-php-ext-install \
    opcache pdo pdo_mysql

# APCU & XDebug
RUN pecl install \
    apcu xdebug \
    && docker-php-ext-enable \
    apcu xdebug

# Composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

WORKDIR /app
