---
title: "Virtualbox question from an Ubuntnoob"
date: 2009-03-02
forum: Virtualisation
---

### Post by breinicke on 2009-03-02
I've installed Ubuntu 10.4, virtual box, and XP SP3 inside.
I have 2 NTFS hard disks that I have not re-connected to the machine since my re-install (I migrated from an XP box).  As a graphic designer, I'm a slave of Adobe's and I must now re-attach my file disks for access in Ubuntu and in XP.

2 questions.
1.  This is my first time connecting NTFS HD's in Ubuntu with vital data on them.  How do I do this safely to have Ubuntu see them.  (re-partitioning is not an option)
2.  How do I then link these HD's so that the VB of XP will see them so that I can access them in Adobe.

---

### Post by bodhi.zazen on 2009-03-02
To mount your partitions either use the mount command or edit fstab.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

To use the partitions in virtualbox, you can use shared folders or , IMO better, samba.

You can use any number of network applications such as ftp, ssh, http, I think samba is easiest and it works "out of the box".

---

