---
title: "Migrate Apache to Nginx"
date: 2015-07-27
forum: Server Platforms
---

### Post by grevan2 on 2015-07-27
[COLOR=#111111][FONT=Ubuntu]Ubuntu 12.04, i´m trying to migrate my site from Apache to Nginx but i´m getting a 403 Forbidden message. Can anyone help me? This is my "/etc/nginx/sites-available/default"
```
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]server {[/FONT][/COLOR]
   listen 80;

    root /srv/www;
    index index.php index.html index.htm;

    server_name mydomain.com www.mydomain.com;

    location / {
        try_files $uri $uri/ /index.php?q=$uri&$args;
    }

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass unix:/var/run/php5-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
    }

    location = /favicon.ico {
        log_not_found off;
        access_log off;
    }

    location = /robots.txt {
        allow all;
        log_not_found off;
        access_log off;
    }

    location ~ /\. {
        deny all;
    }

    location ~* /(?:uploads|files)/.*\.php$ {
        deny all;
    } [COLOR=#111111][FONT=Consolas]}[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
```
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]and here is the error.log:
```
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]2015/07/24 15:41:10 [error] 21834#0: *775 directory index of "/srv/www/" is forbidden, client: 108.162.210.206, server: mydomain.com, request: "GET / HTTP/1.1", host: "www.mydomain.com"[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
```
Can anyone help me?
[/FONT][/COLOR]

---

### Post by PaulW2U on 2015-07-27
*Thread moved to **Server Platforms**.*

---

### Post by CharlesA on 2015-07-27
Directory indexes are disabled by default in Nginx.

Make sure index.html/php/whatever exists in /srv/www/

---

