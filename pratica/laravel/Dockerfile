FROM php:7.4-cli

WORKDIR /var/www

RUN apt-get update && \
    apt-get install libzip-dev -y && \
    docker-php-ext-install zip

# Instalando o Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');"

# Instalando o Laravel
RUN php composer.phar create-project laravel/laravel laravel

# Qualquer pessoa que tiver esse dockerfile ou mesmo, dar um run nessa img que acabamos de colocar
# vai poder rodar o laravel tranquilo, com tudo instalado.
# Deixando a nossa img rodar, precisamos deixar o processo da nossa app rodando
ENTRYPOINT ["php","laravel/artisan", "serve"]
# especificando o host de acesso para qualquer outro host
CMD ["--host=0.0.0.0"]