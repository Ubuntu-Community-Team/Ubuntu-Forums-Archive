---
title: "Raise parallel Active Internet connections"
date: 2012-10-08
forum: Server Platforms
---

### Post by terra3110 on 2012-10-08
Hi,

we run a service with a lot of parallel incoming TCP Connections. We handle Sockets by ourselfes, but the limitation seems me is the Ubuntu Kernel / Network itself. 

What is the limit of parallel Active Internet connections on Ubuntu and how i can raise it ?

Thank you for your help.

Frank

---

### Post by sandyd on 2012-10-08
> **terra3110 said:**
> Hi,

we run a service with a lot of parallel incoming TCP Connections. We handle Sockets by ourselfes, but the limitation seems me is the Ubuntu Kernel / Network itself. 

What is the limit of parallel Active Internet connections on Ubuntu and how i can raise it ?

Thank you for your help.

Frank

A few questions

a) Are you using a consumer-grade router? If you are, consumer grade routers can only handle so much tcp connections.

b) Have you checked how many connections are actually incoming?

c) What is the speed of your network connection?

---

### Post by TheFu on 2012-10-08
I think the settings you'll eventually touch are in /etc/sysctl.conf, but you probably want to do lots of reading about the pros/cons for changing any specific settings first.  **ethtool **is another tool to help manage this stuff.

Worst case, you'll have to rebuild the kernel with settings changed, but I doubt that is needed.

[http://stackoverflow.com/questions/651665/how-many-socket-connections-possible](http://stackoverflow.com/questions/651665/how-many-socket-connections-possible) discusses this same issue.  From the reading there, it seems more likely that you've hit the limit of open file descriptors either per user or per process, which can also be managed in the sysctl.conf file.

---

