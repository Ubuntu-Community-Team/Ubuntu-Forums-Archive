---
title: "Webmin ssl access dying"
date: 2006-03-25
forum: Server Platforms
---

### Post by Gowator on 2006-03-25
I use Webmin to control a headless server and a while ago had problems, basicaly the icons taking forever to display.... I was a bit worried about beiung compromised but I reinstalled and everything has been fine for a while....
Then today again I get the same problem... 

Has anyone else experienced this... am I the only one and even better does anyone know why?  

Please try and respond quicky if you know anything because it worries me that someone may have compromised the server.

---

### Post by Gowator on 2006-04-03
For the benefit of others I finally solved this.

somehow an update had over written the resolv.conf and it was just the name resolution waiting to time out on each item.  

Does anyone know how to pin resolv.conf so it won't be over written?

---

