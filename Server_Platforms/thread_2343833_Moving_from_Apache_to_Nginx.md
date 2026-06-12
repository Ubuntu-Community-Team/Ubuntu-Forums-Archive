---
title: "Moving from Apache to Nginx"
date: 2016-11-19
forum: Server Platforms
---

### Post by courtney2 on 2016-11-19
Hey everyone,

I have an Apache wordpress web server I am moving to nginx since I hear nginx handles memory better (and supposedly) faster when dishing out static content. I have a Let's Encrypt certificate already set up for Apache, and I have nginx pointing to all the right stuff. I followed a couple tutorials and I'm not getting any errors now when starting nginx. My only problem now is I am getting a 502 Bad Gateway error. I hear that can happen when using php-fpm (which I am) and sometimes being behind a reverse proxy (which mine is). My reverse proxy is an HAProxy setup. My Apache server worked just fine before, so I believe this is just my inexperience with nginx. Here are my configurations in my sites-enabled directory for nginx:

```


server_tokens off;

server {
        listen 80;

        server_name [mywebsite.com] www.[mywebsite.com];
        return 301 https://$server_name$request_uri;
}

server {
        listen 443;
        #listen [::]:443 ssl;

        #include snippets/ssl-[mywebsite.com].conf;
        #include snippets/ssl-params.conf;

        root /var/www/html;
        index index.php index.html index.htm;

        server_name [mywebsite.com] www.[mywebsite.com];

        ssl on;
        ssl_certificate /etc/letsencrypt/live/[mywebsite.com]/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/[mywebsite.com]/privkey.pem;



        ssl_session_timeout 1d;
        ssl_session_cache shared:SSL:50m;
        ssl_session_tickets off;

        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;
        ssl_dhparam /etc/ssl/certs/dhparam.pem;
        ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA';

        # OCSP Stapling ---
        # fetch OCSP records from URL in ssl_certificate and cache them
        ssl_stapling on;
        ssl_stapling_verify on;

        # HSTS (ngx_http_headers_module is required) (15768000 seconds = 6 months)
        add_header Strict-Transport-Security max-age=15768000;



        #location ~ /.well-known {
        #       allow all;
        #}

        location / {
                try_files $uri $uri/ /index.php?q=$uri&$args;
        }

        location ~ \.php$ {
                try_files $uri =404;
                fastcgi_pass unix:/var/run/php7.0-fpm.sock;
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
        }
}


```

Am I missing anything? Keep in mind this is just a wordpress server on Ubuntu Server 16.04

---

### Post by courtney2 on 2016-11-19
Okay progress was made:

I found my error in my enabled webpage. I would pointing to a bad php-fpm socket (wrong path). So now I just can't get a webpage, just a white page

---

### Post by courtney2 on 2016-11-19
[FONT=arial]I started by installing nginx, and php7.0-fpm. I then disabled the Apache web server.

Then I edited this file: 
[/FONT][FONT=arial]/etc/php5/fpm/php.ini

So the line that says ";cgi.fix_pathinfo=1" is now "cgi.fix_pathinfo=0"

Next I went to /etc/php/7.0/fpm/pool.d/www.conf[/FONT][FONT=arial]And changed the "listen =" line to "listen = /var/run/php/php7.0-fpm.sock"

Restarted php-fpm -- " sudo service php7.0-fpm restart

Finally, I added the config file I have below to /etc/nginx/sites-available (I justed changed the contents of default) and then started the nginx server

Fixed configs. I had a bad unix socket path to php-fpm and I included "include /etc/nginx/fastcgi.conf;" in my "location ~ \.php$" block. 

```
server_tokens off;

server {
        listen 80;

        server_name [mywebsite.com] www.[mywebsite.com];
        return 301 https://$server_name$request_uri;
}

server {
        listen 443;
        #listen [::]:443 ssl;

        #include snippets/ssl-[mywebsite.com].conf;
        #include snippets/ssl-params.conf;

        root /var/www/html;
        index index.php index.html index.htm;

        server_name [mywebsite.com] www.[mywebsite.com];

        ssl on;
        ssl_certificate /etc/letsencrypt/live/[mywebsite.com]/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/[mywebsite.com]/privkey.pem;



        ssl_session_timeout 1d;
        ssl_session_cache shared:SSL:50m;
        ssl_session_tickets off;

        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;
        ssl_dhparam /etc/ssl/certs/dhparam.pem;
        ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA';

        # OCSP Stapling ---
        # fetch OCSP records from URL in ssl_certificate and cache them
        ssl_stapling on;
        ssl_stapling_verify on;

        # HSTS (ngx_http_headers_module is required) (15768000 seconds = 6 months)
        add_header Strict-Transport-Security max-age=15768000;



        #location ~ /.well-known {
        #       allow all;
        #}

        location / {
                try_files $uri $uri/ /index.php?q=$uri&$args;
        }

        location ~ \.php$ {
                include /etc/nginx/fastcgi.conf;
                try_files $uri =404;
                fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
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
        }
}


```

This is a very abridged version of me doing the transition, but I hope it helps
[/FONT]

---

