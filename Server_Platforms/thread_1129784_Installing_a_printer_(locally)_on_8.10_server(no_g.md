---
title: "Installing a printer (locally) on 8.10 server(no gui)"
date: 2009-04-19
forum: Server Platforms
---

### Post by Mr.N00bLaR on 2009-04-19
I downloaded 8.10 server a few days ago and it seems neat. I'm slowly learning how to make this old dell useful again :)

I have downloaded Samba and cups too. I have done some light seearching but I can't find out how I would actually go about installing/setting up a printer in the server version (WITHOUT GUI). 

I have been using Ubuntu dekstop distros for a few years now but this is my first real venture into the server side. I'm finding I know nothing ;)

I would like to first set this up with an HP PSC1315 that is connected via USB. Eventually I would like to add a printer in an office on the second floor but I need to first figure out how to get these crap routers to play with subnets.

EDIT: I have set up a static IP address btw and do not have a software firewall enabled.

---

### Post by Titan8990 on 2009-04-19
If you don't count a web interface, it would be the most common method for configuring cups. It can be accessed remotely so it won't matter if the server is headless.

In your web browser simply go to:


[http://SERVER:631/](http://SERVER:631/)

Where SERVER is the IP or hostname of your CUPS server.

---

### Post by Mr.N00bLaR on 2009-04-19
> **Titan8990 said:**
> If you don't count a web interface, it would be the most common method for configuring cups. It can be accessed remotely so it won't matter if the server is headless.

In your web browser simply go to:


[http://SERVER:631/](http://SERVER:631/)

Where SERVER is the IP or hostname of your CUPS server.

My server is setup at 192.168.1.146. When I go to [http://192.168.1.146:631](http://192.168.1.146:631) I get 403 Forbidden.
Does this make a difference if I do this from an XPH box? They are on the same network.

---

### Post by Mr.N00bLaR on 2009-04-20
Do I have to modify cupsd.conf to get this feature to work?

Somewhere in there I believe I have 
listen localhost:631
listen 192.168.1.146

---

