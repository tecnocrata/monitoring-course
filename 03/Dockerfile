FROM php:7.4.1-fpm

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN apt-get clean
RUN apt-get update
RUN apt-get install -y libzip-dev zip && docker-php-ext-install zip
RUN pecl install apcu-5.1.18 && docker-php-ext-enable apcu
RUN mkdir /app
WORKDIR /app
COPY ./app/ /app/
RUN /usr/local/bin/composer install --no-dev --prefer-source
ENTRYPOINT ["php", "-S", "0.0.0.0:8081", "index.php"]

EXPOSE 8081