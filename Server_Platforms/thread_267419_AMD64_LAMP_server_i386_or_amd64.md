---
title: "AMD64 LAMP server i386 or amd64?"
date: 2006-09-28
forum: Server Platforms
---

### Post by sitedesign on 2006-09-28
I am ordering another web server from the datacentre which will be loaded with Debian to start but I will then debootstrap Ubuntu server onto it using this guide:
[http://doc.ubuntu.com/ubuntu/install/i386/apds03.html](http://doc.ubuntu.com/ubuntu/install/i386/apds03.html)
then installing the lamp package.

The server will be used for Apache, Php and MySQL only, I'll use ssmtp for outgoing email to one of email servers.

What I need to know, should I use standard i386 or AMD64 version of the server?

Does anyone know of problems with LAMP server (6.06.1). The CPU in the server  will be an AMD64 3200+.

---

### Post by foxylad on 2006-09-29
I'm using the 6.06 amd64 lamp install on an opteron 248 machine. After lots of testing, this is now a production machine exposed to the internet, and I haven't had any issues at all.

---

