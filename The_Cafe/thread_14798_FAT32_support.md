---
title: "FAT32 support"
date: 2005-02-09
forum: The Cafe
---

### Post by dejavu on 2005-02-09
hi


i tried to mount some windows parititions on the linux os  but when i did so it said FAT32 no supported ...
do i need to configure my kernel for it ?  or do i need to install/upgrade something ..
if iam to reconfigure plz tell me how to configure the kernel since i never did one  :!:

---

### Post by carlc on 2005-02-09
What does your fstab entry look like for the fat32 partition? I am wondering if you specified the partition type as fat32. ? It should be vfat in the fstab entry.

---

### Post by Buffalo Soldier on 2005-02-09
[QUOTE=dejavu]hi


i tried to mount some windows parititions on the linux os  but when i did so it said FAT32 no supported ...
do i need to configure my kernel for it ?  or do i need to install/upgrade something ..
if iam to reconfigure plz tell me how to configure the kernel since i never did one  :!:[/QUOTE]

Please refer to [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat) on HowTo mount Windows partition (FAT) on boot-up, and allow all users to read/write.

---

### Post by ThePainter on 2005-02-10
Hi,
Im wondering if you have done what I first did.
I read the guide and it has an entry for NTFS and FAT so I rewrote it to say fat32 instead of fat and it gave me that error.
I think it sees fat32 as fat so just mount it as a fat partition.
Good luck  :-)

---

### Post by gopukrishnantec on 2012-08-06
Hi,

I am new here. I installed latest ubuntu 12 now. I am not able to use pendrive as read write.The format was fat32. But  I am able to when i formatted it as fat.
What should be the problem ?

---

### Post by CharlesA on 2012-08-06
Please create a new thread as this one is ***7*** years old.

---

