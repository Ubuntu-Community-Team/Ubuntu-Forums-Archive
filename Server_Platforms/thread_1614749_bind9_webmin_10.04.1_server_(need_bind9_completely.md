---
title: "bind9 webmin 10.04.1 server (need bind9 completely removed)"
date: 2010-11-06
forum: Server Platforms
---

### Post by shanep-server on 2010-11-06
I just installed bind9 on my ubuntu 10.04.1 server. I need to completely remove bind9 so I can configure it from webmin. I was messing with the bind9 files trying to set it up. I think using webmin will be easier but I need it completely removed first. How do I do that LOL I tried 

sudo apt-get remove bind9 

sudo apt-get install bind9 

but that didn't present me with the option to configure the new install from webmin.

I'm trying to setup bind9 on my server behind a router (w static ip) to host zone files for my dns / webserver so I can host a .info address on my home connection.

---

### Post by lisati on 2010-11-06
*Thread moved to **Server Platforms**.*
You might need to refresh Webmin's list of packages using the "Refresh modules" option.

---

