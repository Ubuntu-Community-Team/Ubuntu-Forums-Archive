---
title: "Diskproblem?"
date: 2009-01-05
forum: Server Platforms
---

### Post by JJL79 on 2009-01-05
I have used this guide to use some old stuff as a NAS [http://www.smallnetbuilder.com/index2.php?option=com_content&task=view&id=30573&pop=1&page=0&Itemid=77](http://www.smallnetbuilder.com/index2.php?option=com_content&task=view&id=30573&pop=1&page=0&Itemid=77). I have three ide disks in raid0.

Then i used this guide to install ISCSI so i can use the storage space in my NAS in my Windows computers [http://ubuntuforums.org/showthread.php?t=213545](http://ubuntuforums.org/showthread.php?t=213545)

And now my problem

Sometimes when i copy/move files to the NAS in Windows something happens. The Ubuntu server freezes and i can no longer access through ISCSI from Windows. If i wait for a while the Ubuntu server calms down and i can try again. This often happens with large files. When this happens i cannot access the machine with Putty either (dont have monitor attached to computer) My problem is that im new to Ubuntu/Linux and dont know how where to start to try to find what is wrong.

When looking in log files i found this in kern.log

ata1.00: BMDMA stat 0x64
ata1.00: cmd c8/00:08:0b:65:db/00:00:00:00:00/e1 tag 0 dma 4096 in
res 51/40:00:0f:65:db/00:00:00:00:00/e1 Emask 0x9 (media error)
ata1.00: status: { DRDY ERR }
ata1.00: error: { UNC }
ata1.00: configured for UDMA/33
ata1.01: configured for MWDMA2

There is a lot of this kind of error in this log file.

---

### Post by windependence on 2009-01-07
Check out FreeNAS. Much more stable. [www.freenas.org](www.freenas.org). Based on FreeBSD with web interface.

-Tim

---

