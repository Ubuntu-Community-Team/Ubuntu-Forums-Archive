---
title: "setting up home web-server with nginx in ubuntu 11.04"
date: 2012-06-15
forum: Server Platforms
---

### Post by deewakar on 2012-06-15
Hello, everyone.
I am trying to setup a web server at my home pc which has ubuntu 11.04 installed.
I am using nginx and have a domain name from no-ip called myboringsite.zapto.org.
Here's my /etc/nginx/nginx.conf file:
```
user www-data;
worker_processes 4;
pid /var/run/nginx.pid;

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
    # Virtual Host Configs
    ##

    include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;
}


#mail {
#    # See sample authentication script at:
#    # http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
# 
#    # auth_http localhost/auth.php;
#    # pop3_capabilities "TOP" "USER";
#    # imap_capabilities "IMAP4rev1" "UIDPLUS";
# 
#    server {
#        listen     localhost:110;
#        protocol   pop3;
#        proxy      on;
#    }
# 
#    server {
#        listen     localhost:143;
#        protocol   imap;
#        proxy      on;
#    }
#}
```and my /etc/nginx/sites-enabled/default file:
```
server
{    
    listen         8080;
    server_name    myboringsite.zapto.org;
 
    access_log /usr/share/nginx/www/myboringsite.zapto.org/logs/access.log;
    error_log /usr/share/nginx/www/myboringsite.zapto.org/logs/error.log;
 
    root /usr/share/nginx/www/myboringsite.zapto.org/public_html/;
    index index.htm index.html index.php;
 
    error_page  401  /errorpages/401.html;
    error_page  403  /errorpages/403.html;
    error_page  404  /errorpages/404.html;
    error_page  500 502 503 504  /errorpages/500.html;
 
    location /
    {
        try_files $uri $uri/ /index.html?$args;
    }
 
    # rewrite adminpanel to use https
    rewrite ^/adminpanel(.*)$ https://$host$uri permanent;
 
    # Add trailing slash to */wp-admin requests. Needed if wordpress is installed later
    rewrite /wp-admin$ $scheme://$host$uri/ permanent;
 
    # Directives to send expires headers
    location ~* \.(js|css|png|jpg|jpeg|gif|ico)$
    {
        expires 30d;
    }
 
    # Deny all attempts to access hidden files such as .htaccess, .htpasswd
    location ~ /\.
    {
        deny all;
        access_log off;
        log_not_found off;
    }
 
    location ~ \.php$
    {
        try_files $uri =404;
        include /etc/nginx/fastcgi_params;
        fastcgi_pass 127.0.0.1:6000;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME /usr/share/nginx/www/myboringsite.zapto.org/public_html$fastcgi_script_name;
    }
}
```Whenever I type in myboringsite.zapto.org into my address bar, it asks for username
 and password for my router settings.So What am I missing. DO I need to forward ports?
and here's the nmap scan results:
```
~$ nmap myboringsite.zapto.org

Starting Nmap 5.21 ( http://nmap.org ) at 2012-06-15 13:11 NPT
Nmap scan report for myboringsite.zapto.org (49.244.240.157)
Host is up (0.0033s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
23/tcp   open  telnet
80/tcp   open  http
2800/tcp open  unknown
8008/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 1.03 seconds

```And one important question, the DDNS option in my router is disabled and even if you
 enable it, it says that it only supports dyndns.org and TZO.com --but mine is no-ip.
 Is that the problem?

---

### Post by deewakar on 2012-06-16
I've never done this kind of thing before and kind of feeling hopeless.  If anybody have done such thing or are experienced in it , can you share it with me please.  I  just need to setup my home pc as a web server to host some static html pages . It need not be with nginx, I just started with it (since I had to start somewhere), i can use apache or something else. I just need some guidelines, that's all.

---

### Post by N0oki3 on 2012-06-16
I've never used nginx. For apache, here you have [simple guide](https://help.ubuntu.com/8.04/serverguide/httpd.html)

---

