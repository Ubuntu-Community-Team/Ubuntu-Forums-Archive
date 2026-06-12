---
title: "HAProxy 502-Bad Gateway erro"
date: 2014-09-17
forum: Server Platforms
---

### Post by imps on 2014-09-17
So I am using HAProxy in front of Jetty servlets.
The goal at the moment is just proof of concept and load and stress testing once everything's configured.
However I have a problem configuring haproxy. I know that it's not a problem with my application cause I have nginx(tengine) running and everything works properly. So it has to be something with the haproxy configuration or just the way haproxy works is not suitable for my needs.


So what my client tries to do is connect to haproxy using two different connections and keep them open.
1. Connect with a chunked streaming mode for upload.
2. Connect with a normal mode and establish a download channel.


Here's how my haproxy.conf file looks like:

```

    global
    log /dev/log    local0
    log /dev/log    local1 notice
    chroot /var/lib/haproxy
    stats socket /run/haproxy/admin.sock mode 660 level admin
    stats timeout 30s
    user haproxy
    group haproxy
    daemon


    # Default SSL material locations
    # ca-base /etc/ssl/certs
    # crt-base /etc/ssl/private


    # Default ciphers to use on SSL-enabled listening sockets.
    # For more information, see ciphers(1SSL).
    ssl-default-bind-ciphers kEECDH+aRSA+AES:kRSA+AES:+AES256:RC4-SHA:!kEDH:!LOW:!EXP:!MD5:!aNULL:!eNULL
    maxconn 2048


    defaults
    log    global
    mode    http
    option forwardfor
    option http-server-close
    option    httplog
    option    dontlognull
    timeout connect 5000
    timeout client  50000
    timeout server  50000
    errorfile 400 /etc/haproxy/errors/400.http
    errorfile 403 /etc/haproxy/errors/403.http
    errorfile 408 /etc/haproxy/errors/408.http
    errorfile 500 /etc/haproxy/errors/500.http
    errorfile 502 /etc/haproxy/errors/502.http
    errorfile 503 /etc/haproxy/errors/503.http
    errorfile 504 /etc/haproxy/errors/504.http
    stats enable
    stats uri /stats
    stats realm Haproxy\ Statistics
    stats auth user:password


    frontend www-http
       bind *:80
       reqadd X-Forwarded-Proto:\ http
       default_backend www-backend


    frontend www-https
       bind *:443 ssl crt /etc/haproxy/server.pem
       reqadd X-Forwarded-Proto:\ https
       default_backend www-backend


    backend www-backend
        redirect scheme https if !{ ssl_fc }
        server www-1 localhost:8080 check maxconn 2048

```

And here's what my logs say when I try to access port 443:

```
Sep 17 11:10:18 xxxxx-pc haproxy[15993]: 127.0.0.1:32875 [17/Sep/2014:11:10:18.464] www-  https~ www-backend/www-1 0/0/0/-1/1 502 212 - - PH-- 0/0/0/0/0 0/0 "GET /test HTTP/1.1"

```

Any ideas what the problem might be?
An issue with the configuration or ?


Thanks.

---

