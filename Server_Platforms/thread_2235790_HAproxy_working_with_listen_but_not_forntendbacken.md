---
title: "HAproxy working with listen but not forntend/backend"
date: 2014-07-22
forum: Server Platforms
---

### Post by chris267 on 2014-07-22
I am about to pull my hair out with this.  For some time now we have been using a simple config with HAproxy.  It was using the listen method in TCP mode and routes traffic to two different servers.  It works fine except the check method was only able to check if the web server was up and serving request ok.  In this case if our Windows IIS server/service was working.  We have several web apps on the server and if one of them is not started or hung then HAproxy still routes traffic as it was only checking that IIS was serving ok.  We needed to build a more logical config that could test individual URLs for health checks as well as do HTTP to HTTPS redirects.  

The old config worked fine with our sites minus the health check issue.  The new config works perfectly for the health check issue but certain tasks in our website/webapp just hang and never finish or go to an error message.  The old config did not cause this.  If I access the site via localhost or its direct IP bypassing HAproxy it still works fine.

Running HAproxy 1.5.2
Ubuntu 14.04

OLD CONFIG

```
global
    log 127.0.0.1    local0
    log 127.0.0.1    local1 notice
    #log loghost    local0 info
    maxconn 2048
    #chroot /usr/share/haproxy
    user haproxy
    group haproxy
    daemon
    #debug
    #quiet

defaults
    log    global
    mode    http
    option    httplog
    option    dontlognull
    retries    3
    option redispatch
    maxconn    2048
    timeout connect    5000
    timeout client    5000

listen    MP-DEV-WEBFARM 192.168.0.128:443
    mode    tcp
    option  tcpka
    balance    source
    option  ssl-hello-chk
    option  httpchk HEAD /check.txt HTTP/1.0
    option  tcplog
    server    MP-DEV-WEBFARM-1 192.168.0.120:443 weight 1 check port 80 inter 2000 fall 2 rise 3
    server    MP-DEV-WEBFARM-2 192.168.0.121:443 weight 1 check port 80 inter 2000 fall 2 rise 3
    option  abortonclose
    timeout server    120000

listen stats 0.0.0.0:9600
    mode http
    balance
    stats uri /haproxy_stats        
    stats realm HAProxy\ Statistics 
    stats auth admin:******
    stats admin if TRUE
```


NEW CONFIG

```
global
    log 127.0.0.1    local0
    log 127.0.0.1    local1 notice
    #log loghost    local0 info
    maxconn 2048
    #chroot /usr/share/haproxy
    user haproxy
    group haproxy
    daemon
    #debug
    #quiet
    tune.ssl.default-dh-param 4096

defaults
    log    global
    mode    http
    option    httplog
    option    dontlognull
    retries    3
    option redispatch
    maxconn    2048
    timeout connect    5000
    timeout client    50000
    timeout server    120000
    option forwardfor
    option http-server-close

frontend www-http-dev-webfarm
   bind 192.168.0.128:80
   reqadd X-Forwarded-Proto:\ http
   acl mpi_dev url_dir /mpi_dev/
   use_backend www-backend-dev-webfarm-mpi_dev if mpi_dev
   default_backend www-backend-dev-webfarm

frontend www-https-dev-webfarm
   bind 192.168.0.128:443 ssl crt /etc/ssl/private/domain.pem
   reqadd X-Forwarded-Proto:\ https
   acl mpi_dev url_dir /mpi_dev/
   use_backend www-backend-dev-webfarm-mpi_dev if mpi_dev
   default_backend www-backend-dev-webfarm

backend www-backend-dev-webfarm
   redirect scheme https if !{ ssl_fc }
   option httpchk HEAD /check.txt HTTP/1.0
   option tcpka
   option abortonclose
   balance source
   errorfile 503 /etc/haproxy/errors/503-MP.http
   server MP-DEV-WEBFARM-1 192.168.0.120:80 weight 1 check port 80 inter 2000 fall 2 rise 3
   server MP-DEV-WEBFARM-2 192.168.0.121:80 weight 1 check port 80 inter 2000 fall 2 rise 3

backend www-backend-dev-webfarm-mpi_dev
   redirect scheme https if !{ ssl_fc }
   option http-server-close
   option forwardfor
   option httpchk GET /mpi_dev/wc.dll?UCoDASrv~mydesktop HTTP/1.0
   option tcpka
   option abortonclose
   balance source
   errorfile 503 /etc/haproxy/errors/503-MP.http
   server MP-DEV-WEBFARM-1 192.168.0.120:80 weight 1 check port 80 inter 2000 fall 2 rise 3
   server MP-DEV-WEBFARM-2 192.168.0.121:80 weight 1 check port 80 inter 2000 fall 2 rise 3

listen stats 0.0.0.0:9600
    mode http
    balance
    stats uri /haproxy_stats        
    stats realm HAProxy\ Statistics 
    stats auth admin:******
    stats admin if TRUE

```

With the new config certain pages/actions in our webapp just hang and do nothing.  

I was looking at FireBug in my browser and HAproxy logs and it just looks like HAproxy just thinks the page is done loading and stops when it's not done.  Any help would be great.  

Thanks

---

