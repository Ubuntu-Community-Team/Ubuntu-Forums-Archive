---
title: "Hang on boot, clean install, 16.04, LVM"
date: 2016-12-03
forum: Server Platforms
---

### Post by arlenn2 on 2016-12-03
After a clean install of 16.04 with LVM, the system hangs at the following

/dev/mapper/****, clean, files ####/####, blocks ####/####

The system responds to ctrl-alt-delete.

This hang does not seem to be related to video per some Googling "nomodeset"
This hang also does seem to be related to fsck per some more Googling "fastboot"

I would appreciate any help.

The system is an older C2D based machine, at least 5 years old.  It is currently running 12.04, without LVM

---

### Post by Graham_Willis on 2016-12-04
1. Have you tried booting up your machine in single user mode? Any differences?
2. Please post all the messages that you can see on the console up to the moment of the hang-up.
3. Try mounting LVM volumes from external media. What's the contents of **/var/log/kern.log **and **/var/log/syslog**, any relevant information there? Also, check if the structure of the file system looks reasonably (no missing directories and things like that?)

---

### Post by arlenn2 on 2016-12-19
Reinstalled with different USB drive and changed boot partition to EXT4.  Changing two variables doesn't help solve a problem; but in the combination of the two, it is now working.

---

