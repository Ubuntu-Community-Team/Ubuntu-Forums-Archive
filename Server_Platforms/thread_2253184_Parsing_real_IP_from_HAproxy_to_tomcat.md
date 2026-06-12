---
title: "Parsing real IP from HAproxy to tomcat"
date: 2014-11-17
forum: Server Platforms
---

### Post by andrew102 on 2014-11-17
Hi,

So I'm having this issue that when I check out the tomcat access logs, all I see is the IP of the load balancer of HAproxy.

I'm getting a new instance of HAproxy up and running. I'm trying  different combinations of option forwardfor , reqidel X-Forwarded-For ,  reqidel X-Real-IP, reqadd

Unfortunately I still haven't been able to see the actual IP of the end-user appear in the tomcat logs.

So my question is, do I need to enable something in tomcat ? or am I just not getting HAproxy to begin with....



Here's the relevant parts of haproxy.cfg


```

defaults
        option  forwardfor except 127.0.0.1
        option  http-server-close

frontend www-http
        bind 0.0.0.0:80
        reqidel ^X-Real-IP:
        reqidel ^X-Forwarded-Proto:.*
        reqadd X-Forwarded-Proto:\ http
        reqadd X-Real-IP

frontend www-https
        bind 0.0.0.0:443 ssl crt /xxxxxxx
        reqidel ^X-Forwarded-For:.*
        reqidel ^X-Real-IP:
        reqadd X-Forward-Proto:\ https
        reqadd X-Real-IPbackend tomcat

backend tomcat
        balance roundrobin
        appsession JSESSIONID len 52 timeout 30m
        #option httpchk HEAD /check.txt HTTP/1.0
        option http-server-close
        option forwardfor header X-Real-IP   #### Think this is incorrect



```

---

