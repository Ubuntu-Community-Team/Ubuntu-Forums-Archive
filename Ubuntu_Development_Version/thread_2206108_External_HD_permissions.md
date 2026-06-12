---
title: "External HD permissions"
date: 2014-02-17
forum: Ubuntu Development Version
---

### Post by donloveslinux on 2014-02-17
Using Trusty, on a desktop, I have an external Seagate HD with about 1.2TB.  Mount says:
sudo ls -l /media/don/f8d24904-06a2-4003-a7b9-8b0366de8667/  says:
drwxrwxrwx 2 don don 16384 Feb 17 09:08 lost+found
df -Th says:
Filesystem     Type      Size  Used Avail Use% Mounted on
  etc ...
/dev/sdb2      ext4      917G   72M  870G   1% /media/don/f8d24904-06a2-4003-a7b9-8b0366de8667
ls -l /dev/sdb2
brw-rw---- 1 root disk 8, 18 Feb 17 10:44 /dev/sdb2
  Root access is my "problem"
/etc/fstab has:
UUID=5e776f64-61d3-4c8b-9d0a-e06dc2dd400e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=745ad034-7a79-46d9-9cf8-1995cdbc6138 none            swap    sw              0       0

I'm no expert, but prefer command line.  The goal is to move this HD from one Linux pc to another Linux pc and copy files onto it as a 
normal user.  I've tried chmod'ing 777 etc but only the "lost+found" sub-folder changes.  BTW what is lost+found?
How can I accomplish my goal (use HD w/o being root)?  Thx.

---

### Post by Herman on 2014-02-17
It has been years now since we needed to use the command line to create a mount point for USB devices before mounting the file system. Now we just plug them in and expect everything to be done for us automatically. In the old days we needed to use sudo commands to create the mount point first, and because of that the mount point was automatically owned by root until we chmodded it and/or chowned it.  I'm not sure what's going on with Trusty, but maybe the developers are in the middle of making some changes to the way things work and for some reason it seems to be affecting the automatic mounting of USBs.

It's the mount point I would be looking at and chmodding, not stuff inside the drive itself.
```
ls -l /media
```
```
sudo chmod 777 /media/don
```
Where: /media/don is your mount point for the file system you want access to.

The lost+found is a directory for the file system checker to put broken fragments of files in when you run a file system check after a hard shut-down or a crash, or if your hard drive is starting to fail.

---

### Post by Bucky Ball on 2014-02-17
*Thread moved to **Ubuntu+1**.*

Any and all disucssion/troubleshooting of 14.04 LTS goes here until release in April. Thanks.

---

