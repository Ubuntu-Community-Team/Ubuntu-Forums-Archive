---
title: "mount point and virtualbox"
date: 2009-06-05
forum: Virtualisation
---

### Post by pjmlmas on 2009-06-05
I have xp on 10 gig ntfs part
I have ubuntu on 8gig part
I have fat32 partition 64gig + partition

I can mount fat32 as f under ubuntu

I want virtualbox to use this mounted drive.

It does not show up as an option for virtual hard drive. It only shows my rather small ubuntu partition...any ideas? I do not want to put virtual images on ubuntu partition. Not enough space...

---

### Post by bodhi.zazen on 2009-06-06
I assume you are running Ubuntu as a host ?

You are likely to run into problems if you use the FAT partition in this way as FAT does not support Linux permissions and you may have problems when virtualbox tries to set or change permissions on the FAT partition.

I suggest you resize the partition and make an ext2 or ext3 system for your vitualbox data.

In order to use the partition yo mount it , ie add an entry in fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

