---
title: "transmission won't work in ubuntu 9.10 virtualbox appliance"
date: 2010-10-06
forum: Virtualisation
---

### Post by waffletten on 2010-10-06
Having a problem downloading torrents with transmission in a virtualized (virtualbox) ubuntu 9.10 appliance.  The appliance has the ethernet bridged to the host OS (windows 7 X64) and I have tested and verified that transmission port is forwarded from router to appliance and is open.  Everything else works great but I can't seem to get this accomplished.  Maybe I am missing something in the windows 7 host OS settings?  Anyone else have any experiences with this?

---

### Post by HermanAB on 2010-10-08
Howdy,

I think torrents use multiple ports, so you got to forward a range of ports:
[http://www.dessent.net/btfaq/](http://www.dessent.net/btfaq/)

---

### Post by waffletten on 2010-10-08
I have this appliance set up with the exact same settings I use for three other physical computers here, all running ubuntu and transmission successfully.  I have been looking at this for a while and am still scratching my head.

All ports are correct and ufw disabled on the appliance.  I am using a non-standard port for transmission and port forwarding from a router.  Anyone else?

Does this have something to do with the isolation of rings with virtualization? Does the separation isolate the virtual NIC from the hardware NIC and prevent torrenting?

Any ideas? I am stumped.

---

