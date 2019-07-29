FROM php:7.3-fpm

RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install mysqli

#ENV XDEBUG_CONFIG remote_host=192.168.0.106 remote_port=9001
# Install and enable xDebug
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

COPY ./xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

# Prevent error in nginx error.log
RUN touch /var/log/xdebug_remote.log
RUN chmod 777 /var/log/xdebug_remote.log

# Xdebug setup
#RUN echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20180731/xdebug.so" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo "error_reporting = E_ALL" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo "display_startup_errors = On" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo "display_errors = On" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#
## relevant to this answer
#RUN echo "xdebug.idekey=\"PHPSTORM\"" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo "xdebug.remote_autostart=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
# docker nginx ip adress

CMD ["php-fpm"]

WORKDIR /var/www/ll-test

EXPOSE 9000
