---
title: "new install on soft-raid 1 boots degraded"
date: 2012-01-02
forum: Server Platforms
---

### Post by jeliocranch on 2012-01-02
Just installed 11.10 server on a newly built system (home-use, vm host).  System is installed on two 500 GB HDD's in software raid 1, but booting takes several minutes, while normal boot time for this hardware+11.10 desktop w/o raid has been 30 seconds or so.  

when server does come up, I see a message about booting in degraded mode, suggesting there may have been a drive failure.  

fdisk shows the drives, configured in raid 1.

admittedly, the drives are different makes and though the speeds are similar, they do differ a bit.

booting to a live cd, I can check drive health/status which looks good.

I've done this install several times with slight variations in attempt to fix it, but no change.  Any help?

---

### Post by rsvancara on 2012-01-02
What does /cat/proc/mdstat show you.  

Also would be a good idea to do a

dmesg |grep md

Thanks

---

