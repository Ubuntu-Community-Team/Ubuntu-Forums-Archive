---
title: "Apache2 not working, port 81 open on router, no access from outside of LAN, help?"
date: 2009-08-25
forum: Server Platforms
---

### Post by Perronah on 2009-08-25
I'm running apache 2 on Ubuntu Jaunty, and my router is configured to open up port 81.

My computers IP is 192.168.2.12
And whatismyip.com says 70.31.29.59 or in other words my routers IP.

Now when I run [http://192.168.2.12:81](http://192.168.2.12:81) everything works fine, but since I want my site accessed from outside I need people to access the http server from 70.31.29.59, but when I run [http://70.31.29.59:81](http://70.31.29.59:81) I get no connection, even though my router has an open port 81.

I have tried many different configurations in my virtual server settings page.  I also can not ssh into my box outside of my LAN.  Inside is of course no problem.  Can Linux somehow be blocking all outside traffic?  My router has multiple ports open for my web and ssh servers.

Any help would be most appreciated.

---

### Post by cdenley on 2009-08-25
> **Perronah said:**
> 
Can Linux somehow be blocking all outside traffic?
It can, but isn't configured to do so by default. I'm guessing you are attempting to access [http://70.31.29.59:81/](http://70.31.29.59:81/) from within your local network, which some routers do not handle. It is currently working for connections made from outside your network (for me). Some routers may have a setting to fix this (I think it was called "local loopback"), some may require a firmware upgrade, some simply will not port forward LAN traffic.

---

