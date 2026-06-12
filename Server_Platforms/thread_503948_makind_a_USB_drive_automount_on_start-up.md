---
title: "makind a USB drive automount on start-up"
date: 2007-07-18
forum: Server Platforms
---

### Post by etechship on 2007-07-18
I have a 100GB USB Hard Drive that I would like to connect to my server to have some more space. What do I have to do to make it work?

---

### Post by yabbadabbadont on 2007-07-18
Please post the contents of your /etc/fstab file as well as the output of the "dmesg" command when run in a terminal window.  Make sure that your drive is plugged in and on before running the "dmesg" command.

---

### Post by etechship on 2007-07-18
This is my /etc/fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/ida/c0d0p1 /               ext3    defaults,errors=remount-ro 0       1
/dev/ida/c0d0p5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Then I tried sudo dmesg (with ssh), and it ran off the screen, even with the scroll I can not get the whole message. I looked for sdb, and I did not find any, but i did find my 1GB jump drive. I am willing to bet that is because the ssh console ran out of room. I can access the drive if I mount it.

thanks

---

### Post by brennydoogles on 2007-07-20
> **etechship said:**
> This is my /etc/fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/ida/c0d0p1 /               ext3    defaults,errors=remount-ro 0       1
/dev/ida/c0d0p5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Then I tried sudo dmesg (with ssh), and it ran off the screen, even with the scroll I can not get the whole message. I looked for sdb, and I did not find any, but i did find my 1GB jump drive. I am willing to bet that is because the ssh console ran out of room. I can access the drive if I mount it.

thanks

try ```
sudo dmesg > dmesg.txt
```
from your home folder, and that should export it to a text file.

---

### Post by merkur2k on 2007-07-20
Your best bet is to mount it by it's filesystem UUID; this is how i keep track of mounting two different usb hard drives to their correct locations on my mythtv box. 
This link should help: [http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

---

