---
title: "Trouble with RAID"
date: 2008-10-19
forum: Server Platforms
---

### Post by Buntubailey on 2008-10-19
Hello,

I am having lots of difficulties trying to set up my HP server with Ubuntu 8.04 Server. I am trying to create a RAID1 and RAID5 array using 4 500GB disks, I have 3 partions on each disk, 10GB for filesystem (/) (RAID1) that is bootable, 5GB for swap (RAID1) and the rest as ext3 filesystem that I will use for data across my network (/home)(RAID5). Everytime linux would install fine and everything goes OK but when I run sudo fdisk -l after install it tells me that all partitions are invalid. I have been trying many different variations of how I am doing it and even gave up and tried to use the onboard fake raid but ubuntu didn't recognise that and still showed all disks as individual. Can someone explain to me what I am doing wrong.:confused:

---

