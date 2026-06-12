---
title: "Ubuntu Server 13.04"
date: 2013-07-20
forum: Server Platforms
---

### Post by dj722000 on 2013-07-20
Hey guys. I was wondering about something with Ubuntu server. I have a router coming in and wifi going out to all my laptops. The router has to stay in its place. I also have in my possesion a Netgear Range Extender WN2000RPT and a simple desktop server I made. I want the server in  spare room away from the router. Can I use the range Extender to get an internet connection to the desktop via lan connection? I know it should be hard wired, but right at the moment, it isnt happening. I just want to use the server. So here is the setup I guess;                Router - WIFI - Laptops
                                                       |
                                                     WIFI / Netgear Range Extender - Lan connection to etho on Desktop Ubuntu Server 13.04

Make sense? I guess I am trying to get the server back on the internet using WIFI through the range Extender. Is this even possible? Sounds plausible. I know it will be slow. but for now it will do. I am pretty knew on the server side, so please be paitent. Thakns.

---

### Post by david83 on 2013-07-30
It makes sense, but I don't think this will work ...

---

### Post by newbie-user on 2013-07-30
Depends if you can use the range extender in a bridged mode. I have a TL-WR702N that I use as a bridge for PXE booting clients around my house.

---

### Post by SeijiSensei on 2013-07-31
If the server only needs to handle a limited range of services, you're probably better off using port forwarding from your router back to the server.  Any arrangement that puts your server behind a masquerading router will prevent it from being visible on the Internet.

---

