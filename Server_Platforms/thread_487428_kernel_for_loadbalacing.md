---
title: "kernel for loadbalacing"
date: 2007-06-29
forum: Server Platforms
---

### Post by Phulerock on 2007-06-29
Hello all,

I'm trying to configure 6.06, 6.10 as a loadbalacing build on shorewall, but have prolem with the kernel.

Exactly, I have:

root@ubuntu:~# cat /boot/config-2.6.17-10-server | grep CONFIG_IP_ADVANCED_ROUTER
CONFIG_IP_ADVANCED_ROUTER=y

root@ubuntu:~# shorewall show capabilities | grep "CONNMARK Target"
   CONNMARK Target: Not available

Loadbalancing can not work properly if CONNMARK not available. So how can I enable CONNMARK Target to iptables with CONNMARK.diff patch file ?

This file is described in [http://www.shorewall.net/MultiISP.html](http://www.shorewall.net/MultiISP.html)

---

