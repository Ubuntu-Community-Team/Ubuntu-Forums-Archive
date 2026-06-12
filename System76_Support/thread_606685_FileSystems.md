---
title: "FileSystems"
date: 2007-11-08
forum: System76 Support
---

### Post by ishmaelm on 2007-11-08
An automatic file system check of the root flesystem failed. A manual fsck must be performed ,then the system rebootred. This fsck can be performed in maintenance mode. Please note that the root flesystem is currently mounted read-only. This fsck should only be performed while the root filesystem is mounted read-only. However, the command to remount it read-only is:
# mount -n -o remount,rw /
(or typr control-D to continue)



Please help,been struggling with this for a week now & it needs to be fixed urgently.

Thanks 
Ishmael Motsoeli

---

### Post by paul.matthijsse on 2007-11-08
Hello,

What's your problem exactly? Just type control-D to continue and (I guess) type "fsck". That way your drive is manually checked. Normally it finds some problems with inodes and such and asks you if that has to be corrected. You can answer yes on that or just hit Enter. When fsck is finished, you need to reboot your machine. 

Paul.

---

