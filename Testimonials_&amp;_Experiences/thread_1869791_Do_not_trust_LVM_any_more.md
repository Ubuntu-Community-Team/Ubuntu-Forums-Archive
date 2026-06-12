---
title: "Do not trust LVM any more"
date: 2011-10-26
forum: Testimonials &amp; Experiences
---

### Post by tannalv on 2011-10-26
So, a few days ago I decided to take out my three 1TB disks in my LVM-system and replace them with one 3TB disk.
I started off by fsck.ext4 -f -p /dev/fileserver/data. So far so good. Then I resize2fs -M /dev/fileserver/data. Nothing. For a long time. Hours. Then, it was just done. Mounted to check and see that everything was still there, and it was good. Everything was still there.
So came the daring task of pvmove -v /dev/sdb1. 0.0%, 0.0%, 0.0%, 0.1%, 0.1%, ... and so on. Did that to two 1TB disks. Took days for one of them. Just a few hours for the other one. Then I vgreduce fileserver /dev/sdb1 on both of them. Everything seemed normal. No warnings. This morning I mounted the filesystem... Yes, you guessed it, 2TB of data is gone! Various backups of mails, of old partitions from old computers, old phone records, a lot of personal stuff... *poff* *gone*. 

root@PartedMagic:~# df -h /mnt/
Filesystem--------------------------Size--Used-Avail-Use%-Mounted on
/dev/mapper/fileserver-data----5.2T--3.4T--1.7T--67%-/mnt

It feels like someone has hit me in my gut. Hard. I am never ever trusting LVM again...

---

