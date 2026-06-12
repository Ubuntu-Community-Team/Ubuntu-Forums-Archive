---
title: "df in chroot :cannot read table of mounted file systems: No such file or directory"
date: 2011-02-14
forum: Virtualisation
---

### Post by moky on 2011-02-14
Hello world !

As written in the title, attempt to know the disk space left in a chroot environment fails on the error

root@k12-math:/# df
df: cannot read table of mounted file systems: No such file or directory


This is one problem.

On the other hand, I have :
1. installed maverick on my usb key by debootstrap
2. installed BOINC (this is a distributed computation system) on the key by apt-get in chroot


Now when I launch boinc in the chroot environment, it complains that it has not enough disk space left.
More precisely, it says that I have 0.0 Mib free while I have still 1.5 Gib.

These two problems may be linked. How can I make a software into chroot know the disk space left ?

Have a good afternoon
Laurent


See also :
(in French) [http://forum.boinc-af.org/index.php/topic,4098.0.html](http://forum.boinc-af.org/index.php/topic,4098.0.html)

---

