---
title: "Ubuntu Change the Tomcat Port From 8080 to 80"
date: 2013-11-12
forum: Server Platforms
---

### Post by libranjie2 on 2013-11-12
Hello, 

I'd like to install the smrtanalysis 2.1.1 ([http://pacificbiosciences.github.io/DevNet/](http://pacificbiosciences.github.io/DevNet/)) on my Ubuntu server.
The default port for tomcat is 8080, this should work. However when I change the port as 80, the web
server cannot connected.
The tomcat and apache is included in the package of smrtanalysis, (apache-tomcat-7.0.23).

How should I change or configure to make the webserver workable?
Within the log file, error is:
```
java.net.BindException: Permission denied <null>:80
```

---

### Post by libranjie on 2013-11-13
iptables -t nat -A OUTPUT -d localhost -p tcp --dport 80 -j REDIRECT --to-ports 8080
iptables -t nat -A OUTPUT -d `hostname` -p tcp --dport 80 -j REDIRECT --to-ports 8080
iptables -t nat -A PREROUTING -d `hostname` -p tcp --dport 80 -j REDIRECT --to-ports 8080

---

