---
title: "Problems Flashing my Gazv3's CDROM/DVD Drive"
date: 2008-01-07
forum: System76 Support
---

### Post by IgnacioMiller on 2008-01-07
Hey,

I also posted this here: ([https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)) and I am reposting it in this forum so that any fix which is found can be posted here and discovered by any users experiencing similar problems in the future.

> 

Hello,

I was directed here to fix my Gazv3 random hanging issues. I followed all the steps up until the DOS prompt step. I typed dir and saw both the necessary files in the USB thumb drive. I then typed the command sfdndos SCO3.BIN PS -n and received this message:
-------------------------------------------------------------------------
SFDNDOS 2.23.6
FLASH DOWNLOAD PROGRAM for DOS, ATAPI DRIVE
Program by Lee, KI-JU
2005.11 Toshiba Samsung Storage Technology Corporation

FILE OPEN FAIL !!
---------------------------------------------------------------------------

I have tried changing the permissions on the file, but I can't seem to be able to change them on the thumb drive and I cannot change permissions on my desktop and then transfer the permissions to my thumb drive, the permissions revert to as they were before. I have also tried using a different USB thumb drive as drive #2 and it still threw the same error.

Anything I am doing wrong? How can I flash my CDROM drive?

Thanks!
IgnacioMiller


---

### Post by thomasaaron on 2008-01-08
Hi, Ignacio.

I'm not sure why it happens, but some GazV3's do not seem to be able to flash the firmware. 

Make sure you don't have any disks in the drive while your flashing. That may have something to do with it. If it still doesn't work, you will need to send it to me for flashing. I've always been able to flash them on my old, white Darter. Contact me at support(at)system76(dot)com for shipping info.

Best,
Tom

---

### Post by IgnacioMiller on 2008-01-12
Quick question:

How can I restore the flash drive that I used as Flash drive #1 to flash the CDROM/DVD drive to its full 4 GB again?

Thanks,
Dan

---

### Post by thomasaaron on 2008-01-14
Run the Gnome Partition Editor (System > Admin > Gnome Par....)

If it's not there:
```
sudo apt-get install gparted

```

You can use gparted to re-format your drive. Make sure you select the thumb drive though.

---

