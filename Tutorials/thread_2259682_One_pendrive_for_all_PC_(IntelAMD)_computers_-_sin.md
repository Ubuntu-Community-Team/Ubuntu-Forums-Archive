---
title: "One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot"
date: 2015-01-06
forum: Tutorials
---

### Post by sudodus on 2015-01-06
Post #1.  One pendrive for all PC (Intel/AMD) computers - Ubuntu 64-bit and Lubuntu 32-bit

Ubuntu 64-bit works in BIOS and UEFI mode, also with secure boot. Lubuntu 32-bit works with 32-bit and 64-bit computer hardware, so it adds ability to boot 32-bit computers including old hardware.
[HR][/HR]
The following posts (6, 7, 8, 10, 11, 48, 49) describe 'grub-n-iso' systems, that can boot 32-bit and 64-bit Ubuntu family operating systems in BIOS and UEFI mode, but these 'grub-n-iso' systems do not work with secure boot.

Post #6.   [A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso']("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523") - Lubuntu  32-bit

Post #7. [Multiboot pendrive system for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302264#post13302264")

Post #8. [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

Post #10. [Create or download a portable system with a small footprint with a potential for isotesting]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310634#post13310634")

Post #11. [Manage the daily built iso files of your choice]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310836#post13310836")

Post #12. [Comments and tips]("http://ubuntuforums.org/showthread.php?t=2259682&p=13320397#post13320397")

Post #48. [Test results with mk-grub-n-iso-s which is built into mkusb version 10](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13365767#post13365767)

Post #49. [A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13399888#post13399888)

Post #144. [Make persistent live drives with casper-rw and home-rw partitions](https://ubuntuforums.org/showthread.php?t=2259682&page=8&p=13761527#post13761527) ***New 2018-04-30***

The system with compressed image files makes it easy for a beginner to  install, but it is rather inflexible. So I made shell-scripts, that  does the main part of the work with the help of a couple of files for  the configuration of the booting system.
 [HR][/HR]
 [SIZE=4]One pendrive for all PC (Intel/AMD) computers[/SIZE]

A compressed image file is made from an Ubuntu iso file and a Lubuntu iso file. The intention is to have one USB pendrive, which can boot the vast majority of computers

***Ubuntu 14.04.1 LTS 64-bit:*** works with 64-bit processors in UEFI and BIOS mode - for new and middle-aged computers. It works also with ***secure boot*** (in UEFI).

***Lubuntu 14.04.1 LTS 32-bit:*** works with 32-bit processors and 64-bit processors in BIOS mode - for old and middle-aged computers. The boot option [forcepae]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M") extends it to Pentium M and Celeron M processors that lack the PAE flag.

Lubuntu is booted via the syslinux interface of Ubuntu - it seems almost seamless.

[SIZE=4]Installation[/SIZE]

Install from the compressed image file

[phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubu64Lubu32-4GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubu64Lubu32-4GB.img.xz)

with the following md5sum (and size 1.7 GB compressed).

```
b7f6dd0002e25dd2f95dda7e71635b16  dd_Ubu64Lubu32-4GB.img.xz
```

 to a USB pendrive (4GB or more) with ***mkusb*** in linux or ***Win32 Disk Imager*** in Windows, which is described in the following links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#in_Windows](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#in_Windows)

