---
title: "Bad PBR"
date: 2005-12-08
forum: Server Platforms
---

### Post by jony_kalavera on 2005-12-08
i have a dell 850 poweredge server with 2 sata drives. I was testing some raid configurations in the ubuntu installation and i accidentaly created a radid 1 array with a swap partition. the partition manager froze so i rebooted and started from scratch so then i tryed to make a raid 1 array with a ext3 partition and 2 swap partitions one on each device so things where something like this:

RAID1 |========== 97GB - EXT3 - /=====================|

sda    |========== 97GB - RAID DEVICE==================||2gb-SWAP|

sdb    |========== 97GB - RAID DEVICE==================||2gb-SWAP|

so installation whent smoothly but then when i rebooted i got BAD PBR. 

what could have happened and how can i fix it?:confused:

---

### Post by bpinkston on 2008-04-09
If you should happen to figure this out let me know.  I did a fresh installation of Ubuntu, Single Installation on a 320GB Sata Drive.  Install went perfect just like yours, when I rebooted it came up Bad PBR.  

Thanks, 

Brent

---

