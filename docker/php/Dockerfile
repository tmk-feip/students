FROM php:8.2-fpm

# Установка Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Установка зависимостей
RUN apt-get update && apt-get install -y \
    libpq-dev \
    libzip-dev \
    zip \
    unzip

# Установка расширений PHP
RUN docker-php-ext-install pdo pdo_pgsql zip

# Allow Composer to use all available RAM while installing packages
ENV COMPOSER_MEMORY_LIMIT="-1"

WORKDIR /var/www/html

COPY . .

RUN chown -R www-data:www-data /var/www/html

CMD ["php-fpm"]