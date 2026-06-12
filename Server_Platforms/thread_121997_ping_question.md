---
title: "ping question"
date: 2006-01-26
forum: Server Platforms
---

### Post by rfruth on 2006-01-26
Firewall or no I can ping my Linksys router (192.168.1.1) but not my website (65.254.69.21 aka [http://www.rfruth.net](http://www.rfruth.net)) (([http://www.rfruth.net](http://www.rfruth.net) is there)) why is this ? =;

EDIT
Okay man ping reads "ping uses the ICMP protocol&#8217;s mandatory ECHO_REQUEST..."
so its good I can't ping rfruth.net ...

---

### Post by MJN on 2006-01-26
Whilst you say you can ping your router that's only the LAN side of it. Many routers are able to disable ICMP responses on their **WAN** side (i.e. your public 65. address) and it is common for this to be set as the default.

Mathew

---

### Post by rfruth on 2006-01-26
Thanks MJN, I do have block LAN request selected, that may be it [http://www.rfruth.net/resume/computers/breezy/linksysrf.png]("http://www.rfruth.net/resume/computers/breezy/linksysrf.png")

---

### Post by MJN on 2006-01-27
Yeah that's the bunny (although it's *W*AN address - I'm sure it was just a typo ;))
 
Mathew

---

