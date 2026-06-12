---
title: "Nginx With Drupal 7 Help with Cron.php"
date: 2015-10-17
forum: Ubuntu/Debian BASED
---

### Post by knarf-musique on 2015-10-17
Hey, I am trying to block access to cron.php on Drupal 7.
I'm on ubuntu 14.04 and i have LEMP up and running. 

This is my current drupal.conf:

```

server {
  listen 80 default_server;
  listen [::]:80 default_server ipv6only=on;
  root /var/www/html/drupal;
  index index.php index.html index.htm;

  error_page 404 /404.html;
  error_page 500 502 503 504 /50x.html;
  location = /50x.html {
      root /usr/share/nginx/html;
  }

  location = /favicon.ico {
    log_not_found off;
    access_log off;
   }

location /phpmyadmin { root /usr/share/; index index.php index.html index.htm; location ~ ^/phpmyadmin/(.+\.php)$ { try_files $uri =404; root /usr/share/; fastcgi_pass unix:/var/run/php5-fpm.sock; fastcgi_index index.php; fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name; include fastcgi_params; } location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ { root /usr/share/; } } location /phpMyAdmin { rewrite ^/* /phpmyadmin last; }

   location = /robots.txt {
     allow all;
     log_not_found off;
     access_log off;
   }
   
   location ~ \..*/.*\.php$ {
     return 403;
   }

   location ~ ^/sites/.*/private/ {
     return 403;
   }

   location ~ (^|/)\. {
     return 403;
   }

   location / {
     try_files $uri @rewrite;
   }
   
   location /cron.php {
         allow 127.0.0.1;
         return 403;
         fastcgi_pass 127.0.0.1:9000;
         deny all;
   }

   location @rewrite {
     rewrite ^ /index.php;
   }

   location ~ \.php$ {
     fastcgi_split_path_info ^(.+\.php)(/.+)$;
     include fastcgi_params;
     fastcgi_param SCRIPT_FILENAME $request_filename;
     fastcgi_intercept_errors on;
     fastcgi_pass unix:/var/run/php5-fpm.sock;
   }

   location ~ ^/sites/.*/files/styles/ {
     try_files $uri @rewrite;
   }

   location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {
     expires max;
     log_not_found off;
   }
         
}
```

Does anyone know what i'm doing wrong. I need to 404 the cron.php file. Cause an anon user keeps updating our cron. I'm new to drupal with ngnix. So Any tips or help would be awesome.

---

