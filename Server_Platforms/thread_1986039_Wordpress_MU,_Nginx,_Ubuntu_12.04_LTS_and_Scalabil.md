---
title: "Wordpress MU, Nginx, Ubuntu 12.04 LTS and Scalability"
date: 2012-05-24
forum: Server Platforms
---

### Post by CheezItMan on 2012-05-24
I'm preparing to deploy a new Nginx server hosting Wordpress MU to our school. Each wordpress site will serve as a student ePortfolio. I'm concerned about when all 500 students hit the site and start editing at the same time. The particulars of my setup are below. What can I expect/do to prepare for the mass hit of users on my site?

I am running Wordpress Quick Cache, & apc (for php caching).


The Server:

OS: Ubuntu Linux 12.04 LTS
Web server: Nginx (naturally)
PHP: php5-fpm
RAM 16 GB
CPUs: 2 CPUs with 4 cores each (total of 8 cores).

My nginx.conf file:

---

user www-data;
worker_processes 8;
pid /var/run/nginx.pid;

events {
worker_connections 2048;
# multi_accept on;
}

http {
sendfile on;
tcp_nopush on;
tcp_nodelay on;
server_tokens off;
include mime.types;
default_type application/octet-stream;
index index.php index.htm index.html redirect.php;

client_max_body_size 512M;

#Gzip
gzip on;
gzip_vary on;
gzip_proxied any;
gzip_comp_level 6;
gzip_buffers 64 32k;
gzip_http_version 1.1;
gzip_disable "MSIE [1-6].(?!.*SV1)";
gzip_types text/plain text/css application/json application/x-javascript text/xml
application/xml application/xml+rss text/javascript;

#FastCGI
fastcgi_intercept_errors on;
fastcgi_ignore_client_abort on;
fastcgi_buffers 32 64k;
fastcgi_buffer_size 256k;
fastcgi_read_timeout 500;
fastcgi_index index.php;

limit_req_zone $binary_remote_addr zone=one:10m rate=1r/s;

##
# Virtual Host Configs
##

include /etc/nginx/conf.d/*.conf;
include /etc/nginx/sites-enabled/*; #Our individual site vhost server files will live here
}

---

My site file:

---
server {
listen 80;

server_name students.scisdragons.net;
root /var/www/students.scisdragons.net;
access_log /var/log/nginx/students.scisdragons.net.access.log;
error_log /var/log/nginx/students.scisdragons.net.error.log;

include global/wordpress-ms-subdir.conf;



location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {
expires 1y;
log_not_found off;
}

}

---

And my Wordpress Config file

---
location / {
try_files $uri $uri/ /index.php?$args;
}


location /phpmyadmin {
root /usr/share/;
index index.php index.html index.htm;
location ~ ^/phpmyadmin/(.+\.php)$ {
# Zero-day exploit defense.
# [http://forum.nginx.org/read.php?2,88845,page=3](http://forum.nginx.org/read.php?2,88845,page=3)
# Won't work properly (404 error) if the file is not stored on this server, which is entirely possible with php-fpm/php-fcgi.
# Comment the 'try_files' line out if you set up php-fpm/php-fcgi on another machine. And then cross your fingers that you won't get hacked.
try_files $uri =404;

fastcgi_split_path_info ^(.+\.php)(/.+)$;
include fastcgi_params;
fastcgi_index index.php;
fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
# fastcgi_intercept_errors on;
fastcgi_pass 127.0.0.1:9000;
}
location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
root /usr/share/;
}
}
location /phpMyAdmin {
rewrite ^/* /phpmyadmin last;
}


# Add trailing slash to */wp-admin requests.
rewrite /wp-admin$ $scheme://$host$uri/ permanent;

# Directives to send expires headers and turn off 404 error logging.
location ~* \.(js|css|png|jpg|jpeg|gif|ico|mov|mp4|avi|doc|docx|pdf)$ {
expires 48h;
log_not_found off;
}

# Pass uploaded files to wp-includes/ms-files.php.
rewrite /files/$ /index.php last;

# For multisite: Use a caching plugin/script that creates symlinks to the correct subdirectory structure to get some performance gains.
set $cachetest "$document_root/wp-content/cache/ms-filemap/${host}${uri}";
if ($uri ~ /$) {
set $cachetest "";
}
if (-f $cachetest) {
# Rewrites the URI and stops rewrite processing so it doesn't start over and attempt to pass it to the next rule.
rewrite ^ /wp-content/cache/ms-filemap/${host}${uri} break;
}

if ($uri !~ wp-content/plugins) {
rewrite /files/(.+)$ /wp-includes/ms-files.php?file=$1 last;
}

# Uncomment one of the lines below for the appropriate caching plugin (if used).
# include global/wordpress-ms-subdir-wp-super-cache.conf;
# include global/wordpress-ms-subdir-w3-total-cache.conf;

# Rewrite multisite '.../wp-.*' and '.../*.php'.
if (!-e $request_filename) {
rewrite ^/[_0-9a-zA-Z-]+(/wp-.*) $1 last;
rewrite ^/[_0-9a-zA-Z-]+(/.*\.php)$ $1 last;
}

# Pass all .php files onto a php-fpm/php-fcgi server.
location ~ \.php$ {
# Zero-day exploit defense.
# [http://forum.nginx.org/read.php?2,88845,page=3](http://forum.nginx.org/read.php?2,88845,page=3)
# Won't work properly (404 error) if the file is not stored on this server, which is entirely possible with php-fpm/php-fcgi.
# Comment the 'try_files' line out if you set up php-fpm/php-fcgi on another machine. And then cross your fingers that you won't get hacked.
try_files $uri =404;

fastcgi_split_path_info ^(.+\.php)(/.+)$;
include fastcgi_params;
fastcgi_index index.php;
fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
# fastcgi_intercept_errors on;
fastcgi_pass 127.0.0.1:9000;
}

---

