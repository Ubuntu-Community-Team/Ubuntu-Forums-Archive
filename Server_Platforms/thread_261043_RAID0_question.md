---
title: "RAID0 question"
date: 2006-09-19
forum: Server Platforms
---

### Post by InDenial on 2006-09-19
I am currently trying to install Ubuntu server on an old pc I have here (PIII 500, 512 MB, 2x80G HD) and I want to combine those two disks into 1. 

During the setup when I partition I did the following:

HD 1: primary partition 80.1 GB Physical Volume for RAID
HD 2: primary partition 80.1 GB Physical Volume for RAID
RAID0 device 160.1 GB Software RAID Device

In my virtual HD I want to create partitions but it starts saying something about max amount of partitions when I let it partition automaticly. It results in a 158.6 GB ext3 partition and a 1.5 Gig unusable partition.

I bet I am doing something wrong and maybe I need to create a logical partition instead of primary partitions. 

My question is: am I on the right track?

---

