---
title: "Recover USB drives"
date: 2016-08-30
forum: Ubuntu, Linux and OS Chat
---

### Post by simonsaysthis on 2016-08-30
I used to have to really tool on Windows from Sandisk which could restore my USB drives to factory settings irrespective of how they been partitioned - it was card SD card formatter. Especially when you been using the USB for a live image it is very hard to restore it with the standard partitioning tools. Gparted definitely does not do the trick. Any recommendations on a similar Linux tool?

---

### Post by sudodus on 2016-08-30
You can use ***mkusb*** and its wipe menu. See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

There are many ways to create partitions and filesystems, that are useful for different purposes. The standard partition table is MSDOS, and the standard file system in FAT32 for USB pendrives.

> "Standard: create MSDOS partition table with FAT32 partition" 

---

### Post by simonsaysthis on 2016-08-30
Thanks for the suggestion. Playing around with the tool now

---

