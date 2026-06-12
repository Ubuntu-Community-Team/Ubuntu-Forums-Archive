---
title: "EXT4 external hard drive failed to be seen in Win7 Host..."
date: 2011-08-15
forum: Virtualisation
---

### Post by jiapei100 on 2011-08-15
Hi, sorry to drop this question again:

My problem continues...

1) Environments first:
Host --- Windows 7 Professional
Guest --- Ubuntu 11.04
one 2T external hard drive, now formatted in EXT4.


2) Phenomenons:
a) Without launch VirtualBox (Guest Ubuntu), I can see the contents in my EXT4 external hard drive, using a Windows tool named Ext2Fsd .

b) After launching VirtualBox (Guest Ubuntu), I can only see the contents in my EXT4 external hard drive under Ubuntu.
Because this EXT4 external hard drive was automatically mounted 
I checked /etc/mtab
```
/dev/sdb1 /media/Z: ext4 rw,nosuid,nodev,uhelper=udisks 0 0
```
But, this EXT4 external hard drive won't be able to be seen in Windows7 any longer.
Under Windows Explorer, there is a questions mark on this drive (was named "Z:", but now named "Local Disk").

c) During my rebooting tests by revising a bit in /etc/fstab, 
I even got the error as mentioned in [http://www.puppychau.com/archives/62](http://www.puppychau.com/archives/62).
However, I did follow the solutions on it and the issue continues, namely, can't recognize this EXT4 external hard drive in Windows 7 Host if I launch Ubuntu 11.04 Guest.


Can anybody give me a hand please!! I do need this external hard drive to be seen under both the Host and Guest.
Please help.


Best Regards
Pei

---

### Post by CharlesA on 2011-08-15
If you need it accessed from both access the drive from Windows and set up a shared folder with the guest from inside virtualbox.

---