[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

[SIZE=4]Method[/SIZE]

I made the 'One pendrive for all PC (Intel/AMD) computers' according to the following steps:

1. ***Wipe*** the first mibibyte of a pendrive with ***mkusb***.

**mkusb** is a tool with a graphical user interface. You navigate via menus. Maybe the quick start manual can help you get started and find the relevant menu, where you can wipe the first MiB (mibibyte, base 2).

[mkUSB-quick-start-manual-12.pdf](https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-12.pdf)

2. ***Create*** a FAT32 partition and and an empty second partition with ***gparted***. Mount the FAT32 partition.

**gparted** is also a tool with a graphical user interface. You navigate via menus. Maybe the following link will help you use it,

[GParted partitioning software - Full tutorial ](http://www.dedoimedo.com/computers/gparted.html)

3. ***Flash*** (extract the content of) the Ubuntu iso file with the ***Startup Disk Creator*** to the FAT32 partiiton.

The Ubuntu **Startup Disk Creator** has been changed in a fundamental way since I wrote these instructions. *You can still use the version that comes with Ubuntu 14.04.x LTS for this purpose.* But the version of the Startup Disk Creator in Ubuntu 16.04 LTS (16.04.x) and newer versions is a cloning tool, and does not do what is intended in step 3. (You can also use another tool for this purpose, a tool to extract the content. It would be possible with for example the command line tool **rsync**. In that case you would install the bootloader separately.)

You find the old version Ubuntu 14.04.1 LTS via this link,

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

4. ***Edit*** the file **syslinux/txt.cfg** (in the FAT32 partition)

```
default live
label live
menu label ^Try Ubuntu amd64 without installing
kernel /casper/vmlinuz.efi
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
label live-install
menu label ^Install Ubuntu amd64
kernel /casper/vmlinuz.efi
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
label check
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
menu label Test ^memory
kernel /install/mt86plus
label hd
menu label ^Boot from first hard disk
localboot 0x80
# ------------------------------------------------------------------
label lubu-live
  menu label ^Try Lubuntu i386 without installing
  kernel /lubuntu/casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true  file=/cdrom/lubuntu/preseed/lubuntu.seed boot=casper initrd=/lubuntu/casper/initrd.lz quiet splash --
label lubu-live-install
  menu label ^Install Lubuntu i386
  kernel /lubuntu/casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true  file=/cdrom/lubuntu/preseed/lubuntu.seed boot=casper only-ubiquity initrd=/lubuntu/casper/initrd.lz quiet splash
```

5. ***Create*** the directory lubuntu in the FAT32 partition. ***Loop mount*** the Lubuntu iso file and ***copy*** its content to the lubuntu directory.

```
sudo mount -o loop /your-path/lubuntu-14.04.1-desktop-i386.iso /mnt/iso
mkdir /mnt/iso
cd /mnt/iso
sudo cp -r * /mnt/usbstick/lubuntu
sudo umount /mnt/iso
```

6. ***Remove*** the big file **lubuntu/casper/filesystem.squashfs** from the FAT32 file system. The squash filesystem will be accessed from the image in the second partition instead.

7. ***Flash*** the Lubuntu iso file to the second partition. [COLOR=#ff0000]***This is risky, so be warned, double check and triple check, that you have the correct target!***[/COLOR] Otherwise you might destroy your family pictures. [COLOR=#ff0000]***Don't do it if you are not sure***[/COLOR]. Use the compressed image file instead. Check with

```
sudo parted -l
df
```

```
sudo dd if=/media/multimed-2/CD/ubuntu/14.04/lubuntu-14.04.1-desktop-i386.iso of=/dev/sdx2 bs=4096
```

where x is the current drive letter for the pendrive (I have three internal disks, so in my case x is d: /dev/sdd2).

8. ***Sync*** the pendrive ```
sync
``` ***Unmount the pendrive***.

Check that it is unmounted with ```
df
``` before you unplug it. Otherwise it might be corrupted.

[SIZE=4]Enjoy :-)
[/SIZE]
You can run a live system from the pendrive as is it and save some files in the remaining space in the FAT32 partition, 2.0 GB. And you can use it to install Ubuntu and Lubuntu 14.04.1 LTS.

```

df -h /dev/sdx?     # in my case /dev/sdd?
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1       3.0G  1.1G  **2.0G**  34% /media/Ubu64Lubu32
/dev/sdd2       696M  696M     0 100% /media/Lubuntu 14.04.1 LTS i386
```

If you have a bigger drive there are several options how to use the remaining drive space.

**- *Live system***

When you run a live system, the FAT32 partition is read-only. You can read files that were written there before you booted. For example, when connected to Windows or another linux computer as a normal data pendrive. If you create other partitions (for example at the end of the drive), you can read and write files by the live system. You can even read the casper-rw partition (if you created it for persistence).

***- Persistence***

- You can create partitions in the unallocated space behind the second partition, for example make a casper-rw partition for persistence and set the label to **casper-rw**. If there is no space behind the second partition (a 4 GB pendrive), you can make a ***casper-rw file*** in the 2 GB available in the FAT32 partition and create an ext2 file system inside the file, but it is not recommended. Use a fast USB 3 pendrive for persistence. Such pendrives have almost always at least 16 GB storage space. (USB 2 pendrives are slow with persistence.)

Add the [boot option]("https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line") **persistent**

- in the file **syslinux/txt.cfg** for BIOS/CSM mode,

 - in the linux line of the [corresponding file]("http://codenuggets.com/2014/04/16/ubuntu-live-usb-persistence-for-uefi/") **boot/grub/grub.cfg** for UEFI mode 

- or add **persistent** only in real time at the boot menu.

[COLOR=#ff0000]But use persistence only with either of Ubuntu or Lubuntu, otherwise it will be corrupted[/COLOR].

When you run a persistent live system, the FAT32 partition is read-write. You can read and write files  to the free space in that partition. For example, you can write and remove  files, that can be read by Windows when connected to another computer as a normal  data pendrive. [COLOR=#ff0000]But beware, do not remove any system files from the FAT32 partition![/COLOR] Persistence is sensitive to other errors too, so[COLOR=#ff0000] ***backup*** the casper-rw partition regularly.
[/COLOR]
- More than one persistent system can be made by adding Knoppix or Puppy Linux. See [this thread]("http://ubuntuforums.org/showthread.php?t=2260697").

. A persistent Ubuntu system and a persistent Knoppix system would work in the same pendrive. In this case I would suggest ***standard Ubuntu desktop 64-bit*** and ***Knoppix 32-bit***. Knoppix is good at recognizing old hardware and has its own system for persistence, different from and independent of Ubuntu.

. Thinking further: In order to extend the pendrive to even older computers, ***Wary Puppy*** or ***TahrPup*** would be a good alternative. They have their own file for persistence, different from those of Ubuntu and Knoppix.

***- Expand the FAT32 partition 'grow it'***

It is also possible to move the second partition to the end of the drive and grow the first partition according to [GrowIt.pdf]("http://phillw.net/isos/linux-tools/9w/GrowIt.pdf").

[SIZE=4]Read more ...[/SIZE]

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sudodus on 2015-01-06
I found that I could remove the the squash filesystem from the FAT32 partition and save 644MiB drive space, 2.0 GB is free in the FAT32 partition after this tweak, and the compressed iso file is also smaller than before.

> 6. Remove the big file **lubuntu/casper/filesystem.squashfs** from the FAT32 file system. The squash filesystem will be accessed from the image in the second partition instead.

---

### Post by ventrical on 2015-01-06
I am looking at this later ... :)

regards..

---

### Post by C.S.Cameron on 2015-01-06
Looks like another good one Sudodos.
Have you tried putting Lubuntu in it's own partiton with it's own Casper-rw file.
(have been wondering if this would work but have not had a chance to try).
It might also be nice to get rid of the try/install from the menu and just give a choice between Ubuntu and Lubuntu.
Just a thought.

---

### Post by sudodus on 2015-01-07
> **C.S.Cameron said:**
> Looks like another good one Sudodos.
Have you tried putting Lubuntu in it's own partiton with it's own Casper-rw file.
(have been wondering if this would work but have not had a chance to try).

I'm not sure I understand. I did not not think it would be possible to assign which casper-rw file or partition to select, where and in which order the system looks for casper-rw devices. Maybe it is possible. I would be happy if you can try that out :-)
> 
It might also be nice to get rid of the try/install from the menu and just give a choice between Ubuntu and Lubuntu.
Just a thought.

Yes, you are right, but there is a reason why I did it this way. I did not want to touch [the part of] the system, that selects between UEFI and BIOS, so I appended Lubuntu in a place, where that selection has already been done.

Maybe it would work to make a subdirectory in the FAT32 partition for ubuntu too (alongside the lubuntu directory), put the Ubuntu stuff there except the squashfs filesystem, and strip the top level menu to a simple selection between Ubuntu-64-bit and Lubuntu-32-bit.

-o-

*Edit*: The discussion about more than one persistent system in the same pendrive continues in the following thread by C.S.Cameron
[URL="http://ubuntuforums.org/showthread.php?t=2260697"]
Multiboot flash drive with second partition[/URL]

---

### Post by sudodus on 2015-06-08
The following posts (6, 7, 8, 10, 11) describe 'grub-n-iso' systems, that can boot 32-bit and 64-bit Ubuntu family operating systems in BIOS and UEFI mode, but these 'grub-n-iso' systems do not work with secure boot. The system described in post #1 works with secure boot.

[SIZE=4]A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso'[/SIZE]

A compressed image file is made from a system that boots via grub and a Lubuntu  iso file. The intention is to have one USB pendrive, which can boot the  vast majority of computers. This is a ***smaller and simpler*** alternative than what is described in post #1.

***The grub system*** works in UEFI and BIOS mode. It is developed from a multiboot system for UEFI by Andre Rodovalho. See the following link,
[URL="http://ubuntuforums.org/showthread.php?t=2276498"]
How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images[/URL]

***Lubuntu 14.04.2 LTS 32-bit:*** works with 32-bit processors and 64-bit processors in old, middle-aged and new computers. The boot option [forcepae]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M") should be used when installing Lubuntu into computers with Pentium M and Celeron M processors that lack the PAE flag.

Lubuntu is booted via grub and the standard Lubuntu ISO file, but in a new way, that allows it to work in both UEFI and BIOS mode. A partition with the label **casper-rw** provides persistence.

[SIZE=4]Installation[/SIZE]

Install from the compressed image file

[dd_lubuntu-14.04.2-desktop-i386_4GB.img.xz]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_lubuntu-14.04.2-desktop-i386_4GB.img.xz")

with the following md5sum (and size 699 Mibibytes compressed).

```
b3844fc5a0b2adea0b943a193538e4ea  dd_lubuntu-14.04.2-desktop-i386_4GB.img.xz
```

to a USB pendrive (4GB or more) with ***mkusb*** in linux or ***Win32 Disk Imager*** in Windows, which is described in the following links

[SIZE=3]Linux[/SIZE]

It is straight-forward with ***mkusb*** in linux according to [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[SIZE=4] [SIZE=3]Windows[/SIZE][/SIZE]

In Windows you should expand the compressed image file with for example ***7-zip*** before using ***Win32 Disk Imager***.

Download the following help programs  
[http://www.md5summer.org](http://www.md5summer.org) 
[http://www.7-zip.org](http://www.7-zip.org) 
[http://sourceforge.net/projects/win32diskimager](http://sourceforge.net/projects/win32diskimager) 

First check that the download was successful with **md5summer**.

Next extract the image file with **7-zip** (It is also possible with **winzip**) 

from **dd_lubuntu-14.04.2-desktop-i386_4GB.img.xz** to **dd_lubuntu-14.04.2-desktop-i386_4GB.img**

And then use ***Win32 Disk Imager*** according to [https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

[SIZE=4]Method[/SIZE]

I made this smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso' - according to [this link]("http://ubuntuforums.org/showthread.php?t=2276498&p=13299549#post13299549")

[SIZE=4]Enjoy :smile:
[/SIZE]
**- *Live system***

When you run a live system, the FAT32 partition is read-only. You can  read files that were written there before you booted. For example, when  connected to Windows or another linux computer as a normal data  pendrive. If you create other partitions (for example at the end of the  drive), you can read and write files by the live system. You can even  read the casper-rw partition (made for persistence).

***- Persistence***

When you run a persistent live system, the FAT32 partition is  read-write. You can read and write files  to the free space in that  partition. For example, you can write and remove  files, that can be  read by Windows when connected to another computer as a normal  data  pendrive. [COLOR=#ff0000]But beware, do not remove any system files from the FAT32 partition![/COLOR] Persistence is sensitive to other errors too, so[COLOR=#ff0000] ***backup*** the casper-rw partition regularly[/COLOR].

There might be problems if you use the casper-rw partition for different iso files and install program packages. Data files can be shared without problems. If the persistence is damaged, you can always remove all files, or simply format it (make a new ext2 file system).

- More than one persistent system can be made by adding Knoppix or Puppy Linux. See [this thread]("http://ubuntuforums.org/showthread.php?t=2260697").

***- Expand the FAT32 partition 'grow it'***

It is possible to move the second partition to the end of the drive and grow the first partition according to [GrowIt.pdf]("http://phillw.net/isos/linux-tools/9w/GrowIt.pdf").

Use the unallocated space, if there is space behind the second partition  (in a bigger than 4 GB pendrive). You can move the casper-rw partition  in order to increase the size of the FAT32 partition to make room for  another iso file or increase the size of the casper-rw partition or  create a completely new partition. Use a fast USB 3  pendrive for  persistence. Such pendrives have almost always at least 16  GB storage  space. (USB 2 pendrives are slow with persistence.)

[SIZE=4]See also ...[/SIZE]

[http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sudodus on 2015-06-11
[SIZE=4]Multiboot pendrive system for all PC (Intel/AMD) computers[/SIZE]

The previous post described how to install a 'grub-n-iso' system to a pendrive from a compressed image file. It is a system with a single Lubuntu iso file. There is also a compressed image file with a multiboot system for an 8 GB or larger pendrive

- that boots via grub in BIOS as well as in UEFI mode

- contains the following iso files

[B][FONT=courier new]kubuntu-14.04.2-desktop-amd64.iso
lubuntu-14.04.2-desktop-i386.iso
ubuntu-12.04-desktop-i386.iso
ubuntu-14.04.2-desktop-amd64.iso
ubuntu-mate-14.04.2-LTS-desktop-i386.iso
xubuntu-14.04.1-desktop-i386.iso
[/FONT][/B]
- contains a casper-rw partition for persistence.

[SIZE=4]Download and install
[/SIZE]
Download from the following link

[dd_ubuntu-flavours-multiboot-G_7.8GB.img.xz]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_ubuntu-flavours-multiboot-G_7.8GB.img.xz")

Check with the following md5sum (and size 5.3 Gibibytes compressed).

```
0c18cff407e339a620a5787ebd7af64a  dd_ubuntu-flavours-multiboot-G_7.8GB.img.xz
```

[SIZE=3]Linux[/SIZE]

Installing is straight-forward with ***mkusb*** in linux, [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[SIZE=4] [SIZE=3]Windows[/SIZE][/SIZE]

In Windows you should expand the compressed image file with for example ***7-zip*** before using ***Win32 Disk Imager***, which is described with more details in the previous post.

[SIZE=4]Usage[/SIZE]

Notice that 32-bit as well as 64-bit iso files can be booted in UEFI mode, so booting from a 32-bit iso file works in most PCs with Intel and AMD processors, from very old 32-bit PCs to new PCs running in UEFI mode.

You can edit the partitions with gparted, for example change the sizes, in order to use the whole pendrive, if it is bigger than what is expanded from the compressed image files (4 GB or 8 GB). The casper-rw partition can be moved without creating problems. The fat32 partitions size can be changed, but its head end should stay where it is.

There might be problems if you use the casper-rw partition for different iso files and install program packages. Data files can be shared without problems. If the persistence is damaged, you can always remove all files, or simply format it (make a new ext2 file system).

[HR][/HR]
The system with compressed image files makes it easy for a beginner to install, but it is rather inflexible.

---

### Post by sudodus on 2015-06-11
[SIZE=4]Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers[/SIZE]

The system with compressed image files makes it easy for a beginner to install, but it is rather inflexible. So I made a shell-script, that does the main part of the work with the help of a couple of files for the configuration of the booting system.

The shell-script is made to be easy to use, but it helps if you have some experience with terminal windows and command lines. If you want to understand what the shell-script is doing under the hood, just read it in a text viewer or editor. Ask here (reply to the thread), if you have questions, and report a bug, if you find one :-)

[SIZE=4]A. This tarball[/SIZE]

[grub-n-iso_multiboot.tar.gz]("http://phillw.net/isos/linux-tools/uefi-n-bios/grub-n-iso_multiboot.tar.gz")

contains the directory 'grub-n-iso_multiboot' and several files.

```
2015-06-11 09:17 about
2015-06-26 00:02 grub.cfg
2015-06-26 16:45 links2check
2015-06-11 15:00 make-alias
2015-06-26 16:36 mk-grub-n-iso
2015-06-23 11:17 mkusb-nox
2015-05-22 10:36 usb-pack_efi.zip

```

[SIZE=3]1. 'about' is a batch file, that writes 'About' information[/SIZE]

```
$ [COLOR=#0000cd]bash about[/COLOR]
#!/bin/bash

#       Copyright 2015 Nio Wiklund alias sudodus
#
#       GPLv3: GNU GPL version 3 <http://gnu.org/licenses/gpl.html>.
#
#       This  is  free  software: you are free to change and redistribute it.
#       There is NO WARRANTY, to the extent permitted by law.
#
#       This scipt is developed from the method developed by
#       Andre Rodovalho alias sysmatck in the Ubuntu Forums
#       [http://ubuntuforums.org/showthread.php?t=2276498](http://ubuntuforums.org/showthread.php?t=2276498)
#       and uses the file 'usb-pack_efi.zip' developed by him.
#
```

[SIZE=3]2. 'grub.cfg' is a template for Ubuntu family iso files[/SIZE]

```
set timeout=10
set default=0

menuentry "ubuntu.iso - live" {
 loopback loop /ubuntu.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso splash --
 initrd (loop)/casper/initrd.lz
}
menuentry "ubuntu.iso - persistent live" {
 loopback loop /ubuntu.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso splash persistent -- persistent
 initrd (loop)/casper/initrd.lz
}

```

This very simple grub.cfg file was developed from the file provided by Pendrivelinux at

[http://pendrivelinux.com/downloads/multibootlinux/grub.cfg](http://pendrivelinux.com/downloads/multibootlinux/grub.cfg)

[SIZE=3]3. 'links2check' is a batch file, that is used for managing the iso files.[/SIZE]

'links2check' help managing the daily iso files, to install those you want and keep them up to date. There are two zenity graphical menus to make it more user friendly to select the iso files. The output, however, is still in text mode, written into the terminal window.

When installed and running from the 'grub-n-iso' pendrive, change directory to '/isodevice' and run 'links2check'

```
[COLOR=#0000cd]$ sudo -H ./links2check[/COLOR]
```


[SIZE=3]4. 'make-alias' is a batch file, that creates the alias 'mkgni'[/SIZE]

that changes directory to 'grub-n-iso_multiboot' and prints a help text

```
[COLOR=#0000cd]$ mkgni[/COLOR]
```

[SIZE=3]5. 'mk-grub-n-iso' is the main subject in this post, a batch file, that builds a [multi]boot drive.
[/SIZE]
[SIZE=3]6. 'mkusb-nox' is a batch file for installing iso files into other pendrives.[/SIZE]

[mkusb-nox]("https://help.ubuntu.com/community/mkusb") is is used for installing 'debian' installer iso files, that work in text mode and do not boot via the 'grub-n-iso' method.

Example:

```
[COLOR=#0000cd]$ sudo mkusb-nox ubuntu.iso[/COLOR]
```

[SIZE=3]7. 'usb-pack_efi.zip' contains configuration files for UEFI mode[/SIZE]

It is made and uploaded by Andre Rodovalho alias sysmatck


[SIZE=4]B. Download the tarball from[/SIZE]

[http://phillw.net/isos/linux-tools/uefi-n-bios/grub-n-iso_multiboot.tar.gz](http://phillw.net/isos/linux-tools/uefi-n-bios/grub-n-iso_multiboot.tar.gz)

and check the md5sum with the file

[http://phillw.net/isos/linux-tools/uefi-n-bios/grub-n-iso.md5.asc](http://phillw.net/isos/linux-tools/uefi-n-bios/grub-n-iso.md5.asc)


[SIZE=4]C. Install grub-n-iso_multiboot[/SIZE]

The tarball is probably in your directory 'Downloads'. If that is where you want to install your directory 'grub-n-iso_multiboot', fine, otherwise I suggest that you move the tarball to where you want it, maybe directly in your home directory, and change directory to there.

[SIZE=3]1. Expand the tarball[/SIZE]

```
[COLOR=#0000cd]tar -cvzf grub-n-iso_multiboot.tar.gz grub-n-iso_multiboot[/COLOR]
```

[SIZE=3]2. Change directory to 'grub-n-iso_multiboot' and create an alias[/SIZE]

```
[COLOR=#0000cd]cd grub-n-iso_multiboot
make-alias[/COLOR]
```

[SIZE=3]3. Open a new terminal window and run
[/SIZE]
```
$ [COLOR=#0000cd]mkgni[/COLOR]
Usage:   sudo /home/sudodus/bin/mk-grub-n-iso <source.iso> <target device> [isotest]
Example: sudo /home/sudodus/bin/mk-grub-n-iso ubuntu.iso /dev/sdx
Example: sudo /home/sudodus/bin/mk-grub-n-iso multiboot /dev/sdx
Example: sudo /home/sudodus/bin/mk-grub-n-iso lubuntu.iso /dev/sdx isotest

Try again with the correct target device according to the list below

MODEL            NAME   FSTYPE LABEL MOUNTPOINT                   SIZE
SAMSUNG HD322HJ  sda                                            298.1G
                 |-sda1                                            80G
                 |-sda2                                            64G
                 |-sda4                                             1K
                 |-sda5              [SWAP]                         8G
                 |-sda6              /                             32G
                 |-sda7                                            14G
                 `-sda8                                         100.1G
OCZ-AGILITY3     sdb                                             55.9G
                 |-sdb1                                           3.7G
                 |-sdb2                                           320M
                 |-sdb4                                             1K
                 `-sdb5                                          51.9G
WDC WD1003FBYZ-0 sdc                                            931.5G
                 |-sdc1                                            50G
                 |-sdc2                                             1K
                 |-sdc5                                            20G
                 |-sdc6                                             8G
                 `-sdc7              /mnt/multimed-2            853.5G
Extreme          sdd                                             14.6G
                 |-sdd1              /media/sudodus/lub14042-32    64M
                 |-sdd2              /media/sudodus/isodevice       5G
                 `-sdd3              /media/sudodus/casper-rw     2.2G
DVD+-RW GSA-H21L sr0                                             1024M


```

'mkgni' is changing directory to 'grub-n-iso_multiboot' and running 'mk-grub-n-iso' without parameters, so that it writes help output. We see
that it should be run with superuser privileges, and that there should be two parameters, the <source file> and the <target device>. See the first example in the usage output

```
[COLOR=#0000cd]sudo ./mk-grub-n-iso ubuntu.iso /dev/sdx[/COLOR]
```

It is also possible to use the following four tokens, **-h**, **-v**,  **multiboot**, and **isotest**.

**-h** makes it write the same help output as without parameters.

**-v** makes it write version information

```
$ [COLOR=#0000cd]./mk-grub-n-iso -v[/COLOR]
mk-grub-n-iso 1.1
```

'multiboot' makes 'mk-grub-n-iso' look for all iso files in the current directory (grub-n-iso_multiboot), *.iso, and use them as source files.
See the ***second demo example*** and the output from the command

```
[COLOR=#0000cd]sudo ./mk-grub-n-iso multiboot /dev/sdx[/COLOR]
```

'isotest' makes 'mk-grub-n-iso' prepare for managing daily iso files in the current  directory, and make them bootable by adding menuentries to the target 'grub.cfg' file.
See the ***fourth demo example*** and the output from the command

```
[COLOR=#0000cd]sudo ./mk-grub-n-iso lubuntu-14.04.2-desktop-i386.iso /dev/sdd isotest[/COLOR]
```

The target device letter x should be selected according to the tree view of the devices. In this case the system is booted from '/dev/sda', so
'/dev/sdb' should be selected as the target device.

[COLOR=#ff0000]***WARNING!***

Check carefully that you specify the correct target device, otherwise you might destroy valuable data![/COLOR]

Wait a while! There is no iso file in the directory 'grub-n-iso_multiboot'


[SIZE=4]D. Get iso files[/SIZE]

[SIZE=3]1. Download one or more iso files with Ubuntu family desktop operating systems.[/SIZE]

You can find download information via this link

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

and check the md5sum.

Not now, but when the system is installed, you can also download, update incrementally with rsync and check the md5sum with

```
[COLOR=#0000cd]$ sudo -H ./links2check[/COLOR]
```

[SIZE=3]2. If you download an iso file with another distro,[/SIZE]

you need to configure the menuentry in grub.cfg manually. The following links may help

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

[SIZE=3]3. Make the iso files available
[/SIZE]
Single iso files can be entered with the full path (in the command line).

But if you want to create a multiboot pendrive, the source files (or links to the source files) must be in the directory 'grub-n-iso_multiboot'. It is also convenient the create links, even when you intend to install single iso files.

Create links from the location of the downloaded iso files to 'grub-n-iso_multiboot' (or move the files if you like). You can use symbolic
links as well as hard links. Avoid copying because it is a waste of disk space.

***Examples***

```
$ [COLOR=#0000cd]ls -1 ~/Downloads/iso[/COLOR]
kubuntu-14.04.2-desktop-amd64.iso
lubuntu-14.04.2-desktop-i386.iso
ubuntu-12.04-desktop-i386.iso
ubuntu-14.04.2-desktop-amd64.iso
ubuntu-mate-14.04.2-LTS-desktop-i386.iso
xubuntu-14.04.1-desktop-i386.iso

$ [COLOR=#0000cd]mkgni[/COLOR]
```

Example 1 - link all files (the final dots in the command lines are important)
```
[COLOR=#0000cd]ln -s ~/Downloads/iso/*.iso .[/COLOR]
```

Example 2 - link only standard ubuntu files
```
[COLOR=#0000cd]ln -s ~/Downloads/iso/ubuntu-1*.iso .[/COLOR]
```

Example 3 - link only 32-bit files
```
[COLOR=#0000cd]ln -s ~/Downloads/iso/*i386*.iso .[/COLOR]
```

Example 4 - link only 64-bit files
```
[COLOR=#0000cd]ln -s ~/Downloads/iso/*amd64*.iso .[/COLOR]
```


[SIZE=4] E. Demo runs[/SIZE]

[SIZE=3] 1. Create a portable system with a small foot-print[/SIZE]

```
[COLOR=#0000cd]sudo ./mk-grub-n-iso ~/Downloads/iso/lubuntu-14.04.2-desktop-i386.iso /dev/sdx[/COLOR]
```

```

sudodus@xw8400:/mnt/andre/grub-n-iso_multiboot$ [COLOR=#0000cd]sudo ./mk-grub-n-iso lubuntu-14.04.2-desktop-i386.iso /dev/sdd[/COLOR]
'lubuntu-14.04.2-desktop-i386.iso' is identified as the source ISO file

MODEL            NAME   FSTYPE LABEL       MOUNTPOINT   SIZE
Extreme          sdd                                   29.8G
                 |-sdd1 vfat   lub14042-32              787M
                 `-sdd2 ext2   casper-rw                  3G

Go ahead and overwrite /dev/sdd ? (g/q) [COLOR=#0000cd]**g**[/COLOR]
Using 'grub.cfg' in the current directory
Using 'usb-pack_efi' in the current directory
---------------------------------------------------------------------------
Create new system or Add new iso file? (c/a)? [COLOR=#0000cd]**c**[/COLOR]
 **[COLOR=#ff0000]FINAL WARNING:[/COLOR]**  Are you sure /dev/sdd ? (y/n) [COLOR=#0000cd]**y**[/COLOR]
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 0.16422 s, 6.4 MB/s
---------------------------------------------------------------------------
     Use gparted and create an msdos partition table
---------------------------------------------------------------------------
Suggested values, may be changed according to the size of 'lubuntu-14.04.2-desktop-i386.iso'
/dev/sdd1:  file system=[COLOR=#ff0000] fat32[/COLOR]   size= [COLOR=#ff0000]787[/COLOR]  Mibibytes to host grub and iso files
/dev/sdd2:  file system= [COLOR=#ff0000]ext2[/COLOR]    size=rest of device
======================
libparted : 2.3
======================
fatlabel: warning - lowercase labels might not work properly with DOS or Windows
tune2fs 1.42.9 (4-Feb-2014)
---------------------------------------------------------------------------
source=lubuntu-14.04.2-desktop-i386.iso
---------------------------------------------------------------------------
UEFI Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
BIOS Bootloader (maybe complaints)  : Installing for i386-pc platform.
Installation finished. No error reported.
Copying files ...
sending incremental file list
./
EFI/
EFI/BOOT/
EFI/BOOT/bootia32.efi
EFI/BOOT/bootx64.efi
boot/
boot/grub/
boot/grub/menu.lst
boot/grub4dos/
boot/grub4dos/g2ldr
boot/grub4dos/grub.exe
boot/memtest/
boot/memtest/memtest.bin
boot/memtest/memtest86+-5.01.bin

sent 2,311,447 bytes  received 188 bytes  4,623,270.00 bytes/sec
total size is 2,310,239  speedup is 1.00
mount: block device /mnt/multimed-2/test/lubuntu/trusty-desktop-i386.iso is write-protected, mounting read-only
< lubuntu-14.04.2-desktop-i386.iso pv > /mnt/target/lubuntu-14.04.2-desktop-i386.iso
 703MB 0:00:26 [26.2MB/s] [===============================================>] 100%            
Syncing the target device ...
MODEL            NAME   FSTYPE LABEL       MOUNTPOINT   SIZE
Extreme          sdd                                   29.8G
                 |-sdd1 vfat   lub14042-32              787M
                 `-sdd2 ext2   casper-rw                  3G
The target device is ready to use.
'lubuntu-14.04.2-desktop-i386.iso' was installed
sudodus@xw8400:/mnt/andre/grub-n-iso_multiboot$ 

```

[SIZE=3] 2. Create a multiboot system with only standard ubuntu files[/SIZE]

You can create extra space in the fat32 partition and add more iso files later.

```
[COLOR=#0000cd]mkgni
rm *.iso
ln -s ~/Downloads/iso/ubuntu-1*.iso .
sudo ./mk-grub-n-iso multiboot /dev/sdx
[/COLOR]
```

```

sudodus@xw8400:/mnt/andre/grub-n-iso_multiboot$ [COLOR=#0000cd]sudo ./mk-grub-n-iso multiboot /dev/sdd [/COLOR]
[sudo] password for sudodus: 
multi-boot: all iso files in the current directory will be used
kubuntu-14.04.2-desktop-amd64.iso
lubuntu-14.04.2-desktop-i386.iso
ubuntu-12.04-desktop-i386.iso
ubuntu-14.04.2-desktop-amd64.iso
ubuntu-mate-14.04.2-LTS-desktop-i386.iso
xubuntu-14.04.1-desktop-i386.iso
 WARNING:  the target device will be wiped and re-partitioned

MODEL            NAME   FSTYPE LABEL       MOUNTPOINT                   SIZE
Extreme          sdd                                                   29.8G
                 |-sdd1 vfat   lub14042-32 /media/sudodus/lub14042-32   787M
                 `-sdd2 ext2   casper-rw   /media/sudodus/casper-rw       3G

Go ahead and overwrite /dev/sdd ? (g/q) [COLOR=#0000cd]**g**[/COLOR]
Using 'grub.cfg' in the current directory
Using 'usb-pack_efi' in the current directory
 [COLOR=#ff0000]**FINAL WARNING:**[/COLOR]  Are you sure /dev/sdd ? (y/n) [COLOR=#0000cd]**y**[/COLOR]
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 0.162574 s, 6.4 MB/s
---------------------------------------------------------------------------
     Use gparted and create an msdos partition table
---------------------------------------------------------------------------
Suggested values, may be changed according to the size of 'multiboot'
/dev/sdd1:  file system= [COLOR=#ff0000]fat32[/COLOR]   size= [COLOR=#ff0000]5749[/COLOR]  Mibibytes to host grub and iso files
/dev/sdd2:  file system= [COLOR=#ff0000]ext2[/COLOR]    size=rest of device
======================
libparted : 2.3
======================
fatlabel: warning - lowercase labels might not work properly with DOS or Windows
tune2fs 1.42.9 (4-Feb-2014)
---------------------------------------------------------------------------
source=*.iso
---------------------------------------------------------------------------
UEFI Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
BIOS Bootloader (maybe complaints)  : Installing for i386-pc platform.
Installation finished. No error reported.
Copying files ...
sending incremental file list
./
EFI/
EFI/BOOT/
EFI/BOOT/bootia32.efi
EFI/BOOT/bootx64.efi
boot/
boot/grub/
boot/grub/menu.lst
boot/grub4dos/
boot/grub4dos/g2ldr
boot/grub4dos/grub.exe
boot/memtest/
boot/memtest/memtest.bin
boot/memtest/memtest86+-5.01.bin

sent 2,311,443 bytes  received 188 bytes  4,623,262.00 bytes/sec
total size is 2,310,239  speedup is 1.00
mount: block device /mnt/multimed-2/CD/ubuntu/14.04/kubuntu-14.04.2-desktop-amd64.iso is write-protected, mounting read-only
< kubuntu-14.04.2-desktop-amd64.iso pv > /mnt/target/kubuntu-14.04.2-desktop-amd64.iso
1.02GB 0:00:34 [30.4MB/s] [===============================================>] 100%            
mount: block device /mnt/multimed-2/test/lubuntu/trusty-desktop-i386.iso is write-protected, mounting read-only
< lubuntu-14.04.2-desktop-i386.iso pv > /mnt/target/lubuntu-14.04.2-desktop-i386.iso
 703MB 0:01:24 [8.29MB/s] [===============================================>] 100%            
mount: block device /mnt/multimed-2/CD/ubuntu/12.04/ubuntu-12.04-desktop-i386.iso is write-protected, mounting read-only
< ubuntu-12.04-desktop-i386.iso pv > /mnt/target/ubuntu-12.04-desktop-i386.iso
 701MB 0:00:46 [15.2MB/s] [===============================================>] 100%            
mount: block device /mnt/multimed-2/CD/ubuntu/14.04/ubuntu-14.04.2-desktop-amd64.iso is write-protected, mounting read-only
< ubuntu-14.04.2-desktop-amd64.iso pv > /mnt/target/ubuntu-14.04.2-desktop-amd64.iso
 996MB 0:00:59 [16.9MB/s] [===============================================>] 100%            
mount: block device /mnt/multimed-2/CD/ubuntu/14.04/ubuntu-mate-14.04.2-LTS-desktop-i386.iso is write-protected, mounting read-only
< ubuntu-mate-14.04.2-LTS-desktop-i386.iso pv > /mnt/target/ubuntu-mate-14.04.2-LTS-desktop-i386.iso
1.05GB 0:02:10 [8.23MB/s] [===============================================>] 100%            
mount: block device /mnt/multimed-2/CD/ubuntu/14.04/xubuntu-14.04.1-desktop-i386.iso is write-protected, mounting read-only
< xubuntu-14.04.1-desktop-i386.iso pv > /mnt/target/xubuntu-14.04.1-desktop-i386.iso
 916MB 0:01:29 [10.3MB/s] [===============================================>] 100%            
Syncing the target device ...
 The following iso files are found in the target drive:
/mnt/target/kubuntu-14.04.2-desktop-amd64.iso
/mnt/target/lubuntu-14.04.2-desktop-i386.iso
/mnt/target/ubuntu-12.04-desktop-i386.iso
/mnt/target/ubuntu-14.04.2-desktop-amd64.iso
/mnt/target/ubuntu-mate-14.04.2-LTS-desktop-i386.iso
/mnt/target/xubuntu-14.04.1-desktop-i386.iso
---------------------------------------------------------------------------
MODEL            NAME   FSTYPE LABEL     MOUNTPOINT   SIZE
Extreme          sdd                                 29.8G
                 |-sdd1 vfat   multiboot                8G
                 `-sdd2 ext2   casper-rw                6G
The target device is ready to use.
'*.iso' was installed
sudodus@xw8400:/mnt/andre/grub-n-iso_multiboot$ 

```

[SIZE=3] 3. Add another iso file to an existing [multi]boot pendrive.[/SIZE]

```
[COLOR=#0000cd]sudo ./mk-grub-n-iso ~/Downloads/iso/ubuntu-mate-14.04.2-LTS-desktop-i386.iso /dev/sdx[/COLOR]
```

```

sudodus@xw8400:/mnt/andre/grub-n-iso_multiboot$ [COLOR=#0000cd]sudo ./mk-grub-n-iso /mnt/multimed-2/CD/ubuntu/14.04/ubuntu-mate-14.04.2-LTS-desktop-i386.iso /dev/sdd[/COLOR]
[sudo] password for sudodus: 
'/mnt/multimed-2/CD/ubuntu/14.04/ubuntu-mate-14.04.2-LTS-desktop-i386.iso' is identified as the source ISO file

MODEL            NAME   FSTYPE LABEL     MOUNTPOINT                 SIZE
Extreme          sdd                                               29.8G
                 |-sdd1 vfat   multiboot                              8G
                 `-sdd2 ext2   casper-rw /media/sudodus/casper-rw     6G

Go ahead and overwrite /dev/sdd ? (g/q) [COLOR=#0000cd]**g**[/COLOR]
Using 'grub.cfg' in the current directory
Using 'usb-pack_efi' in the current directory
---------------------------------------------------------------------------
Create new system or Add new iso file? (c/a)? [COLOR=#0000cd]**a**[/COLOR]
 [COLOR=#ff0000]**FINAL WARNING: **[/COLOR] Are you sure /dev/sdd ? (y/n) [COLOR=#0000cd]**y**[/COLOR]
---------------------------------------------------------------------------
     Use gparted to check (and maybe change) the partitions
---------------------------------------------------------------------------
 The following iso files are found in the target drive:
kubuntu-14.04.2-desktop-amd64.iso
lubuntu-14.04.2-desktop-i386.iso
ubuntu-12.04-desktop-i386.iso
ubuntu-14.04.2-desktop-amd64.iso
ubuntu-mate-14.04.2-LTS-desktop-i386.iso  is already installed.
xubuntu-14.04.1-desktop-i386.iso
[COLOR=#ff0000]Exiting. Add another iso file![/COLOR]
sudodus@xw8400:/mnt/andre/grub-n-iso_multiboot$ [COLOR=#0000cd]sudo ./mk-grub-n-iso /mnt/multimed-2/CD/ubuntu/14.04/xubuntu-14.04.1-desktop-amd64.iso /dev/sdd[/COLOR]
'/mnt/multimed-2/CD/ubuntu/14.04/xubuntu-14.04.1-desktop-amd64.iso' is identified as the source ISO file

MODEL            NAME   FSTYPE LABEL     MOUNTPOINT   SIZE
Extreme          sdd                                 29.8G
                 |-sdd1 vfat   multiboot                8G
                 `-sdd2 ext2   casper-rw                6G

Go ahead and overwrite /dev/sdd ? (g/q) [COLOR=#0000cd]**g**[/COLOR]
Using 'grub.cfg' in the current directory
Using 'usb-pack_efi' in the current directory
---------------------------------------------------------------------------
Create new system or Add new iso file? (c/a)? [COLOR=#0000cd]**a**[/COLOR]
[COLOR=#ff0000]** FINAL WARNING:**[/COLOR]  Are you sure /dev/sdd ? (y/n) [COLOR=#0000cd]**y**[/COLOR]
---------------------------------------------------------------------------
     Use gparted to check (and maybe change) the partitions
---------------------------------------------------------------------------
 The following iso files are found in the target drive:
kubuntu-14.04.2-desktop-amd64.iso
lubuntu-14.04.2-desktop-i386.iso
ubuntu-12.04-desktop-i386.iso
ubuntu-14.04.2-desktop-amd64.iso
ubuntu-mate-14.04.2-LTS-desktop-i386.iso
xubuntu-14.04.1-desktop-i386.iso
======================
libparted : 2.3
======================
fatlabel: warning - lowercase labels might not work properly with DOS or Windows
tune2fs 1.42.9 (4-Feb-2014)
---------------------------------------------------------------------------
source=/mnt/multimed-2/CD/ubuntu/14.04/xubuntu-14.04.1-desktop-amd64.iso
---------------------------------------------------------------------------
UEFI Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
BIOS Bootloader (maybe complaints)  : Installing for i386-pc platform.
Installation finished. No error reported.
Copying files ...
sending incremental file list
./
EFI/
EFI/BOOT/
boot/grub/
boot/grub4dos/
boot/memtest/

sent 360 bytes  received 40 bytes  266.67 bytes/sec
total size is 2,310,239  speedup is 5,775.60
mount: block device /mnt/multimed-2/CD/ubuntu/14.04/xubuntu-14.04.1-desktop-amd64.iso is write-protected, mounting read-only
< /mnt/multimed-2/CD/ubuntu/14.04/xubuntu-14.04.1-desktop-amd64.iso pv > /mnt/target/xubuntu-14.04.1-desktop-amd64.iso
 930MB 0:01:25 [10.9MB/s] [===============================================>] 100%            
Syncing the target device ...
 The following iso files are found in the target drive:
/mnt/target/kubuntu-14.04.2-desktop-amd64.iso
/mnt/target/lubuntu-14.04.2-desktop-i386.iso
/mnt/target/ubuntu-12.04-desktop-i386.iso
/mnt/target/ubuntu-14.04.2-desktop-amd64.iso
/mnt/target/ubuntu-mate-14.04.2-LTS-desktop-i386.iso
/mnt/target/xubuntu-14.04.1-desktop-amd64.iso
/mnt/target/xubuntu-14.04.1-desktop-i386.iso
---------------------------------------------------------------------------
MODEL            NAME   FSTYPE LABEL     MOUNTPOINT   SIZE
Extreme          sdd                                 29.8G
                 |-sdd1 vfat   multiboot                8G
                 `-sdd2 ext2   casper-rw                6G
The target device is ready to use.
'/mnt/multimed-2/CD/ubuntu/14.04/xubuntu-14.04.1-desktop-amd64.iso' was installed
sudodus@xw8400:/mnt/andre/grub-n-iso_multiboot$ 

```

[SIZE=3]4. Create a portable system with a small footprint with a potential for isotesting[/SIZE]

This demo example features a new version of ***mk-grub-n-iso***.

i. The FAT32 boot partition is very small, and the iso files reside in an own partition will the ext4 file system, which is better when we expect to update these files during isotesting.

ii. The sizes of the partitions do not match the recommended values. ***The isodevice partition is big, 5GB***, to host several iso files. The whole pendrive is not used, because the system is prepared for a compressed image file, that should fit in a (slightly undersized) 8 GB pendrive (7,8 GB ~7.26 Gibibytes). Normally you should use the whole pendrive. See the attached screenshot, attachment #5.

iii. There are additional tools, that come with the system in order to manage the iso files. ***links2check*** help managing the daily iso files, to install those you want and keep them up to date. ***mkusb-nox*** is an alternative to make another USB boot drive for Ubuntu-Server and Lubuntu Alternate, which cannot boot via 'grub-n-iso'.

iv. When installed and running from the 'grub-n-iso' pendrive, change directory to '/isodevice' and run 'links2check'

```
[COLOR=#0000cd]$ sudo -H ./links2check[/COLOR]
```
[HR][/HR]
```
[COLOR=#0000cd]sudo ./mk-grub-n-iso lubuntu-14.04.2-desktop-i386.iso /dev/sdd isotest[/COLOR]
```

```

sudodus@xw8400:/mnt/multimed-2/test/grub-n-iso/andre$ [COLOR=#0000cd]sudo ./mk-grub-n-iso lubuntu-14.04.2-desktop-i386.iso /dev/sdd isotest[/COLOR]
'lubuntu-14.04.2-desktop-i386.iso' is identified as the source ISO file
---------------------------------------------------------------------------
links2check: iso files of the current developing version can be managed
(downloaded and upgraded) in a multi-boot type pendrive.
Select a stable system (released version) to have a working system
even if the developing version is broken for a period of time!

When installed and running from the 'grub-n-iso' pendrive, 
change directory to '/isodevice' and run 'links2check'

sudo -H ./links2check
---------------------------------------------------------------------------

MODEL            NAME   FSTYPE LABEL       MOUNTPOINT   SIZE
Extreme          sdd                                   14.6G
                 |-sdd1 vfat   lub14042-32               64M
                 |-sdd2 ext4   isodevice                  5G
                 `-sdd3 ext4   casper-rw                2.2G

Go ahead and overwrite /dev/sdd ? (g/q) [COLOR=#0000cd]**g**[/COLOR]
Using 'grub.cfg' in the current directory
Using 'usb-pack_efi' in the current directory
---------------------------------------------------------------------------
Create new system or Add new iso file? (c/a)? [COLOR=#0000cd]**c**[/COLOR]
**[COLOR=#ff0000]FINAL WARNING:[/COLOR]**  Are you sure /dev/sdd ? (y/n) [COLOR=#0000cd]**y**[/COLOR]
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 0.16773 s, 6.3 MB/s
---------------------------------------------------------------------------
     Use gparted and create an msdos partition table
---------------------------------------------------------------------------
Suggested values, may be changed according to the size of
lubuntu-14.04.2-desktop-i386.iso
/dev/sdd1:  file system= fat32   size= 64  Mibibytes for the grub files
/dev/sdd2:  file system= ext4   size= 787  Mibibytes or more* for iso files
/dev/sdd3:  file system= ext4   size=the rest of device for persistence
*) If you want to update the iso file here, you should have space for a
   temporary iso file while updating, so approximately an extra Gibibyte.
   You might also reserve space for installing more iso files later on.
======================
libparted : 2.3
======================
Information: You may need to update /etc/fstab.                           

fatlabel: warning - lowercase labels might not work properly with DOS or Windows
tune2fs 1.42.9 (4-Feb-2014)
tune2fs 1.42.9 (4-Feb-2014)
tune2fs 1.42.9 (4-Feb-2014)
---------------------------------------------------------------------------
source=lubuntu-14.04.2-desktop-i386.iso
---------------------------------------------------------------------------
UEFI Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
BIOS Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
Copying files ...
sending incremental file list
./
EFI/
EFI/BOOT/
EFI/BOOT/bootia32.efi
EFI/BOOT/bootx64.efi
boot/
boot/grub/
boot/grub/menu.lst
boot/grub4dos/
boot/grub4dos/g2ldr
boot/grub4dos/grub.exe
boot/memtest/
boot/memtest/memtest.bin
boot/memtest/memtest86+-5.01.bin

sent 2,311,447 bytes  received 188 bytes  4,623,270.00 bytes/sec
total size is 2,310,239  speedup is 1.00
mount: block device /mnt/multimed-2/CD/ubuntu/14.04/lubuntu-14.04.2-desktop-i386.iso is write-protected, mounting read-only
'grub.cfg' -> '/tmp/isotrg/grub.cfg'
'links2check' -> '/tmp/isotrg/links2check'
'mkusb-nox' -> '/tmp/isotrg/mkusb-nox'
< lubuntu-14.04.2-desktop-i386.iso pv > /tmp/isotrg/lubuntu-14.04.2-desktop-i386.iso
 703MB 0:00:14 [48.8MB/s] [=====================================================>] 100%            
Syncing the target device ...
MODEL            NAME   FSTYPE LABEL       MOUNTPOINT   SIZE
Extreme          sdd                                   14.6G
                 |-sdd1 vfat   lub14042-32               64M
                 |-sdd2 ext4   isodevice                  5G
                 `-sdd3 ext4   casper-rw                2.2G
The target device is ready to use.
'lubuntu-14.04.2-desktop-i386.iso' was installed

When installed and running from the 'grub-n-iso' pendrive,
change directory to '/isodevice' and run 'links2check'

sudo -H ./links2check

sudodus@xw8400:/mnt/multimed-2/test/grub-n-iso/andre$ 

```

[SIZE=4] F. System requirements[/SIZE]

[SIZE=3] 1. Host system[/SIZE]

An Ubuntu family operating system of ***version 14.04 LTS or newer***.

It is possible to use Ubuntu 12.04 LTS too, but it has an older version  of grub, and it can only make pendrives that boot in BIOS mode. Other linux distros are not tested.

Current LTS systems:

- Ubuntu 14.04 has grub version 2.02~beta2-9ubuntu1 and makes systems that work in UEFI mode and BIOS mode
- Ubuntu 12.04 has grub version 1.99-21ubuntu3.17 and makes systems that work in BIOS mode

- Example: HP Elitebook 8560p is typical of 'middle-aged to newer' HP professional class laptops that 'are difficult to boot from USB via grub'. Booting from grub2 works with the version of grub that comes with Ubuntu 14.04 LTS, but only when the **boot flag** is added to the partition.

[SIZE=3] 2. The installer 'mk-grub-n-iso' uses bash and built-in commands.[/SIZE]

'gparted' is used to create and edit partitions and create file systems. There must be a graphical mode for gparted to work.

```
[COLOR=#0000cd]sudo apt-get install gparted[/COLOR]
```

You may appreciate the improved feedback during the copying process with 'pv'.

```
[COLOR=#0000cd]sudo apt-get install pv[/COLOR]
```

[SIZE=3] 3. Computer[/SIZE]

'mk-grub-n-iso' does not need much computing power or RAM. It is possible to use 32-bit as well as 64-bit PCs (with Intel or AMD processors).

[SIZE=3] 4. Target system[/SIZE]

Automatic configuring for current Ubuntu family desktop iso files. Ubuntu 12.04 LTS works well as target system.

Manual configuring (creating the menuentries) using for example this link

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

[SIZE=3] 5. Target computer[/SIZE]

The target computers, where grub-n-iso_multiboot pendrives can run, include BIOS and UEFI mode, 32-bit and 64-bit hardware, 32-bit and 64-bit operating systems.

The system created by demo run 1:

```
[COLOR=#0000cd]sudo ./mk-grub-n-iso ~/Downloads/iso/lubuntu-14.04.2-desktop-i386.iso /dev/sdx[/COLOR]
```

can boot most PCs.

- There is a hardware limit. The computer may be too weak to boot a current version of Lubuntu, or there is some hardware, for example graphics chip, where the available drivers do not work. But then it is possible to include iso files for other linux distros.

- Another limit is where the system is so locked down by a non-standard UEFI system, that nothing but Windows works.

---

### Post by sudodus on 2015-06-19
Booting linux via grub does not use the boot flag, but the BIOS of 'middle-aged to newer' HP computers needs the boot flag to recognize a USB pendrive as a boot drive.

- Example: HP Elitebook 8560p is typical of 'middle-aged to newer' HP  professional class laptops that 'are difficult to boot from USB via  grub'. Booting from grub2 works with the version of grub that comes with  Ubuntu 14.04 LTS, but only when the **boot flag** is added to the partition.

I think a boot flag will do no harm in other computers, so I ***added a boot flag*** to these grub-n-iso systems, to the uploaded compressed image files as well as in the shell-script ***mk-grub-n-iso***.

---

### Post by sudodus on 2015-06-26
I have prepared a new version of the shell-script ***mk-grub-n-iso*** and a new shell-scripts ***links2check*** and ***links2update***. This will offer a new possibility to make a multiboot pendrive with the same properties as described earlier in this thread: they work in (almost) all PC computers. You will be able to ***manage the daily build iso files*** of the Ubuntu family flavours, to install and update them incrementally directly in the pendrive, which saves time and effort. So it should be a convenient tool  for all our iso-testers as well as for other people who want to try the bleeding edge version.

You are welcome to ask questions and suggest improvements :-)
[HR][/HR][SIZE=4]
Create or download a portable system with a small footprint with a potential for isotesting[/SIZE]

[SIZE=3]1. Create the system according to 'Demo run' 4 in post #8 or[/SIZE]

[SIZE=3]2. Download a compressed image file - an upgraded version of the system in post #6[/SIZE]

A compressed image file is made from a system that boots via grub and a  Lubuntu  iso file. The intention is to have one USB pendrive, which can  boot the  vast majority of computers. This is a ***smaller and simpler*** alternative than what is described in post #1, with the additional benefit, that it can easily be maintained with the daily build of the developing version of Ubuntu and the Ubuntu flavours.

The integrity is checked with md5sum, and the iso files are updated incrementally with rsync from the Ubuntu server. This is done automatically, but must be started by you. The intention is not to kill the server by continuous requests, but you initiate a request, when you have time to test an iso file ;-)

***The grub system*** works in UEFI and BIOS mode. It is developed from a multiboot system for UEFI by Andre Rodovalho. See the following link,
[URL="http://ubuntuforums.org/showthread.php?t=2276498"]
How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images[/URL]

***Lubuntu 14.04.2 LTS 32-bit:*** works with 32-bit processors and 64-bit processors in old, middle-aged and new computers. The boot option [forcepae]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M") should be used when installing Lubuntu into computers with Pentium M and Celeron M processors that lack the PAE flag.

Lubuntu is booted via grub and the standard Lubuntu ISO file, but in a  new way, that allows it to work in both UEFI and BIOS mode. A partition  with the label **casper-rw** provides persistence. Other versions and flavours, also the daily built ISO files will be booted in the same way.

[SIZE=4]Installation[/SIZE]

Install from the compressed image files

[[COLOR="#FF8C00"]dd_lubu-14.04.2-desktop-i386_isotest_7.8GB.img.xz[/COLOR]]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_lubu-14.04.2-desktop-i386_isotest_7.8GB.img.xz")
[[COLOR="#FF8C00"]dd_lubu-14.04.2-desktop-i386_isotest1_7.8GB.img.xz[/COLOR]]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_lubu-14.04.2-desktop-i386_isotest1_7.8GB.img.xz"), links2update added and some tweaks saved in the casper-rw partition.
[dd_lubu-14.04.2-desktop-i386_isotest2_7.8GB.img.xz]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_lubu-14.04.2-desktop-i386_isotest2_7.8GB.img.xz"), some tweaks saved in the .bashrc file in the home-rw partition.

with the following md5sums (and sizes 695, 698, [COLOR="#0000FF"]733[/COLOR] Mibibytes compressed).

```

25303e85a9b2c026ff4e68d24dba3fc1  dd_lubu-14.04.2-desktop-i386_isotest_7.8GB.img.xz
6621a6bd66296a7fc11a8eca7ddc1fe6  dd_lubu-14.04.2-desktop-i386_isotest1_7.8GB.img.xz
[COLOR="#0000FF"]97e9113c4d94e12992f76f004bb8cef1  dd_lubu-14.04.2-desktop-i386_isotest2_7.8GB.img.xz[/COLOR]

```

to a USB pendrive (8 GB or more) with ***mkusb*** in linux or ***Win32 Disk Imager*** in Windows, which is described in the following links

[SIZE=3]Linux[/SIZE]

It is straight-forward with ***mkusb*** in linux according to [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[SIZE=4] [SIZE=3]Windows[/SIZE][/SIZE]

In Windows you should expand the compressed image file with for example ***7-zip*** before using ***Win32 Disk Imager***.

Download the following help programs  
[http://www.md5summer.org](http://www.md5summer.org) 
[http://www.7-zip.org](http://www.7-zip.org) 
[http://sourceforge.net/projects/win32diskimager](http://sourceforge.net/projects/win32diskimager) 

First check that the download was successful with **md5summer**.

Next extract the image file with **7-zip** (It is also possible with **winzip**) 

from **dd_lubuntu-14.04.2-desktop-i386_4GB.img.xz** to **dd_lubuntu-14.04.2-desktop-i386_4GB.img**

And then use ***Win32 Disk Imager*** according to [https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

[SIZE=4]Method[/SIZE]

I made this system for USB pendrives to boot all PC (Intel/AMD) computers - 'grub-n-iso' - according to [this link]("http://ubuntuforums.org/showthread.php?t=2276498&p=13299549#post13299549")

[SIZE=4]Enjoy :smile:
[/SIZE]
**- *Live system***

When you run a live system, the FAT32 partition is read-only. You can   read files that were written there before you booted. For example, when   connected to another linux computer as a normal data   pendrive. If you create other partitions (for example at the end of the   drive), you can read and write files by the live system. You can even   read the casper-rw partition (made for persistence).

But Windows can only read from the first partition, which is very small in this case. Build your own system according to post #8 if you want a bigger first partition for transfer of files to and from Windows.

***- Persistence***

When you run a persistent live system, the FAT32 partition is   read-write. You can read and write files  to the free space in that   partition. For example, you can write and remove  files, that can be   read by Windows when connected to another computer as a normal  data   pendrive. [COLOR=#ff0000]But beware, do not remove any system files from the FAT32 partition![/COLOR] Persistence is sensitive to other errors too, so[COLOR=#ff0000] ***backup*** the casper-rw partition regularly[/COLOR].

There might be problems if you use the casper-rw partition for different  iso files and install program packages. Data files can be shared  without problems. If the persistence is damaged, you can always remove  all files, or simply format it (make a new ext4 file system and turn of journaling for speed and decreased wear).

- More than one persistent system can be made by adding Knoppix or Puppy Linux. See [this thread]("http://ubuntuforums.org/showthread.php?t=2260697").

***- Expand the FAT32 partition 'grow it'***

It is possible to move the second partition to the end of the drive and grow the first partition according to [GrowIt.pdf]("http://phillw.net/isos/linux-tools/9w/GrowIt.pdf").

Use the unallocated space, if there is space behind the second partition   (in a bigger than 8 GB pendrive). You can move the casper-rw partition   in order to increase the size of the FAT32 partition to make room for   another iso file or increase the size of the casper-rw partition or   create a completely new partition. Use a fast USB 3  pendrive for   persistence. Such pendrives have almost always at least 16  GB storage   space. (USB 2 pendrives are slow with persistence.)

It is also possible to run this system from HDD or SSD in an external USB 3 and eSATA box. That can make it almost as fast as running from an internal drive, but if you are testing to install, it is a better idea to use the fast drive as target for the installation.

***- Manage the daily built iso files of your choice***

Notice that a pendrive with this system can  be upgraded directly. So you get the upgrade directly from the Ubuntu server to the pendrive without a detour to a hard disk drive.

When installed and running from the 'grub-n-iso' pendrive, change directory to **/isodevice** and run ***links2check***

 ```

cd /isodevice
sudo -H ./links2check
sudo -H ./links2update

```

to maintain the system. There are more details in the next post #11.

Use [mkusb-nox]("https://help.ubuntu.com/community/mkusb/v7") to install from the Ubuntu Server and Lubuntu alternate iso files, that do not boot via grub.

[SIZE=4]See also ...[/SIZE]

[http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sudodus on 2015-06-26
You will be able to ***manage the daily build iso files***  of the Ubuntu family flavours, to install and update them incrementally  directly in the pendrive, which saves time and effort. So a 'grub-n-iso' pendrive with the shell-scripts ***links2check*** and ***links2update*** should be a  convenient tools  for all our iso-testers as well as for other people  who want to try the bleeding edge version.

[SIZE=4] Manage the daily built iso files of your choice[/SIZE]

Notice that a pendrive with this system can  be upgraded directly. So  you get the upgrade directly from the Ubuntu server to the pendrive  without a detour to a hard disk drive. Of course you have to reboot to  test/use the new version, but this direct method is convenient and saves  time. Pendrives are often slow, and I have found that rsync behaves  much better than zsync, when the target drive for updating is a  pendrive. (So this system uses rsync instead of zsync, that seemed  better at first glance.)

One big advantage is that there is no need for copying/cloning/flashing  from the internal drive to the pendrive. The slowness of the internet  connection matches quite well the slowness of a USB 2 connection, so you  don't lose much time anyway. 

When installed and running from the 'grub-n-iso' pendrive, change directory to **/isodevice** and run ***links2check*** to create and maintain the system. You arrive at the main (zenity) menu. See attachment #1, where you can select a flavour (in this case Ubuntu). After that you arrive at the iso file menu, where you select architecture (in this case 64-bit). See attachment #2. You can follow the process in the terminal window, how the MD5SUMS file is downloaded, and used, but there is no iso file yet. Then rsync starts downloading the iso file and finally it is checked with md5sum.

```

[COLOR=#0000cd]cd /isodevice
sudo -H ./links2check
sudo -H ./links2update[/COLOR]

```

Starting from the compressed image file [dd_lubu-14.04.2-desktop-i386_isotest1_7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_lubu-14.04.2-desktop-i386_isotest1_7.8GB.img.xz) and running a ***persistent*** live session, you are helped by some tweaks, that are prepared and saved in the casper-rw file, so that you arrive easily in the directory **/isodevice** and can start managing the ISO files.

***links2update*** makes daily updating of the ISO files easy. There is only one (zenity) menu, and you select one file or all files to update.

But you are not ready yet. You should also link to the targets in the current directory. Start ***links2check*** again and select the first or last line for this linking mode. See attachment #3. There is also output text in the terminal window (similar to the following example).

```
$ [COLOR=#0000cd]sudo -H ./links2check [/COLOR]
Using template 'grub.cfg' in the current directory
'ubuntu-wily-desktop-amd64.iso' -> 'cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.iso'
1 linked daily iso file(s)   - with grub menuentries
1 linked regular iso file(s) - with grub menuentries
0 iso file(s) that cannot be booted by the 'grub-n-iso' method
$ 

```

There are grub menuentries for two iso files, the original 'Lubuntu-14.04.2-desktop-i386.iso' and the new 'Ubuntu-wily-desktop-amd64.iso'. The file grub-final.cfg is copied ***automatically*** to the active boot directory.

```
[COLOR=#0000cd]sudo cp grub-final.cfg 'mountpoint'/boot/grub/grub.cfg[/COLOR]
```

```
set timeout=10
set default=0

menuentry "Lubuntu-14.04.2-desktop-i386.iso - live" {
 set root=(hd0,2)
 loopback loop /lubuntu-14.04.2-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lubuntu-14.04.2-desktop-i386.iso splash --
 initrd (loop)/casper/initrd.lz
}
menuentry "Lubuntu-14.04.2-desktop-i386.iso - persistent live" {
 set root=(hd0,2)
 loopback loop /lubuntu-14.04.2-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lubuntu-14.04.2-desktop-i386.iso splash persistent -- persistent
 initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu-wily-desktop-amd64.iso - live" {
 set root=(hd0,2)
 loopback loop /cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.iso
 linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=/cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.iso splash --
 initrd (loop)/casper/initrd.lz
}
menuentry "Ubuntu-wily-desktop-amd64.iso - persistent live" {
 set root=(hd0,2)
 loopback loop /cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.iso
 linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=/cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.iso splash persistent -- persistent
 initrd (loop)/casper/initrd.lz
}

```

The next time you boot, there will be grub menu items also for the Ubuntu wily daily build (according to this example).

Use links2update to let rsync update the iso file the next day or later, when you have time again to test your favourite Ubuntu flavour daily iso file(s).

Use [mkusb-nox]("https://help.ubuntu.com/community/mkusb/v7") to install from the Ubuntu Server and Lubuntu alternate iso files, that do not boot via grub.

---

### Post by sudodus on 2015-07-13
[SIZE=4]Comments and tips[/SIZE]

***Where does it work?***

Post #1. One pendrive for all PC (Intel/AMD) computers - Ubuntu 64-bit and Lubuntu 32-bit

Ubuntu 64-bit works in BIOS and UEFI mode, also with secure boot. Lubuntu 32-bit works with 32-bit and 64-bit computer hardware, so it adds ability to boot 32-bit computers including old hardware.

The posts #(6, 7, 8, 10, 11) describe 'grub-n-iso' systems, that can boot 32-bit and 64-bit Ubuntu family operating systems in BIOS and UEFI mode, but these 'grub-n-iso' systems do not work with secure boot.

***Ramdrive***

Using the [boot option](https://help.ubuntu.com/community/BootOptions) **toram** makes it possible to unmount the mounted partition(s) on the boot drive, and it can be removed. **toram** makes the system copy all of the content from the squashfs to RAM, so the boot process is slower, but after that the system is very fast and responsive.

If you haven't got enough RAM, there can be problems, otherwise it works very well.

***casper-rw and home-rw***

A casper-rw partition is standard for persistence. [C.S.Cameron](http://ubuntuforums.org/member.php?u=317145) suggests casper-rw + home-rw partitions, and it is even better, particularly if you have plenty of space in the pendrive or where you keep the partitions for persistence, because the home-rw partition will probably survive even if the casper-rw partition is damaged.

---

### Post by sudodus on 2015-07-22
[SIZE=4]'grub-n-iso' works also with a Linux Mint 17 iso file[/SIZE]

I downloaded linuxmint-17.2-cinnamon-64bit.iso, copied it to a 'grub-n-iso' pendrive and ran

```
cd /isodevice
sudo -H ./links2check
```

selected 'Link to targets in the current directory'

and rebooted. It worked without tweaks, and now I know that the 'grub-n-iso' system according to this thread works also with current Linux Mint iso files.

---

### Post by sudodus on 2015-07-24
[SIZE=4]New features in a new compressed file for a 'grub-n-iso' system to manage iso-testing[/SIZE]

The compressed image file [dd_lubu-14.04.2-desktop-i386_isotest1_7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_lubu-14.04.2-desktop-i386_isotest1_7.8GB.img.xz) contains some tweaks. They are activated if you run a ***persistent*** live session, so that you arrive easily in the directory **/isodevice** and can start managing the ISO files.

You start with ***links2check*** but the new script ***links2update*** makes daily updating of the ISO files easier than before.

-o-

I have found that you can have more than one set of persistence in the casper-rw partition. You start with persistence for a released system Lubuntu 14.04.2 LTS.

After that you install one or more daily build flavours of Ubuntu (when this is written it is the version Wily). If you boot Wily with persistence, it will be stored in

```
.../casper-rw/upper
```

and will not interfere with Lubuntu 14.04.2 LTS, which is stored in ```
/casper-rw
```

But the different flavours of Ubuntu Wily will interfere with each other, which is no problem for data files, but if you test both 32-bit and 64-bit versions and install or update program packages, where 32-bit versions are different from 64-bit versions, there can be big problems. So it is a good idea to back up the content of the casper-rw file, for example in a tarball.

---

### Post by sudodus on 2015-07-29
During iso-testing of Lubuntu Wily alpha 2, I booted the installer via this 'grub-n-iso' method. It seems to have confused the alternatives of the installer for automatic selection: I did not get any option to 'Install alongside and auto-resize', only upgrade 14.04.2 LTS, erase 14.04.2 LTS, erase the whole drive, and 'something else'. It was not possible to run the testcase 'Install (auto-resize)'.

[Bug #1479405](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1479405) affects booting via 'grub-n-iso', while booting from a pendrive made with [mkusb](https://help.ubuntu.com/community/mkusb) brings 'Install alongside with auto-resize'.

The other alternatives of the installer (ubiquity) work as they should when booted via 'grub-n-iso'.

---

### Post by sudodus on 2015-07-31
@ ventrical,

What about the attached screenshots of mkusb windows? (Legacy is the fallback when zenity is not compiled with webkit, so there is no rendering of html).

1. Do you suggest further changes to some of these four windows?

2. Is there any more window, where you think that the text should be changed?

-o-

I [s]intend to move[/s] moved this dialogue to the thread where it belongs, [Howto make USB boot drives](http://ubuntuforums.org/showthread.php?t=1958073) except this post - with a link to help you find the new location.

---

### Post by Dkaz on 2015-08-03
@ Sudodus

I'm a newbie to Linux as a whole so I want to start by thanking you for the detailed guides :).  I am currently dual booting Windows 7 and Ubuntu on my secondary laptop.  I was wondering if it is possible/bad/ok/whatever to have more than just those 2 operating systems.  Per se, could I trio boot my current setup plus Linux Mint?  If so, would I just go through the normal installation process like I was setting up a dual boot? I am going into college in the fall as a computer engineering student so I'm trying to broaden my horizons as much as possible.  Thanks!

---

### Post by sammiev on 2015-08-03
> **Dkaz said:**
> @ Sudodus

I'm a newbie to Linux as a whole so I want to start by thanking you for the detailed guides :).  I am currently dual booting Windows 7 and Ubuntu on my secondary laptop.  I was wondering if it is possible/bad/ok/whatever to have more than just those 2 operating systems.  Per se, could I trio boot my current setup plus Linux Mint?  If so, would I just go through the normal installation process like I was setting up a dual boot? I am going into college in the fall as a computer engineering student so I'm trying to broaden my horizons as much as possible.  Thanks!

I had many OS on one laptop with little issues. 

If you have the room it can be done.

As always, backup any or all data.

---

### Post by sudodus on 2015-08-04
Welcome to the Ubuntu Forums :-)

+1 (I confirm the reply by sammiev.)

You can install many linux distros/versions in the same computer (in the same or different internal or external drives). I suggest that you

0. backup your current systems, because things can go wrong,

1. boot a live session from the install DVD/USB drive,

2. edit the partitions with ***gparted*** before you start installing. This way you can 'see' what you are doing in the graphical user interface, so that you get a good structure and suitable sizes of the partitions. Maybe 8 GB is minimum size for testing a distro and 20 GB to run it and have some space for new program packages and various data files. You can share the swap file unless you want to hibernate the systems. It is a good idea to have a common **data** partition. Since you have Windows, the data partition should have the NTFS file system (because Windows does not read linux file systems). Do not write from linux into the system partition of Windows, C:

3. run the installer and install the third system into the partitions you have prepared. Use manual partitioning: select ***Something else*** at the partitioning window.

---

### Post by Dkaz on 2015-08-04
Thanks for the info! Got it working

---

### Post by sudodus on 2015-08-06
[SIZE=4]New features in a new compressed file for a 'grub-n-iso' system to manage iso-testing[/SIZE]

The compressed image file [dd_lubu-14.04.2-desktop-i386_isotest2_7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_lubu-14.04.2-desktop-i386_isotest2_7.8GB.img.xz) contains some tweaks. They are activated if you run a ***persistent*** live session, so that you arrive easily in the directory **/isodevice** and can start managing the ISO files.

You start with ***links2check*** but the new script ***links2update*** makes daily updating of the ISO files easier than before.

rsync is run with the option -v so that the actual amount downloaded is shown after updating.

Alongside the casper-rw partition there is also a **home-rw** partition, which makes the content of your home directory safer than when it is stored within the casper-rw partition.

```
$ sudo lsblk -fm
NAME   FSTYPE   LABEL                    MOUNTPOINT                 NAME     SIZE OWNER GROUP MODE
sda                                                                 sda     14.6G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat     lub14042-32              /media/lubuntu/lub14042-32 &#9500;&#9472;sda1    64M root  disk  brw-rw----
&#9500;&#9472;sda2 ext4     isodevice                /isodevice                 &#9500;&#9472;sda2     4G root  disk  brw-rw----
&#9500;&#9472;sda3                                                              &#9500;&#9472;sda3     1K root  disk  brw-rw----
&#9500;&#9472;sda5 ext4     casper-rw                                           &#9500;&#9472;sda5   1.6G root  disk  brw-rw----
&#9492;&#9472;sda6 ext4     home-rw                  /home                      &#9492;&#9472;sda6   1.6G root  disk  brw-rw----

```

---

### Post by sudodus on 2015-08-12
[SIZE=4]Test results with mk-grub-n-iso-s which is built into mkusb 10[/SIZE]

I have been able to boot ToriOS that uses an old Ubuntu 12.04 LTS non-pae kernel (not forcepae, not fake-pae, really non-pae) in UEFI mode. I did it with ***mkusb version 10 with a modified grub-n-iso installer*** added to create persistent live USB drives. This system does not boot directly from grub and an iso file, but from a copy of the iso file cloned into partition #2. Partition #1 is the boot partition (and EFI partition). Partition #3 is a casper-rw partition. ***The idea is to add persistence and make it a more complete tool for the Ubuntu family and some community re-spins with similar boot structure.*** Booting via grub from a cloned copy of the iso file into partition #2 makes it work with some re-spins that do not boot from an iso file (at least I cannot do it).

```
[SIZE=3]sdf                                                sdf    119,2G
&#9500;&#9472;sdf1 **vfat**    ToriOSdaily      /media/ToriOSdaily &#9500;&#9472;sdf1  59,3G
&#9500;&#9472;**sdf2 iso9660 **torios-live      /media/torios-live &#9500;&#9472;sdf2   645M
&#9492;&#9472;sdf3 **ext4 **   live-rw          /media/live-rw     &#9492;&#9472;sdf3  59,3G[/SIZE]
```

This version of mkusb (10.0.1) needs testing before even getting into the unstable PPA, and you find the way to get it via this link: [ Re: Howto make USB boot drives post #120](http://ubuntuforums.org/showthread.php?t=1958073&page=6&p=13337410#post13337410)

[HR][/HR]
***Boot alternatives in the grub menu:***

[LIST]
[*]"distro - persistent live"
[*]"distro - live"
[*]"distro - recovery mode"
[/LIST]

***The following distros are tested and work***

**[COLOR="#446600"]The whole Ubuntu family's *desktop* iso files work**[/COLOR]: Kubuntu, Lubuntu, standard Ubuntu, Xubuntu, ...

[LIST]
[*]ubuntu-14.04.2-desktop-amd64.iso
[*]wily-desktop-amd64.iso ...
[/LIST]

The following linux distros based on Ubuntu are also tested and work

[LIST]
[*]bento-trusty-rc2-i386.iso
[*]bodhi-2.4.0-64.iso
[*]extix-14.2-64bit-isoh-persistent-836mb-141024.iso
[*]linuxmint-17.2-cinnamon-64bit.iso
[*]lxle-12044-32.iso (not isohybrid, current versions of LXLE have hybrid iso files)
[*]ToriOS-beta.iso (based on Ubuntu 12.04 i386 non-pae)
[/LIST]

***The following distros boot but persistence fails***

The computer boots but cannot get persistence. (Debian advices to clone and add an ext partition with the label live-rw. It boots but I can not make persistence work with Ubuntu systems and not with Debian Wheezy and Jessie that way either.)

[LIST]
[*]debian-live-8.0.0-i386-gnome-desktop.iso
[*]obi_Trusty-nonpae-txt5-9w.iso (based on Debian Wheezy)
[/LIST]

***Complete failure***

No Ubuntu/Debian based distro has failed completely yet, but for example Mageia does not work at all. The boot structure is not recognized. You must edit the file 'boot/grub/grub.cfg' in the first partition.

[LIST]
[*]Mageia-4.1-LiveDVD-GNOME-x86_64-DVD.iso
[/LIST]

***I think that cloning is still the best method. It is the standard method of mkusb.***

Cloning works also for distros with different boot structure as long as the iso file is treated with isohybrid. And most modern linux distros are, so cloning makes a working live session also for most of these linux distros, and I think that it is still the best method. Most of the time there is no need for persistence, and a tool for Ubuntu need not work for all other distros. But it should be very reliable for the Ubuntu family of operating systems.

---

### Post by sudodus on 2015-08-28
[SIZE=4]Fine-tuning in mkusb 10.0.3[/SIZE]

A new version (able to create 'live only' as well as 'persistent live' USB drives) is uploaded and available via the **unstable PPA** and **phillw.net**

See this link [https://help.ubuntu.com/community/mkusb/gui](https://help.ubuntu.com/community/mkusb/gui)

---

### Post by Raymond Petit on 2015-09-07
Dear sudodus,

I followed the instructions in post #7, because I don't have access to any computer that is running Linux.  I used my HP Envy X2 which is currently on Windows 10.  The picture below is what I have on the pen drive I created.  It fails to boot!  All I get is a black screen.  I reformatted the drive after the first attempt and still, no go.  Secure boot in the bios is turned off!  USB is set before the ssd in the boot order.  The only thing I was unable to do was check the md5 sum, the utility in this thread doesn't see the downloaded zip file.  What am I missing or any suggestions?

---

### Post by sudodus on 2015-09-08
Hi Raymond,

> It fails to boot! All I get is a black screen.

Please specify with more details what happens!

1. Do you get to the grub menu (as in the attached screendump in post #7)?

1.1 If that is the case it boots, but cannot get the Ubuntu system running.

1.2 Is your HP Envy a 32-bit system? If that is the case, you should try to boot from an i386 iso file.

2. If you do not get to the grub menu: Is the screen black all the time? Is there any 'sign of life' from the computer, when you boot?

-o-

Did you follow this instruction?
> In Windows you should expand the compressed image file with for example 7-zip before using Win32 Disk Imager, which is described with more details in the previous post.


You can use [Md5summer in Windows](http://www.md5summer.org/) to check the md5sum.

I could add these details: [how to run Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

If the md5sum of the compressed image file is good, and the process to expand and copy it to the pendrive was successful, but it does not boot, we have to do some trouble-shooting.

I know that there are problems with some of the new HP computers. They use an UEFI system, that does not comply with the UEFI standard, but are tweaked in order to make it hard to boot anything but Windows. I'm not sure, but that might be the problem with your HP Envy X2. We have two older HP laptops (with Intel i5) in my family, and 'my grub-n-iso pendrives' work in UEFI mode and BIOS mode in those computers.

1. Can you boot from the grub-n-iso multiboot pendrive in another computer?

2. Can you boot from the grub-n-iso multiboot pendrive in BIOS mode (not UEFI), maybe in another computer?

3. Does it work better with another pendrive (if you have one)? Some pendrives are good booters and some are no so good.

-o-

You can search the internet for ***ubuntu HP Envy X2***. I did, and found several relevant links, that might help you make it work.

---

### Post by Raymond Petit on 2015-09-08
Answers:  

1. No, there is no Grub menu.
1.2  Yes, it is a 32 bit system!  (From reading the suggestion for this unit was to boot from a 64 bit file.)
2.  Yes there is signs of life!  The windows light comes on, then you can see the back light is obviously on, but that's it.  It just sits there.

Next question:  I had to use an application called "Unpack"  The 7zip and WinZip versions I downloaded from Microsoft's store could not see the folder in my downloads folder (strange and annoying)  Used win32 disk imager which ran with no problems.  To be sure, I did it again after reformatting the drive to make certain it was on fat32.  I take it from your questions that the picture I attached of the the file system on the drive is correct?  I checked the md5 by copying the file to my phone, I'll attach a screen shot.  It does match!

Finish:  I'll try to borrow another computer to test this drive (Kingston 8gig).  I can also use another drive that I have (16 gig) and test that.  I'll re-read the instruction and try to find a 32 bit process of what I did according to your instructions.  Plus, I'll follow your links for further reading.  Thanks for helping!!!

---

### Post by sudodus on 2015-09-09
> I take it from your questions that the picture I attached of the the file system on the drive is correct?

It look OK, but that picture does not tell everything. It is a good idea to try with another computer. I have Kingston pendrives, that boot work well except one 8 GB pendrive. They are 'individuals'.

Did you find any interesting tips, when you searched the internet for ***ubuntu HP Envy X2***?

---

### Post by Raymond Petit on 2015-09-09
> **sudodus said:**
> It look OK, but that picture does not tell everything. It is a good idea to try with another computer. I have Kingston pendrives, that boot work well except one 8 GB pendrive. They are 'individuals'.

Did you find any interesting tips, when you searched the internet for ***ubuntu HP Envy X2***?

Yes.  Some I've seen before, but one from a guy claiming to have it running on one of the X2 models.  He says he used something called "boot repair".  Now, I'm not entirely sure how that works, but am looking for a video tutorial.  I already read how to install in on a separate pen drive, but It would be nice to ascertain that using it won't irreparably screw up the UEFI on this unit.  Also, since the pen drive I've already made won't boot who says this one will do anything but just sit there also, lol!  I'm confused as to how one will boot while the other won't, seems to me it would be a process done through command line.  Haven't managed to borrow a laptop yet so I am as yet not able to test the drive as is.  Will keep appraised.  Again, thanks for helping!

[http://ubuntuforums.org/showthread.php?t=2123975&page=2](http://ubuntuforums.org/showthread.php?t=2123975&page=2)

EDIT:  After reading it again maybe the process hinges on first creating another partition on Windows that tricks UEFI into believing there is something else to boot into?  Then, once you are able to run Ubuntu from the disk, you can make the "boot repair" operation?  Am I on the right track?

EDIT:  Reading another post there is mention of setting a password to get further options in the UEFI menu (probably why mine are blacked out) and then being able to set anther boot medium as "trusted".  It may be as simple as that, though I doubt it.  At least it's another clue.  Unfortunately for me I don't have more time today to do anything else about it.

---

### Post by sudodus on 2015-09-09
Maybe. Anyway this link helps you get started with Boot-Repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It is a good idea to first create a ***BootInfo summary*** (without doing any repair). Upload the BootInfo summary report, and post a link to it in a reply. That will help us help you.

---

### Post by Raymond Petit on 2015-09-11
> **sudodus said:**
> Maybe. Anyway this link helps you get started with Boot-Repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It is a good idea to first create a ***BootInfo summary*** (without doing any repair). Upload the BootInfo summary report, and post a link to it in a reply. That will help us help you.

At the moment I'm at a standstill.  Boot Repair doesn't seem to be available as an ISO download anywhere.  Not on Sourceforge or anywhere else!  I had hoped to test this guys claim that he got his Envy working by installing Boot Repair on a flash drive, but that's not possible without being able to download it.  I may be able to track down a physical copy on a disk by going to a local business that deals in Linux.  You wouldn't have the ISO file lying around would you?

EDIT:  Nevermind, I finally found a download link.  Sheesh, you'd think it would be easier to find.

---

### Post by QDR06VV9 on 2015-09-11
Here you go [http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)
Ublock origin will warn you This
> uBlock Origin has prevented the following page from loading:[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Because of the following filter
||sourceforge.net^$other
Found in: uBlock filters – Badware risks
Seems they have changed their policy's over there. Do not know if other ad blockers do the same
I just temporarily allow 1 time

---

### Post by Raymond Petit on 2015-09-15
> **runrickus said:**
> Here you go [http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)
Ublock origin will warn you This

Seems they have changed their policy's over there. Do not know if other ad blockers do the same
I just temporarily allow 1 time

I edited my last post.  I was able to download those files on Friday, but have not had time to try making a disk.  In the meantime I did make it over to a business called, Free Geek on Saturday and purchased two Mint install disks to see if they would boot from my external drive.  They don't!  (Must also say I was not impressed with their Tech Support since they didn't have any copies of Boot Repair in house.  They install Mint [formerly Ubuntu] on all their PC's, so this is a mystery!)  Also while I was there, I was able to place my pen drive I made following the directions in this thread into the laptop of one of the volunteers there.  The picture below was the result.  I guess he has a Command line interface installed, but I'm sure this is proof that the Pen Drive was made properly.

Next Steps:  Install Boot Repair on both Pen Drive and Disk and see if they will boot.  Try to do some reading up on the UEFI configuration that HP used on this unit.  It does not conform to the UEFI standard (the real problem).

I have to say that if these next steps fail, it is time to abandon this quest since there is no real proof anyone has ever gotten any Linux distro to boot from a usb/live disk or install from a usb/live disk.  The few who claim they did, provided no detailed instructions for anyone else to follow.  Hence, I call BS!

---

### Post by QDR06VV9 on 2015-09-15
I saw that you edited your post after i made my post. You could say covering all bases?LOL
Thanks for the info from your Free Geek visit.
FYI I boot a pen drive with Lubuntu(15.04) installed for months now. [http://ubuntuforums.org/showthread.php?t=2280658&page=4](http://ubuntuforums.org/showthread.php?t=2280658&page=4)
Some thumbdrives are better than others. I kind of like the 32 Gig Sandisk Ultra.
I hardly notice any difference from being installed to a Hardrive.  
Kind Regards

---

### Post by sudodus on 2015-09-15
Thanks for this information and feedback :-)

> **Raymond Petit said:**
> I edited my last post.  I was able to download those files on Friday, but have not had time to try making a disk.  In the meantime I did make it over to a business called, Free Geek on Saturday and purchased two Mint install disks to see if they would boot from my external drive.  They don't!  (Must also say I was not impressed with their Tech Support since they didn't have any copies of Boot Repair in house.  They install Mint [formerly Ubuntu] on all their PC's, so this is a mystery!)  Also while I was there, I was able to place my pen drive I made following the directions in this thread into the laptop of one of the volunteers there.  The picture below was the result.  I guess he has a Command line interface installed, but I'm sure this is proof that the Pen Drive was made properly.

When you get that text screen, it means that the computer boots to grub, but something is wrong or missing. Otherwise you should get a grub menu or if there is only one system installed: it should boot into the operating system.

Without knowing exactly what was installed in the pendrive, and what hardware was in the computer, it is very hard to find what is wrong and needs changing.
> 
Next Steps:  Install Boot Repair on both Pen Drive and Disk and see if they will boot.  Try to do some reading up on the UEFI configuration that HP used on this unit.  It does not conform to the UEFI standard (the real problem).

I have to say that if these next steps fail, it is time to abandon this quest since there is no real proof anyone has ever gotten any Linux distro to boot from a usb/live disk or install from a usb/live disk.  The few who claim they did, provided no detailed instructions for anyone else to follow.  Hence, I call BS!

Are you still trying to install into the HP Envy? I'm afraid that there are problems with it because it was made to only boot into Windows.

---

### Post by Raymond Petit on 2015-09-19
> **runrickus said:**
> I saw that you edited your post after i made my post. You could say covering all bases?LOL
Thanks for the info from your Free Geek visit.
FYI I boot a pen drive with Lubuntu(15.04) installed for months now. [http://ubuntuforums.org/showthread.php?t=2280658&page=4](http://ubuntuforums.org/showthread.php?t=2280658&page=4)
Some thumbdrives are better than others. I kind of like the 32 Gig Sandisk Ultra.
I hardly notice any difference from being installed to a Hardrive.  
Kind Regards

Sorry, I thought you were sudodus, lol!  I didn't know somebody else was looking in here.  So, are you saying you have Lubuntu running on one of the Envy varients?  I don't see that in your posts!

---

### Post by Raymond Petit on 2015-09-19
> **sudodus said:**
> Thanks for this information and feedback :-)


When you get that text screen, it means that the computer boots to grub, but something is wrong or missing. Otherwise you should get a grub menu or if there is only one system installed: it should boot into the operating system.

Without knowing exactly what was installed in the pendrive, and what hardware was in the computer, it is very hard to find what is wrong and needs changing.

I see, so something is wrong with the pen drive even though I got a better result on that PC than I did on this one.  I need to find another to test PC, just to make sure!  I'm creating a boot repair pen drive with Lili as I write this.  I will keep you appraised.  I know HP did not follow the standard for UEFI, but not giving up yet.  A couple of people say they have done it, still have a little hope there is a way around that.

---

### Post by sudodus on 2015-09-19
When I said 'Something is wrong or missing' I did not mean specifically in the pendrive. It could be somewhere else too (in the computer's hardware or UEFI system or settings). Try to get into a direct dialogue with someone who has already succeeded with the same kind of computer, and the missing parts might be added :-) Sometimes the written descriptions are too brief to help, but after a couple of questions and replies, ...

---

### Post by Raymond Petit on 2015-09-19
> **sudodus said:**
> When I said 'Something is wrong or missing' I did not mean specifically in the pendrive. It could be somewhere else too (in the computer's hardware or UEFI system or settings). Try to get into a direct dialogue with someone who has already succeeded with the same kind of computer, and the missing parts might be added :-) Sometimes the written descriptions are too brief to help, but after a couple of questions and replies, ...

That's a good suggestion.  I know of only two who claim to have gotten in running.  I'll see if they will reply after all this time (still calling BS!).  My test of the pen drive made with Lili also failed, although in a different way.  I'm going to read up on this particular configuration of UEFI for any clues on how to get around the lockout of booting other systems.

---

### Post by Raymond Petit on 2015-09-20
> **Raymond Petit said:**
> That's a good suggestion.  I know of only two who claim to have gotten in running.  I'll see if they will reply after all this time (still calling BS!).  My test of the pen drive made with Lili also failed, although in a different way.  I'm going to read up on this particular configuration of UEFI for any clues on how to get around the lockout of booting other systems.

I found a little information on UEFI configuration online.  Made a little progress, but still it doesn't look good at all!  Turns out, pressing f9 at boot, will give you boot options.  Pressing f6, will give you some system diagnostics while f10, of course, gets you into the UEFI menu.  The USB I made from this thread can be seen, but it fails to boot.  The external disk drive is not seen at all even though it is ahead of the SSD in the boot order and I had a copy of Mint in it while testing.  Screenies below of the results.  I am on Insyde rev 5, if that means anything to you.  I have seen other versions that do not look the same as in they have options for Legacy Boot and some others.  I'm sure flashing that is not possible as it's made for different hardware???

I also made a pen drive with Boot Repair on it and it does nothing!  I fact, I can't get into the UEFI settings unless I put the drive in after pressing the power button, hit ctrl>alt>delete to start over, then put the pen drive in as it's booting.  I can then see BOOTx64.EFI and grubx64efi in the UEFI file browser.  They booth do not boot.

---

### Post by Raymond Petit on 2015-09-20
> **sudodus said:**
> When I said 'Something is wrong or missing' I did not mean specifically in the pendrive. It could be somewhere else too (in the computer's hardware or UEFI system or settings). Try to get into a direct dialogue with someone who has already succeeded with the same kind of computer, and the missing parts might be added :-) Sometimes the written descriptions are too brief to help, but after a couple of questions and replies, ...

Holy Crap, finally got somewhere!!!  I suddenly remembered the Lili said something about the Linux version not being on the compatibility list, so I Googled that list and downloaded directly from there.  Then I choose the 64 bit version and remade it (Lili still reported it as incompatible even though I got it direct from the site!  Hmmmm!).  There was no icon created when I put the pen drive back in so I opened it and ran the .exe!  The results below!  Now, I'm just a tinkerer who knows nothing, but I can follow directions.  What is different about my CPU that is conflicting with Lili?  It's i686 which should equal x686, right?  Nvm, maybe I need to try the 32 bit version, duh, I'm blind.

EDIT:  What I'm going to do is the only thing I know how and that is to see if this will boot before I use the 32bit version.  Reason being as I remember reading several times the only way to get Linux running on this unit was to use a 64bit version with Secure Boot turned off.  Will pick this up again tomorrow.  Will keep you appraised.  I an hoping this will eventually help someone.  I can live with getting VM to work, so I've got some hope again!

---

### Post by Raymond Petit on 2015-09-20
Holy Crap, I know I said I wouldn't do anything else today, but I couldn't resist.  Tried booting the 64 bit version, no go!  Tried 'Virtualize this Key' and got the blue crash screen, lol!  So then I remade the pen drive again and fired up VirtualBox.  Threw no errors like before.  It's cycling through those buttons, but won't boot.  Progress!:D:o

Spoke too soon, it's throwing errors, but l should be able to capture those logs!:D  Oh, yeah, gotta put this down or I won't get anything else done today, lol!

---

### Post by sudodus on 2015-09-21
Thanks for sharing :KS

Maybe you will also get some tips from other people who try to do the similar things with the same hardware.

Good luck :-)

---

### Post by Raymond Petit on 2015-09-22
> **sudodus said:**
> Thanks for sharing :KS

Maybe you will also get some tips from other people who try to do the similar things with the same hardware.

Good luck :-)

Funny thing!  Running Virtual Box will throw errors.  This time I tried "Virtualize this Key (32 bit version)" and I actually made it to the " Try Ubuntu Install" options screen.  I chose to 'try without making any changes' and the progress wheel is just spinning, at least 8 minutes now with no progress that I can see.  Update:  That failed too.  I'll try attaching some logs!  I will have to upload to my Dropbox.  Will do later.  Will you read them?

---

### Post by sudodus on 2015-09-23
I can read the logs, but can't promise that I understand them. There are other people who know much better how to understand log files. I'm afraid that you would need help from one of those people to understand them.

On the other hand: Before you reach to the screen shown in post #43, there is a screen with two small 'icons' at the bottom. When you are there, please press a key (for example the spacebar or enter key), and you should arrive at another menu, where you should be able to select boot options. Try those boot options, and you might be able to continue :-)

It is also possible the computer has too little RAM size or CPU or GPU horsepower for standard Ubuntu to run in VirtualBox. Maybe you have better luck with Lubuntu or Xubuntu or Ubuntu MATE.

---

### Post by Raymond Petit on 2015-09-23
> **sudodus said:**
> I can read the logs, but can't promise that I understand them. There are other people who know much better how to understand log files. I'm afraid that you would need help from one of those people to understand them.

On the other hand: Before you reach to the screen shown in post #43, there is a screen with two small 'icons' at the bottom. When you are there, please press a key (for example the spacebar or enter key), and you should arrive at another menu, where you should be able to select boot options. Try those boot options, and you might be able to continue :-)

It is also possible the computer has too little RAM size or CPU or GPU horsepower for standard Ubuntu to run in VirtualBox. Maybe you have better luck with Lubuntu or Xubuntu or Ubuntu MATE.

Will try your suggestions.  Having trouble posting logs.

EDIT:  Finally got them changed to .ODT something this forum can load.  Please, anyone who can read and interpret these, I'd appreciate it!

---

### Post by sudodus on 2015-09-24
I looked at the logs, and I'm sorry, but I really can't use them to help you solve your problem.

Maybe we can find someone who can help you, if you make ***an own thread*** with a copy of your post (#45) with the two attached log files in the [virtualisation subforum](http://ubuntuforums.org/forumdisplay.php?f=308). Please make a good descriptive title and add a post with a good description of the computer and the setup of VirtualBox, and what you are trying to run in it.

---

### Post by Raymond Petit on 2015-09-24
> **sudodus said:**
> I looked at the logs, and I'm sorry, but I really can't use them to help you solve your problem.

Maybe we can find someone who can help you, if you make ***an own thread*** with a copy of your post (#45) with the two attached log files in the [virtualisation subforum](http://ubuntuforums.org/forumdisplay.php?f=308). Please make a good descriptive title and add a post with a good description of the computer and the setup of VirtualBox, and what you are trying to run in it.

OK, thanks!

---

### Post by sudodus on 2015-10-01
> **sudodus said:**
> [SIZE=4]Test results with mk-grub-n-iso-s which is built into mkusb 10[/SIZE]

I have been able to boot ToriOS that uses an old Ubuntu 12.04 LTS non-pae kernel (not forcepae, not fake-pae, really non-pae) in UEFI mode. I did it with ***mkusb version 10 with a modified grub-n-iso installer*** added to create persistent live USB drives. This system does not boot directly from grub and an iso file, but from a copy of the iso file cloned into partition #2. Partition #1 is the boot partition (and EFI partition). Partition #3 is a casper-rw partition. ***The idea is to add persistence and make it a more complete tool for the Ubuntu family and some community re-spins with similar boot structure.*** Booting via grub from a cloned copy of the iso file into partition #2 makes it work with some re-spins that do not boot from an iso file (at least I cannot do it).

```
[SIZE=3]sdf                                                sdf    119,2G
&#9500;&#9472;sdf1 **vfat**    ToriOSdaily      /media/ToriOSdaily &#9500;&#9472;sdf1  59,3G
&#9500;&#9472;**sdf2 iso9660 **torios-live      /media/torios-live &#9500;&#9472;sdf2   645M
&#9492;&#9472;sdf3 **ext4 **   live-rw          /media/live-rw     &#9492;&#9472;sdf3  59,3G[/SIZE]
```

This version of mkusb (10.0.1) needs testing before even getting into the unstable PPA, and you find the way to get it via this link: [ Re: Howto make USB boot drives post #120](http://ubuntuforums.org/showthread.php?t=1958073&page=6&p=13337410#post13337410)

[HR][/HR]
***Boot alternatives in the grub menu:***

[LIST]
[*]"distro - persistent live"
[*]"distro - live"
[*]"distro - recovery mode"
[/LIST]

***The following distros are tested and work***

**[COLOR="#446600"]The whole Ubuntu family's *desktop* iso files work**[/COLOR]: Kubuntu, Lubuntu, standard Ubuntu, Xubuntu, ...

[LIST]
[*]ubuntu-14.04.2-desktop-amd64.iso
[*]wily-desktop-amd64.iso ...
[/LIST]

The following linux distros based on Ubuntu are also tested and work

[LIST]
[*]bento-trusty-rc2-i386.iso
[*]bodhi-2.4.0-64.iso
[*]extix-14.2-64bit-isoh-persistent-836mb-141024.iso
[*]linuxmint-17.2-cinnamon-64bit.iso
[*]lxle-12044-32.iso (not isohybrid, current versions of LXLE have hybrid iso files)
[*]ToriOS-beta.iso (based on Ubuntu 12.04 i386 non-pae)
[/LIST]

***The following distros boot but persistence fails***

The computer boots but cannot get persistence. (Debian advices to clone and add an ext partition with the label live-rw. It boots but I can not make persistence work with Ubuntu systems and not with Debian Wheezy and Jessie that way either.)

[LIST]
[*]debian-live-8.0.0-i386-gnome-desktop.iso
[*]obi_Trusty-nonpae-txt5-9w.iso (based on Debian Wheezy)
[/LIST]

***Complete failure***

No Ubuntu/Debian based distro has failed completely yet, but for example Mageia does not work at all. The boot structure is not recognized. You must edit the file 'boot/grub/grub.cfg' in the first partition.

[LIST]
[*]Mageia-4.1-LiveDVD-GNOME-x86_64-DVD.iso
[/LIST]

***I think that cloning is still the best method. It is the standard method of mkusb.***

Cloning works also for distros with different boot structure as long as the iso file is treated with isohybrid. And most modern linux distros are, so cloning makes a working live session also for most of these linux distros, and I think that it is still the best method. Most of the time there is no need for persistence, and a tool for Ubuntu need not work for all other distros. But it should be very reliable for the Ubuntu family of operating systems.

> **sudodus said:**
> [SIZE=4]Fine-tuning in mkusb 10.0.3[/SIZE]

A new version (able to create 'live only' as well as 'persistent live' USB drives) is uploaded and available via the **unstable PPA** and **phillw.net**

See this link [https://help.ubuntu.com/community/mkusb/gui](https://help.ubuntu.com/community/mkusb/gui)

[SIZE=4]mkusb version 10.2[/SIZE]

[LIST]
[*]has a clean[er] GUI interface and
[*]a 'wipe menu' with several useful options and
[*]it can create persistent live drives with the Ubuntu family operating systems for all PC (Intel/AMD) computers.
[/LIST]

The bleeding edge version of mkusb is available for testing [from phillw.net](https://help.ubuntu.com/community/mkusb/gui#from_phillw.net)

and 10.2 (which is rather well tested now) is available from [from the unstable PPA](https://help.ubuntu.com/community/mkusb/gui#from_the_unstable_PPA)

---

### Post by sudodus on 2015-12-01
[SIZE=4]A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4[/SIZE]

Installed Ubuntu based systems in UEFI mode can use mkusb to create 'any' system by cloning, where the installed system depends only on the contents of the iso file or compressed image file. But the method to create persistent live systems is limited to UEFI mode (with and without secure boot).

In order to provide an alternative that works in BIOS mode, this compressed image file was created. It contains a persistent live system of ***Lubuntu 14.04.3 LTS i386*** (32-bit) and ***mkusb version 10.4***. And this system is a very good booter in 32-bit as well as 64-bit PC (Intel/AMD) computers in BIOS mode and UEFI mode. But it does not work with secure boot. So this way it is possible to create a persistent live system that boots in BIOS mode (with 32-bit as well as 64-bit PCs) from a computer running in UEFI mode.

It is easy to add another iso file to **/isodevice**, link boot menu entries to it and run other Ubuntu based operating systems in the same system. Download any iso file of a current version and flavour of Ubuntu via the official web-sites, for example [http://releases.ubuntu.com/]() where you also find the corresponding md5sums. After that you use the desktop icons ***links2check*** and ***links2update*** to link boot menu entries. (The last icon can also be used to update the current developing version's daily iso files.)

The current version of the  ***One pendrive for all PC (Intel/AMD) computers*** compressed image file can be downloaded from this link

[dd_lubu-14.04.3-desktop-i386_one-pendrive_7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_lubu-14.04.3-desktop-i386_one-pendrive_7.8GB.img.xz)

and has the following md5sum

```
d001805e78369dba97f1183e5d31da6b  dd_lubu-14.04.3-desktop-i386_one-pendrive_7.8GB.img.xz
```

Use [mkusb](https://help.ubuntu.com/community/mkusb) in linux or [7-zip](http://www.7-zip.org/) and [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows to expand and {copy/clone/flash/burn/restore/install} it into a USB pendrive, a flash memory card or a hard disk drive or SSD with ***at least 8 GB***.

[hr][/hr]
These posts (6, 7, 8, 10, 11) describe similar 'grub-n-iso' systems, that can boot 32-bit and 64-bit Ubuntu family operating systems in BIOS and UEFI mode. (None of these systems works with secure boot.)

Post #6.   [A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso']("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523") - Lubuntu  32-bit

Post #7. [Multiboot pendrive system for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302264#post13302264")

Post #8. [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

Post #10. [Create or download a portable system with a small footprint with a potential for isotesting]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310634#post13310634")

Post #11. [Manage the daily built iso files of your choice]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310836#post13310836")

Post #12. [Comments and tips]("http://ubuntuforums.org/showthread.php?t=2259682&p=13320397#post13320397")

---

### Post by haoz2 on 2016-01-16
That's awesome. UEFI&BIOS images I download from [http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/) can work on Surface Pro 3, except for keyboard.
I was trying to upgrade kernel however it seems impossible for live USB.
So I wonder if there is 15.10 Ubuntu UEFI & BIOS image file we can download? Thanks.

---

### Post by sudodus on 2016-01-17
@haoz2,

I think most compressed image files are built with the LTS version(s). I had intended to wait until the next LTS version, which is developed now with the codename Xenial Xerus, and will be released as 16.04 LTS.

Please tell me exactly which image file you tried! Then I can make a corresponding file with 15.10 :-)

---

### Post by haoz2 on 2016-01-17
Great!
These two work fine except for keyboard:
dd_Ubuntu_12.04-UEFI-n-BIOS-7.8GB.img.xz
dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz

Actually I'm not sure if 15.10 works with SP3 without these patches. [https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/](https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/)
I just tried Ubuntu 15.10 without installation.
type cover 3                       : keyboard [COLOR=#545454][FONT=arial]&#10003;   [/FONT][/COLOR]Touchpad x
type cover 4 with fingerprint: keyboard x   Touchpad [COLOR=#545454][FONT=arial]&#10003;[/FONT][/COLOR]

If you would customize an image, that'd be super awesome for Surface users! :popcorn::D

---

### Post by sudodus on 2016-01-17
- Do you plan to boot several computers from a USB pendrive made from such a compressed image file or run only the Surface Pro 3?

- Do you plan to install the system into an internal drive of the Surface Pro 3 (or 'only' run from a USB pendrive)?

- Have you been running the ***live*** system or the ***installed*** system from **dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz**?

I'm asking because you might need only a [persistent] live system or only an installed system, which would make it smaller and simpler than a system with both.

-o-

But first I suggest that you try ***Xenial Xerus*** alpha 1, or the Xenial daily iso file of any flavour (including standard Ubuntu) from the following link,

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) or more specifically for standard Ubuntu

[Download links for Ubuntu Desktop amd64](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/110535/downloads)

It may already contain a kernel with the drivers that you need for SP3 built-in. In that case it would be a waste of effort to make a compressed image file of 15.10, which has a short lifetime (only until July), while Xenial will be released as 16.04 LTS with long time support until April 2021.

---

### Post by haoz2 on 2016-01-17
SP3 only. 
No. I don't want to mess with the internal drive.
Yes. 

I'm trying to install an independent Ubuntu on USB while keep my laptop intact.
Writing **dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz** to USB gives me exactly what I expect except for keyboard support.

I tried xenial-desktop-amd64.iso without installation. Same result for keyboard as 15.10. (Would full installation make a difference?)

---

### Post by sudodus on 2016-01-18
I see. I'm sorry, but I cannot develop and test a system with a patched kernel to support that keyboard, because I haven't got any SP3 computer. I could make a compressed image file with Ubuntu 15.10, or the current daily version of Xenial, but it would not solve your problem with the keyboard. I don't think an 'installed system' would work, when a live system does not work.

The kernel version of Xenial will be updated during the development cycle, and let us hope that the beta version or the final released version will support the SP3 keyboard.

-o-

But ***you*** might be able to compile a new kernel in an 'installed system'. I mean a system that is installed from the 'first USB pendrive' to a 'second USB pendrive'. Installed in the same way as you would install it into an internal drive, but into a USB pendrive. I think it would work, at least as long as you avoid booting and or upgrading Windows with the pendrive inserted.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

It is important that you select ***'Something else'*** at the partitioning window for manual selection of partitions and target for the bootloader.

---

### Post by haoz2 on 2016-01-18
Thanks!

@Tom_S. figured out a way: [http://ubuntuforums.org/showthread.php?t=2309963](http://ubuntuforums.org/showthread.php?t=2309963)
But there's still some issue with keyboard support. I'll just try 16.04 and see how it goes.

---

### Post by sudodus on 2016-01-18
I made a ***compressed image file with Ubuntu 15.10***, that I thought should be rather stable (should not be destroyed easily when updating itself or updating Windows. It can boot in UEFI mode as well as in BIOS mode (but it works only in computers with 64-bit architecture). It is up to date (updated/dist-upgraded 2016-01-18) and a clean *installed Ubuntu system without any tweaks or patches except that it can boot in UEFI and BIOS mode*, and that some 'cruft' is cleaned.

See this link

[dd_Ubuntu_15.10-UEFI-n-BIOS-11GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu_15.10-UEFI-n-BIOS-11GB.img.xz)

with the following md5sum

```
c9b8bb5f3d2d50754f3c66664f3275ae  dd_Ubuntu_15.10-UEFI-n-BIOS-11GB.img.xz

```

Log in with the following user ID and password

[B]user:     guru
password: changeme[/B]

and change the password ;-)

@*haoz2*, You can install this system into a pendrive and try various patches and tweaks for the Surface Pro 3.

***Edit (more details)***

I made this system in a computer without an internal drive by installing in UEFI mode into a pendrive with an MSDOS partition table and two partitions, with FAT32 for the EFI (boot) partition, and with ext4 for the root partition. I skipped the swap partition, but it is easy enough to add, if you wish. After the installation I remade the booting (re-installed grub twice, once for UEFI and once for BIOS, and with the option --removable, which I think makes it less vulnerable to attacks from Windows or from the UEFI system. I also added the mount option noatime for the root partition in /etc/fstab in order to reduce wear.

... and last but not least,
- in linux: use [mkusb](https://help.ubuntu.com/community/mkusb) to install from the compressed image file,
- in Windows: use [7zip](http://www.7-zip.org/) to uncompress and after that [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) to install from the [uncompressed] image file.

***Edit 2:***

After some more testing, I found some boot problems in UEFI mode. So this compressed image must be improved.

***Edit 3:***

I am rather sure that the system in the following link is stable, and a better alternative if you want a portable installed system with Ubuntu 15.10:

[Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

---

### Post by haoz2 on 2016-01-18
Thanks sooooo much!

But this doesn't boot...unlike earlier version 14.04 that can boot even with secure boot enabled. 
A difference I notice is the size and content of EFI partition (FAT32).

---

### Post by sudodus on 2016-01-18
That's right, it is not enabled for secure boot. But it does boot and run well in my two laptops in UEFI as well as BIOS mode (both modes in both computers). It works also in a BIOS only desktop computer.

Can you test how it works in another computer (just to make sure it was installed correctly)?

I can try to make a new system, that boots in a different way (similar to the previous systems that boot in your SP3, but where you cannot use the keyboard),

- with secure boot
- via the boot system for live drives

but it is more complicated, and takes longer time to make.

---

### Post by haoz2 on 2016-01-18
I can't test that right now...but it won't boot either though secure boot is disabled.

Do you mean this img is able to upgrade kernel, unlike previous ones?
I guess I can follow [COLOR=#000000]@Tom_S.[/COLOR] method and try 16.04. But it looks like keyboard won't work either :( Anyway...

Thanks so much for your efforts!

---

### Post by sudodus on 2016-01-18
Yes, this img is able to upgrade the kernel like any installed system. But I have to make its boot system different, so that it will boot in the SP3.

-o-

After some more testing, I found some boot problems too in UEFI mode. So this compressed image must be improved.

---

### Post by sammiev on 2016-01-19
Installed it to a 16GB USB using EFI with no issues.

Thanks

---

### Post by sudodus on 2016-01-20
*@haoz2,*

I made a new system, that boots in a different way (similar to the previous systems that boot in your SP3, but where you cannot use the keyboard),

- with secure boot
- via the boot system for live drives

It is more complicated, but it is done now, and I hope it will be useful :-)

You can find the new system in the following link. I think it is stable, and a better alternative if you want a portable installed system with Ubuntu 15.10:

[Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

---

### Post by haoz2 on 2016-01-22
Thanks @sudodus! This new system is amazing. Type cover 3 is working by just simply editing conf file. [http://ubuntuforums.org/showthread.php?t=2300868](http://ubuntuforums.org/showthread.php?t=2300868)

But upgrading kernel won't do. (I still wanna try other kernel since multi-touch & typecover 4 aren't fully working.)
1. I downloaded kernel binaries and installed it. New initrd & linux images are present in /boot/.
2. Delete old symbolic links and re-link them.
3. Edit [COLOR=#000000][FONT=Ubuntu Mono]/media/guru/usb-live/boot/grub/grub.cfg [/FONT][/COLOR](I find the only line I can edit in a menuentry is the last line:  **initrd    /boot/initrd.img-4.2.0-25-generic **)

Then reboot and choose corresponding entry. It loads a while and says "Gave up waiting for root device".

---

### Post by sudodus on 2016-01-23
There are ***two*** lines to edit, so that they point to your new kernel:

A. the line starting with **linux** and the line starting with **initrd**

B. alternatively two symbolic links to update, one for **initrd.img** and one for **vmlinuz**.

---

### Post by haoz2 on 2016-01-23
Thanks! I though it has to be ".efi.signed" but actually not.
After upgrading to latest patched kernel [here]("https://github.com/neoreeps/surface-pro-3"),  everything seems working perfectly!

---

### Post by sudodus on 2016-01-23
Congratulations *haoz2* :-)

---

### Post by haoz2 on 2016-01-23
Cheers!:popcorn:

---

### Post by deitcher on 2016-04-06
Have you ever seen it able to boot to grub using both BIOS and UEFI, but the individual ISOs only will boot if the system was booted BIOS?

- If set to BIOS/CSM, I get the grub menu, can pick one of my 6 (and growing) options, and I see system startup log messages immediately. 
- If set to EFI, I get the grub menu, I can pick one of my options, I get "error: no suitable video mode found. Booting in blind mode." and then it hangs. It doesn't matter what ISO or distro I use.

I tried this both under VirtualBox (on Ubuntu and on Mac) and booting the physical machine directly.

---

### Post by sudodus on 2016-04-06
Please tell me more about this problem!

I know that this grub-n-iso method does not work with secure boot.

(There is an alternative for secure boot, but does not work with 32-bit systems: [mkusb/persistent: Using data from the source iso file](https://help.ubuntu.com/community/mkusb/persistent#A2._Using_data_from_the_source_iso_file))

I know that there are problems with graphics when I try to boot Ubuntu Server in UEFI mode. See this link: [installing Ubuntu Server in UEFI mode](http://ubuntuforums.org/showthread.php?t=2315007)

If I understand correctly, you are talking about problems, that are related to graphics.

Please tell me

- which iso files you have tried

- which version of VirtualBox you are using

- the specification of the computer:
. Brand name and model
. CPU
. RAM (size)
. graphics chip/card
. wifi chip/card

I will try to see what can be done with your problem.

***Edit:*** I have not developed this method for all [major] linux distros. But it works for me (and several other users) with the current versions of Ubuntu and Ubuntu based distros and re-spins. Your problem might be that the menuentry must be modified for each non-Ubuntu iso file.

See this link: [https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by deitcher on 2016-04-06
I definitely have SecureBoot disabled (and VirtualBox doesn't support SecureBoot anyways). I tried using the Ubuntu 15.10 Desktop live ISO, Ubuntu 15.10 Server install ISO, and a few others (CentOS 7.3 Live, Alpine Linux 3.3.0, etc.). VirtualBox 5.0.16 on Ubuntu, 5.0.14 on Mac. Direct boot is off of a Dell Latitude e6320.

The problem itself doesn't appear to be graphics related... oh, wait. Are you saying that it might actually be booting the ISO, but because it is in blind mode, I am not seeing the output? I guess that is possible; it didn't even occur to me. I assumed the ISO simply wasn't booting at all.

OK, so I guess the first question is, how can I validate if it is a problem with the ISO not booting at all, or if the ISO is booting fine, but I am getting no visual output?

---

### Post by deitcher on 2016-04-06
@sudodos, I believe you are 100% right. It is not a boot problem, but a video problem. Here is what I did (all in VBox):

1. Set to BIOS
2. Set to Host-Only networking
3. Boot USB key, select Ubuntu Desktop
4. Confirm that I can ping from host to first address of DHCP Host-Only Network range (in this case 192.168.56.101) and no other
5. Shut down VM
6. Confirm that I no longer can ping it
7. Confirm that MAC address remains unchanged
8. Change to EFI mode
9. Boot VM, select Ubuntu Desktop, get same error message
10. Wait a few minutes
11. Ping same address... and it responds!

This confirms that the OS is, indeed, booting... but I am getting no console. 

First, thank you for pointing in the right direction.
Second, any idea how to resolve it?

---

### Post by sudodus on 2016-04-06
Let us focus on Ubuntu 15.10 (i386 and amd64). These iso files should work in both UEFI and BIOS mode with the grub-n-iso systems described in this thread.

I have VirtualBox Version 5.0.16_Ubuntu r105871, so it matches your verson on Ubuntu.

I have only an old Dell without UEFI. I have understood, that Dell is rather good at running linux. I looked at a [web page describing you computer model](http://www.notebookcheck.net/Dell-Latitude-E6320-Laptop-Review.67762.0.html), and it says 'Intel HD Graphics 3000'. Is that what you have in your computer? Could it be that the UEFI system of you Dell is somehow non-standard or faulty?

---

### Post by deitcher on 2016-04-06
For UEFI, you can simulate it in VirtualBox, under the VM's Settings->System.

I figured it out. For whatever reason, the graphics mode set for grub and by extension the kernels wasn't good. I ended up copying it out of the Ubuntu desktop iso grub.cfg, and now it works.

Here is what I added to grub.cfg:

```

if load font /boot/grub/fond.pf2 ; then
  set gfxmode=auto
  insmod efi_gop
  insmod efi_uga
  insmod gfxterm
  terminal_output gfxterm
  set gfxpayload=keep
fi

```

If this were chainloaded, it wouldn't be an issue, but because it is direct kernel loading, it needs to be set just right.

(how do I format code in this reply?)

---

### Post by sudodus on 2016-04-06
> **deitcher said:**
> @sudodos, I believe you are 100% right. It is not a boot problem, but a video problem. Here is what I did (all in VBox):

1. Set to BIOS
2. Set to Host-Only networking
3. Boot USB key, select Ubuntu Desktop
4. Confirm that I can ping from host to first address of DHCP Host-Only Network range (in this case 192.168.56.101) and no other
5. Shut down VM
6. Confirm that I no longer can ping it
7. Confirm that MAC address remains unchanged
8. Change to EFI mode
9. Boot VM, select Ubuntu Desktop, get same error message
10. Wait a few minutes
11. Ping same address... and it responds!

This confirms that the OS is, indeed, booting... but I am getting no console. 

First, thank you for pointing in the right direction.
Second, any idea how to resolve it?

Great progress :-)

I have read that there are problems with VirtualBox in UEFI mode. Maybe this is one of the problems.

It would be interesting to look at running this system in the computer itself (not in VirtualBox) with an Ubuntu 15.10 iso file. Try with some boot option, for example nomodeset.

If possible, I suggest that you test it in some other computer too (in UEFI mode). I have two computers, that run in UEFI mode, a Toshiba and a Lenovo (described [here](http://ubuntuforums.org/showthread.php?t=2315007&p=13445875#post13445875).)

---

### Post by sudodus on 2016-04-06
> **deitcher said:**
> For UEFI, you can simulate it in VirtualBox, under the VM's Settings->System.

I figured it out. For whatever reason, the graphics mode set for grub and by extension the kernels wasn't good. I ended up copying it out of the Ubuntu desktop iso grub.cfg, and now it works.

Here is what I added to grub.cfg:

```
if load font /boot/grub/fond.pf2 ; then
  set gfxmode=auto
  insmod efi_gop
  insmod efi_uga
  insmod gfxterm
  terminal_output gfxterm
  set gfxpayload=keep
fi
```

If this were chainloaded, it wouldn't be an issue, but because it is direct kernel loading, it needs to be set just right.

(how do I format code in this reply?)

This is interesting :-)

-o-

Edit the format: Select the advanced editor with the big red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**; the **#** icon puts the marked text within [noparse]```
tags
```[/noparse]

---

### Post by deitcher on 2016-04-06
Got it. Edited the previous post. Been so long on github that I automatically tried to wrap it with backticks (````) :-)

It is working. Hats off to you (if I were wearing a hat now....).

FYI, when you do the multiboot, if you try to use the server install CD, it doesn't quite find the iso as cdrom. You need to escape to shell, manually mount the USB and then mount the iso as /cdrom. Any way to pass that on to the kernel in grub.cfg?

---

### Post by sudodus on 2016-04-06
1. I just tried with Ubuntu 15.10 amd64 in my two computers with UEFI capability. It works all the way. So I think the problem with your system is a problem with the [default] graphics in UEFI mode. Should we think that it is the same problem, that appears both in Virtualbox and when booting the computer itself?

I have not yet tried in VirtualBox, and it may not be necessary now that you have solved your problem. In the longer perspective, it might be worthwhile including your if statement about graphics for Ubuntu.

2. The server iso file boots in a different way, and I think it needs a different menuentry. I have not really done much to make it work. I have focused on systems that run in live mode (the 'desktop' iso files). Do you think chainloading would make it work (within the same pendrive)? In that case, how would you implement it with grub2?

---

### Post by deitcher on 2016-04-06
1. Graphics: It could be. But I had the same issue in all cases: VirtualBox on my Mac; VBox on my Dell; straight on my Dell. Graphics is pretty far off my usual beaten path. :-)

2. Yes, I think chainloading would make it work, because then grub isn't loading the kernel and initrd, it is just handing it off completely, as if booted. But I think there is an issue with EFI, grub2 and chainloading. I just don't recall what it was. I am pretty sure you also lose some of the EFI hooks, but again, not sure.

---

### Post by sudodus on 2016-04-06
Things are much more complicated with UEFI compared to the old BIOS - I think UEFI was developed in order to make it hard to boot anything else than the system delivered with the computer. Several computer vendors use non-standard UEFI systems, which makes it even harder.

---

### Post by deitcher on 2016-04-06
I think the idea behind UEFI makes a lot of sense. The problem is the many closed implementations. We have many choices for open-source bootloader or manager - grub, lilo, refind, refit, etc. If we had the same (in a usable sense) for firmware, it would all be much better.

---

### Post by sudodus on 2016-04-06
I don't know much about the original idea behind it. It feels better to think, that it is a good original idea, maybe also the official standard is good, but that there are problems with closed implementations :-)

---

### Post by deitcher on 2016-04-06
LOL! There need stop be a "like" button on comments; yours just got it.

How strange. Well, I managed to boot, had to hack my way through on the missing mount and cdrom, but I got it. It even installed /boot, but the grub2 entries for the server have no initrd at all, just a linux entry. Obviously, the mount just hangs.

I guess I could boot into a live desktop CD (or an installed one), mount the root from the server install, and then run mkinitramfs? Would it be set up correctly?

---

### Post by sudodus on 2016-04-06
It might work :-)

But the question is, how important is it to have the Ubuntu Server iso file as one of many iso files in a multiboot  iso file. I would think that it is a special case, and it is rather easy to have an own pendrive for it.

-o-

I loop mounted **ubuntu-14.04.1-server-amd64.iso** (which is an LTS version, that I happen to have locally),

This is the content of its grub configuration file **./boot/grub/grub.cfg**:

```
if loadfont /boot/grub/font.pf2 ; then
        set gfxmode=auto
        insmod efi_gop
        insmod efi_uga
        insmod gfxterm
        terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install Ubuntu Server" {
        set gfxpayload=keep
        linux   /install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
        initrd  /install/initrd.gz
}
menuentry "OEM install (for manufacturers)" {
        set gfxpayload=keep
        linux   /install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet oem-config/enable=true --
        initrd  /install/initrd.gz
}
menuentry "Multiple server install with MAAS" {
        set gfxpayload=keep
        linux   /install/vmlinuz  modules=maas-enlist-udeb vga=788 initrd=/install/initrd.gz quiet --
        initrd  /install/initrd.gzhttps://help.ubuntu.com/community/mkusb/persistent
}
menuentry "Check disc for defects" {
        set gfxpayload=keep
        linux   /install/vmlinuz  MENU=/bin/cdrom-checker-menu quiet --Edit:
        initrd  /install/initrd.gz
}
menuentry "Rescue a broken system" {
        set gfxpayload=keep
        linux   /install/vmlinuz  rescue/enable=true --
        initrd  /install/initrd.gz
}https://help.ubuntu.com/community/mkusb/persistent
./boot/grub/grub.cfg (END)
```

and I think you can 'borrow' it (or part of it) and modify it to point to the correct locations in the multiboot pendrive.

***Edit:*** If something is missing for loop mounting, it should still be possible to clone from the iso file into a dedicated partition, and point to it in a way similar to what I do with [mkusb for persistent live drives](https://help.ubuntu.com/community/mkusb/persistent).

---

### Post by deitcher on 2016-04-06
> How important is it?

Moderately. I gave everything else working off of it.

Actually, my problem now is that the install fails. When I said the initrd is missing, I meant is missing after the install is done. There is no initrd file, and no line for it in grub (probably because the "install system" didn't include initrd. There is an error during the install that says something like 

```

in-target: dpkg: error pressing package linux-signed-image-generic (--configure):
in-target:   dependency problems - leaving unconfigured
in-target: dpkg: dependency problems prevent configuration of linux-signed-generic:
in-target:   linux-signed-generic depends on linux-signed-image-generic (= 4.2.0.16.1.8)
in-target:     Package linux-signed-image-generic is not configured yet.
....
in-target: E: unable to locate package linux-headers-signed-generic
base-installer: error: exiting on error base-installer/kernel/failed-install

```

Sigh.

---

### Post by deitcher on 2016-04-06
FYI, I am doing a clean install in VirtualBox booted directly from live iso, to see if it is related to that.

---

### Post by deitcher on 2016-04-06
Yes, quite confirmed. If the live iso really is mounted "as a CD", the install runs smoothly, the initrd.img file is there, it is configured correctly in grub. 
And I can even use an encrypted root disk. It does the right thing, loads the right scripts and modules into initrd.

So basically the ubuntu server install absolutely must be run off of a "CD" or an iso-booted as such. I find it surprising. I would have thought a server install (well, any Linux, but especially a server) would be a clean modular install that I could run off of anywhere.

---

### Post by sudodus on 2016-04-06
- Is it Ubuntu Server 15.10 amd64 or some other server version? Actually, I would recommend to use only long time support versions for server installations, in this case 14.04.1 LTS (and when 16.04.1 LTS will be released I would recommend that version). Only in very special cases I would suggest using other versions.

Are you trying to install Ubuntu Server
- in BIOS mode or UEFI mode? (and if UEFI mode, why?)
- in VirtualBox only, or also directly into a computer?

I have a strong memory of installing Ubuntu Server from a USB pendrive with a ***cloned*** iso file. This was into a computer (not a virtual machine). I can try again you want me to try :-)

---

### Post by deitcher on 2016-04-06
Oh, good point. it is 15.10. I probably should do 14.04.1 LTS. I am still at the "let's see that the install process" works stage, so just grabbed latest stable image.

- UEFI mode. It is required for various reasons. Eventually we will do SecureBoot, not immediately.
- In both cases, if I boot off the image - direct iso for VBox, installed to USB key or direct via EFI for hardware - it works. But if I try off the multiboot, no go.

What do you mean "cloned" iso file? Do you mean dd onto the USB?

---

### Post by sudodus on 2016-04-06
I just confirmed that Ubuntu Server 14.04.1 LTS installs from a USB pendrive, which is cloned from the iso file. (But I see from post #89, that you have another problem.)

I use ***mkusb*** to clone. It wraps security around dd - so, yes, in essence it is ***cloning with dd***. For servers, there is ***mkusb-nox*** (no X) with a simple text interface, but still helping you to avoid overwriting the wrong device. dd is nick-named 'disk destroyer' and 'data destroyer' for a reason ;-)

In order to make it work in a multiboot drive, I think you have to mimic what is done in some working system in the grub.cfg file. The important files are not located exactly at the same places, so you have to modify things to match. If something is missing so that you cannot make it boot from the iso file, I think you can make it boot when the iso file is cloned into a partition, as I tried to describe at the end of post #84. You can also extract the files from the iso file into the EFI (FAT32) partition, if that partition is big enough. It works in EFI mode without any extra bootloader. I think this is the same thing or similar to what you describe as 'direct via EFI for hardware'. (You need a BIOS bootloader to make it boot in BIOS mode.)

---

### Post by deitcher on 2016-04-07
Yep. Got that. I was hoping the single grub-n-iso single format with bunch of iso files would work. It actually works fine for Ubuntu desktop.

I will try to find a way to configure it so that it works.

---

### Post by deitcher on 2016-04-07
Ah, got it. Right. Apparently grub2 does not support chainloading iso images. 

This is old, but...

[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

---

### Post by sudodus on 2016-04-07
I will be very interested to learn how you manage to make it work with the server iso file in the multiboot pendrive :-)

[COLOR="#696969"]-o-

Unfortunately I haven't got the time to make it work right now. Remember, that I have the additional problem with the graphics in UEFI mode, that affects my two UEFI capable computer. (This problem affects only the debian installers of Ubuntu Server, Lubuntu Alternate and Debian, but it does not affect the desktop installers, which work in graphics mode.) I should start finding a computer that can manage the graphics of the Ubuntu Server installer and then use that computer to find out how to configure the multiboot configuration, and it is too much for me right now.[/COLOR]

---

### Post by deitcher on 2016-04-07
It has something to do with how it mounts the iso (or doesn't). I opened a question at askubuntu.com, so we will see.

---

### Post by Sbininit on 2016-04-24
Greetings folks! I was trying to get 14.04 booting on usb and nothing I have tried has worked. I simply wanted Grub2 and 14.04 Ubuntu on USB so can install it to my HD where 10.04 upgrade failed and left it crippled. All I have left of that install is a root shell and I might could fix it but can't access anything anymore. All I get is a can't find package reply from apt-get. 

I found this thread and downloaded the dd_lubu_14.04 file but can't seem to down load with apt- get the mkusb program nor much anything else for that matter. Cant' seem to get add- apt

I don't have add-apt in my command list and haven't had any luck finding it. 

 it seems like now days apt-get can't find recources for darn near anything. I guess all my stuff is out of date? 


 What can I do to have the repositories available again. I have uncomented in /etc/apt/sources.list multiverse and universe and I get the same cant find packages when I run apt-get update.

Thanks in adavance!

---

### Post by sudodus on 2016-04-25
Welcome to the Ubuntu Forums, Sbininit :-)

Ubuntu 10.04 LTS passed end of life long ago. If it is borked, it is not worth trying to get it working again. Maybe the best way is to borrow a computer. If it runs Windows, you can use 7-zip and Win32 Disk Imager to install from the compressed image file to a USB pendrive. There are several tools, that can install from an Ubuntu iso file to a USB pendrive. See these links

[Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Sbininit on 2016-04-25
Thanks sudodus! I do have Win XP on a 2nd HD but now I finally have Grub2 installed and working on a usb drive except its not loading grub.cfg only the command line shows up so have to sort that out.

 Also I finally for the first time have grub2 on my main PC booting ISO's directly. 
Once I got 14.04 booted it has grub2 and so could install grub2 easily. On the grub legcy OS's they would alwasy load grub legacy over and over.

I have Arch, Win XP,  2 puppies,  5.1 Knoppix,  5,3.1, Knoppix  and 6.2 DVD Knoppix, 8.10 ubuntu, 9.04 and 10.04. ubuntu. I'm using 9.04 and Knoppix 6.2 installed lately,

grub-update has botched some of my menu entries to where some of those won't boot and Knoppix is finiky about booting if its sees more than one KNOPPIX file on board so those have to be renamed temporarily to boot one Knoppix version. 


 Only one OS on my machine has Grub2 and that's the broken one. And its not very convenient with that one root shell thats left that freezes up, there's no hitting F2 or 3 and grabbing another shell they're not working. I've since moved grub2 to a separate bootloader partition as well. so grub2 is not botched by new installes and update grub commands.

 
I have booted Ubuntu 14.04 on a partition that I will not be installing to, is it safe to install from a live booted iso?

---

### Post by sudodus on 2016-04-26
Installing an operating system is always ***risky***, so you should ***backup*** all important files before doing it.

Usually it works well to install from a live system. It makes no difference if it is booted via grub or syslinux, but normally you should avoid installing to the partition, when you have the active grub and the iso file.

I'm not sure if you would be 'allowed' to do it, and in the case if it would work. Maybe if you run from RAM (with the boot option **toram**), you can do it successfully and overwrite your live system, if that is what you want. But as a general rule I would advice to install to another drive, not to the drive where you have the live operating system.

---

### Post by Sbininit on 2016-04-27
All right! I have Grub 2 loading the grub.cfg now and have all of my os's listed and a couple of iso's. 

Also I have Lubuntu 14.04 loading into ram from the USB.
Some menuentry's still need editng a bit but the important ones are working.. I have also booted several of my OS's from the usb as well simply by chaning hd order since the USB is recognised as (hd0,1). 


One problem I'm having though, after Unutnu 14.04 boots,  the screen occasionally  goes fuzzy on me like TV's did in the 70's with poor antenna reception, except I have color. I can tap a key and it clears back up.


 If I tap a key on the board the screen clears back up. I'm  a bit concerned about trying to install this with it acting like this. It does it whether I boot it from HD or USB.

Is there possibly a simple adjustment or command I can add to the  menu to get rid of the fuzzy screen? 

I want to try persistant mode out next. . I  DD'd a casper-rw on to the 2nd partition in my USB drive and haven't booted again to see if it saved any of my settings.

---

### Post by sudodus on 2016-04-27
We can continue the discussion here about booting - right now about trying out persistent live mode. Did you use dd to clone from a 'casper-rw' file to a partiiton? If it does not work, it might work better to simply create a partition with its file system and copy the directories and files with rsync (or cp) as superuser and with the archive flag

```
sudo rsync -Havn source/ target
```

where source and target are the paths to the directories. If you do not succeed, do not worry. With Ubuntu, you can start with an empty casper-rw partition, and it will be filled with whatever you add to your system. (It works automatically.)

-o-

For the problems with the graphics it is better to start a separate thread in the [hardware sub-forum](http://ubuntuforums.org/forumdisplay.php?f=332). Write a good descriptive title and describe your computer and the problem in the first post. The brand name and model of the graphics chip/card is important.

---

### Post by Sbininit on 2016-04-28
[QUOTE=sudodus;13479162]We can continue the discussion here about booting - right now about trying out persistent live mode. Did you use dd to clone from a 'casper-rw' file to a partiiton? If it does not work, it might work better to simply create a partition with its file system and copy the directories and files with rsync (or cp) as superuser and with the archive flag

```
sudo rsync -Havn source/ target
```

where source and target are the paths to the directories. If you do not succeed, do not worry. With Ubuntu, you can start with an empty casper-rw partition, and it will be filled with whatever you add to your system. (It works automatically.)

I did DD a 512 MB image partition with ext3 file system named casper-rw. Im fixin to boot into it and see if it saved my last settings.

So your saying if I just label another partition casper-rw that ubuntu will use that just as well?.

---

### Post by sudodus on 2016-04-28
Yes, it will use the first one it finds. I suggest that you have only one partition with the label 'casper-rw'.

I wonder if you copied a casper-rw ***file*** to a partition.

-o-

Are you making your persistent live system from scratch with simple command line tools, or are you starting with one of the special tools to create live and persistent live drives? From where did you get the 512 MB image partition with ext3 file system named casper-rw?

---

### Post by Sbininit on 2016-04-28
> **sudodus said:**
> Yes, it will use the first one it finds. I suggest that you have only one partition with the label 'casper-rw'.

I wonder if you copied a casper-rw ***file*** to a partition.

-o-

Are you making your persistent live system from scratch with simple command line tools, or are you starting with one of the special tools to create live and persistent live drives? From where did you get the 512 MB image partition with ext3 file system named casper-rw?

Yes Im  making and image file with DD from scratch.

 Here are the commands -- 
dd if=/dev/zero of=/media/USB/casper-rw bs=1M count=256
mkfs.ext3 -F /media/USB/casper-rw.

I put the casper-rw on the 2nd partition in my USB drive so I can boot non persistent and  edit the casper-rw, resize , delete the contents etc, if need be.

  it worked great on 8.10 trhru 10.04 Ubuntu versions with only adding persistent to the boot menu.


I was wondering what becomes of the 40_custom file when grub2 is installed to USB? There's no etc file so I just copied my 40_custom file into the grub.cfg and relaxed permissions to where I can edit it on the fly.

---

### Post by sudodus on 2016-04-29
You can wipe the partition before making the file system, but in general, I think it is not necessary and causes unnecessary wear of the flash memory cells.

Make the casper-rw partition in a straight-forward way, for example with gparted or parted and mkfs (instead of making a casper-rw file with a file system inside, and after that cloning it to a partition).

See this link (wiping can be applied to partitions as well as whole USB pendrives), [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

-o-

It still works well (in Ubuntu and Ubuntu based flavours, re-spins and distros) to create a **casper-rw** file or partition and add the boot option **persistent** to the boot menu. As you have probably seen already, I add an extra menuentry with the boot option persistent, so that it will be easy to select live-only or persistent live with the grub menu.

Since 12.04 LTS I make persistent live drives with grub2. For grub2 booting via USB is no different than booting from any other mass storage device connected via for example IDE (PATA), SATA or eSATA. 40_custom can be used as before if you have a complete installed system, that can run update-grub. Otherwise, yes, just like you, I have copied it manually to grub.cfg.

---

### Post by Sbininit on 2016-05-01
> **sudodus said:**
> You can wipe the partition before making the file system, but in general, I think it is not necessary and causes unnecessary wear of the flash memory cells.

Make the casper-rw partition in a straight-forward way, for example with gparted or parted and mkfs (instead of making a casper-rw file with a file system inside, and after that cloning it to a partition).

See this link (wiping can be applied to partitions as well as whole USB pendrives), [Repair the partition table and file system of a pendrive]("http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986")

-o-

It still works well (in Ubuntu and Ubuntu based flavours, re-spins and distros) to create a **casper-rw** file or partition and add the boot option **persistent** to the boot menu. As you have probably seen already, I add an extra menuentry with the boot option persistent, so that it will be easy to select live-only or persistent live with the grub menu.

Since 12.04 LTS I make persistent live drives with grub2. For grub2 booting via USB is no different than booting from any other mass storage device connected via for example IDE (PATA), SATA or eSATA. 40_custom can be used as before if you have a complete installed system, that can run update-grub. Otherwise, yes, just like you, I have copied it manually to grub.cfg.


Something happened after editing grub.cfg on USB and all my menuentries are not showing. I had added several .iso menuentry's at the bottom but they don't all show up. Do you have any idea as to why? I never could get grub-mkconfig to run on the USB. 

I wonder if a very small OS install like Puppy linux would make Grub2 work better on USB? Or something else with just enough of an OS so 40_custom works like it should, grub-update etc?

---

### Post by sudodus on 2016-05-01
It is a good idea to have ***backup*** copies of grub.cfg in another drive. If you want help to restore it, please post it here with  [noparse]```
tags
```[/noparse] (or if it is very long, make a copy, compress the copy (for example with gzip or a graphical user interface tool) and attach the compressed file to a reply.

-o-

If you want grub to work like in an installed system, you should have an installed system. There is a brand new one now, where you start by flashing from a compressed image file to an Ubuntu mini system with text screen only. This system works as a normal installed system with grub2. The next step would be to add Fluxbox + a few more packages as suggested in the first install option after reboot into the installed system. You can also add Lubuntu Core or Xubuntu Core and get more tools and more eye candy.

See these links with new images/new tarball of Ubuntu 'mini-text' Xenial alias 16.04 LTS

The 64-bit version, which runs in UEFI and BIOS mode, installed from a compressed image file with mkusb:

[A new compressed image file is uploaded: 'dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz'](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13481136#post13481136)

[UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

The 32-bit version:

Installed from a compressed image file with mkusb: [compressed images](http://phillw.net/isos/linux-tools/compressed-images/), **dd_Xenial-32-txt.img.xz**

Installed from a tarball, **Xenial-32-txt.tar.xz**, with the One Button Installer: [OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

---

### Post by Sbininit on 2016-05-01
> **sudodus said:**
> It is a good idea to have ***backup*** copies of grub.cfg in another drive. If you want help to restore it, please post it here with  [noparse]```
tags
```[/noparse] (or if it is very long, make a copy, compress the copy (for example with gzip or a graphical user interface tool) and attach the compressed file to a reply.

-o-

If you want grub to work like in an installed system, you should have an installed system. There is a brand new one now, where you start by flashing from a compressed image file to an Ubuntu mini system with text screen only. This system works as a normal installed system with grub2. The next step would be to add Fluxbox + a few more packages as suggested in the first install option after reboot into the installed system. You can also add Lubuntu Core or Xubuntu Core and get more tools and more eye candy.

See these links with new images/new tarball of Ubuntu 'mini-text' Xenial alias 16.04 LTS

The 64-bit version, which runs in UEFI and BIOS mode, installed from a compressed image file with mkusb:

[A new compressed image file is uploaded: 'dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz']("http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13481136#post13481136")

[UEFI-and-BIOS/stable-alternative]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative")

The 32-bit version:

Installed from a compressed image file with mkusb: [compressed images]("http://phillw.net/isos/linux-tools/compressed-images/"), **dd_Xenial-32-txt.img.xz**

Installed from a tarball, **Xenial-32-txt.tar.xz**, with the One Button Installer: [OBI/Xenial-32-txt]("https://help.ubuntu.com/community/OBI/Xenial-32-txt")

I have plenty of backups of grub.cfg's, that's the only thing that saved me. I had to get one from my broken 10.04 install to get the USB up and running again. Trying to get an .iso to load in ram so I could install 14.04, so I could have an editable working Grub2 again, I almost lost the boot on the USB and hard drive.

 I never could get any menuentrys edited to work in the broken 10.04 install where Grub2 was and my DVD-RW is not working currently plus  my control key doesn't work either so I couldn't edit a menuentry at boot time and hit Cont X to boot.

I like the idea of a mini OS on USG grub2 functions normally. Great stuff!

Here is my grub.cfg , I had moved Knoppix 6.2 and Ubuntu 14.04 iso to the top so I could boot those since only 3 or 4 entry's show up at boot.
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set B586-5380
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set B586-5380
set locale_dir=($root)/boot/grub/locale
set lang=
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###
menuentry 'Knoppix DVD 6.2 on sdb9' {
        recordfail
        insmod ext2
        set root='(hd1,9)'
        search --no-floppy --fs-uuid --set b9b2a745-e246-4d84-bfe5-6065fbd734b8
        linux  /isolinux/linux root=UUID=b9b2a745-e246-4d84-bfe5-6065fbd734b8 ramdisk_size=100000 lang=en vt.default_utf8=0 apm=power-off vga=0x311 initrd=minirt.gz nomce quiet loglevel=0 tz=localtime noadriane
        initrd  /isolinux/minirt.gz
}
menuentry 'Lubuntu 14.04 iso' {
        set isofile="/iso/ubuntu14.04.4amd64.iso"
        loopback loop (hd0,2)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile liveimg toram noprompt noeject quiet splash --
        initrd (loop)/casper/initrd.lz
}
menuentry "configfile /boot/grub/scripts/autoiso.cfg" {
configfile /boot/grub/scripts/autoiso.cfg
}
menuentry 'Damn Small Linux' {
       recordfail
       insmod ext2
       set root='(hd0,1)
       search --no-floppy --fs-uuid --set B586-5380  
       Linux    /DSL/boot/isolinux/linux24 root=/dev/sda1 ro lang=us toram noeject frugal
       initrd   /DSL/boot/isolinux/minirt24.gz
}
menuentry 'Ubuntu, with Linux 2.6.32-74-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 73a305ff-fc38-49b3-951c-222e11fc77d5
    linux    /boot/vmlinuz-2.6.32-74-generic root=UUID=73a305ff-fc38-49b3-951c-222e11fc77d5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-74-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-74-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 73a305ff-fc38-49b3-951c-222e11fc77d5
    echo    'Loading Linux 2.6.32-74-generic ...'
    linux    /boot/vmlinuz-2.6.32-74-generic root=UUID=73a305ff-fc38-49b3-951c-222e11fc77d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-74-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-73-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 73a305ff-fc38-49b3-951c-222e11fc77d5
    linux    /boot/vmlinuz-2.6.32-73-generic root=UUID=73a305ff-fc38-49b3-951c-222e11fc77d5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-73-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-73-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 73a305ff-fc38-49b3-951c-222e11fc77d5
    echo    'Loading Linux 2.6.32-73-generic ...'
    linux    /boot/vmlinuz-2.6.32-73-generic root=UUID=73a305ff-fc38-49b3-951c-222e11fc77d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-73-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch Linux (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set fb8ea3ad-4a97-4f39-87db-2cd4f9ebdcf8
    linux /boot/vmlinuz26 root=/dev/sda11 ro
    initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set fb8ea3ad-4a97-4f39-87db-2cd4f9ebdcf8
    linux /boot/vmlinuz26 root=/dev/sda11 ro
    initrd /boot/kernel26-fallback.img
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6D27211F2621B5B5
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-19-generic (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set d83e9742-f246-46a9-99ea-34417a1c2513
    linux /boot/vmlinuz-2.6.28-19-generic root=UUID=d83e9742-f246-46a9-99ea-34417a1c2513 ro quiet splash
    initrd /boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set d83e9742-f246-46a9-99ea-34417a1c2513
    linux /boot/vmlinuz-2.6.28-19-generic root=UUID=d83e9742-f246-46a9-99ea-34417a1c2513 ro single
    initrd /boot/initrd.img-2.6.28-19-generic
}

### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Knoppix 5.31 on sda2' {
        recordfail
        insmod ext2
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 2a3ede04-1123-4729-a7db-ebf34caf90d8
        linux  /boot/vmlinuz-2.6.28-16-generic root=UUID=2a3ede04-1123-4729-a7db-ebf34caf90d8 ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt.gz nomce highres=off loglevel=0 libata.atapi_enabled=1 quiet SELINUX_INIT=NO nmi_watchdog=0 BOOT_IMAGE=knoppix
        initrd  /boot/initrd.img-2.6.28-16-generic
}
menuentry 'Knoppix DVD 6.2 on sdb9' {
        recordfail
        insmod ext2
        set root='(hd1,9)'
        search --no-floppy --fs-uuid --set b9b2a745-e246-4d84-bfe5-6065fbd734b8
        linux  /isolinux/linux root=UUID=b9b2a745-e246-4d84-bfe5-6065fbd734b8 ramdisk_size=100000 lang=en vt.default_utf8=0 apm=power-off vga=0x311 initrd=minirt.gz nomce quiet loglevel=0 tz=localtime adriane
        initrd  /isolinux/minirt.gz
}
menuentry 'Knoppix 5.1 ISO sda2' {
set isofile="(hd0,2)/iso/KNOPPIX5.1.iso"
loopback loop (hd0,2)$isofile
linux (loop)/boot/isolinux/linux ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt.gz nomce loglevel=0 quiet BOOT_IMAGE=knoppix noprompt noeject
initrd (loop)/boot/isolinux/minirt.gz
} 

menuentry 'grml-rescue system from harddisk (ISO = grml64.iso)' {
  set isofile='/iso/grml64.iso
  loopback loop (hd0,2)$isofile 
  linux    (loop)/boot/grml64/linux26 findiso=/iso/grml64.iso boot=live quiet vga=791 noeject noprompt toram
  initrd   (loop)/boot/grml64/initrd.gz
}
menuentry 'Puppy 4.21 on USB' {
        recordfail
        insmod reiserfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set "B586-5380 iitrd=initrd.gz pmedia=cd
        linux  /puppy421/vmlinuz root=UUID="B586-5380 
        initrd  /puppy421/initrd.gz
}
menuentry 'Ubuntu, 10.04 ISO sda2' --class ubuntu --class gnu-linux --class gnu --class os {
    set isofile="/iso/ubuntu10.04amd64.iso
    loopback loop (hd0,2)$isofile
        linux (loop)/casper/vmlinuz toram noprompt noeject quiet splash 
    initrd    /casper/initrd.lz
}
menuentry 'USB Lubuntu 14.04 iso' {
        set isofile="/iso/ubuntu14.04.4amd64.iso"
        loopback loop (hd0,1)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile liveimg toram noprompt noeject quiet splash --
        initrd (loop)/casper/initrd.lz
}

menuentry 'Lubuntu 14.04 iso' {
        set isofile="/iso/ubuntu14.04.4amd64.iso"
        loopback loop (hd0,2)$isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile liveimg toram noprompt noeject quiet splash --
        initrd (loop)/casper/initrd.lz
}
### END /etc/grub.d/40_custom ###
```

---

### Post by sudodus on 2016-05-02
> **Sbininit said:**
> Something happened after editing grub.cfg on USB and all my menuentries are not showing. I had added several .iso menuentry's at the bottom but they don't all show up. Do you have any idea as to why? I never could get grub-mkconfig to run on the USB. 

I wonder if a very small OS install like Puppy linux would make Grub2 work better on USB? Or something else with just enough of an OS so 40_custom works like it should, grub-update etc?

Please tell me which menu entries that show up, and which of them that don't show up! That would help me and someone else to find the problem. Let us hope that also other people read this post (and the previous one with your grub.cfg) and someone (not only I) might see how to fix it :-)

- Have you tried scrolling the grub menu with the arrow keys?
- Have you tried changing the resolution of the grub screen (the graphics mode)?

> **Sbininit said:**
> I have plenty of backups of grub.cfg's, that's the only thing that saved me. I had to get one from my broken 10.04 install to get the USB up and running again. Trying to get an .iso to load in ram so I could install 14.04, so I could have an editable working Grub2 again, I almost lost the boot on the USB and hard drive.

 I never could get any menuentrys edited to work in the broken 10.04 install where Grub2 was and my DVD-RW is not working currently plus  my control key doesn't work either so I couldn't edit a menuentry at boot time and hit Cont X to boot.

I like the idea of a mini OS on USG grub2 functions normally. Great stuff!

Here is my grub.cfg , I had moved Knoppix 6.2 and Ubuntu 14.04 iso to the top so I could boot those since only 3 or 4 entry's show up at boot.
...

I think the F10 key is an alternative to ctrl X to boot after editing in a grub menu entry.

---

### Post by Sbininit on 2016-05-02
> **sudodus said:**
> Please tell me which menu entries that show up, and which of them that don't show up! That would help me and someone else to find the problem. Let us hope that also other people read this post (and the previous one with your grub.cfg) and someone (not only I) might see how to fix it :-)

- Have you tried scrolling the grub menu with the arrow keys?
- Have you tried changing the resolution of the grub screen (the graphics mode)?



I think the F10 key is an alternative to ctrl X to boot after editing in a grub menu entry.
  I haven't tried any diff screen resolution.
Oddly it seems to show the very last couple of menu's that I edit. Now it shows the top two Knoppix 6.2, Ubuntu 14.04.iso Damn small linux and Puppy linux.

It doesn't matter how many  different grub.cfg's I try, all I get is 3 to 4 entry's. I can remove all the header leaving only default= 0 timeout= 10 and I get the same thing.

Maybe its because I can't do update-grub? Should I chroot into the usb and do update-grub?
I did update-grub media/sdc1 but it just updated and wrote a new cfg for Ubuntu 14.04 install.

I booted Puppy 421 and remember now why I don't like it. If it had Ubuntu's package resources it would rock, its fast and light. I love the way it shows every HD on desktop... sda1, sda2, sdb1 sdb2 etc. Its so much easier to find the exact HD than 14.04's current handle of the situation.
I'm not a big fan of Unity desktop and actually is the reason I quit upgrading Ubuntu after 10.04.
Some things just work and don't need fixing you know.

---

### Post by sudodus on 2016-05-02
What is this entry doing?

```
menuentry "configfile /boot/grub/scripts/autoiso.cfg" {
configfile /boot/grub/scripts/autoiso.cfg
}
```

I think these are the errors:

menuentry 'Damn Small Linux' {
recordfail
insmod ext2
set root='(hd0,1)
search --no-floppy --fs-uuid --set B586-5380
Linux /DSL/boot/isolinux/linux24 root=/dev/sda1 ro lang=us toram noeject frugal
initrd /DSL/boot/isolinux/minirt24.gz
}

there is an ***unpaired single quote*** in

```
set root='(hd0,1)
```

and ***similar unpaired single and double quotes*** in

menuentry 'grml-rescue system from harddisk (ISO = grml64.iso)' {
set isofile='/iso/grml64.iso
loopback loop (hd0,2)$isofile
linux (loop)/boot/grml64/linux26 findiso=/iso/grml64.iso boot=live quiet vga=791 noeject noprompt toram
initrd (loop)/boot/grml64/initrd.gz
}

and 

menuentry 'Ubuntu, 10.04 ISO sda2' --class ubuntu --class gnu-linux --class gnu --class os {
set isofile="/iso/ubuntu10.04amd64.iso
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz toram noprompt noeject quiet splash
initrd /casper/initrd.lz
}

---

### Post by Sbininit on 2016-05-02
That configfile was something I got from another tutorial. I came with a grub.cfg titled auto.iso placed inside a scripts folder inside of grub folder I believe with about 20 different auto iso entry's. I just wanted to see it load. At that time I was still trying to get my first .iso to boot and looking everywhere for answeres. LOL! 

I'll fix those entry's and see if they work again. Thanks for looking over them, I know its time consuming. 

There may be a few more errors. Some entries were originally taken from grub legacy menu.lst and moved around copied and pasted.
 
One thing that was nice about grub legacy you could edit its boot/menu.lst from a live CD, save it and the OS would boot from it. Grub2 seems to be a bit more finiky especially when the OS is sort of broken down of course grub legacy would fail under a crashed system I suppose.

I was reading that you can go back to having a grub legacy style menu in Grub2 by placing everything in 40_custom and turning off 10, 20 and 30 probers in grub.d. by remove them or make them unexecutable.

I lost boot on the PC after uprgrading to grub 2.02 from 1.98 right before installing 14.04 from .iso loaded toram.

 Aparently there was some vital to grub2 files not working correctly in the broken system. I thought I could get a fresh install of grub2 functioning better from Lubuntu14.04 live but was not the case. It left me with only the broken 10.04 entry.

At the time of the install I booted the .iso on HD 2 from the usb. It was only showing two menuentry's then. LOL!

---

### Post by sudodus on 2016-05-02
Tweaking and breaking the system is part of learning. I think you will soon have a system that can boot most if not all the iso files you want to boot.

Good luck :-)

---

### Post by Sbininit on 2016-05-03
Wow! A little bit of tweaking those menuentry's and now I have all 15 loading.

I've typed sudo umount -a lately so much that I finally made a tiny executable script that I can click and do that task.

---

### Post by sudodus on 2016-05-03
Congratulations, *Sbininit* :KS

---

### Post by Sbininit on 2016-05-03
Thanks Sudodus! Hey I want to try the 16.04 Ubuntu on USB. I might as well grab the 32 bit so I can use it on any system shouldn't I? 

My Desktop is amd64 but most of our lap tops are 32 bit. One of our lap tops shuts down immedieately if I try to boot a linux USB in it.

---

### Post by sudodus on 2016-05-04
Yes, please try 16.04 LTS, ***not only standard Ubuntu***, but also one the lighter flavours :-)

The method, that I describe in this thread installs grub in a way that boots in UEFI as well as in BIOS mode, and you can boot most PC (Intel/AMD) computers with a ***32-bit Lubuntu, Ubuntu MATE or Xubuntu*** iso file. Standard Ubuntu might need more CPU 'horsepower', a more modern graphical chip and/or more RAM than what is available in some old computers and some weak netbooks. if I try to boot a linux USB in it

-o-

I suggest that you create a separate thread at the [Installation & Upgrades Forum](http://ubuntuforums.org/forumdisplay.php?f=333) about the problems with your laptop, that shuts down immediately, if you try to boot a linux USB in it. Make a good descriptive title. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

 and describe your problem with as many details as possible in the first post. That will increase the chances to find a solution.

---

### Post by Sbininit on 2016-05-04
Is the EFI kernel in Ubuntu developed for working in UEFI booting PC's?

I have the 32 bit Lubuntu 16.04 dd'd onto my 2nd partition now and it is working fabulous on my PC without the screen going fuzzy. 

I have grub2 and Puppy 421 on sdc1, lubuntu 16.04 image on sdc2 and sdc3 is  a 12.3 gig empty drive to create casper-rw I suppose.

Do I have to start all over to get the EFI boot installed to this drive or just wipe the first partition and install EFI boot loader first?

---

### Post by sudodus on 2016-05-05
The EFI kernel (which is a 64-bit kernel) can manage also secure boot in UEFI mode. It works in UEFI mode (obviously) and also in BIOS mode, but not in computers with 32-bit CPUs.

If you are happy without secure boot, the 32 bit kernel can run in both BIOS and UEFI mode when booted via this 'One pendrive for all PC (Intel/AMD) computers' system.

This is explained at the following link: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Compare '1. Method developed from 'grub-n-iso' and '2. Using data from the source iso file'.

-o-

***mkusb***'s '1. Method developed from 'grub-n-iso' is booting 'almost in the same way' as the method of this thread. But instead of an iso file, the content of the iso file is cloned to a partition, which makes it work with iso files that are not prepared for booting via grub. It makes it work with some community re-spin iso files (based on Ubuntu or Debian).

-o-

> Do I have to start all over to get the EFI boot installed to this drive or just wipe the first partition and install EFI boot loader first? 

I'm not sure what your current system is like.

[SIZE=3]***A.***[/SIZE] If you started according to the links in the first post of this thread, for examplle ***post #6 and #8*** it should work in UEFI mode already (but not with secure boot).

The following posts (6, 7, 8, 10, 11, 48, 49) describe 'grub-n-iso' systems, that can boot 32-bit and 64-bit Ubuntu family operating systems in BIOS and UEFI mode, but these 'grub-n-iso' systems do not work with secure boot.

Post #6.   [A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso']("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523") - Lubuntu  32-bit

Post #7. [Multiboot pendrive system for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302264#post13302264")

Post #8. [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

Post #10. [Create or download a portable system with a small footprint with a potential for isotesting]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310634#post13310634")

Post #11. [Manage the daily built iso files of your choice]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310836#post13310836")

Post #12. [Comments and tips]("http://ubuntuforums.org/showthread.php?t=2259682&p=13320397#post13320397")

Post #48. [Test results with mk-grub-n-iso-s which is built into mkusb version 10](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13365767#post13365767)

Post #49. [A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13399888#post13399888)

[SIZE=3]***B.***[/SIZE] If you started in another way, you have two alternatives.

***B 1.*** Start with a fresh system or

***B 2.*** try to fix the bootloader in UEFI mode according to the description in [post #11 in *sysmatck*'s tutorial thread](http://ubuntuforums.org/showthread.php?t=2276498&p=13302294#post13302294). See also the other posts in that thread. Start with *sysmatck*'s post #1. You need a pack with all necessary files for you to modify as you need. *sysmatck* made the original version, usb-pack_efi.zip, and I made a modified version.

This will probably need a lot of 'trial and error', so make backup copies after each step forward :-)

---

### Post by Sbininit on 2016-05-05
I like the USB live version of Lubuntu 16.04 but I'm having a few issues. 
1. I have zero permission to do anything with my HD's and have no power to change it in root.

2.In persistent mode I try to do restore bookmarks backup from json or html from my bookmarks backup folder and have absolutely no luck. No bookmarks are created.

---

### Post by sudodus on 2016-05-05
I am not the best person to solve those problems.

I think you have better luck with two separate threads in the [forum: General Help](http://ubuntuforums.org/forumdisplay.php?f=331) in order to get good help to solve those problems: One thread about permissions in a live session to manage partitions on the HDD, and one thread about restoring bookmarks in a persistent live session. That way you can get the attention of people who know more about those things :-)

---

### Post by Sbininit on 2016-05-07
Thanks man! Is there a way to mount those dd_ubuntu.img.xz  file's

---

### Post by sudodus on 2016-05-07
A dd_ubuntu.img.xz file is simply an image of an installed Ubuntu system, and the image is compressed with the program xz.

After expansion it might be possible with to mount an uncompressed image file with kpartx, but I would not recommend it. Instead you should use mkusb to install (alias clone, flash, restore, burn) directly from the compressed image file to a [target mass storage] device, for example a USB pendrive. It is also possible to install into an internal drive, or an external drive connected via eSATA or USB.

After that install process with mkusb the target drive will be bootable.

---

### Post by C.S.Cameron on 2016-11-18
Following up on post 4 it is possible to use multiple casper-rw files on a single partition by adding a path to persistence in grub "persistent-path=/(folderx)/"

The menuentries looks like:

```

menuentry "ubuntu1.iso" {
set root=(hd0,1)
loopback loop /isos/ubuntu1.iso
linux (loop)/casper/vmlinuz.efi boot=casper persistent persistent-path=/casper1/ iso-scan/filename=/isos/ubuntu1.iso noeject noprompt --
initrd (loop)/casper/initrd.lz
}

menuentry "ubuntu2.iso" {
set root=(hd0,1)
loopback loop /isos/ubuntu2.iso
linux (loop)/casper/vmlinuz.efi boot=casper persistent persistent-path=/casper2/ iso-scan/filename=/isos/ubuntu2.iso noeject noprompt --
initrd (loop)/casper/initrd.lz
}
```

The first menuentry boots an iso named "ubuntu1.iso" located in the folder named "isos" using the casper-rw file located in the folder named "casper1".

The second menuentry boots an iso named "ubuntu2.iso" located in the folder named "isos" using the casper-rw file located in the folder named "casper2".

I am now looking for a way to use this to use multiple persistent partitions.

---

### Post by sudodus on 2016-11-18
I will look into this task, but it will probably take a long time until I find a good solution. It requires not only testing, but also thinking and getting ideas from other people.

- Did you try with an **ext** partition (and BIOS mode), where a casper-rw file (and a home-rw file) can be bigger than 4 GB?

- Would it be possible to link (symbolic link) from a limited casper-rw file (and a home-rw file) to a partition which is bigger, and keep programs, that need not run during boot in the linked partition? I'm thinking of something similar to linking from the home partition to a data partition.

---

### Post by mikodo on 2016-11-18
Hi sudodus, I hope you are well! Thank you, for the tools you develop.

If I may, I would like to ask two questions, to help me decide, (through testing later and experimentation with), to determine, if I would prefer to use this process starting at Post #1, 'One pendrive for all PC (Intel/AMD) computers - Ubuntu 64-bit and Lubuntu 32-bit' and with the subsequent Posts you have outlined, to use for my testing of 'persistent' usb multi-boot 'buntu's. (This, to probably replace my traditional methods for testing with 1/ Multi-boot internal disk installs & 2/ Virtualization).

Question 1.

 Am I correct in assuming Post #1 and your subsequent Posts, are what I need to, (read, experiment with and test the 'persistent', usb multi-booting), and that the OS updates can be updated and the Ubuntu 'release' Kernels, can be upgraded?

Question 2. 

Could I make symlinks in the 'persistent' usb drive's OS's, to my Data Drive/Partition (for my ~600 GB 'Data' partition) with each 'persistent usb' OS? (I have large unused and new 64 GB pendrives I can use, and of course could buy more, when needed later).

If, answers to both questions are 'Yes', then, that is all I need in a response from you. I could take it from there myself, as your documentation is clear, concise, organized and prolific.  

Addendum:

 I have been reading through this thread a bit. If, you answer to the affirmative with my 2 questions, I think I will probably pay attention to  posts (6, 7, 8, 10, 11, 48, 49) > 'grub-n-iso' systems, and as you suggested in, Post #8 "compressed image files makes it easy for a beginner to install". I am not planning for using this for a server install. But, for 'released' 64-bit .iso's. Not testing of 'next' releases. 

Thank you.

---

### Post by sudodus on 2016-11-19
I am not sure that I understand, but this is my reply:

> Question 1.

Am I correct in assuming Post #1 and your subsequent Posts, are what I need to, (read, experiment with and test the 'persistent', usb multi-booting), and that the OS updates can be updated and the Ubuntu 'release' Kernels, can be upgraded?

In persistent live systems you can update & upgrade application programs, but not the kernel itself and its drivers, because they are started before the overlay structure that implements persistence is started.

The way to keep a persistent live system up to date is to get a new version of the iso file (as can be done with the daily iso files), and this can be done incrementally with rsync as described in some of my previous posts.

But, and this is crucial, with a new iso file you [s]must often[/s] should clear the casper-rw partition except the home directory (.../upper/home). For this reason it is a good idea to create a separate home-rw partition. Then you can clear the whole casper-rw partition and keep the home-rw partition. And you have to install your application programs again. (So it is more complicated than to keep an installed system up to date.)
> 
Question 2.

Could I make symlinks in the 'persistent' usb drive's OS's, to my Data Drive/Partition (for my ~600 GB 'Data' partition) with each 'persistent usb' OS? (I have large unused and new 64 GB pendrives I can use, and of course could buy more, when needed later).

Linux symlinks work in linux file systems (typically ext2, ext3, ext4), but I think not in FAT32 and NTFS file systems. Please *test* if it works to do what you want to do!

-o-

Please ask again, if I misunderstood your questions :-)

---

### Post by mikodo on 2016-11-19
^^ Thanks, sudodus.

That answers my questions. I understand, what needs to be done to update the .iso's. Yep, following your guides and testing to get it done right.

Cheers.

---

### Post by kinghov on 2016-12-06
Thanks so much, that solves my problem!

---

### Post by sudodus on 2016-12-06
I'm glad it works :-)

Does this solve the problem you reported in the other thread too, [in this post](https://ubuntuforums.org/showthread.php?t=1958073&page=26&p=13579213#post13579213)?

---

### Post by greengalaxy on 2017-05-04
I too am seeking to get a multi-boot with multible persistent paritions.   And I have an IDEA /solution, but it requires some programming (or else manually rename each at each OS switch):

Essentially, create separate 'casper' partitions, but each named/labeled after the OS they will work with.  Then re-name the needed one to 'casper-rw' whenever it is needed for use.   This could be done automatically:   when user boots up, they choose which OS from the grub GUI, and then some new program code would change the name of its persistent partition to to 'casper-rw', before actually booting.

The next time user chooses another OS, it will rename the first one back to its original name (ex:  'ubuntu-1-persistance', before changing the name/label of next partition, 'ubuntu-2-persistance' to 'casper-rw'.   To keep track of the original names, each such partition will have this txt file:   '! PartitionName-Do Not Delete!.txt', which will store its value.

Do you know a programmer who could do this?
—-

---

### Post by greengalaxy on 2017-05-04
Hmm..  I now says that you wrote in an earlier past, #14 on this thread, that you can have more than 1 persistents in 1 partition, it will be store in: .../casper-rw/upper

So, perhaps its possible to edit the configs or other sopmehow, so you have:
.../casper-rw/kubuntu
.../casper-rw/xubuntu
.../casper-rw/mint16
ETC...?

---

### Post by sudodus on 2017-05-05
@greengalaxy

It is complicated to have persistence with partitions in a multiboot system, if the different operating systems use the same label, like 'casper-rw' for the Ubuntu family.

I think what you want might work, if you connect the drive to a computer with a running operating system, or add a small quick system, for example Tiny Core, and rename the partitions when that system is running. And after that reboot again into the system you want to run.

I don't know a programmer who would do this for you. Maybe you can do it yourself :-P

In that case, please report back here to tell us about it!

---

### Post by C.S.Cameron on 2017-05-05
> **greengalaxy said:**
> I too am seeking to get a multi-boot with multible persistent paritions.
&#8212;-

I still haven't found a way to use multiple casper-rw partitions with a multiboot drive but there are some alternatives:

- Multiple casper-rw files work if they are located in uniquely named folders, (casper1, casper2...). and path is given in grub, (persistent-path=/casper1/), size is limited to 4GB each.

- Multiple casper-rw partitions can be located each on it's own flash drive, plug in the persistence you want before booting the MB drive.

- Puppy Linux can have multiple persistence files of whatever size required, if you are not particular about OS.

---

### Post by sudodus on 2017-05-05
> **C.S.Cameron said:**
> I still haven't found a way to use multiple casper-rw partitions with a multiboot drive but there are some alternatives:

- Multiple casper-rw files work if they are located in uniquely named folders, (casper1, casper2...). and path is given in grub, (persistent-path=/casper1/), size is limited to 4GB each.

- Multiple casper-rw partitions can be located each on it's own flash drive, plug in the persistence you want before booting the MB drive.

- Puppy Linux can have multiple persistence files of whatever size required, if you are not particular about OS.

@greengalaxy,

I agree with @C.S.Cameron. These workarounds are good alternatives, because I think it might be rather difficult and not very convenient to do what you want (unless you find a new way to do it).

---

### Post by ccheath on 2017-08-25
> **sudodus said:**
> [SIZE=4]Method[/SIZE]

I made the 'One pendrive for all PC (Intel/AMD) computers' according to the following steps:

1. ***Wipe*** the first megabyte of a pendrive with ***mkusb***.

2. ***Create*** a FAT32 partition and and an empty second partition with ***gparted***. Mount the FAT32 partition.

3. ***Flash*** the Ubuntu iso file with the ***Startup Disk Creator*** to the FAT32 partiiton.

You lost me at step 1.
i've got mkusb installed but,
"wipe the first megabyte" ?
you're really gonna do all this awesome documentation but not give a simple (i assume) command to accomplish step 1??
(also i'm curious as to why you do this... i have my assumptions but ... ya'know...)

as i begin reading ahead, i am stopped on step 2 
it is the same, and so is step 3.

they're like great sourcecode comments without the source code itself


i'm resisting my urge to be cynical about why the first three steps in such a thorough write-up lack critical detail

i'm willing to help you help me if you'll help me help you

i've got an 8gb usb2 flash drive i've been using to live boot linux mint and ubuntu for years...  
(sometimes with persistence) but i stopped really caring that much  about persistence lately and care more about multi booting

i want to do what you've done here and have two linux distros that can boot into and install a great OS on any computer
but i also want to put a couple other things on there
how about a dos or freedos? mainly for GRC's SpinRite but yeah, DOS
and finally a rescue/antivirus - i might choose bitdefender-rescue-cd 

what do you think?

---

### Post by sudodus on 2017-08-26
> **ccheath said:**
> You lost me at step 1.
i've got mkusb installed but,
"wipe the first megabyte" ?
you're really gonna do all this awesome documentation but not give a simple (i assume) command to accomplish step 1??

**mkusb** is a tool with a graphical user interface. You navigate via menus, so there is no command line to offer. Maybe the quick start manual can help you get started and find the relevant menu, where you can wipe the first megabyte (actually mibibyte, base 2).

[mkUSB-quick-start-manual-12.pdf](https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-12.pdf)
> 
(also i'm curious as to why you do this... i have my assumptions but ... ya'know...)

as i begin reading ahead, i am stopped on step 2 

**gparted** is also a tool with a graphical user interface. You navigate via menus, so there is no command line to offer. Maybe the following link will help you use it,

[GParted partitioning software - Full tutorial ](http://www.dedoimedo.com/computers/gparted.html)
> 
it is the same, and so is step 3.

The Ubuntu **Startup Disk Creator** has been changed in a fundamental way since I wrote those instructions. You can still use the version that comes with Ubuntu 14.04.x LTS for this purpose. But the version of the Startup Disk Creator in Ubuntu 16.04 LTS (16.04.x) and newer versions is a cloning tool, and does not do what is intended in step 3. You would need another tool for that purpose, a tool to extract the content. It would be possible with for example the command line tool **rsync**. And you would install the bootloader separately.
> 
they're like great sourcecode comments without the source code itself


i'm resisting my urge to be cynical about why the first three steps in such a thorough write-up lack critical detail

i'm willing to help you help me if you'll help me help you

i've got an 8gb usb2 flash drive i've been using to live boot linux mint and ubuntu for years...  
(sometimes with persistence) but i stopped really caring that much  about persistence lately and care more about multi booting

i want to do what you've done here and have two linux distros that can boot into and install a great OS on any computer
but i also want to put a couple other things on there
how about a dos or freedos? mainly for GRC's SpinRite but yeah, DOS
and finally a rescue/antivirus - i might choose bitdefender-rescue-cd 

what do you think?

I don't use multiboot pendrives nowadays. Instead I treat USB pendrives as temporary devices. I keep the systems (and update them) as iso files, and when I need a boot drive with an installer, a live system or a persistent live system, I create it with mkusb into a USB pendrive (and I use another tool, when the iso file and mkusb are not compatible).

I know that some people want a multiboot device, that is easy to carry around. So if you want to try according to my instructions, you are welcome, and I will try to help you, but it might be a bumpy ride.

You might also try one of the polished tools, that are maintained for this purpose, for example multibootUSB or YUMI

[http://multibootusb.org/](http://multibootusb.org/)

[www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by ccheath on 2017-08-26
[QUOTE=sudodus]**mkusb** is a tool with a graphical user interface. You navigate via menus, so there is no command line to offer. Maybe the quick start manual can help you get started and find the relevant menu, where you can wipe the first megabyte (actually mibibyte, base 2).

[mkUSB-quick-start-manual-12.pdf](https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-12.pdf)

**gparted** is also a tool with a graphical user interface. You navigate via menus, so there is no command line to offer. Maybe the following link will help you use it,

[GParted partitioning software - Full tutorial ](http://www.dedoimedo.com/computers/gparted.html)

The Ubuntu **Startup Disk Creator** has been changed in a fundamental way since I wrote those instructions. You can still use the version that comes with Ubuntu 14.04.x LTS for this purpose. But the version of the Startup Disk Creator in Ubuntu 16.04 LTS (16.04.x) and newer versions is a cloning tool, and does not do what is intended in step 3. You would need another tool for that purpose, a tool to extract the content. It would be possible with for example the command line tool **rsync**. And you would install the bootloader separately.[/quote]


i get your point but the level of documentatino/info you're giving here is making me take a step back and be careful then a novice is going to be lost ... 

i'll admit that maybe i'm nitpicking  here but let's move on

[QUOTE=sudodus]I don't use multiboot pendrives nowadays. Instead I treat USB pendrives as temporary devices. I keep the systems (and update them) as iso files, and when I need a boot drive with an installer, a live system or a persistent live system, I create it with mkusb into a USB pendrive (and I use another tool, when the iso file and mkusb are not compatible).

I know that some people want a multiboot device, that is easy to carry around. So if you want to try according to my instructions, you are welcome, and I will try to help you, but it might be a bumpy ride.

You might also try one of the polished tools, that are maintained for this purpose, for example multibootUSB or YUMI

[http://multibootusb.org/](http://multibootusb.org/)

[www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)[/QUOTE]
my aim and approach is similar to yours i think 
i'm looking to have one usb drive for just about any computer utilizing two iso's (a 32bit and a 64 bit)
plus maybe a couple other if possible

in all walks of life (business being one of those walks/subsets of life) time management is a major factor in productivity/profit/learning/etc

some people say that the best sysadmins are lazy
they're supposedly putting in tons of "work" to save themselves time in the long run

i'll be back in a while with an update once i get some time to finish this (Hopefully) or hit a dead end

---

### Post by ccheath on 2017-08-26
btw, mkusb wil wipe a Mibibyte... not Megabyte
not sure who's typo ... but that's neither here nor there

---

### Post by sudodus on 2017-08-26
I agree that this thread is not intended for a novice. And yes, mkusb wipes the first mibibyte (at the head end of the drive).

I hope that I will get time and energy enough to improve the documentation in this thread. But I cannot promise to do more than a few fixes, those that you find and report as a starter :-P

---

### Post by ccheath on 2017-08-26
also, getting through gparted could use some step by step
and now i'm on step 3... you're saying that i can't use the current Startup Disk Creator?

> **sudodus said:**
> I agree that this thread is not intended for a novice. And yes, mkusb wipes the first mibibyte (at the head end of the drive).

I hope that I will get time and energy enough to improve the documentation in this thread. But I cannot promise to do more than a few fixes, those that you find and report as a starter :-P

cool
now we're on the same page
...
help me help you [help me] [help you]

---

### Post by sudodus on 2017-08-26
You can use the current Startup Disk Creator for its main purpose, to create a USB boot drive, that lets you 'Try Ubuntu' and/or 'Install Ubuntu'. It clones the content of the iso file to a partition with the read-only iso9660 file system. The old version of Startup Disk Creator (from Ubuntu 14.04.x and older) extracts the content of the iso file into a partition with the FAT32 file system. And that is what is wanted for what you intend to do.

---

### Post by ccheath on 2017-08-26
so do i need to find the old version or should i use a different method?

---

### Post by sudodus on 2017-08-26
You find the old version Ubuntu 14.04.1 LTS via this link,

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

But I think it will be easier if you select the other method described in this thread, the grub-n-iso method. See Posts #6, 7, 8, 10, 11, 48, 49. There are direct links from the first post (the opening post of this thread) to these posts.

---

### Post by sudodus on 2018-04-30
[SIZE=4]Make persistent live drives with casper-rw and home-rw partitions[/SIZE]

The background and starting point to this method and tool are described with many details in the following link (in this same thread),

**Post #8. [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")**

The shellscript **mk-grub-n-iso multiboot** was forked into a new shellscipt (still in a crude state, but it can do two importnat tasks automatically.

The new shellscript has a long descriptive name, **mk-persistent-live_with_home-rw**. I know that it is too long, but I have not found any good short name yet, maybe mkusb-cup (Create Update Persistent live [USB] drives).

> **mk-persistent-live_with_home-rw** is a text mode shellscript, that builds
a persistent boot drive with a 'casper-rw' partition for system persistence
and a 'home-rw' partition for home persistence. There are two modes, to

- **create** a persistent live system
- **upgrade** a persistent live system,
. replace the iso file
. wipe: create new file system in the 'casper-rw' partition
. preserve: keep the content in the 'home-rw' partition.


The purpose of this tool is to make it easy to keep the persistent live drive up to date. Usually it does not work to simply replace the iso file (or cloned or extracted) because the previous overlay of the system flles do not match. But *it is usually possible to keep the home directory including personal files and the settings* (usually in hidden configuration files in the user's home directory).

This is possible to do manually, but it is somewhat tricky and making this task automatic makes it both easier and safer.

Use **mk-persistent-live_with_home-rw**

- with USB drives and memory cards with 8 GB memory size or more. Splitting the available memory in two partitions is a bad idea in small drives,

- if you intend to use the persistent live system for a longer time,

- if you need to upgrade the system for other reasons, for example to get security upgrades or have software that need upgrades of the operating system.

**Testing**

I have tested standard Ubuntu, Lubuntu, Xubuntu and Ubuntu Studio. All these work, when upgraded within the same version (I tested all of them in 18.04 LTS). 

I tested also upgrading standard Ubuntu, Lubuntu, Xubuntu from 16.04.1 LTS to 18.04 LTS, and it works (the content of the home partition is still compatible).

Finally I tested from Lubuntu 18.04 LTS to Xubuntu-Core 18.04 LTS, and it worked too (but not in the other direction). We should not expect it to work, if the desktop environments have incompatible configuration files.

**Demo example**

I installed Ubuntu 18.04 LTS in a 60 GB SSD and used that system to check that **mk-persistent-live_with_home-rw** works not only in my 'production system', Xubuntu + Lubuntu 16.04.1 LTS still keeping the xenial kernel series. The I created a persistent live USB 3 pendrive with 16 GB. The attached screenshots and the 'console dialogue' illustrates what it looks like and how it works.

**mk-persistent-live_with_home-rw** is bundled with **grub-n-iso_multiboot** and you can get it by downloading a tarball and check its md5sum, that you find at

**[phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)**

- grub-n-iso_multiboot.tar.gz
- grub-n-iso_tarfile.txt
- grub-n-iso.md5.asc

**Feedback is welcome. Please test it and tell me what works, and what needs improvement.**

I know, that this shellscript is not very user friendly, but it works, and in due time, I hope to add a better user interface.

```

ubuntu@ubuntu:~/Downloads/grub-n-iso_multiboot$ [COLOR="#0000FF"]./mk-persistent-live_with_home-rw[/COLOR]

Usage:   sudo ./mk-persistent-live_with_home-rw <source.iso> <target device>
Example: sudo ./mk-persistent-live_with_home-rw ubuntu.iso /dev/sdx

This shellscript './mk-persistent-live_with_home-rw'

can create and upgrade persistent live drives with two partitions for
persistence, 'casper-rw' for system data and 'home-rw' for the home data.

It works only with iso files of Ubuntu Desktop, Ubuntu community flavours,
and maybe some linux distros and respins with the same boot structure.

Try again with the correct target device according to the list below

Press Enter to continue
MODEL            NAME   FSTYPE   LABEL                  MOUNTPOINT                     SIZE
                 loop0  iso9660  Ubuntu 18.04 LTS amd64 /cdrom                         1.8G
                 loop1  squashfs                        /rofs                          1.7G
                 loop2  squashfs                        /snap/core/4486               86.6M
                 loop3  squashfs                        /snap/gnome-3-26-1604/59       140M
                 loop4  squashfs                        /snap/gnome-calculator/154     1.6M
                 loop5  squashfs                        /snap/gnome-characters/69     12.2M
                 loop6  squashfs                        /snap/gnome-logs/25             21M
                 loop7  squashfs                        /snap/gnome-system-monitor/36  3.3M
OCZ-AGILITY3     sda                                                                  55.9G
                 |-sda1 vfat     UBU1804-64                                             63M
                 |-sda2 ext4     isodevice              /isodevice                     2.5G
                 |-sda3 ext4     casper-rw                                            14.5G
                 `-sda4 ext4     home-rw                /home                         38.9G
Extreme          sdb                                                                  14.6G
                 `-sdb1 vfat     MY_STORAGE                                           14.6G
CDDVDW SN-208AB  sr0                                                                  1024M
ubuntu@ubuntu:~/Downloads/grub-n-iso_multiboot$ [COLOR="#0000FF"]sudo ./mk-persistent-live_with_home-rw xubuntu-18.04-core-amd64.iso /dev/sdb[/COLOR]
'xubuntu-18.04-core-amd64.iso' is identified as the source ISO file

MODEL            NAME   FSTYPE LABEL      MOUNTPOINT  SIZE
Extreme          sdb                                 14.6G
                 `-sdb1 vfat   MY_STORAGE            14.6G

Using 'grub.cfg' in the current directory
Using 'usb-pack_efi' in the current directory
-------------------------------------------------------------------------
Did you check and if necessary copy any valuable files from
the device '/dev/sdb' before re-using it as a persistent live drive?

Are ready to go ahead and overwrite '/dev/sdb'?
-------------------------------------------------------------------------
Create new system or upgrade with new iso file or quit? (c/u/q)? [COLOR="#FF0000"]**c**[/COLOR]
**[COLOR="#FF0000"] Final checkpoint [/COLOR] Create '/dev/sdb' [COLOR="#FF0000"] Are you sure? (y/n) [/COLOR] **[COLOR="#FF0000"]**y**[/COLOR]
512+0 records in
512+0 records out
2097152 bytes (2.1 MB, 2.0 MiB) copied, 0.236252 s, 8.9 MB/s
mkfs.fat 4.1 (2017-01-24)
/dev/sdb1 has 64 heads and 32 sectors per track,
hidden sectors 0x0800;
logical sector size is 512,
using 0xf8 media descriptor, with 129024 sectors;
drive number 0x80;
filesystem has 2 32-bit FATs and 1 sector per cluster.
FAT size is 993 sectors, and provides 127006 clusters.
There are 32 reserved sectors.
Volume ID is ce44440d, no volume label.
 **Automatic or manual selection of partition sizes **
Do you want *automatic* partitioning? (y/n) [COLOR="#FF0000"]**y**[/COLOR]
Warning: The resulting partition is not properly aligned for best performance.
256+0 records in
256+0 records out
1048576 bytes (1.0 MB, 1.0 MiB) copied, 0.0248828 s, 42.1 MB/s
256+0 records in
256+0 records out
1048576 bytes (1.0 MB, 1.0 MiB) copied, 0.0750604 s, 14.0 MB/s
256+0 records in
256+0 records out
1048576 bytes (1.0 MB, 1.0 MiB) copied, 0.21233 s, 4.9 MB/s
mke2fs 1.44.1 (24-Mar-2018)
Creating filesystem with 524288 4k blocks and 131072 inodes
Filesystem UUID: fafb8bba-c1c9-4231-942f-2c8ee1365db0
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information: done 

mke2fs 1.44.1 (24-Mar-2018)
Creating filesystem with 1079933 4k blocks and 270336 inodes
Filesystem UUID: 2fc49f5f-13a4-4519-a744-951b9b140277
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information: done 

mke2fs 1.44.1 (24-Mar-2018)
Creating filesystem with 2210855 4k blocks and 553792 inodes
Filesystem UUID: a42d5db1-872a-4e88-be68-710fc4c91238
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information: done 

---------------------------------------------------------------------------
     Use gparted to check (and maybe change) the partitions
---------------------------------------------------------------------------
======================
libparted : 3.2
======================
Information: You may need to update /etc/fstab.

tune2fs 1.44.1 (24-Mar-2018)                                              
tune2fs 1.44.1 (24-Mar-2018)
tune2fs 1.44.1 (24-Mar-2018)
tune2fs 1.44.1 (24-Mar-2018)
tune2fs 1.44.1 (24-Mar-2018)
---------------------------------------------------------------------------
source=xubuntu-18.04-core-amd64.iso
---------------------------------------------------------------------------
UEFI Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
BIOS Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
Copying files ...
Archive:  usb-pack_efi.zip
   creating: usb-pack_efi/
   creating: usb-pack_efi/EFI/
   creating: usb-pack_efi/EFI/BOOT/
  inflating: usb-pack_efi/EFI/BOOT/bootia32.efi  
  inflating: usb-pack_efi/EFI/BOOT/bootx64.efi  
   creating: usb-pack_efi/boot/
   creating: usb-pack_efi/boot/grub/
  inflating: usb-pack_efi/boot/grub/grub.cfg  
  inflating: usb-pack_efi/boot/grub/menu.lst  
   creating: usb-pack_efi/boot/grub4dos/
  inflating: usb-pack_efi/boot/grub4dos/g2ldr  
  inflating: usb-pack_efi/boot/grub4dos/grub.exe  
   creating: usb-pack_efi/boot/memtest/
  inflating: usb-pack_efi/boot/memtest/memtest.bin  
  inflating: usb-pack_efi/boot/memtest/memtest86+-5.01.bin  
   creating: usb-pack_efi/iso/
sending incremental file list
./
EFI/
EFI/BOOT/
EFI/BOOT/bootia32.efi
EFI/BOOT/bootx64.efi
boot/
boot/grub/
boot/grub/menu.lst
boot/grub4dos/
boot/grub4dos/g2ldr
boot/grub4dos/grub.exe
boot/memtest/
boot/memtest/memtest.bin
boot/memtest/memtest86+-5.01.bin

sent 2,311,429 bytes  received 188 bytes  4,623,234.00 bytes/sec
total size is 2,310,239  speedup is 1.00
mount: /tmp/looper: WARNING: device write-protected, mounted read-only.
rm: cannot remove '/tmp/isotrg/*.iso': No such file or directory
< xubuntu-18.04-core-amd64.iso pv > /tmp/isotrg/xubuntu-18.04-core-amd64.iso
 663MiB 0:00:01 [ 350MiB/s] [=============================================================================>] 100%            
Syncing the target device ...
MODEL            NAME   FSTYPE LABEL       MOUNTPOINT  SIZE
Extreme          sdb                                  14.6G
                 |-sdb1 vfat   XUB1804CORE              63M
                 |-sdb2 ext4   isodevice                 2G
                 |-sdb3 ext4   casper-rw               4.1G
                 `-sdb4 ext4   home-rw                 8.4G
The target device is ready to use.
'xubuntu-18.04-core-amd64.iso' was installed
ubuntu@ubuntu:~/Downloads/grub-n-iso_multiboot$ 

```

**Edit:** new version (improved but still a testing version) uploaded 2018-05-04

---

### Post by sudodus on 2018-05-01
[SIZE=4]Make persistent live drives with casper-rw and home-rw partitions - more testing[/SIZE]

I tested upgrading directly

- from Ubuntu 12.04.1 LTS to Ubuntu 18.04 LTS works
- from Ubuntu 14.04.1 LTS to Ubuntu 18.04 LTS works
- (from Ubuntu 16.04.1 LTS to Ubuntu 18.04 LTS was tested already and works)


Upgrading works from these old versions. The home directory survives, and it is compatible (at least the things that I have tested).

- The command line history in **~/.bash_history** survives (of course).
- Other files survive too (in this example an old screenshot).
- The setting of my keyboard (Swedish) survives and is selected directly after booting the upgraded pendrive.

See the attached screenshots.

---

### Post by C.S.Cameron on 2018-05-01
I was doing good until it gave me a warning about using drives less than 8GB, then it shut down.

There could possibly be a good reason to have one on a 4GB drive, I'm just not sure what it could be.

All my drives 8GB and over are in use.

I really like the idea.

---

### Post by sudodus on 2018-05-02
@C.S.Cameron,

- Do you want a special edition, that works with a 4 GB pendrive, just for testing?

- Or do you want the standard version to work also with a 4 GB pendrive? It means smaller margins for upgrading to new versions with bigger iso files, but I hope it should be OK for using daily iso files within the same (LTS) version.

[hr][/hr]
Edit: Anyway, when you use 'mk-persistent-live_with_home-rw' on a 4 GB pendrive, you had better stay with small iso files, I suggest Lubuntu. Otherwise there may not be enough space for it to work.

The problem is that the iso files are growing for each new version, and I designed a method to give the partitioning a margin for some future growth.

The current Ubuntu iso file size is 1.8 GiB (1921843200 bytes), so there will be very limited space left for persistence in a 4 GB pendrive.

```

695M ubuntu-12.04.1-desktop-amd64.iso
981M ubuntu-14.04.1-desktop-amd64.iso
1,5G ubuntu-16.04.1-desktop-amd64.iso
1,8G ubuntu-18.04-desktop-amd64.iso

1,1G lubuntu-18.04-desktop-amd64.iso

```

The easy alternative (for me) would be that you buy a brand new and [fast USB 3 pendrive](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed) but it costs money :-P

---

### Post by sudodus on 2018-05-04
A new version of **mk-persistent-live_with_home-rw** (improved but still a testing version) was [uploaded](http://phillw.net/isos/linux-tools/uefi-n-bios/?C=M;O=D) 2018-05-04.

There are several improvements:

- Main improvement: The previous version created good boot drives, when the shellscript, mk-persistent-live_with_home-rw, was run in 16.04 LTS, but not in 18.04 LTS because of some problems with the bootloader (grub). This version does not install the bootloaders (for UEFI and BIOS) but instead clones from a compressed image file to the head end of the drive including the first partition.

This means that it is possible to install from UEFI mode to BIOS mode (which can be very tricky). The systems created work in UEFI mode and BIOS mode, but not with secure boot. See [this link about mkusb](https://help.ubuntu.com/community/mkusb/persistent#Using_data_from_the_source_iso_file), if you want a persistent live drive that works with secure boot (in UEFI mode).

- Improved user interface: still text only, but better logical order of the questions.

- Improved management, unmounting, if/when the operating system mounts the partitions automatically, while the shellscript is doing its job.

---

### Post by sudodus on 2018-05-20
[SIZE=4]Backup and restore the /home directory in casper-rw partitions of mkusb persistent drives[/SIZE]

This is an alternative to **mk-persistent-live_with_home-rw** which was created some weeks ago.

The new shellscript has a descriptive name, **[SIZE=3]mkusb-backup-n-restore-home[/SIZE]**. I know that it might be too long, but I have not found any good short name yet.

**It is a bash shellscript with a zenity graphical user interface, that 'only' manipulates the /home directory in casper-rw partitions of mkusb persistent drives**.

It is merged into mkusb version 12.3.2 and you can select it from the starter menu "Install / Backup / Restore / Wipe"

There are two modes, to

- **backup** the /home directory to a tarball
- **restore** the /home directory from a tarball

The purpose of this tool is to make it easy to keep the persistent live drive up to date. Usually it does not work to simply transfer the whole content of the 'casper-rw' partition because the previous overlay of the system files does not match. But *it is usually possible to keep the home directory including personal files and the settings* (usually in hidden configuration files in the user's home directory).

This is possible to do manually, but it is somewhat tricky and automation makes it both easier and safer.

[SIZE=3]Use **mkusb-backup-n-restore-home**[/SIZE]

- with USB drives and memory cards, that are made persistent live with mkusb. The size limit depends on the iso file, but normally you would use a drive with 4 GB or more. In order to get a *fast* USB 3 drive, you need 16 GB,

- if you intend to use the persistent live system for a longer time,

- if you need to upgrade the system for other reasons, for example to get security upgrades or have software that need upgrades of the operating system.

[SIZE=3]Upgrade (or repair) a persistent live system like this[/SIZE]

1. Backup the /home directory to a tarball using 'mkusb-backup-n-restore-home' or if you have mkusb 12.3.2 (or a newer version), select it from the starter menu "Install / Backup / Restore / Wipe"

2. Create a fresh persistent live system of standard Ubuntu or the same flavour (Kubuntu, Lubuntu ... Xubuntu) using **mkusb**. Use the daily iso files of the LTS versions to get a system that is up to date.

3. Restore the /home directory from the tarball to the fresh persistent live system.

[SIZE=3]Testing[/SIZE]

I have tested standard Ubuntu, Lubuntu and Xubuntu. All these work, when upgraded within the same version (I tested all of them in 18.04 LTS). 

I tested also upgrading Lubuntu from 16.04.1 LTS to 18.04 LTS, and it works (the content of the home partition is still compatible).

You need only one standalone shellscript file (and its corresponding md5sum file). Get it by downloading a tarball and check its md5sum, that you find at

**[phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)**

- mkusb-backup-n-restore-home.tar.gz
- mkusb-backup-n-restore-home.tar.gz.md5

```

$ md5sum -c mkusb-backup-n-restore-home.tar.gz.md5
mkusb-backup-n-restore-home.tar.gz: OK

```
Version 0.0.4 dated 2018-05-26 has the following md5sums:
```

$ md5sum mkusb-backup-n-restore-home*
eb38def3b40455d27cc43d85546e07a4  mkusb-backup-n-restore-home.tar.gz
40812f817efa1ae3ca0e6a91c8fdec58  mkusb-backup-n-restore-home.tar.gz.md5

```

**Feedback is welcome. Please test it and tell me what works, and what needs improvement.**

This shellscript is relatively user friendly with a text console and zenity dialogue windows as a GUI. It is made to work in Wayland without extra tweak (the tasks with elevated permissions are done in text mode).

```

sudodus@m4800:~$ echo $XDG_SESSION_TYPE
wayland

sudodus@m4800:~/Hämtningar$ ./mkusb-backup-n-restore-home
Usage:    ./mkusb-backup-n-restore-home -b or -r
Examples: ./mkusb-backup-n-restore-home -b  # backup
          ./mkusb-backup-n-restore-home -r  # restore
          backup-home   # if in PATH, otherwise add directory path
          restore-home  #                 - '' -                   

sudodus@m4800:~/Hämtningar$ ./mkusb-backup-n-restore-home -b
live system or temporary superuser permissions
bupfile=/home/olle/mkusb-backup-home.tar-lubuntu.gz
mpcrw=/tmp/tmp.CLx4roLVee
---------------------------------------------------
Extreme sdb 14,9G sdb5 10,2G casper-rw
Extreme sdc 29,8G sdc5 14G casper-rw
---------------------------------------------------
srcdev=/dev/sdb5
 Device: /dev/sdb  OS: Lubuntu 18.04 LTS amd64 
umount: /dev/sdb2: inte monterad.
mount casper-rw partition
Filsystem      Storlek Använt Ledigt Anv% Monterat på
/dev/sdb5          11G    41M   9,6G   1% /tmp/tmp.CLx4roLVee
-----------------------------------------------------------------
Quit

sudodus@m4800:~/Hämtningar$ ./mkusb-backup-n-restore-home -b
live system or temporary superuser permissions
bupfile=/home/olle/mkusb-backup-home.tar-lubuntu.gz
mpcrw=/tmp/tmp.VcMklDP71A
---------------------------------------------------
Extreme sdb 14,9G sdb5 10,2G casper-rw
Extreme sdc 29,8G sdc5 14G casper-rw
---------------------------------------------------
srcdev=/dev/sdb5
 Device: /dev/sdb  OS: Lubuntu 18.04 LTS amd64 
umount: /dev/sdb1: inte monterad.
umount: /dev/sdb2: inte monterad.
umount: /dev/sdb3: inte monterad.
umount: /dev/sdb4: inte monterad.
umount: /dev/sdb5: inte monterad.
mount casper-rw partition
Filsystem      Storlek Använt Ledigt Anv% Monterat på
/dev/sdb5          11G    41M   9,6G   1% /tmp/tmp.VcMklDP71A
-----------------------------------------------------------------
upper/home/
upper/home/lubuntu/
upper/home/lubuntu/.config/
upper/home/lubuntu/.config/ubuntu-system-settings/
...
upper/home/lubuntu/Templates/
upper/home/lubuntu/Music/
upper/home/lubuntu/.profile
upper/home/lubuntu/.xsession-errors
 Done :-) 
'/home' from 'casper-rw'  backed up  to the file
 /home/olle/mkusb-backup-home.tar-lubuntu.gz 

sudodus@m4800:~/Hämtningar$ ./mkusb-backup-n-restore-home -r
live system or temporary superuser permissions
bupfile=/home/olle/mkusb-backup-home.tar-lubuntu.gz
mpcrw=/tmp/tmp.wcMZQ67Ctv
---------------------------------------------------
Extreme sdb 14,9G sdb5 10,2G casper-rw
Extreme sdc 29,8G sdc5 14G casper-rw
---------------------------------------------------
srcdev=/dev/sdb5
 Device: /dev/sdb  OS: Lubuntu 18.04 LTS amd64 
umount: /dev/sdb1: inte monterad.
umount: /dev/sdb2: inte monterad.
umount: /dev/sdb3: inte monterad.
umount: /dev/sdb4: inte monterad.
umount: /dev/sdb5: inte monterad.
mount casper-rw partition
Filsystem      Storlek Använt Ledigt Anv% Monterat på
/dev/sdb5          11G    41M   9,6G   1% /tmp/tmp.wcMZQ67Ctv
-----------------------------------------------------------------
upper/home/
upper/home/lubuntu/
upper/home/lubuntu/.config/
upper/home/lubuntu/.config/ubuntu-system-settings/
...
upper/home/lubuntu/Templates/
upper/home/lubuntu/Music/
upper/home/lubuntu/.profile
upper/home/lubuntu/.xsession-errors
 Done :-) 
'/home' in 'casper-rw'  restored  from the file
 /home/olle/mkusb-backup-home.tar-lubuntu.gz 
sudodus@m4800:~/Hämtningar$ 

```

---

### Post by C.S.Cameron on 2018-05-22
I like mBNR.
Everything works for me backing up and restoring the home directory embedded in casper-rw.
How do I use mBRN to backup the desktop's home directory and copy it to casper-rw on a USB?
And maybe vice-versa.

---

### Post by sudodus on 2018-05-22
Do you mean to transfer /home between an installed system and a persistent live system?

I have not addressed that task, but it should be possible, maybe even rather easy, to add it.

---

### Post by C.S.Cameron on 2018-05-22
It has worked the times I have tried it, once was from a Full install to a USB with persistent home-rw file.

---

### Post by sudodus on 2018-05-23
[SIZE=4]New version of mkusb-backup-n-restore-home[/SIZE]

I found some bugs and some lack of information in the dialogues, so I made a new version of mkusb-backup-n-restore-home.

Please notice that the screenshots illustrate an upgrade from Lubuntu 16.04.1 LTS to Lubuntu 18.04 LTS.

I have tested upgrading using Ubuntu and Lubuntu iso files. It works to

[LIST]
[*]**upgrade from 14.04.1 LTS** to 16.04.1 LTS and directly to 18.04 LTS,

[*]**downgrade from 18.04 LTS** to 16.04.1 LTS and directly to 14.04.1 LTS,

[*]**upgrade and downgrade from 16.04.1 LTS** to 18.04 LTS and 14.04.1 LTS.

[*]**Edit 1**: test with Ubuntu 12.04 LTS,
[LIST]
[*]mkusb has general problems with 12.04.1 LTS. It is not a hybrid iso file, but after [treatment with isoybrid](https://help.ubuntu.com/community/mkusb/isohybrid), cloning made a bootable USB drive. mkusb could not make persistence work because the overlay structure does not match what mkusb expects. 12.04 LTS has passed end of life, but I wanted to test anyway,

[*]mkusb works with **12.04.5 LTS** (with the trusty kernel). I used the 32-bit version, because I had that iso file already,

[*]**mkusb-backup-n-restore-home** can backup /home from the 'casper-rw' partition of Ubuntu 12.04.5 LTS (32-bit) and restore it to the 'casper-rw' partition of Ubuntu 18.04 LTS, (64-bit),

[*]Ubuntu 18.04 LTS works as it should with /home from 12.04.5 LTS.
[/LIST]
[*]**Edit 2**: Improved finish of the shellscript
[LIST]
[*]"Please wait for sync (flushing file system buffers to the device)"
[/LIST]
[*]**Edit 3**:
[LIST]
[*]Further improved finish of the shellscript
[*]Merged into mkusb-dus version 12.3.2 - as options in the 'starter' menu. See screenshot #5.
[/LIST]
[/LIST]
[hr][/hr]
The same links are upgraded with a new tarball and a corresponding md5sum file

[phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)

```
$ md5sum -c mkusb-backup-n-restore-home.tar.gz.md5
mkusb-backup-n-restore-home.tar.gz: OK

```

Please test that it works for *you* too. Feedback is welcome :-)

End of output to console during backup:
```

...
home/lubuntu/.config/user-dirs.locale
home/lubuntu/.bash_history
'/home' from 'casper-rw'  backed up  to the file
 /home/olle/mkusb-backup-home-lubuntu-16.04.tar.gz 
from the device
 name:  /dev/sdb 
 model: Extreme          
 size:  29,8G 
 OS:    Lubuntu 16.04.1 LTS amd64 
Please wait for sync (flushing file system buffers to the device)
 Done :-) 

```

End of output to console during restore:
```

home/lubuntu/.config/user-dirs.locale
home/lubuntu/.bash_history
'/home' in 'casper-rw'  restored  from the file
 /home/olle/mkusb-backup-home-lubuntu-16.04.tar.gz 
to the device
 name:  /dev/sdc 
 model: Extreme          
 size:  14,9G 
 OS:    Lubuntu 18.04 LTS amd64
Please wait for sync (flushing file system buffers to the device)
 Done :-) 


```

---

### Post by sudodus on 2018-05-24
> **C.S.Cameron said:**
> I like mBNR.
Everything works for me backing up and restoring the home directory embedded in casper-rw.
How do I use mBRN to backup the desktop's home directory and copy it to casper-rw on a USB?
And maybe vice-versa.

> **sudodus said:**
> Do you mean to transfer /home between an installed system and a persistent live system?

I have not addressed that task, but it should be possible, maybe even rather easy, to add it.

> **C.S.Cameron said:**
> It has worked the times I have tried it, once was from a Full install to a USB with persistent home-rw file.

I have thought about transfer between a full install to a USB with persistent home-rw file and vice-versa.

- If the user IDs are different, you must either create a user ID that matches the subdirectory in /home or rename that subdirectory.

- The user's numeric ID is 999 in [persistent] live systems, but 1000, 1001, ... for user IDs in installed systems. I think this should also be fixed for the ownership and permissions to work correctly. You can also add a matching user.

- There is a corresponding issue between flavours of Ubuntu. The live user ID in standard Ubuntu is ubuntu, but lubuntu in Lubuntu. (The live user's numeric ID is 999 in both cases, so in this case it is enough to rename the subdirectory in /home.)

But these things are beyond what I ***think*** should be included in this shellscript tool. I suggest that advanced users (like you) can do it manually.

Please tell me if you have a different opinion, and in that case what you suggest :-)

Finally, there is an issue about size. It should work well to use the /home directory from a persistent live system in an installed system, but after using an installed system for a while, the /home directory can be quite big, and may not fit in the casper-rw or home-rw partition of a persistent live system. Maybe you can **exclude** the personal files, when making the tarball.

---

### Post by C.S.Cameron on 2018-05-24
I recall that it only worked for me if user name and passwords were the same on desktop and on persistent flash drive.
I did not try to find a solution to user names being different.
I think it should be easy enough to make a backup of the desltop home folder manually and then use mBRN to extract home to the flash drive.

Well done!

---

### Post by sudodus on 2018-05-25
[SIZE=4]Using /home from an installed system in a persistent live system[/SIZE]

[SIZE=3]I tested with Ubuntu 18.04 LTS.[/SIZE]

1. In an installed system with a lot of data (iso files, other compressed image files and multimedia files) I checked the size with a dry run with rsync

```

sudo rsync -Havn --exclude={Downloads,Video} /home /target-directory

```

2. Then used the same exclude setting to create a tarball

```

sudo tar -cvz --exclude={Downloads,Video} -f /target-directory/backup-home-of-installed-system.tar.gz /home

```

An alternative is to exclude the file types, that are big and should not be backup to (and not transferred to the new system),

```
... --exclude=*.{iso,img*} ...
```

This way I could get a fair size of the tarball.

3. I created a persistent live system in a USB pendrive with mkusb.

4. I restored from the tarball to the persistent live system.

5. I booted into the persistent live system. It used the user ID 'ubuntu' (and not my name), and did not use the restored settings and files.

6. I moved /home/ubuntu to /home/ubuntu-orig

7. I moved /home/my-name to /home/ubuntu

8. I changed owner of this /home/ubuntu

```

sudo chown -R 999:root ubuntu

```

9. and rebooted.
[hr][/hr]
[size=3]Now the persistent live system can use the settings and files.[/size]

There is a glitch that I have not fixed. The system wants you to

**Enter password to unlock your login keyring**

and is not happy with the blank password (typical for a [persistent] live system), but it works to

**click on the 'Cancel' button**

in the log in dialogue window and arrive at the desktop. It works to enter the password of the original installed system too, but as a lazy user I will click on the Cancel button ;-)
[hr][/hr]
[SIZE=3]Edit 1:[/SIZE] The password from the installed system works, but the persistent live system can be logged in via the cancel button.

In the installed system, before creating the tarball, if you install the package **gnome-system-tools**, you get the program **users-admin**, that you can use to make the system skip the login window. This should be inherited to the persistent live system. I will check and confirm later ... and here is the result:

See this link: [How to Enable Automatic Login in Ubuntu](https://www.maketecheasier.com/enable-automatic-login-in-ubuntu/)

> For GNOME users, the process is pretty much the same, but it’s not worth the effort, as you are required to unlock your password keyring on startup rendering auto-login meaningless.

So this should work for Ubuntu community flavours, but it will not work with standard Ubuntu 18.04 LTS.

See also this link: [How to enable Automatic Login on Ubuntu 18.04 Bionic Beaver Linux](https://linuxconfig.org/how-to-enable-automatic-login-on-ubuntu-18-04-bionic-beaver-linux)

which seems more helpful, but does not really help, because the problem is that the window asks you to unlock the keyring, as the previous link informed about.

- Click near the top right corner of the desktop
- Click on the 'tools' button
- Select 'Details' (in English at the bottom of the list)
. Select 'Users'
 . if necessary: click on 'Unlock' at the top right corner of the window
 . Click on the "button" ON/OFF to set Automatic Login (might already be selected)

Close and reboot.
[hr][/hr]
[SIZE=3]Edit 2: I tested with Lubuntu 18.04 LTS.[/SIZE]

The method described works without any glitch with Lubuntu 18.04 LTS. There is no complaint about the login keyring after /home is transferred from an installed system to a persistent live system.

---

### Post by sudodus on 2018-06-02
[SIZE=4]Update and upgrade of persistent live systems[/SIZE]

The partition that stores persistent overlay data is easily damaged, particularly if you remove the pendrive before it is unmounted.

**Update and upgrade**

It is a good idea to use persistence to add functionality by installing packages and tweak the system to what you like.

**Common experience**

But it is **bad idea to update/upgrade a persistent live system continuously**. Then you will soon get a borked system according to the experience of several people.

**Test with update and full-upgrade**

I have tested (and am still testing) a persistent live Lubuntu 16.04.1 LTS system in a 60 GB SSD. Compared to a typical USB pendrive the SSD is fast, big and reliable. **It was possible to update and upgrade it to be up to date in June 2018, which is almost 2 years after the iso file was released, and the system works after several reboots and installation of new program packages.**

```
sudo apt update
sudo apt full-upgrade
```

'df -h' reports **1.9 GiB used** space in the 'casper-rw' partition, and there are no problems so far. Maybe this system will fail soon, maybe it will continue working for a long time. Anyway, particularly if you have a rather small USB pendrive, you don't want to waste drive space on system upgrades. So it is a good idea upgrade by switching to a system made from an iso file, that is up to date.

There are reasons to use a current kernel and its hardware drivers in the kernel series or skip to the next kernel series of 16.04.2 - 16.04.5 and 18.04 LTS. A persistent live system will only use the kernel from the iso file, so start from a current iso file for this purpose too.

**home directory survives**

If/when the persistence no longer works you may need to start all over again by removing what has been stored. Often you can **keep** the [overlay copy of the] **home** directory (and delete all other subdirectories of your overlay system in the casper-rw partition). Delete while running it live-only! This will save many settings, tweaks and personal files, but you must reinstall the program packages, that have been added.

[hr][/hr]
**Edit**: I should 'admit' that apt full-upgrade throws errors caused by cryptsetup (and affecting the installer ubiquity too), but these are not affecting the way I use the persistent live drive. For example,

- I can still install new program packages into the persistent live system,

- I tested today, and I can install (Lubuntu 16.04.1) from the persistent live system, so ubiquity is still working,

- It is always possible to select 'Try Lubuntu' or 'Install Lubuntu' when booting and run live-only, in order to install (with or without encrypted disk alias LVM with LUKS encryption).

```

$ sudo apt full-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up cryptsetup (2:1.6.6-5ubuntu2.1) ...
update-initramfs is disabled since running on read-only media
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service checkroot has to be enabled to start service cryptdisks-early
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cryptsetup (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubiquity:
 ubiquity depends on cryptsetup; however:
  Package cryptsetup is not configured yet.

dpkg: error processing package ubiquity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity-frontend-gtk:
 ubiquity-frontend-gtk depends on ubiquity (= 2.21.63.6); however:
  Package ubiquity is not configured yet.

dpkg: error processing package ubiquity-frontend-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 cryptsetup
 ubiquity
 ubiquity-frontend-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
lubuntu@lubuntu:~$ 


```

---

### Post by sudodus on 2018-07-22
[SIZE=4]Replace the 'usbdata' label and the NTFS file system partition of a mkusb persistent drive with a 'home-rw' label and the UDF file system.[/SIZE]

This is an alternative to **mk-persistent-live_with_home-rw** and **mkusb-backup-n-restore-home** which was created some months ago.

The new shellscript has a descriptive name, **udf2home-rw**.

Please download the attached gzip-compressed file, extract the file, and test it. Notice that it is an experimental shellscript. 

Edit: A third version is uploaded (replacing the earlier versions).

```

$ gzip -d udf2home-rw.gz
$ md5sum udf2home-rw
470ad275030ec462015bd35eb32616f5  udf2home-rw

```

End of edit.

1. Create a persistent live drive with mkusb.

2. Run ./udf2home-rw locally.

```

$ ./udf2home-rw
udf2home-rw
live system or temporary superuser permissions
mpcrw=/tmp/tmp.71OiVQxST8
Device      Model            Size     Persistent live OS
/dev/sdc    Extreme          29,8G    Xubuntu Core 18.04 - amd64
cntcrw=1
srcdev=/dev/sdc5
 Device: /dev/sdc  OS: Xubuntu Core 18.04 - amd64 
bupfile=
umount: /dev/sdc1: inte monterad.
umount: /dev/sdc3: inte monterad.
umount: /dev/sdc4: inte monterad.
umount: /dev/sdc5: inte monterad.
1+0 poster in
1+0 poster ut
1048576 byte (1,0 MB, 1,0 MiB) kopierade, 0,0387125 s, 27,1 MB/s
filename=/dev/sdc1
label=home-rw
uuid=5b548178af6da87e
blocksize=512
blocks=30314496
udfrev=2.01
start=0, blocks=64, type=ERASE 
start=64, blocks=13, type=VRS 
start=77, blocks=19, type=ERASE 
start=96, blocks=16, type=MVDS 
start=112, blocks=16, type=ERASE 
start=128, blocks=16, type=LVID 
start=144, blocks=112, type=ERASE 
start=256, blocks=1, type=ANCHOR 
start=257, blocks=30313982, type=PSPACE 
start=30314239, blocks=1, type=ANCHOR 
start=30314240, blocks=96, type=ERASE 
start=30314336, blocks=16, type=RVDS 
start=30314352, blocks=143, type=ERASE 
start=30314495, blocks=1, type=ANCHOR 
mkudffs: Warning: Creating new UDF filesystem on partition, and not on whole disk device
mkudffs: Warning: UDF filesystem on partition cannot be read on Apple systems
Please wait for sync (flushing file system buffers to the device)
Partprobe: 
Umount: 
umount: /dev/sdc3: ingen monteringspunkt angavs.
umount: /dev/sdc4: ingen monteringspunkt angavs.
umount: /dev/sdc5: ingen monteringspunkt angavs.

MODEL            NAME   FSTYPE  LABEL                      MOUNTPOINT  SIZE
Extreme          sdc                                                  29,8G
                 &#9500;&#9472;sdc1 udf     home-rw                               14,5G
                 &#9500;&#9472;sdc2                                                  1M
                 &#9500;&#9472;sdc3 vfat    usbboot                                244M
                 &#9500;&#9472;sdc4 iso9660 Xubuntu Core 18.04 - amd64             682M
                 &#9492;&#9472;sdc5 ext4    casper-rw                             14,5G
 Created UDF file system on home-rw partition '/dev/sdc1' :-) 

```

3. Boot a computer from the modified persistent live drive and test that things work.

4. Connect the modified persistent live drive to Windows, and check that Windows can 'see' it and use it (read/write).

[hr][/hr]
It works to boot and run a persistent live drive with the UDF file system in the casper-rw partition, but some important tasks do not work. For example, it is not possible to install programs with apt (and apt-get and other tools from the repositories), so it is not a useful alternative.

Instead I think this shellscript is a good alternative, but there is still a problem, that Windows wants to format the casper-rw partition.

---

### Post by sudodus on 2018-07-24
[QUOTE=C.S.Cameron]I have downloaded the script and purchased a new flash drive. will test in the morning.

The new drive is a Kingston DT50 16GB, not that fast ~100R ~35W, but boots USB3.

I've been a little horrified reading about TLC drive, kinda changes my perspective on preserving writes.[/QUOTE]

1. Hardware discussion

We have several threads going on here and at AskUbuntu discussing how to use USB pendrives to boot linux looking at wear as well as other issues.

I think you are right about the hardware (including the memory cells and the programmed electronic systems in the pendrives for input/output and wear leveling). 

*There can be big differences, and it is hard for end users to find out what is actually inside a particular pendrive, and how many write cycles it can be expected to last.*

By the way, the 'best' USB pendrives with high end memory cells and programmed electronic systems are more expensive than standard SSD SATA drives of the same size. (I would say more than the double price. You can buy an external box or adapter too for the same money.) But the 'best' USB pendrives are more convenient to use.

2. UDF

I'm looking forward to your test of the script to convert partition #1 to a home-rw partition with UDF.

- Does it work correctly for what you [want to] do with persistent a live drive?

- If it works, would it be worthwhile to provide a means for backup and restore (similar to what I made some weeks ago for /home in casper-rw)?

- Is it worthwhile, when the casper-rw partition needs an ext file system anyway, and Windows 10 is eager to format it?

3. USB pendrives versus persistent live systems

- How much are you into creating installed systems in USB pendrives instead of persistent live systems? Do you think we should focus on that, maybe a special feature of mkusb to prepare a USB pendrive for it, or a separate shellscript/program?

---

### Post by C.S.Cameron on 2018-07-24
The script runs well from another Persistent drive but not from a Full install drive.
Attached screen shots, a red warning and gparted.
How to find how much space left in home?
Script seems to move everything from home in the casper-rw partition to the home partition.
I'm still playing will let you know if I notice anything else.
I'm not sure I am too hot on UDF though. 
It is only a small pain for me when windows wants to reformat, except if I have a lot of partitions then it takes a while.

I really like the idea of having an flexible sdx4 that could be used for ISO9660 as is, or for a Full installed system, or maybe for multibootin ISO's. I'm wondering if there should be a basic page in mkusb and maybe a pro page or advanced page.
But I would hate to see mkusb messed up, it is pretty good as is. There are lots of uses for Persistent and Live installs.

I think mkusb would be the first USB tool to make Full installs, which is the future.

Edit:
There is a new unknown partition where usbdata used to be but stuff dumped on the desktop is still going to home in casper-rw, I think.

---

### Post by sudodus on 2018-07-25
> **C.S.Cameron said:**
> The script runs well from another Persistent drive but not from a Full install drive.
Attached screen shots, a red warning and gparted.

Have you tested the new version, which works for me also from an active persistent live drive?
> 
How to find how much space left in home?

```

df -h  # and look for the partition mounted at **/home**

```
> 
Script seems to move everything from home in the casper-rw partition to the home partition.

This is a surprise. I did nothing for that to happen. For me the new home partition will be empty until I reboot and start using it.
> 
I'm still playing will let you know if I notice anything else.
I'm not sure I am too hot on UDF though. 
It is only a small pain for me when windows wants to reformat, except if I have a lot of partitions then it takes a while.

I can see what you mean, particularly because the casper-rw partition needs a file system, that the current Windows 10 system wants to format.

- A small(?) advantage is that the data in a home partition with UDF will not be subject to such attacks from Windows 10, so it is more likely to survive.

- Another advantage is that partition #1 will be available for Ubuntu as /home and at the same time for Windows as external storage of files.

- A disadvantage is that there is no well known tool to repair the UDF file system.

So to summarize, unless I get positive feedback from other users, I will not push this issue further.
> 
I really like the idea of having an flexible sdx4 that could be used for ISO9660 as is, or for a Full installed system, or maybe for multibootin ISO's. I'm wondering if there should be a basic page in mkusb and maybe a pro page or advanced page.
But I would hate to see mkusb messed up, it is pretty good as is. There are lots of uses for Persistent and Live installs.
I think mkusb would be the first USB tool to make Full installs, which is the future.

OK, let us agree that both [persistent] live and full installs are useful, and we need methods and tools for both :-)
> 
Edit:
There is a new unknown partition where usbdata used to be but stuff dumped on the desktop is still going to home in casper-rw, I think.

Please describe this new unknown partition and how you see it! You can run the same commands as I show in the following code window and compare your result.

```

xubuntu@xubuntu:~$ [COLOR="#0000FF"]**df -h**[/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           383M  1.3M  382M   1% /run
/dev/sdb4       663M  663M     0 100% /cdrom
/dev/loop0      580M  580M     0 100% /rofs
/cow            6.9G  101M  6.5G   2% /
/dev/sdb1       7.1G  2.3M  7.1G   1% /home
tmpfs           1.9G     0  1.9G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G  8.0K  1.9G   1% /tmp
tmpfs           383M   12K  383M   1% /run/user/999
xubuntu@xubuntu:~$ [COLOR="#0000FF"]**sudo lsblk -fm**[/COLOR]
NAME   FSTYPE   LABEL                      UUID                                 MOUNTPOINT   SIZE OWNER GROUP MODE
loop0  squashfs                                                                 /rofs      579.8M root  disk  brw-rw----
sda                                                                                        111.8G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat                                1357-5B02                                         300M root  disk  brw-rw----
&#9492;&#9472;sda2 ext4                                2e1f47a4-0518-4429-ad23-65893d154ebe            111.5G root  disk  brw-rw----
sdb                                                                                         14.9G root  disk  brw-rw----
&#9500;&#9472;sdb1 udf      home-rw                    5b57ab9c1ab1c194                     /home          7G root  disk  brw-rw----
&#9500;&#9472;sdb2                                                                                         1M root  disk  brw-rw----
&#9500;&#9472;sdb3 vfat     usbboot                    A178-47CB                                         244M root  disk  brw-rw----
&#9500;&#9472;sdb4 iso9660  Xubuntu Core 18.04 - amd64 2018-04-26-21-58-14-00               /cdrom       682M root  disk  brw-rw----
&#9492;&#9472;sdb5 ext4     casper-rw                  c5b2ce97-a934-4de2-acc8-6a5fa0080a70                7G root  disk  brw-rw----
sr0                                                                                         1024M root  cdrom brw-rw----
xubuntu@xubuntu:~$ [COLOR="#0000FF"]**sudo parted -ls**[/COLOR]
Model: ATA KINGSTON SUV400S (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      2098kB  317MB  315MB  fat32              boot, esp
 2      317MB   120GB  120GB  ext4


Model: SanDisk Extreme (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 2      1049kB  2097kB  1049kB               primary  bios_grub
 3      2097kB  258MB   256MB   fat32        primary  boot, esp
 4      258MB   973MB   715MB                primary
 5      973MB   8493MB  7520MB  ext2         primary
 1      8493MB  16.0GB  7520MB               primary  msftdata


xubuntu@xubuntu:~$ 

```

When running the script from an active persistent live drive, stuff dumped on the desktop is still going to home in casper-rw. But at least for me (tested with Lubuntu 16.04.1, 18.04 and Xubuntu-Core 18.04) after rebooting twice, the new 'home-rw' partition with UDF will store the persistence for /home.

---

### Post by C.S.Cameron on 2018-07-25
Oops, had a senior moment trying to recall how to post screen shots in the Forums.
Showing Warning and GParted.

---

### Post by sudodus on 2018-07-25
@C.S.Cameron,

I intend to reproduce your error and warning output, and need details in order to do it.

The persistent live system is Ubuntu 18.04 LTS amd64. **What is the running operating system?** The controls are on the left side indicating Unity. Is it an Ubuntu 16.04 LTS system (live or installed)?

Edit:

What is **/dev/sdf** ? Is the 'Datatraveler 3.0'  the 'Kingston DT50 16GB' USB 3 pendrive?

I'm guessing here: Maybe there are other USB devices connected, that confuse the USB system. Can you disconnect [at least some of] them so that the 'Datatraveler 3.0'  can be seen as /dev/sdb or /dev/sdc? Then the script might work better.

---

### Post by C.S.Cameron on 2018-07-25
I was running 16.04.4. Persistent.
I tried 16.04 Full install but could not get the script to run.
I then booted the 18.04 disk and the script gave the same results as 16.04 drive.
(I'm working on an old P5, no internal disk, only USB is mouse, keyboard and bootdrive).
The 4GB DataTraveler is 16.04 (sde), the DT50 16GB is the 18.04 (sdf).
For some reason there is no sda - sdd, only sde and sdf.
I've tried clearing the target casper-rw partition before running, (so there would be no existing home), but this did not make an active home-rw partition.
I will freshen up these drives and test on another computer.

---

### Post by sudodus on 2018-07-25
It is not your fault. There was a bug in the script.

I could reproduce your result and found the bug: In 16.04.4 persistent, the universe repository must be activated, because that's where the package udftools resides. So it was simply not installed, and there was no way to create a UDF file system.

I have updated post [#158](https://ubuntuforums.org/showthread.php?t=2259682&p=13785835#post13785835) with a **new version of the shellscript**, that works for me in 16.04.4 persistent. I hope that you will have better luck with this new version :-)

```

ubuntu@ubuntu:~$ [COLOR="#0000FF"]./udf2home-rw [/COLOR]
udf2home-rw
live system or temporary superuser permissions
mpcrw=/tmp/tmp.aTHgQeQxv2
Device      Model            Size     Persistent live OS
/dev/sdb    Extreme          29.8G    Ubuntu 16.04.4 LTS amd64
/dev/sdc    Extreme          14.9G    Ubuntu 18.04 LTS amd64
cntcrw=2
srcdev=/dev/sdc5
 Device: /dev/sdc  OS: Ubuntu 18.04 LTS amd64 
bupfile=
umount: /dev/sdc1: not mounted
umount: /dev/sdc3: not mounted
umount: /dev/sdc4: not mounted
umount: /dev/sdc5: not mounted
'universe' distribution component enabled for all sources.
Ign:1 cdrom://Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228) xenial Release
Hit:4 http://archive.ubuntu.com/ubuntu xenial InRelease                    
Hit:5 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                                      
Hit:6 http://security.ubuntu.com/ubuntu xenial-security InRelease                                    
Get:7 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7,532 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [361 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en [4,354 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [135 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [107 kB]         
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [142 kB]            
Get:13 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata [3,410 kB]              
Get:14 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons [7,448 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [645 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [260 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [246 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [331 kB]
Fetched 25.0 MB in 3s (6,511 kB/s)                                 

** (appstreamcli:4193): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  dvd+rw-tools pmount
The following NEW packages will be installed:
  udftools
0 upgraded, 1 newly installed, 0 to remove and 284 not upgraded.
Need to get 62.1 kB of archives.
After this operation, 230 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial/universe amd64 udftools amd64 1.0.0b3-14.4 [62.1 kB]
Fetched 62.1 kB in 0s (243 kB/s)    
Selecting previously unselected package udftools.
(Reading database ... 195541 files and directories currently installed.)
Preparing to unpack .../udftools_1.0.0b3-14.4_amd64.deb ...
Unpacking udftools (1.0.0b3-14.4) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for systemd (229-4ubuntu21.1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up udftools (1.0.0b3-14.4) ...
Processing triggers for systemd (229-4ubuntu21.1) ...
Processing triggers for ureadahead (0.100.0-19) ...
1+0 records in
1+0 records out
1048576 bytes (1.0 MB, 1.0 MiB) copied, 0.0141386 s, 74.2 MB/s
start=0, blocks=64, type=RESERVED 
start=64, blocks=12, type=VRS 
start=76, blocks=180, type=USPACE 
start=256, blocks=1, type=ANCHOR 
start=257, blocks=16, type=PVDS 
start=273, blocks=1, type=LVID 
start=274, blocks=13491693, type=PSPACE 
start=13491967, blocks=1, type=ANCHOR 
start=13491968, blocks=239, type=USPACE 
start=13492207, blocks=16, type=RVDS 
start=13492223, blocks=1, type=ANCHOR 
Please wait for sync (flushing file system buffers to the device)
Partprobe: 
Umount: 
umount: /dev/sdc[1345]: mountpoint not found

MODEL            NAME   FSTYPE  LABEL                  MOUNTPOINT  SIZE
Extreme          sdc                                              14.9G
                 &#9500;&#9472;sdc2                                              1M
                 &#9500;&#9472;sdc5 ext4    casper-rw                          6.4G
                 &#9500;&#9472;sdc3 vfat    usbboot                            244M
                 &#9500;&#9472;[COLOR="#B22222"]**sdc1 udf     home-rw                            6.4G**[/COLOR]
                 &#9492;&#9472;sdc4 iso9660 Ubuntu 18.04 LTS amd64             1.8G
 Created UDF file system on home-rw partition '/dev/sdc1' :-) 
If modifying an active persistent live drive, you may need to reboot twice
ubuntu@ubuntu:~$

```

---

### Post by C.S.Cameron on 2018-07-25
OK, that is running with no warnings. making an unknown file system partition in GParted labeled home-rw.
Plugged the drive into a Win 10 machine and Windows still wanted to format three partitions but not home-rw.
Having Ubuntu home partition visible in Windows is kinda neat, and hopefully works for a Windows - Linux partition, but it is also kinda spooky.
I made a few changes to the next flash drive, background image, and dumped some big files on the desktop.
The script ran OK from the Full install flash drive.
None of the data in home moved to the new location.
The drive booted to Live session user and asked for password.
The second, third and fourth try froze.
I think home folder needs to be empty when running script.
The script should probably be run as part of the install process.
Maybe a toggle NTFS vs UDF home.

---

### Post by sudodus on 2018-07-26
@C.S.Cameron,

Thanks for your patience during these tests :-)

> **C.S.Cameron said:**
> OK, that is running with no warnings. making an unknown file system partition in GParted labeled home-rw.
Plugged the drive into a Win 10 machine and Windows still wanted to format three partitions but not home-rw.
Having Ubuntu home partition visible in Windows is kinda neat, and hopefully works for a Windows - Linux partition, but it is also kinda spooky.
I made a few changes to the next flash drive, background image, and dumped some big files on the desktop.
The script ran OK from the Full install flash drive.
None of the data in home moved to the new location.

OK, this is what I would expect.
> 
The drive booted to Live session user and asked for password.

This is what happens for me too, when modifying the currently running persistent live system.
> 
The second, third and fourth try froze.

This should not happen. But I made it happen, when booting with more than one mkusb-persistent-live pendrives connected when booting. I think the problem is confusion concerning which casper-rw (and home-rw if available) partition to use, and I think it it a general problem with mkusb-persistent-live systems (not specific to home-rw with UDF).

If this is the cause also in your case, you can work around it by booting with only one mkusb-persistent-live pendrive connected. After booting (when booting has finished and you are at the desktop), you can plug in the target pendrive and do the things to convert 'usbdata' to 'home-rw' with UDF.
> 
I think home folder needs to be empty when running script.
The script should probably be run as part of the install process.
Maybe a toggle NTFS vs UDF home.

In my tests, the home folder in the 'casper-rw' partition need *not* be empty. But it will not be transferred to the new UDF home.

[hr][/hr]
Edit 1: The drive booted to Live session user and asked for password.

This is what happens for me 

- when modifying the currently running persistent live system

- when there is content in the 'casper-rw' partition (I tested it right now).

The solution is a second reboot.

Edit 2: You wrote that the script should probably be run as part of the install process. Maybe a toggle NTFS vs UDF home.

You may have some other things 'on the wishlist' for this script too. If you think it can be useful, please let discuss it now :-)

For example: should the content in the 'casper-rw' partition be copied or moved to the new home-rw partition?

---

