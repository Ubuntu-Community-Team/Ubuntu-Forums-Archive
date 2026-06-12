---
title: "Successful Ubuntu 9.10 installation on a Mac Mini (Macmini2,1) system"
date: 2009-12-07
forum: Testimonials &amp; Experiences
---

### Post by elegie on 2009-12-07
When it comes to successfully installing the Ubuntu 9.10 release on Intel-based Mac systems, the following tale may be of interest. In this case, the target system for the install was a Mac Mini (model Macmini2,1) unit with an Intel Core 2 Duo processor setup. This Mac Mini had not been connected to the Internet.

Under the OSX 10.5 environment, the Boot Camp Assistant utility was used to partition the internal hard drive. From what one remembers, this produced a new FAT32 partition that was removed when partitioning the drive under the Linux environment. In the Ubuntu installer, the main Linux partition was at /dev/sda3 and the swap partition was at /dev/sda4. With the Advanced option on the last installer screen, it was probably specified that the bootloader be installed at /dev/sda3 and not (hd0).

Even though the Mac Mini system easily handled an Ubuntu 9.10 liveCD, the process of getting the hard drive installation to be usable took a number of reinstalls, repartitioning actions, and various other attempts to try and adjust aspects of the Linux software, along with the usage of information gained from looking on the Internet from a different system. By starting up the Mac Mini system and holding down the Option key, it is possible to access a graphical boot disk selector. (If an Open Firmware password has been set, it is necessary to enter the password in order to access the boot disk selector.) At least at first, however, the main Linux partition did not appear in the boot disk selector. Later on, though the Linux partition did appear in the boot disk selector (the partition being incorrectly labeled as "Windows", though this is probably due to the boot disk selector itself), one seems to remember that the partition did not boot successfully. Version 0.13 of the rEFIt utility did not indicate a need to synchronize partition tables. (In at least one case, the rEFIt utility said something about a partition of an "unknown" type and about not touching the disk.) In addition, one remembers the Linux install appearing as a "legacy" operating system in the rEFIt utility.

One thing that seemed to help was installing the grub package. This involved downloading the grub_0.97-29ubuntu59_i386.deb file (probably from the Ubuntu site) and saving it on a portable USB drive. Under the liveCD environment, the grub-pc package was removed before installing the grub package. From what one remembers, a command, perhaps sudo grub-install --root-directory=/mnt /dev/sda3, was used to put the bootloader onto the /dev/sda3 partition. (At some point, the /dev/sda3 partition was mounted at /mnt, so that the /boot directory, for instance, on /dev/sda3 could be accessed as /mnt/boot.) Among other things, the stage1 and stage2 files were added to the /mnt/boot/grub directory.

Eventually, it was possible to boot the hard drive Linux install to the command prompt for the Grub bootloader. It appears that the Grub bootloader can use a boot menu via the /boot/grub/menu.lst file. The process of generating the correct entries in this file was something like the following:


[LIST=1]
[*]Booting the Mac Mini system from the Ubuntu 9.10 liveCD.
[*]Mounting the /dev/sda3 partition at /mnt.
[*]Removing the grub-pc package and installing the grub package.
[*]Copying the vmlinuz-2.6.31-14-generic and initrd.img-2.6.31-14-generic files from /mnt/boot to the /boot directory, since the menu.lst generation command was run under the liveCD installation.
[*]Running a command, possibly sudo update-grub.
[*]Copying the menu.lst file from /boot/grub/ to /mnt/boot/grub.
[/LIST]
Towards the end of the menu.lst file, getting the correct entries produced something like the following, though this may have involved some editing.

title    Ubuntu 9.10, kernel 2.6.31-14-generic
root    (hd0,2)
kernel    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 ro quiet splash
initrd    /boot/initrd.img-2.6.31-14-generic

title    Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root    (hd0,2)
kernel    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 ro  single
initrd    /boot/initrd.img-2.6.31-14-generic

title    Ubuntu 9.10, memtest86+
root    (hd0,2)
kernel    /boot/memtest86+.bin

It may also have helped to have created an aufs directory under the /boot directory on /dev/sda3 as /mnt/boot/aufs. From what one remembers, the entries in the menu.lst file previously had the reference "root=/home/ubuntu/aufs".

At the current time, in the Startup Disk control panel under the OSX 10.5 environment, the main Linux partition does not appear. It is possible to choose the main Linux partition from the boot disk selector (accessed by holding down the Option key on startup, as previously mentioned.)

---

### Post by Zoot7 on 2009-12-07
Thanks for sharing and welcome to the community! :)

---

### Post by BFG on 2009-12-07
Hi and welcome!

I also have this situation and I've been meaning to try this for a while, so I gave it a go as you suggest.  I also have....

> **elegie said:**
> Mac Mini (model Macmini2,1) unit with an Intel Core 2 Duo processor setup. 


I used bootcamp to create a 30Gb windows partition.  Then rebooted with a 32bit live 9.10 CD and held the alt key (I have a windows keyboard on this mac).

It attempted something and then I had a black screen with...
**no bootable device -- insert boot disk and press any key**

I'll keep working on it!  Good article, thanks for sharing,

---

