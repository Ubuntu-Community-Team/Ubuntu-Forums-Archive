---
title: "apache2 service  configuration nighmarre"
date: 2015-11-22
forum: Server Platforms
---

### Post by hoboy on 2015-11-22
I have am application running on port 8080 on Ubuntu 14.04.
I want to setup a <VirtualHost *:80>
I am following this link [https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)
 when I start service apache2 i get error that port 80 is in used.
I have google for few days now.
tks

---

### Post by Lars Noodén on 2015-11-22
Check to see what is using port 80 with [netstat](http://manpages.ubuntu.com/manpages/trusty/en/man8/netstat.8.html)

```

sudo netstat -nltp

```

---

### Post by hoboy on 2015-11-22
Tks I will do that then what shall I look for as it is work computer I do not have access to it right now.

---

### Post by Lars Noodén on 2015-11-22
You should look for something like this, but with another process ID and maybe a different program name:

```

...
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
...
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2749/apache2        
...
tcp6       0      0 :::80                   :::*                    LISTEN      2749/apache2 
...

```

In the example, you can see that process 2749 is apache2 listening for IPv4 connections on all interfaces on port 80.  Same for IPv6

If something is hogging port 80 it will be listed there by netstat

---

### Post by cariboo on 2015-11-22
Moved to Server Platforms, as this is  really more a question about servers, rather than security.

---

