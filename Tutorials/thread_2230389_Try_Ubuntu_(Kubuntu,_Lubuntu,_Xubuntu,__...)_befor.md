---
title: "Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it"
date: 2014-06-19
forum: Tutorials
---

### Post by sudodus on 2014-06-19
Post #1:  ***Backup*** & ***try*** before installing a new system (this post)
Post #2:  [***UEFI***]("http://ubuntuforums.org/showthread.php?t=2230389&p=13063865#post13063865")
Post #3:  [***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")
Post #6:  [Is the computer running in UEFI mode or in classical BIOS mode?](http://ubuntuforums.org/showthread.php?t=2230389&p=13370798#post13370798)
Post #7:  [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)
Post #12: [How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)
[HR][/HR]
[SIZE=4]Backup before installing a new system and create a regular habit to backup your personal data[/SIZE]

Editing partitions and installing operating systems are risky operations, and I recommend that you backup at least all your personal data (documents, pictures, ...) before you start. In general, it is a good idea to have a regular habit to backup the personal data. You never know, when something bad will happen to the computer, and you will need to restore the backed up data.

**[SIZE=4]Try Ubuntu (and the community Ubuntu flavours) before installing[/SIZE]**

It is a good idea to try [Ubuntu]("http://www.ubuntu.com/download/desktop") and some of the Ubuntu community flavours before installing into an internal drive. This can save a lot of trouble compared to installing directly.

This link contains links to all Ubuntu flavours: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

[SIZE=4]1. Run a live session booted from a CD/DVD/USB drive and select 'Try Ubuntu without installing'[/SIZE]

Download a desktop iso file, create a CD/DVD/USB boot drive and reboot the computer from that drive. Check that the download was successful with [md5sum]("https://help.ubuntu.com/community/UbuntuHashes").

[SIZE=4][SIZE=3]a. Basic install drive (live drive)[/SIZE][/SIZE]

See instructions at these links

