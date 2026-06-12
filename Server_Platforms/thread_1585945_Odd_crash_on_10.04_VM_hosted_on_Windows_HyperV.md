---
title: "Odd crash on 10.04 VM hosted on Windows HyperV"
date: 2010-10-01
forum: Server Platforms
---

### Post by danielhedley on 2010-10-01
For no apparent reason an Ubuntu 10.04 server VM hosted on Windows HyperV just ground to a complete halt the other day; the console was completely unresponsive and only a "hard" reset brought it back to life.

In /var/log/messages are lots of entries at the time of the crash along the lines of:

```
Sep 28 06:59:02 vJustisKB kernel: [512997.483280] BLKVSC_DRV: CHS (41610, 16, 63)
Sep 28 06:59:02 vJustisKB kernel: [512997.483392] BLKVSC_DRV: CHS (41610, 16, 63)
Sep 28 06:59:02 vJustisKB kernel: [512997.483401] BLKVSC_DRV: CHS (41610, 16, 63)
```

I've been Googling around and have not been able to find a useful explanation of what's going on.

Am I missing something?  Any Ubuntu Gods able to shed light?

Many thanks for your help.

---

### Post by abix_adam_pl on 2010-10-01
CHS (41610, 16, 63)

That looks like a Cylinder , Head, Sector in disk. Maybe something with SATA/SCSI Subsystem ?

Adam

---

### Post by danielhedley on 2010-10-01
That was my thought too, although of course being a VM there is no physical disk.

fsck checks out too.  Hmmm.

---

### Post by Inigo Montoya on 2011-05-26
any news on this topic? i seem to have a same/similar problem.
my setup:
Hyper-V  2008 R2 SP1
Ubuntu Server 11.04 (but had the same issue with 10.04 LTS)

---

### Post by stevellion on 2011-07-22
Me too - same problem.

---

### Post by stevellion on 2011-07-22
Anyone think it is related to this?

[http://ns3.spinics.net/lists/linux-virtualization/msg12861.html](http://ns3.spinics.net/lists/linux-virtualization/msg12861.html)

---

