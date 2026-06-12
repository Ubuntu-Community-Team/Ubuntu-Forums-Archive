---
title: "problem with driver natsemi and atl1"
date: 2008-07-08
forum: Server Platforms
---

### Post by horeon on 2008-07-08
Hi,

I've three networkcards on my server. ( r8169, atl1, natsemi)
2 for LACP and 1 for another network.

But when server boot, it load natsemi before atl1 and theses two last cards won't work. :confused:
I must unload theses drivers to load atl1 first.

What can I do to load automatically in this order and someone know why I must do it?  
I tried to load on /etc/modules but it doesn't work too... :(

hardy 8.04.1 server AMD64
Kernel 2.6.24-19-xen

Thanks,
Franck

---

