---
title: "Nginx 502 Bad Gateway"
date: 2015-06-30
forum: Server Platforms
---

### Post by jason_gibson2 on 2015-06-30
Redoing a few things on my server, having a touch of trouble. Freshly installed Ubuntu 14.04.2 server, all updates. I haven't tried to customize anything, this is what it installed as.

```
sudo nginx -t
nginx: [emerg] "user" directive is not allowed here in /etc/nginx/conf.d/kimchi.conf:23
nginx: configuration file /etc/nginx/nginx.conf test failed

```

```
# Project Kimchi
#
# Copyright IBM, Corp. 2014-2015
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
# 02110-1301  USA


# This is a template file to be used to generate a nginx
# proxy config file at kimchid script.


user  www-data;
worker_processes  1;


error_log  /var/log/nginx/error.log;


events {
    worker_connections  1024;
}


http {


    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';


    access_log  /var/log/nginx/access.log  main;
    sendfile    on;


    client_max_body_size 4194304k;


    # Timeout set to 10 minutes to avoid the 504 Gateway Timeout
    # when Kimchi is processing a request.
    proxy_connect_timeout       600;
    proxy_send_timeout          600;
    proxy_read_timeout          600;
    send_timeout                600;


    server {
        listen 8001 ssl;


        ssl_certificate /etc/kimchi/kimchi-cert.pem;
        ssl_certificate_key /etc/kimchi/kimchi-key.pem;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA:@STRENGTH';
        ssl_prefer_server_ciphers on;
        ssl_dhparam /etc/kimchi/dhparams.pem;


        add_header Strict-Transport-Security "max-age=31536000; includeSubdomains;";
        add_header X-Frame-Options DENY;
        add_header X-Content-Type-Options nosniff;
        add_header X-XSS-Protection "1; mode=block";


        location / {
            proxy_pass http://127.0.0.1:8010;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_redirect http://127.0.0.1:8010/ https://$host:8001/;
        }
    }

    server {
        listen 8000;
        rewrite ^/(.*)$ https://$host:8001/$1 redirect;
    }
}
```


```

sudo nginx -t -c /etc/nginx/conf.d/kimchi.conf
nginx: the configuration file /etc/nginx/conf.d/kimchi.conf syntax is ok
nginx: configuration file /etc/nginx/conf.d/kimchi.conf test is successful

```



```
user www-data;
worker_processes 4;
pid /run/nginx.pid;


events {
        worker_connections 768;
        # multi_accept on;
}


http {


        ##
        # Basic Settings
        ##


        sendfile on;
        tcp_nopush on;
        tcp_nodelay on;
        keepalive_timeout 65;
        types_hash_max_size 2048;
        # server_tokens off;


        # server_names_hash_bucket_size 64;
        # server_name_in_redirect off;


        include /etc/nginx/mime.types;
        default_type application/octet-stream;


        ##
        # Logging Settings
        ##


        access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;


        ##
        # Gzip Settings
        ##


        gzip on;
        gzip_disable "msie6";


        # gzip_vary on;
        # gzip_proxied any;
        # gzip_comp_level 6;
        # gzip_buffers 16 8k;
        # gzip_http_version 1.1;
        # gzip_types text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript;


        ##
        # nginx-naxsi config
        ##
        # Uncomment it if you installed nginx-naxsi
        ##


        #include /etc/nginx/naxsi_core.rules;


        ##
        # nginx-passenger config
        ##
        # Uncomment it if you installed nginx-passenger
        ##


        #passenger_root /usr;
        #passenger_ruby /usr/bin/ruby;


        ##
        # Virtual Host Configs
        ##


        include /etc/nginx/conf.d/*.conf;
        include /etc/nginx/sites-enabled/*;
}




#mail {
#       # See sample authentication script at:
#       # http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
#
#       # auth_http localhost/auth.php;
#       # pop3_capabilities "TOP" "USER";
#       # imap_capabilities "IMAP4rev1" "UIDPLUS";
#
#       server {
#               listen     localhost:110;
#               protocol   pop3;
#               proxy      on;
#       }
#
#       server {
#               listen     localhost:143;
#               protocol   imap;
#               proxy      on;
#       }
#}

```

---

