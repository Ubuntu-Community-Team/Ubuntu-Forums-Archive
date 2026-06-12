---
title: "Ubuntu and Software RAID"
date: 2009-05-12
forum: Server Platforms
---

### Post by Mets on 2009-05-12
hi all,

I'm building a file server running Ubuntu and I'm trying to figure out a RAID strategy for it.  I have 4 hdd's that I want to use - a a 500GB, a 1TB and two 1.5TB drives.  I'd like to maximize space and be able to use all the drives.  I know if I use a RAID controller, the array will be limited by the 500GB drive.  

Is there a way to do this in software?  I.e. is there some RAID software that works for a RAID 5 setup with different size disk drives?  I know that Drobo essentially does exactly what I am talking about, but I'd like to avoid buying one if possible :)

---

### Post by fjgaude on 2009-05-12
In any raid5 array all partitions of the array have to be the same size. With Linux **mdadm** that's true also, but you can use the other free space for other partitions, like you could have two or more arrays from the three or four drives. One at 500MB, another at 1TB, and so on. Here's so links to get you on the road to software raid, Ubuntu Linux style:

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)
[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

Hope these help...

---

### Post by Mets on 2009-05-12
Thanks a lot fjgaude, the links were helpful.  I also did some googling and I came up with these two, just in case anybody wants to read them, using the LVM:
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)
[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

I guess what I'm really looking for is some piece of software that runs on Ubuntu that gives your data redundancy and lets you use multiple hard drive sizes.  This way you can upgrade drives on the fly instead of having to purchase a set of identical drives and rebuild an entire array.

---

### Post by fjgaude on 2009-05-15
Thanks for the links... I've given you all I know on partition sizes and multiple arrays using the same drives. Gook luck in finding what you seek.

---

