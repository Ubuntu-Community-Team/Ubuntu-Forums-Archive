---
title: "Resize partition"
date: 2012-03-15
forum: Server Platforms
---

### Post by viperce on 2012-03-15
Hi,

I need a little advise/Help I currently have a VM running Ubuntu Linux 11.04 the original partition was 8Gigs 

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


I am now getting to a stage where my disk space is running low and i would like to increase the partition size. If it possible in linux to re size the hard drive or can i image the VM to another larger drive or larger partition.

please could someone give me some advise on this.

---

### Post by viperce on 2012-03-19
is it not possible to re size the partition?
or to maybe create another drive then ghost to a bigger partition?

---

