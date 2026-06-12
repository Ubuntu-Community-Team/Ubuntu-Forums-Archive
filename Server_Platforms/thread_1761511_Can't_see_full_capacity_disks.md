---
title: "Can't see full capacity disks"
date: 2011-05-18
forum: Server Platforms
---

### Post by dig_it on 2011-05-18
Hello,

Allow me to present my setup
1 Areca controller 1222 divided into
2x250Gb in RAID 1 for my Ubuntu installation
6x 2Tb in RAID 5 for my data (mounted as logical drive) resulting in 8Tb of available space (also visible in the disk utility of Ubuntu)
Ubuntu 10.04 LTS

Now the problem; when I check the capacity in the file browser on my mounted data drive, I only see 5,1 Tb of total space. :-k
Any idea how to solve this? 

Thank you for your support

---

### Post by jerrrys on 2011-05-19
open a terminal and enter **df**, see if that will do a better job of telling you whats going on

---

