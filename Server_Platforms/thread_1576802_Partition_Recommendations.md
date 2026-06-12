---
title: "Partition Recommendations"
date: 2010-09-17
forum: Server Platforms
---

### Post by WhiteElephant on 2010-09-17
I will be using Ubuntu Server 10.4 for an office server and need partition recommendations. The server has two 500GB drives but I want to use the secondary drive purely for /backup. Should I just go with the default partition settings?
 
Software & Services I will be using:
Samba as Domain Controller
Squid Proxy
DansGuardian
ClamAV
UFW with GUFW
DropBox
 
All user's data will be held in their own home folder.

---

### Post by Girya on 2010-09-18
> **WhiteElephant said:**
> I will be using Ubuntu Server 10.4 for an office server and need partition recommendations. The server has two 500GB drives but I want to use the secondary drive purely for /backup. Should I just go with the default partition settings?
 
Software & Services I will be using:
Samba as Domain Controller
Squid Proxy
DansGuardian
ClamAV
UFW with GUFW
DropBox
 
All user's data will be held in their own home folder.

Checkout lvm2, it allows for alot of flexibility. I use it on a home server and my desktop. you can resize volumes easily, take snapshots for backups and the such. it takes the headaches out of planning partitions. Allocate what you think you'll need and hold some of the disk in reserve to add to the volumes/partitions as they grow. Its really that easy.

My scheme: 
/ on a standard partition.
/home, /music and /video on logical volumes with about 500gb held back to be allocated as needed.

---

