---
title: "computer stats ok for this?"
date: 2008-05-16
forum: Server Platforms
---

### Post by opportunity on 2008-05-16
Hi,

Is a PII 450 computer with 512MB ram ok enough for Squid proxy/webfilter + LDAP services for 25 computers or should i build a new $300 comp for it?

Also i dont like the idea of a non-transparent proxy where another point of fault for internet connectivity is created. is the above stats enough to run a transparant for 25 users?

---

### Post by SpaceTeddy on 2008-05-16
yes and no. It all depends on the load. How much traffic do you have going over the machine ? how often is the LDAP queried ?

In general - i'd say, try it. Install the thing, and just test it. If it is slow, buy the new comp, and copy over the configs (or just stuff the hd in the new computer). There is nothing preventing this :)


PS: I've been running router on pentium-pro 200 with 128M RAM for about 300 people. Also, i had an OpenVPN server for 75 User on a PII-350 with 256 Megs ram. All worked (the gateway is still running)

---

### Post by songshu on 2008-05-16
LDAP does not need much, the first bottleneck with squid would be the harddisk.

25 users? i would say go for it

---

