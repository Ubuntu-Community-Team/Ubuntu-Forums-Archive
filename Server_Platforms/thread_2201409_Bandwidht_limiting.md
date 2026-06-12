---
title: "Bandwidht limiting"
date: 2014-01-24
forum: Server Platforms
---

### Post by Rakesh_vijayan on 2014-01-24
Hi friends 

I am using pfsense as router and ubuntu 12.04 server edition configured as dhcp server .I wish to know how can I limit client systems bandwidth useage with the server .In my office . I dont want to use pfsense for this purpose . I am expecting your Ideas Please replay with your suggestion 


Thanks

---

### Post by sububtu on 2014-01-27
You can use delay pools in the sqiud.conf
what you nedd is to install squid.
Later just configure squid for bandwidth allocation
just check [this]("http://adeptus-mechanicus.com/codex/sqddelay/sqddelay.html")

---

