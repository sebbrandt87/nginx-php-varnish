# nginx-php-varnish
Git repo for nginx-php-varnish Docker image.

Running container provides an instance of nginx & php-fpm fromted by varnish.

Default configuration files for the container are provided in the /config folder

Default web content is provided in the /web folder.

To run an instance, create a data container providing all host config & use the --volumes-from option to the docer run command e.g.

~~~~
docker create -v /etc/httpd -v /etc/php5 -v /etc/varnish --name config alpine
docker cp config/etc/httpd/www.conf config:/etc/httpd
docker cp config/etc/php5/php-fpm.conf config:/etc/php5/
docker cp config/etc/php5/php.ini config:/etc/php5/
docker cp config/etc/varnish/secret config:/etc/varnish/
docker cp config/etc/varnish/www.vcl config:/etc/varnish/

docker run --name nginx_php_varnish --volumes-from config -d -p 80:80 d0nroberto/nginx-php-varnish
~~~~
