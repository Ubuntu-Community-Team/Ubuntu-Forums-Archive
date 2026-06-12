---
title: "How to enable boot from degrated RAID on 18.04"
date: 2018-09-20
forum: Server Platforms
---

### Post by barrydocks2 on 2018-09-20
Just done a fresh install of Ubuntu 18.04 server, I haven't done this since 12.04. I have set up a software RAID1 during the install but now I can't work out how to enable the system to boot from a degraded array.  If I disconnect a drive then the system only boots to an initramfs prompt.

Here's what I have tried:
1. The old method of editing "/etc/initramfs-tools/conf.d/mdadm" doesn't seem to be available as the file does not exist.  
2. using "dpkg-reconfigure mdadm" does not give an option for this
3. Adding "bootdegraded=true" to the Kernel argument on boot doesn't seem to work

Help??!!

Thanks

---

