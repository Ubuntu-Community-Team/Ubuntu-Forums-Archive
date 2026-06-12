---
title: "booting trouble in kubuntu"
date: 2010-06-30
forum: Ubuntu Studio
---

### Post by 1991sudarshan on 2010-06-30
:confused:Before the installation of Ubuntu Studio I had three os viz ubuntu 9.10 , kubuntu 9.10 and windows XP with a GRUB boot loader. The installtion of ubuntu studio went on well and got properly installed with another boot loader.
 
 
now coming to the problem !!  the Kubuntu also is not booting up when i go inside the kubuntu i get a blank screen after the boot loading and the system freezes up!!
 
 
is there any other way to retrive my Kubuntu os??  but the data in the kubuntu partiton are intact and secure!!!

---

### Post by psy-man on 2010-06-30
hi,
Are linux os on seperate partitions/disks or do they share?

 when you install ubuntu studio, did you
1 resize existing partition and install to a new partition?
or
2 did you add ubuntu studio meta package to existing ubuntu 9.10?

 if 1 then maybe resizing  broke kubuntu, try to boot it single user mode 
(see here [http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/) )
that will get you to a command line in kubuntu if it isn't badly broken you can fix it
try 
sudo dpkg --configure -a

and then

sudo apt-get install -f

if that not work
boot to ubuntu
find your home folder in the kubuntu partition and copy it to a safe place in ubuntu. 
you can then reinstall kubuntu ,get it working then restore home folder.

If 2 and / or kubuntu / ubuntu share common partitions then kubuntu is lost maybe use synaptic to add kubuntu desktop metapackage
system/administrator/synaptic
look in meta packages
good luck

---

### Post by 1991sudarshan on 2010-07-02
i just installed the ubuntu studio in a fresh partition and i did not do any resizing i got the following error message in the kubuntu recovery mode 
 
 
 
[B]Begin: Loading essentialDrivers....
Done
Begin: Runnning ?scripts/init-premount....
Done
Begin : Mounting root file system......
Begin : Running /scripts/local-top.....
Done
Begin: waiting for the root file system
Done
WARNING bootdrive may be renammed Try root=/dev/sda1[/B]
[B]Gave up waiting for boot device. Common problem
 -Boot args (cat /proc/cmdline)
  -check rootdelay= (did the system wait long enough?)
  -check root= (did the system wait for the right device?)
 -Missing /dev/hda1 doesnot exist. Dropping to a shell[/B]

[B]BusyBoxv1.13.3 (ubuntu1:13.3-1ubuntu7) buit-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)
[/B]

---

### Post by psy-man on 2010-07-03
good news
grub is confused about were kubuntu's root partition should be
so am I 
 
boot into ubuntu studio
 
> cat  /boot/grub/menu.lstoutput will display the boot parameters being passed
make sure it is sane

> sudo fdisk -l -uwill display were partitions are

---

### Post by ken78724 on 2010-07-05
hi fellow ubuntu users, let me butt in. Decided I'd review my issue with that command psyman. What do I make of ? I mean, I boot up okay in kubuntu and run ubuntustudio, but get no sound. Here's my output: 
k78724@Kproductions:~$ sudo fdisk -l -u
[sudo] password for k78724: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057fae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   131074334    65537136   83  Linux
/dev/sda2      1459167885  1465144064     2988090    5  Extended
/dev/sda3       131074335   147460634     8193150   83  Linux
/dev/sda4       147460635  1459167884   655853625   83  Linux
/dev/sda5      1459167948  1465144064     2988058+  82  Linux swap / Solaris

Partition table entries are not in disk order
k78724@Kproductions:~$ 
Does disc order make a difference or is this par for course? Unlike the thread owner, I built from 9.04>9.10> 10.04 with some tear downs & work arounds along the way. Apologies but am glad to be in school. 

Cheers, and thanks to both of you!
Ken

---

### Post by psy-man on 2010-07-06
no sound in ubu-stu is a different issue, better to search the forum or start a new thread

partition table entries  _not_ need to be in disk order order

in your case ken, all partitions on one drive at /dev/sda  , it is  sata drive or usb

1991sudarshan it looks like you are booting from sata or usb but busybox is expecting to find the root file system for kubuntu on the first partition of an IDE drive. 
Have you changed the boot order of drives ? or maybe add sata or PCI IDE card? what ever; has changed 
/boot/grub/menu.lst  must make sense, either you figure it out or post here output of > cat  /boot/grub/menu.lst

---

