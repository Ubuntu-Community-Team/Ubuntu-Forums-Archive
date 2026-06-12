---
title: "Add Second Hard Drive as /var/www/"
date: 2010-06-16
forum: Server Platforms
---

### Post by senkusha on 2010-06-16
Hi all!

I've recently moved from Fedora 7 to Ubuntu Server 9.10.  This server has been in operation for quite a few years, and currently has two 110 GB IDE hard drives in one volume group...I think they are both mounted at /.

What I want to do is the following:
1.  Have the system files on the IDE volume group of /
2.  Add a 2TB SATA drive, mounting at at /var/www/  I also want this partition to be extendable, if I want to add a second 2 TB SATA drive, to be "Volumed"?? with this one
3.  Add another IDE HDD, mounting at /var/log

I remember I used (I think it was GParted...a GUI when I added the second IDE drive a couple years ago), but now I'm in a Terminal-only world.  After I install the hard drives, what process would I need to follow to accomplish my above listed tasks?

Thank you very much for all your help! :)

---

### Post by The Real Dave on 2010-06-16
What could you possibly need more than 2TB of /var/www for? o.O

LVM allows you to add on harddrives like you wish if I remember correctly, so maybe the following [Ubuntu Doc]("https://help.ubuntu.com/community/FileServerOnLVMOnRAID1") could be of interest?

---

### Post by senkusha on 2010-06-16
Thanks.

You'd be surprised how much storage space a server may need.  I just don't want to run out of space again.

Anyway, that Guide you pointed to appears to possibly be GUI?  I need instructions on a Terminal Only approach.  Not only for enhancing the already existing LVM I have, but to make new partitions also

---

