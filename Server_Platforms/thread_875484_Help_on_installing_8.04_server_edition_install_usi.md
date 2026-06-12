---
title: "Help on installing 8.04 server edition install using USB flash drive"
date: 2008-07-30
forum: Server Platforms
---

### Post by macki_kun on 2008-07-30
I'm relatively new to ubuntu. I'm currently installing the said version via usb. I used the unetbootin via windows to make a live USB.. however when I get to the "detect and mount CD-ROM" part of the installation.. it says that it can't load cdrom drivers. The box I'm currently using has no CD-ROM drives and I'm only using a USB key.. I tried editing the module to look at the USB device for source instead of looking for a cdrom but i'm still stuck. Did i forget something?

---

### Post by ChumleyEX on 2008-07-31
Can you mount the ISO in windows as a cdrom drive via daemon tools?


[http://www.daemon-tools.cc/dtcc/download.php?mode=ViewCategory&catid=5](http://www.daemon-tools.cc/dtcc/download.php?mode=ViewCategory&catid=5)

---

### Post by djamu on 2008-07-31
I regularly use USB sticks for booting, mostly just as bootstrap when PXE is not available. 
( I don't use CD's or floppys anymore, all my compute nodes are diskless too )

Haven't used Unetbootin yet, but do know what surely works on hardy. You probably have got that info on Unetbootin from here > [https://help.ubuntu.com/community/Installation/FromLinux?highlight=((Installation|FromLinux](https://help.ubuntu.com/community/Installation/FromLinux?highlight=((Installation|FromLinux))) 
If not this is good reading material. 
The  "Alternate CD procedure 2" is best applicable.
Leaves only the problem with the usb stick that normally is FAT/FAT32 formatted and unpartitioned...

you can take 2 routes.. both require your USB stick to have the bootflag enabled ( make it bootable !!! )


**Keeping FAT/FAT32**
because FAT32 can't handle the required file permissions. You need a dos version of the grub bootloader.

GRUB4DOS 
home page  > [https://gna.org/projects/grub4dos/](https://gna.org/projects/grub4dos/)
wiki       > [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)


**Using ext3**
you can format your USB stick to ext3, but most of those devices don't like to be partitioned ( they are in fact superfloppy's, some Bios's refer like this to them )

To use ext3 ( which is the same as ext2 but ext3 has journalling ) on windoz use > [http://www.fs-driver.org/](http://www.fs-driver.org/)


the trickiest part is to change the needed menu.lst file that GRUB uses. I've included one that I just used. 
```
title  isoinstall
kernel (hd0,1)/boot/isoinstall/vmlinuz file=/cdrom/preseed/ubuntu-server.seed
initrd (hd0,1)/boot/isoinstall/initrd.gz

```

the (hd0,1) reference is important because it points to the CDrom ( in your case the location of the ISO file ) and simple means 

(hd0,1) = HD 1 partition 2 ( starts counting from zero )
if you use it on an unpartitioned USB stick use
(hd0) = 1st disk 

the actual nrs. (hd0) (hd1) etc.. are the nrs. the bootloader gets from BIOS. So if your USB stick is the first HD / preferred boot disk in your BIOS setting then it will likely become (hd0)...


**IMPORTANT**
you can't use **boot.img.gz** and **vmlinuz** files supplied with the CD 
get them here ( you can use all 3 files on the link ) [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/)
**make sure your usb devices have the bootable flag enabled** use a partitioning tool for that ( CFDISK for example )



The final bootable USB stick will only have a couple of files on them.


I use this method often to boot custom CD's from USB.
Live custom CD's are easily made with the remastersys package. If you don't like fiddling around with source code, you can just add it from the medibuntu repos.
( medibuntu contains all packages that for legal reasons may not be used in the USA & the likes )
get the repos here > [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)
howto change repos & use remastersys > [http://easierbuntu.blogspot.com/2008/07/backing-up-your-system-with-remastersys.html](http://easierbuntu.blogspot.com/2008/07/backing-up-your-system-with-remastersys.html)
this link tells you how to add the remastersys repo only.. just use the medibuntu repo & you'll never have to add any other sources .....


Also I strongely advice against using USB sticks as live system disks, simply because that type of memory ( EEPROM & the likes ) can't handle the billions of rewrites normal ram can handle.. if you decide on using it for a system over prolonged time > use a custom live ISO this way the ISO will be loaded into ram + all sys logs etc.. will be stored in RAMFS...

hope that helps a bit. 
 
;)

---

### Post by modmadmike on 2008-09-07
Cool these instructions will work for my super Repair Ipod which has a working install of linux in it and I'll make x64 and x32 installers in its grub menu :).

---