the official Ubuntu instructions: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
more tips: [Checking the iso file and the boot drive - detailed tips](http://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608)

with instructions to burn a DVD on Ubuntu, Windows, MacOS
and instructions to create a bootable USB stick (pendrive) on Ubuntu, Windows, MacOS

CD disks can be used to install [Lubuntu 14.04.1 LTS]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") and Ubuntu [mini.iso]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") while the other iso files are too big for CD disks. (But [mini.iso]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") does not run a live session, it only installs.)

Find more details for booting from USB at [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[I][B]Basic install drives (live drives) are the standard tool to  try Ubuntu live, and if it works well, to install Ubuntu to an internal  drive.
[/B][/I]
[SIZE=3]b. Persistent live drive[/SIZE]

It is fairly easy to create a persistent live drive with a USB pendrive using ***Unetbootin***, ***mkusb***, ***grub-n-iso*** or some similar dedicated tool or method as described [here]("https://help.ubuntu.com/community/Installation/FromUSBStick"). There are detailed instructions at the following links to get persistence with CD/DVD and USB drives.

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)
[One pendrive for all PCs - 'grub-n-iso' with persistence described in post #6 and the following posts](http://ubuntuforums.org/showthread.php?t=2259682)

Persistent live drives are similar to basic live drives, and in addition can save settings, installed programs and data files, but are slower (with the  same hardware). The kernel cannot be upgraded (except by upgrading to a new iso file in a 'grub-n-iso' pendrive).

The persistent data are stored in a file with the name or a partition with the label **casper-rw** (and sometimes with an additional file or partition **home-rw**). Several tools create persistent live drives with the file system FAT32 and a file for persistence. This limits the size to 4 GiB. Other tools, for example [mkusb](https://help.ubuntu.com/community/mkusb), create a casper-rw **partition** for persistence, which is limited only by the available drive space.

[SIZE=4]2. Install (a complete installed system) to a USB stick or pendrive and boot from it.[/SIZE]

This way you can find which version and flavour that works best when installed without touching the internal drive. It is also the way to try, if you use an installer which does not offer a live session, for example from the Ubuntu [mini.iso]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") or an alternate iso file and Ubuntu Server. You find working mini.iso files for 12.04 LTS (32-bits pae (and non-pae in a subdirectory)) at [this link]("http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-i386/current/images/netboot/").

It is a two step procedure: Make a CD/DVD/USB boot drive, boot from it   and install into a[nother] USB pendrive. Make sure that you install the   bootloader into the head of the target pendrive (not into the internal   drive or the source pendrive and not into a partition). Install almost like you would do (into an internal drive), but into the pendrive. In BIOS mode it is easier, if you remove the internal drive, or you must use ***Something else*** at the partitioning window and ***point the bootloader into the pendrive***. Otherwise it will be installed into the internal drive /dev/sda. In UEFI mode the system will install the bootloader into the internal drive unless you disconnect or unplug it. So ***it is a good idea to unplug the internal drive, if it is possible***.

This will ***test a complete installed system***  (but in a USB pendrive). Boot  from this installed system and check what  works directly, and what needs  tweaking ([boot options]("https://help.ubuntu.com/community/BootOptions"), or drivers for graphics, wifi etc).

It is also a method to create a ***portable Ubuntu system*** in a USB drive. The normal installation method described above works also to create an  installed system in a pendrive. It is a bit more complicated to make an installed  system, that works in UEFI as well in BIOS mode. See this link,

[Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS model](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13468260#post13468260)

USB pendrives have a rather bad reputation concerning lifetime, but there is evidence that they have improved, and can last quite long nowadays, at least when managed in a good way. If you intend to use an installed system in a USB pendrive, you should add the mount option **noatime** to the line controlling the root partition '/' in the file **/etc/fstab**. You can also consider running the ext4 file system without journaling (but there is a tradeoff - journaling makes the file system much more reliable).

```
sudo tune2fs -O ^has_journal /dev/sdxy
``` where x is the drive letter and y is the partition number of the root partition.

You can also ***avoid swapping***. If you remove the swap partition, you should also remove or 'comment' (put a # character in the beginning of) the 'swap' line in /etc/fstab.

[hr][/hr]
See also these links describing  different methods to create installed systems in USB sticks or pendrives

for new or middle-aged computers:

- [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
- [Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

for old or middle-aged computers:

- [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

and finally these links for old computers:

- [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")
- [General tips, that may help]("http://ubuntuforums.org/showthread.php?t=2130640&p=13311591#post13311591")

---

### Post by sudodus on 2014-07-02
[SIZE=4]This post is about UEFI[/SIZE]

***[COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]***

[LIST]
[*=left]if the other systems (Windows  Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode,  then you must install Ubuntu in EFI mode too. 
[*=left][FONT=inherit]if the  other systems (Windows, GNU/Linux...) of your computer are installed in  Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too.  Eg if your computer is old (<2010), is 32bits, or was sold with a  pre-installed Windows XP.[/FONT] 
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not. 
[/LIST]

***[COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[/FONT][/COLOR]***

[LIST]
[*=left][FONT=inherit]Use a DVD or USB drive made from a ***64bit desktop iso file*** of Ubuntu ([Ubuntu 32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"). Ubuntu mini.iso does not work.)[/FONT] 
[*=left][FONT=inherit]Use a  supported version of Ubuntu, 14.04 LTS, 16.04 LTS, 17.10.1, 18.04 LTS ...[/FONT] 
[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[/FONT] 
[*=left]Then:
[LIST]
[*=left]nothing  special is required if you use the automatic installer of Ubuntu  ("Install Ubuntu alongside others" or "Erase the disk and install  Ubuntu"). Important: ***if you have a pre-installed Windows and you want to  keep it, make a Backup***, and choose "***Something else***" at the partitioning page. The other options are likely to overwrite Windows. 
[*=left][FONT=inherit]if you  use the manual partitioning ("Something else"), the difference is that  you will have to set the /boot/efi mount point to the EFI partition. And  if there was not any EFI partition on your HDD, you first will have to  create it (see the "[Creating an EFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition")" paragraph below).[/FONT] 
[/LIST]
         
[/LIST]

***Notice this:***

[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT] 
[/LIST]
[I][B]
See these links for more details:[/B][/I]
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]
UEFI Installing - Tips[/URL]
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/In.../UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

With Ubuntu we can get the benefits of both UEFI and Secure Boot. I can  offer no assurances that the following link is useful or accurate.

[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by sudodus on 2015-01-20
[SIZE=4]mini.iso, minimal install, netboot iso[/SIZE]

Learn how to use ***Ubuntu mini.iso***. If you add  no extras at all, you will get a very minimal system (which boots into a  text screen). From that system you can install lubuntu-desktop to get Lubuntu, xubuntu-desktop to get Xubuntu etc. You can install several server alternatives or you can build your own system 'almost' from scratch,  well at least your desktop environment and set of application programs. ***bash*** will be there from right after rebooting into the very minimal system.

[HR][/HR]***Edit***: This general link works in order to find and download the Ubuntu mini.iso files [http://cdimages.ubuntu.com/netboot/](http://cdimages.ubuntu.com/netboot/)
[HR][/HR]
You can find the corresponding md5sums in each version's parent directory.

-o-

The following link may help you get started with the Ubuntu mini (it is   about Lubuntu, but can be applied more generally to other flavours of   Ubuntu)

[http://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](http://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

-o-

Unfortunately the mini.iso does not work in UEFI mode. If you must run in UEFI mode, you should start the installation from a 64-bit desktop iso file or from a 64-bit Ubuntu Server iso file, for example

**ubuntu-16.04.1-desktop-amd64.iso**
**ubuntu-16.04.3-server-amd64.iso**

---

### Post by David_Slack on 2015-05-15
Thank you!

---

### Post by sudodus on 2015-05-15
You are welcome David,

When you have tested Ubuntu and feel that your problem is solved, please browse to your thread [Reassurance needed]("http://ubuntuforums.org/showthread.php?t=2278308"), click on **Thread Tools** at the top of the page and mark that thread as SOLVED :-)

---

### Post by sudodus on 2015-10-10
[SIZE=4]Is the computer running in UEFI mode or in classical BIOS mode?[/SIZE]

You may want to test if your Ubuntu flavour is running in [U]EFI mode. An installed system and a live system too is using the directory **/sys/firmware/efi**, so you can [cut and paste and] run the following command line (when linux is running)

```
test -d /sys/firmware/efi && echo "booted via EFI (UEFI)" || echo "booted via BIOS (legacy boot)"
```
or simplified if you can't cut and paste
```
test -d /sys/firmware/efi && echo efi || echo bios
```

If you boot via syslinux, I think you are running in BIOS mode.

At the grub menu you can run the following command:

```
echo $grub_platform
```

It will print 'pc' in BIOS mode and 'efi' in UEFI mode.

[Colin Watson@askubuntu](https://askubuntu.com/questions/399732/how-to-check-if-grub-is-in-efi-or-bios-mode):
> As of GRUB 2.00, assuming GRUB is working well enough to get into normal mode rather than rescue mode, "echo $grub_platform" from the GRUB shell will show "pc" in BIOS mode and "efi" in UEFI mode.

The BIOS build corresponds to the grub-pc package, and the UEFI build corresponds to the grub-efi-amd64 (or, less commonly, grub-efi-ia32) package.

---

### Post by sudodus on 2015-10-10
[SIZE=4]Boot options[/SIZE]

When there are problems to boot and run Ubuntu or an Ubuntu flavour, you can add some *boot options* according to the following tips.

**nomodeset** is good if there are problems with ***nvidia*** or ***AMD/ATI/Radeon*** graphics. It can help you get a simple user interface, so that you can install a proprietary graphics driver and after reboot get good graphics.

See this link to [a post by *oldfred* for details about boot options for Intel graphics](http://ubuntuforums.org/showthread.php?t=2305646&p=13403459#post13403459).

**forcepae** is good for old Pentium M and Celeron M processor, that lack the PAE flag, but have PAE capability.

**acpi=off** might be good if there are problems with the [power management](https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface).

You can add several boot options at the same time. See these links:

1. For syslinux boot (in BIOS mode)
[BootOptions](https://help.ubuntu.com/community/BootOptions)

2. For grub boot (in UEFI mode and BIOS mode)
[Editing the GRUB 2 Menu During Boot](https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot)
[Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

See the section about **GRUB_CMDLINE_LINUX**

3. See also this link with detailed illustrated descriptions how to add a boot option in syslinux and grub:
[Enter the boot option persistent](https://help.ubuntu.com/community/mkusb/sp/screendumps#Enter_the_boot_option_persistent)

[hr][/hr]
The following link contains a long list of boot options, so there are many more options, than those suggested in the syslinux menu.

[An exhaustive list of kernel boot parameters from kernel.org](http://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt)

---

### Post by Eanruig on 2015-11-09
Part of the instructions on installing Ubuntu to a USB drive says, "Make sure that you install the    bootloader into the head of the target pendrive (not into the  internal   drive or the source pendrive and not into a partition)."

I don't understand what is meant by

(1) install into the head of the target pendrive

(2) not into a partition

If I look at my potential target USB drive with gparted, I see a 3.76 GiB ext4 partition that fills the largest part of the drive, plus a small, dull yellow area at the left end, probably the 132.13 MiB under "Used". 

I am firmly of the opinion that the only stupid question is the one you don't ask, so I ask:

A: Does the "Used" area contain the firmware for the drive, and is that where viruses or other bad actors are sometimes hidden?

B: Does the installation, with the bootloader pointing to the pendrive, install the bootloader **to the head** of the target pendrive?

C: Do I need to delete the partition before installing to the pendrive? (Is such an installation even possible?)

Thank you for any clarification.

Henry IX

---

### Post by sudodus on 2015-11-09
> **Eanruig said:**
> Part of the instructions on installing Ubuntu to a USB drive says, "Make sure that you install the    bootloader into the head of the target pendrive (not into the  internal   drive or the source pendrive and not into a partition)."

I don't understand what is meant by

(1) install into the head of the target pendrive

The head is the beginning (if looked at linearly with a beginning and an end. You see it graphically in ***gparted***: The head is the left edge, and it is described by the block files /dev/sda, /dev/sdb ... /dev/sdx for drive a, b, ...x.
> 
(2) not into a partition

Partitions are parts of a drive, and can contain file systems or other partitions or swap. You see them graphically in ***gparted***: Segments of the drive, and they are described by the block files /dev/sda1, /dev/sda2 ..., /dev/sdb1, /dev/sdb2 ..., ... for the first, second, ... partitions of drives a, b, ...

In very special cases you want to install the bootloader to a partition, but this is not covered in this tutorial thread.
> 
If I look at my potential target USB drive with gparted, I see a 3.76 GiB ext4 partition that fills the largest part of the drive, plus a small, dull yellow area at the left end, probably the 132.13 MiB under "Used". 

I am firmly of the opinion that the only stupid question is the one you don't ask, so I ask:

A: Does the "Used" area contain the firmware for the drive, and is that where viruses or other bad actors are sometimes hidden?

The used area is what is used by the file system's own administration plus storage of files and directories.
> 
B: Does the installation, with the bootloader pointing to the pendrive, install the bootloader **to the head** of the target pendrive?

The automatic alternatives usually install the bootloader to the head of the first drive, /dev/sda. This is often, but not always, what you want. Use **Something else** at the partitioning window, if you want better control where to install the file system, swap and the bootloader
> 
C: Do I need to delete the partition before installing to the pendrive? (Is such an installation even possible?)

You need not delete the partition. But you can do it. You can overwrite the existing partition table and install to the whole drive. You can also install into existing partitions. In that case you should normally format the partition (not delete it). But if you want to keep your home partition, you must leave it as it is. Formatting would destroy what you want to keep.

Sometimes there is data on a drive, that will confuse the installer or gparted. In such cases it might help to wipe the first megabyte (overwrite with zeros), and after that create a new partition table (and maybe also partitions).
> 

Thank you for any clarification.

Henry IX

---

### Post by Eanruig on 2015-11-11
I installed Lubuntu 14.04.2 (persistent) to a USB flash  drive, and it boots perfectly but slowly. I suppose that is because a USB drive is slower than a hard drive. 

I also had no wireless  connectivity, but found the thread 

[http://askubuntu.com/questions/35497/how-to-fix-very-slow-ubuntu-booting](http://askubuntu.com/questions/35497/how-to-fix-very-slow-ubuntu-booting) 

and following the information there found the cure for the wireless problem - the Broadcom card needed a firmware update.

Thank you again.

---

### Post by sudodus on 2015-11-11
You are welcome, Eanruig,

Thanks for sharing your solution :-)

It might be worthwhile to get a fast USB 3 pendrive. See this link: [Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

### Post by sudodus on 2016-09-06
[SIZE=4]How to select the version and flavour of Ubuntu[/SIZE]

***0. Search the internet and ask at the Ubuntu Forums, when you intend to buy new hardware***

It is a good idea is to start by searching the internet, and after that ask at the Ubuntu forums, for example in the [hardware forum](https://ubuntuforums.org/forumdisplay.php?f=332), when you intend to *buy a new computer or add some hardware* (internal and external), and we will try to give you good advice, so that you get a computer, that works well with linux in general and the Ubuntu flavours in particular.

***1. If the computer is new, or you have a new hardware***

There is a continuous development of the linux kernel and drivers in order to co-operate with new hardware. This means that the newest version [of Ubuntu and the Ubuntu flavours] is most likely to work well.

[LIST]
[*]Start with the newest version with long time support: 16.04.x LTS [, 18.04.x LTS ...]
[*]Next try the newest version, which might be a short-life (9 months) version: 17.10.1, 18.10 ...
[*]If still no luck, try the developing release. You can get a milestone iso file (alpha or beta) or a *daily* iso file via [this link (browse into it ...)](http://iso.qa.ubuntu.com/). Notice that this version might work well with the hardware, but other things might break a few times after upgrades until the version is released. The software is developing rapidly, and some programs might fail to co-operate with some other program.
[*] Avoid versions that have passed end of life, because they will receive no updates, not even security updates.[/LIST]

***2. If the computer is middle-aged***

[LIST]
[*]Start with the newest version with long time support: 16.04.x LTS, 18.04.x LTS ...
[*]Next try the previous version with long time support: 14.04.x LTS
[*]Next try a short-life (9 months) version, when available: 17.10.1, 18.10 ...
[*]Avoid versions that have passed end of life, because they will receive no updates, not even security updates.[/LIST]

***3. If the computer or some hardware is old***

[LIST]
[*]Start with the oldest version with long time support: 14.04.x LTS , 16.04.x LTS ...
[*]Next try the newer versions with long time support: 16.04.x LTS, 18.04.x LTS ...
[*]Next try a short-life (9 months) version, when available: 17.10.1, 18.10 ...
[*]Select a flavour of Ubuntu with an ultra light or medium light desktop environment, lighter than standard Ubuntu
[LIST]
[*]Lubuntu - ultra light
[*]Ubuntu Budgie - medium light
[*]Ubuntu MATE - medium light
[*]Xubuntu - medium light[/LIST]
[*]Avoid versions that have passed end of life, because they will receive no updates, not even security updates.[/LIST]

***4. If you want to improve video playing or make the computer more responsive***

Select a flavour of Ubuntu with an ultra light or medium light desktop environment, lighter than standard Ubuntu
[LIST]
[*]Lubuntu - ultra light
[*]Ubuntu Budgie - medium light
[*]Ubuntu MATE - medium light
[*]Xubuntu - medium light[/LIST]

***[COLOR="#0000CD"]5. In general, try the different flavours live, and install the flavour, that you like best :-)[/COLOR]***

***6. Lifetime of the Ubuntu versions***

Notice that the standard Ubuntu LTS versions are supported for 5 years, while the LTS versions of the other flavours are supported for 3 years.

See this link, [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

[TABLE="class: cms_table"][tr]
[td="bgcolor: #CCFF99"]
It is somewhat tricky to find **Ubuntu Desktop 16.04.1 LTS** (the version with the longest support time).

The following link works (2017-03-04), [http://old-releases.ubuntu.com/releases/xenial/](http://old-releases.ubuntu.com/releases/xenial/)
[hr][/hr]
There is also a link for **Lubuntu** 16.04, **16.04.1** and 16.04.2: [cdimage.ubuntu.com/lubuntu/releases/16.04.1/release](http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/)
[/td][/tr][/table]

[hr][/hr]
See also these links describing different methods to create installed systems in USB sticks or pendrives

[LIST]
[*]for all computers [https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/) and [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and links from them
[*]for new or middle-aged computers [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[*]for old computers [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640") and [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)[/LIST]

---

