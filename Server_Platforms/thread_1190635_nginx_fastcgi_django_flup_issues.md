---
title: "nginx fastcgi django flup issues"
date: 2009-06-18
forum: Server Platforms
---

### Post by vanderkerkoff on 2009-06-18
I'm on ubuntu hardy heron, 2.6.24-19-server 64 bit
nginx/0.5.33
django 1.0.2
Python 2.5.2
mysql 5.0.51a-3ubuntu5.4

Here's how I installed everything

[http://pastie.org/515408](http://pastie.org/515408)

Here's how I restart my django app

#!/bin/sh
if [ -f /var/www/django/conf/pid/$1.pid ]; then
        echo stopping $1 site
  kill `cat /var/www/django/conf/pid/$1.pid`
else
        echo $1 was not running
fi
/usr/bin/python /var/www/django//$1/manage.py runfcgi method=prefork minspare=1 maxspare=1 socket=/var/www/django/conf/sockets/$1.sock pidfile=/var/www/django/conf/pid/$1.pid
chmod 777 /var/www/django/conf/sockets/$1.sock

Here's the server directive in the /etc/nginx/sites-available/default file
server
{
    listen   80;
    server_name $1.com;
    access_log /var/www/django/log/access.log;
    error_log /var/www/django/log/error.log error;
    location /
    {
        fastcgi_pass unix:/var/www/django/conf/sockets/$1.sock;
        fastcgi_param SERVER_NAME $server_name;
        fastcgi_param SERVER_PORT $server_port;
        fastcgi_param SERVER_PROTOCOL $server_protocol;
        fastcgi_param PATH_INFO $fastcgi_script_name;
        fastcgi_param REQUEST_METHOD $request_method;
        fastcgi_param QUERY_STRING $query_string;
        fastcgi_param CONTENT_TYPE $content_type;
        fastcgi_param CONTENT_LENGTH $content_length;
        fastcgi_pass_header Authorization;
        fastcgi_intercept_errors off;
    }
}

Here's the /etc/nginx/nginx.conf
user username groupname;
worker_processes  6;
error_log  /var/log/nginx/error.log;
pid        /var/run/nginx.pid;
events {
    worker_connections  1024;
}
http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;
    access_log  /var/log/nginx/access.log;
    sendfile        on;
    #tcp_nopush     on;
    #keepalive_timeout  0;
    keepalive_timeout  65;
    tcp_nodelay        on;
    gzip  on;
    include /etc/nginx/sites-enabled/*;
}

Every now and then the web site returns a 502 bad gateway error. It's a very small site with hardly any traffic, so  resources are not a problem.  It usually happens immediately after I restart the site with the script above, I'm wondering if the restarting is a problem.

Here's what nginx says about it, running in error mode

2009/06/17 17:09:22 [error] 17715#0: *10888 connect() to unix:/var/www/django/conf/sockets/$1.sock failed (111: Connection refused) while connecting to upstream, client: 82.15.29.187, server: servername, URL: "/news/2009/jun/09/summer-fund-now-open-applications-continuing-stude/", upstream: "fastcgi://unix:/var/www/django/conf/sockets/$1.sock:", host: "servername", referrer: "http://somewebsite.com/"

I've switched file caching on now in django, so I'm not getting any errors any more, but I need to understand what is causing those errors, for my own sanity if nothing else

I can get any log information if needed, and perform any tests.  I think I've got something setup slightly wrong, but I have no idea what it is.

If anyone can shed any light on the topic I'd be most grateful.

V

---

### Post by mothes on 2009-06-29
use this how to 
[http://www.linuxspace.org/archives/1576]("http://www.linuxspace.org/archives/1576")

---

