---
title: "ubuntu, LAMP, and web hosting"
date: 2009-08-10
forum: Server Platforms
---

### Post by fhunkydelix on 2009-08-10
hello, newbie here. i have an old desktop and installed ubuntu server with gnome and LAMP.  now i was wondering if i could host websites these outside my local area network, i am also behind a router.

---

### Post by LowSky on 2009-08-10
[http://digg.com/linux_unix/Host_Your_Own_Website_Using_Ubuntu_and_Your_DSL_or_Cable_Line](http://digg.com/linux_unix/Host_Your_Own_Website_Using_Ubuntu_and_Your_DSL_or_Cable_Line)

---

### Post by hessiess on 2009-08-10
Asuming your ISP isnt putting multiple customers behind a NAT router, you just need to set the port forwarding on your local router to point to the servers IP, then set up a dynamic DNS servace like dyndns. If your ISP is placing customers behind a NAT, the only option is to switch ISP or request a static IP.

If it is only running a server get rid of X11 and gnome, they do nothing but waste resources on a server.

---

