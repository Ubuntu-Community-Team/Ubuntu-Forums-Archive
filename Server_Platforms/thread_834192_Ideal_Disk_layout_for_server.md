---
title: "Ideal Disk layout for server"
date: 2008-06-19
forum: Server Platforms
---

### Post by mmcsherr on 2008-06-19
I have 2 disk ontrollers, SATA, with 5 disks attached.  The following table is my first crack at a disk layout.  I am asking for help to make sure I am not doing something stupid with the disks.  What is the ideal disk layout for ubuntu 8.0.4 64-bit server?

controller;disk;/dev;size;partition 0;partition 1;partition2, etc
0;hd0;/dev/sda;1 TB;1TB, md2, /srv, raid 5			
0;hd1;/dev/sdb;1 TB;1TB, md2, /srv, raid 5			
0;hd2;/dev/sdc;1 TB;1TB, md2, /srv, raid 5			
1;hd3;/dev/sdd;300 GB;146GB, md0, /, raid 1;7.5GB, swap;146GB, md1, /home, raid 1;0.5GB, /boot
1;hd4;/dev/sde;300 GB;146GB, md0, /, raid 1;7.5GB, swap;146GB, md1, /home, raid 1;0.5GB, unused

---

