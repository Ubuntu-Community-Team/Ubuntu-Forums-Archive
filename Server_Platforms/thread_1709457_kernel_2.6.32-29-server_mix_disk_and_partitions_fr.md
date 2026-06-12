---
title: "kernel 2.6.32-29-server mix disk and partitions from Raid10 array"
date: 2011-03-18
forum: Server Platforms
---

### Post by zeroheure on 2011-03-18
Hello
big problem here. Ona DELL R515 server, with 5 disks in software RAid10 (1 disk is spare), an upgrade to kernel 2.6.32-29-server resulted in unusable raid.
Syslog shows that disk and partitions from Raid array are randomly mixed. If I reboot, the mix change. Strange. Here's a sample output:
[   12.5]  sda:
[   12.5]  sdc:
[   12.5]  sdd:
[   12.5]  sde: sdd1
[   12.5]  sdf: sdc1
[   12.5]  sda1 sda2
[   12.5]  sdg: sde1
[   12.5]  sdf1

Disks are all SATA-3 hard-drive, system is on a SSD sata-2 (sdb).
Booting on previous kernel has no usable result.
Any ideas?

xavier

---

### Post by zeroheure on 2011-03-18
Forgot to say that it is the same with 2.6.32-28-server but 2.6.32-27-server freeze after *ureadahead-other (...) terminated with status 4*.
Pressing Return key has no effect. 
I can only reboot with Alt + SysRq + REISUB keys

---

