---
title: "Resize partition"
date: 2012-05-09
forum: Virtualisation
---

### Post by viperce on 2012-05-09
Hi,

I am in need of some assistance, a few months ago i started playing around with Linux.

I created a VM Proxy server and only allocated 8gb to the virtual drive thinking thats more than enough, I was wrong........


anyway I am running out of space currently having to clear the proxy cache every few months. 

What would you recommend i do to increase the disk size? (expand the volume)
 
> 
fdisk -l

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009de3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        1045     8136705    5  Extended
/dev/sda5              32        1045     8136704   8e  Linux LVM
I have tried dd if=/dev/sda(8gb) of=/dev/sdb(80gb)
but that only uses 8gb of the 80gb partition.

Please could someone advise me on what i can do to solve this problem.

---

### Post by howefield on 2012-05-10
Thread moved to the "*Virtualization*" forum.

---

