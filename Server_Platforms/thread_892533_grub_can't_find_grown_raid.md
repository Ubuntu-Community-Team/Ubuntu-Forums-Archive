---
title: "grub can't find grown raid"
date: 2008-08-17
forum: Server Platforms
---

### Post by gaspedalo on 2008-08-17
Hi,
I've got an Ubuntu server 8.04.1. It's set up with 3 disks, each divided into three partitions. Those partitions are connected to raids like this

sda1,sdb1 -> Raid 1 mounted at /boot
sda2,sdb2,sdc2 -> Raid 5 mounted at /
sda3,sdb3,sdc3 -> Raid 5 mounted at SWAP

Yesterday I added another disc to increase space on /. Therefore I took ubuntu live session cd, added the disk as spare, reshaped the Raid, resized the fs. Everythingsfine, data is there, raid (/dev/md1) is bigger now.

Just when I remove the live session and try to start the os on disc ubuntu stops after loading the kernel (it says "kernel alive). So I asume it must have some troubles in finding /
Maybe I do have to tell grub the new assembly method of /dev/md1 ?

---

### Post by fjgaude on 2008-08-17
What does your menu.lst file look like, down near its ending?

---

