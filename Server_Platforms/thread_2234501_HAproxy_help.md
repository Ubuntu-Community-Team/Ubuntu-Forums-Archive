---
title: "HAproxy help"
date: 2014-07-15
forum: Server Platforms
---

### Post by ionbasa on 2014-07-15
So recently I have been working on setting up my own webserver. I decided to use Ubuntu 14.04, and use Apache to server my web pages.
Recently a friend asked if he could also host some pages. I ended up using KVM to create him a debian guest. The guest has an actual ip (not NATed) on my subnet.

Now I need some help on setting up HAproxy to reverse proxy http requests based on domain names. It is supported, but I am unable to get it to work with my configuration.

Here is my configuration file:
```

global
    log 127.0.0.1 local0 notice
    maxconn 4096
    user haproxy
    group haproxy
    daemon

defaults
    log global
    mode http
    option httplog
    option dontlognull
    option forwardfor
    option http-server-close
    stats enable
    stats auth someuser:somepassword
    stats uri /haproxyStats

frontend http-in
    bind 192.168.1.17:80
    # Define hosts
    acl host_charlie hdr_end(host) -i test.no-ip.biz
    acl host_john hdr_end(host) -i example.noip.me
    # figure out which one to use
    use_backend starwarsman13 if host_charlie
    use_backend college if host_john

backend starwarsman13
    balance leastconn
    option httpclose
    option forwardfor
    cookie JSESSIONID prefix
    server Local 192.168.1.17:8080 cookie Local

backend college
    balance leastconn
    option httpclose
    option forwardfor
    cookie JSESSIONID prefix
    server Local 192.168.1.11:80 cookie Local

```
Something interesting though is that I cannot access HAproxy's statistics file, and I also get no alerts on running the startup script, only a few warning, and it starts up correctly.

---

