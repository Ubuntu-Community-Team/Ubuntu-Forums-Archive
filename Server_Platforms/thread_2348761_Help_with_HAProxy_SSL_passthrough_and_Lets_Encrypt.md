---
title: "Help with HAProxy SSL passthrough and Lets Encrypt"
date: 2017-01-07
forum: Server Platforms
---

### Post by courtney2 on 2017-01-07
I'm having an impossible time getting SSL certs on my servers sitting behind HAProxy. I have ports 80 and 443 forwarded to HAProxy, and I have 2 web services behind that (also using ports 80 and 443) which need certs. I don't want to terminate at HAProxy because I want internal network security too. My issue is I'm failing the TLS-SNI-01 challenge on both the web servers. One server is using Apache and the other is using Nginx. They both have domain names that I have set up with duckdns. I have received certificates before on these very same servers but all of a sudden I no longer have success. I don't believe it to be a server issue, but an issue with HAProxy configurations.

HAProxy configs:

```

global
        #chroot /var/lib/haproxy
        #log /dev/log   local0
        #log /dev/log   local1 notice
        ulimit-n        65536
        log   127.0.0.1 local1 info notice
        stats socket /run/haproxy/admin.sock mode 660 level admin
        stats timeout 30s
        maxconn 4096
        user haproxy
        group haproxy
        daemon


defaults
        log     global
        mode    tcp
        option  tcplog
        option  dontlognull
        timeout connect 15s
        timeout client  15s
        timeout server  15s
        errorfile 400 /etc/haproxy/errors/400.http
        errorfile 403 /etc/haproxy/errors/403.http
        errorfile 408 /etc/haproxy/errors/408.http
        errorfile 500 /etc/haproxy/errors/500.http
        errorfile 502 /etc/haproxy/errors/502.http
        errorfile 503 /etc/haproxy/errors/503.http
        errorfile 504 /etc/haproxy/errors/504.http


frontend localhost80
        bind *:80
        mode http
        redirect scheme https code 301 if !{ ssl_fc }

frontend localhost443
        bind *:443
        option tcplog
        mode tcp

        #acl tls req.ssl_hello_type 1

        tcp-request inspect-delay 15s
        tcp-request content accept if { req_ssl_hello_type 1 }

        acl is_wordpress req_ssl_sni -i domain2.duckdns.org   #10.0.0.165
        acl is_nextcloud req_ssl_sni -i www.domain1.duckdns.org                #10.0.0.160
        acl is_nextcloud2 req.ssl_sni -i domain1.duckdns.org

        use_backend nextcloud_cluster if is_nextcloud
        use_backend nextcloud_cluster if is_nextcloud2
        use_backend wordpress_cluster if is_wordpress


backend wordpress_cluster
        mode tcp

        stick-table type binary len 32 size 30k expire 30m

        acl clienthello req_ssl_hello_type 1
        acl serverhello rep_ssl_hello_type 2

        tcp-request inspect-delay 5s
        tcp-request content accept if clienthello

        tcp-response content accept if serverhello

        stick on payload_lv(43,1) if clienthello
        stick store-response payload_lv(43,1) if serverhello


        option ssl-hello-chk

        server is_wordpress 10.0.0.165:443 check


backend nextcloud_cluster
        mode tcp

        stick-table type binary len 32 size 30k expire 30m


        acl clienthello req_ssl_hello_type 1
        acl serverhello rep_ssl_hello_type 2

        tcp-request inspect-delay 5s
        tcp-request content accept if clienthello

        tcp-response content accept if serverhello

        stick on payload_lv(43,1) if clienthello
        stick store-response payload_lv(43,1) if serverhello

        option ssl-hello-chk

        server is_nextcloud 10.0.0.160:443 check



```

My Apache server configs:
```
<VirtualHost *:80>

        ServerName www.domain1.duckdns.org
        ServerAlias domain1.duckdns.org

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html


        Redirect permanent / https://www.domain1.duckdns.org/

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined



Alias /nextcloud "/var/www/html/"

<Directory /var/www/html>
  Options +FollowSymlinks
  AllowOverride All

  <Ifmodule mod_dav.c>
    Dav off
  </Ifmodule>

  SetEnv HOME /var/www/html
  SetEnv HTTP_HOME /var/www/html

</Directory>




    <Location /webrtc>
        ProxyPass http://127.0.0.1:8080/webrtc
        ProxyPassReverse /webrtc
    </Location>

    <Location /webrtc/ws>
        ProxyPass ws://127.0.0.1:8080/webrtc/ws
    </Location>

    ProxyVia On
    ProxyPreserveHost On
    RequestHeader set X-Forwarded-Proto 'https' env=HTTPS


RewriteEngine on
RewriteCond %{SERVER_NAME} =domain1.duckdns.org [OR]
RewriteCond %{SERVER_NAME} =www.domain1.duckdns.org
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,QSA,R=permanent]
</VirtualHost>



```

Configurations for Nginx web server:
```

server_tokens off;

server {
        listen 80;

        #error_page 401 403 40 /404.html;

        root /var/www/html;
        index index.php index.html index.htm;

        server_name domain2.duckdns.org;
        return 301 https://$server_name$request_uri;
}

server {
        listen 443 ssl;

        error_page 401 403 404 /404.html;

        root /var/www/html;
        index index.php index.html index.htm;

        server_name domain2.duckdns.org;

        ssl on;
        ssl_certificate /etc/letsencrypt/live/domain2.duckdns.org/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/domain2.duckdns.org/privkey.pem;


        ssl_session_timeout 1d;
        ssl_session_cache shared:SSL:50m;
        ssl_session_tickets off;

        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;
        ssl_dhparam /etc/ssl/certs/dhparam.pem;
        ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA';

        # OCSP Stapling 
        # fetch OCSP records from URL in ssl_certificate and cache them
        ssl_stapling on;
        ssl_stapling_verify on;


        add_header Strict-Transport-Security "max-age=15768000; includeSubdomains; preload";


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

---

### Post by courtney2 on 2017-01-12
Can I get an answer if I change HAProxy to Nginx? I need something. I haven't had an answer that has helped in over a month

---

