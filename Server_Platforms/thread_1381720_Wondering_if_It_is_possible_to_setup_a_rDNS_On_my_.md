---
title: "Wondering if It is possible to setup a rDNS On my Server"
date: 2010-01-15
forum: Server Platforms
---

### Post by Rob@ThePCWiz.info on 2010-01-15
I would like to say right now, I have Comcast for my ISP. I've seen people running servers on Comcast with a working DNS Reversal.
 I want this to mask my host to say "mydomain.com" rather than "##-##-###-##.hsda1.mi.comcast.net"

---

### Post by Roger_Smith on 2010-01-16
Call comcast and have them setup the rDNS for your IP.  Since they are authoritative for the ip space according ARIN they will have to do it. 

Unless you have your own subnet through them then you could request to host the rDNS but not sure what their policy is on it.

---

### Post by samosamo on 2010-01-16
It has nothing to do with "your server."  It has everything to do with your ISP.  Call them.

---

