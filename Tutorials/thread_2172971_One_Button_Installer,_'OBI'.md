---
title: "One Button Installer, 'OBI'"
date: 2013-09-07
forum: Tutorials
---

### Post by sudodus on 2013-09-07
[SIZE=5]**One Button Installer, 'OBI'**[/SIZE]

The One Button Installer is described at the following wiki page.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

The plans are to develop that page into the main tutorial and to move it  to some other location within the Ubuntu wiki. This tutorial thread  will stay at its present location. I intend to keep it up to date with  references to the wiki page and other links. I also intend to describe  new features and systems to install.

The One Button Installer itself can be installed from a compressed image  file with terminal window commands or with the shell-script **[FONT=courier new]mkusb[/FONT]**, described at the tutorial [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073"). 

A special version for very old computers (without PAE capability or which cannot boot from USB) is shown at this wiki page

[OBI-9w installer]("https://help.ubuntu.com/community/9w#Ubuntu_14.04_LTS_text_non-pae_.27Trusty-npae124-text.iso.27_and_.27obi_Trusty-npae124-text-9w.iso.27")

[SIZE=4]**Typical cases for the One Button Installer**[/SIZE]

**Tool that is easy to use and just works**

 The normal linux installers that come with iso files are complicated to use or freeze during the installation process, and you want a tool that is easier to use and just works. 
 
**Replace Windows XP**

 Replace Windows XP because you want the computer to work faster or smoother with an Ubuntu based linux operating system, or at the end of life in April 2014, when there will be no more security updates for Windows XP. 
 
**Backup**

 You want a simple method to backup (and restore) your whole installed linux system. The One Button Installer combines installation, backup and restore in one set of tools. 
 
**Your own portable Ubuntu based linux system**

 You want to make your own linux system portable and port it to a USB pendrive or to be installed in another computer to be used by yourself, or to be uploaded to the internet for sharing with other people. The One Button Installer can do it in a simpler way than to remaster the code and make an own iso file. 
 
[SIZE=4]**General description**[/SIZE]

 Please view or download [this General description file]("https://help.ubuntu.com/community/OBI?action=AttachFile&do=view&target=DescriptionoftheOneButtonInstaller-2.pdf").
 
[SIZE=4]**How to install and run the OBI**[/SIZE]

**OBI quick start manual**

Please view or download [this OBI quick start manual file]("https://help.ubuntu.com/community/OBI?action=AttachFile&do=view&target=OBI-quick-start-manual-6.pdf") with a *short description* how to make a boot drive with the OBI and how to use  the OBI to install an Ubuntu based linux operating system.

**README**

 If you want to read more, please view or download [this README file]("https://help.ubuntu.com/community/OBI?action=AttachFile&do=view&target=README-3.pdf"), * which describes with more details* how to make a boot drive with the OBI and how to use  the OBI to install an Ubuntu based linux operating system to your  computer, to make a portable system or to make a tarball from an  existing system for backup or sharing. 
 
**Download the following files**

 Select one of the compressed image files

```

dd_blank-obi_4GB_23_text.img.xz                    # if you need a really small system    (324MiB)
dd_blank-obi_7.8GB_25_LubuntuTrusty_nonpae.img.xz  # if you need a non-pae kernel         (677MiB)
dd_precise-obi_4GB_29_text.img.xz                  # to install tarballs made for precise (183MiB)
[COLOR=#0000cd]dd_blank-obi_7.8GB_33_LubuntuTrusty.img.xz[/COLOR]         # current main choice for most cases   (695MiB)

```

and at least one of the tarballs (check for new tarballs at the websites for downloading).

***User: *****guru*****, Password: *****changeme** if nothing else is stated,
except for the One Button Installer itself, that comes with ***User: *****myself*****, Password: *****123456**

```

Bento12.04.04-oem0.tar.xz              # in OEM mode, password: 123456
Bento12.04.04-oem1.tar.xz              # OEM: ready for the end user
Bento12.04.04.tar.xz                   # user: guru, password: changeme
bodhi-230-nonpae.tar.xz
GnomeClassic1204-oem.tar.xz            # in OEM mode, password: changeme
GnomeClassic1204.tar.xz
Kubuntu_13.10oem-nov23.tar.xz          # OEM: ready for the end user
KubuntuPrecise.tar.xz
Lubuntu_14.04oem-npae5.tar.xz          # in OEM mode, password: 123456
Lubuntu_14.04oem-npae.tar.xz           # in OEM mode, password: 123456 (old)
Lubuntu_14.04_eu-npae.tar.xz           # OEM: ready for the end user
Lubuntu_16.04_oem-uxa.tar.xz           # in OEM mode, password: 123456, (up to date 2016-05-08)
[COLOR="#0000FF"]Lubuntu_16.04_oem-intel.tar.xz         # in OEM mode, password: 123456, (up to date 2016-05-08)[/COLOR]
[COLOR="#0000FF"]Lubuntu_16.04_oem-intl_amd64.tar.xz    # in OEM mode, password: 123456, (up to date 2016-05-14)[/COLOR]
lxle-2013-08-19.tar.xz               # tweaked, old but possible to update/upgrade
lxle32-12.04.4-oem0.tar.xz           # in OEM mode, password: 123456
lxle32-12.04.4-oem1.tar.xz           # OEM: ready for the end user
OBI_noswap_07.tar.gz
OBI_noswap_23_text.tar.xz
OBI_noswap_27_LubuntuTrusty.tar.xz
precise-mini-txt.tar.xz             # Ubuntu text system with portable wired network (from mini.iso)
ToriOS-pae-OEM_[COLOR="#0000FF"]prec[/COLOR]_use-by-OBI-in-trusty-2016-may.tar.xz  # in OEM mode, password: 123456
ToriOS-pae-OEM_[COLOR="#0000FF"]trus[/COLOR]_use-by-OBI-in-trusty-2016-may.tar.xz  # in OEM mode, password: 123456
ToriOS-mini_trusty_use-by-OBI-in-trusty-2016-may.tar.xz   # user: guru, password: changeme
Trusty-mini-txt6.tar.xz                # user: guru, password: changeme
[COLOR=#0000cd]Trusty-mini-txt7.tar.xz                # user: guru, password: changeme, (up to date 2016-05-06)
Trusty-nonpae-txt5.tar.xz              # user: guru, password: changeme[/COLOR]
Xenial-32-txt.tar.xz                   # user: guru, password: changeme
Xenial-32-txt_2016-06-28_intel.tar.xz  # user: guru, password: changeme
[COLOR="#0000FF"]X32-Txt-Startx-Intl_2016-06-29.tar.xz  # user: guru, password: changeme[/COLOR]
xubuntu-precise.tar.xz                 # good for old systems but past end of life of desktop packages
XubuntuTrusty-oem-feb13.tar.xz         # OEM: ready for the end user
[COLOR="#4B0082"]# good for old systems but past end of life, so there are no updates, not even security updates
lubuntu-10.04.tar.gz                   # past end of life
ubuntu-10.04.tar.gz                    # past end of life[/COLOR]

```

plus a script file and a signed list of the md5sums

```
mkusb
md5sums.txt.asc
```

from [http://phillw.net/isos/linux-tools/one-button-installer](http://phillw.net/isos/linux-tools/one-button-installer)
[B]
Download a virtual disk for testing the OBI in Virtual Box[/B]

 Virtual  Box can connect to peripheral devices and mass storage devices via USB,  but not boot. Instead, the OBI can be installed to a [virtual] hard  disk drive. The virtual machine will boot from the first virtual disk,  so you must put it on top in the 'storage managing window'. Later, when  you want to boot from the installed system, you must switch the order of  the virtual disks. There are two compressed virtual disks with the OBI in 
 
[http://phillw.net/isos/linux-tools/one-button-installer/vboxdisks/](http://phillw.net/isos/linux-tools/one-button-installer/vboxdisks/) 

Expand the new one (with OBI version 3.3) and connect it to a virtual machine, and you can test the OBI in Virtual Box without the extra problems to get the OBI into the virtual  machine and installing it.

**KVM can boot from a USB drive and even an image file**

If a 64-bit host operating system in a machine with hardware virtualization is available, install a KVM virtual machine. Otherwise Virtualbox might be more efficient.

Install a virtual machine using KVM, qemu, and virt-manager according to this wiki page 
[URL="https://help.ubuntu.com/community/KVM/VirtManager"]
https://help.ubuntu.com/community/KVM/VirtManager[/URL] 

It is fast and very similar to installing and running in a real system.

You need no special virtual disk file for KVM. You can mount the OBI image file (after expansion from img.gz to img) and it can be used as a virtual SATA disk. If it is the first disk, the virtual machine will boot from it.

And the standard tarballs can be imported via sftp, wget or lynx to this virtual SATA disk and used in order to install systems to a second virtual disk. 

[SIZE=4]**Follow the instructions in the README file step by step**[/SIZE]

 Just a reminder of [the README file]("https://help.ubuntu.com/community/OBI?action=AttachFile&do=view&target=README.pdf")...
 [B][SIZE=4]
Make you own tarball[/SIZE][/B]

[This is a link to a detailed description how to make your own tarball]("https://help.ubuntu.com/community/OBI/MakeOBItarball")

**[SIZE=4]Improvements[/SIZE]**

OBI versions 0.7, 1.0, ... :

[SIZE=4]1.0:[/SIZE]

1. The dialogue has been improved by using screens made with the linux program ***dialog***. It means a menu style similar to that of the alternate installer and the mini.iso. See the attached pictures.

2. The ***compression*** of the dd-image files and the tarballs is improved. The original compression was using ***gzip***. It is still available, but now ***xz*** compression is also available, and ***xz compression is more than 20% more efficient***,  often 30% (meaning that the size of the compressed file is 20-30%  smaller than a gzipped file). xz is slower and needs more memory, but  not too much. During a test with low RAM, 128 MB, extracting the tarball  with xz used 62 MB while extracting with gzip used 49 GB. Downloading  is usually the bottleneck, so small files are preferred.

[SIZE=4]1.1:[/SIZE]

1.** Own directory for tarballs** (plus symlink)

Put and find the tarballs in

```
/tarballs
~/tarballs -> /tarballs
```

2. **Download tarball**

There is a new download system with a dialog menu, that you run from the main menu with

[COLOR=#ff0000]d[/COLOR] Download tarball

3. **Make tarball**

From version 1.1 ***xz*** is the default compression in ***mktbl***. You can also enter a tarball name as parameter #3 when you run ***mktbl*** from the bash shell.
[SIZE=4][SIZE=4]
1.2:
[/SIZE][/SIZE][B]
Basic and advanced OBI level

[/B] Most users are recommended to use the **basic** OBI level. This means that the OBI will **install a system from a tarball into a whole device**, typically an internal hard disk drive or a USB 3 pendrive. It is easy and takes only a few minutes to install a system at the basic OBI level. 

The advanced level opens the door to dual boot (mainly for internal disks) and a first FAT32 partition for access from Windows (for USB pendrives). In the advanced level the OBI will let you **select the partitions**. It means that you can install a system from a tarball into two partitions, one root file system partition and one swap partition. This way it is possible to create a **dual boot** device with an existing (already installed) operating system. It is also possible to create a separate **data partition** with an NTFS or FAT32 file system, that can be used by linux as well as Windows. 

The intention with the advanced level is to edit and create partitions with **Gparted** (booted from a 'regular' boot CD/DVD/USB device). One partition is labelled 'obi-root' and one (smaller) partition is labelled 'obi-swap'. Such partitions can be identified and selected automatically in the advanced level, but manual selection is also possible. 

Editing partitions is risky (so you need a good backup) and it takes long time (hours) to shrink an existing partition with a lot of data (Windows), so that there will be space for new partitions.

[SIZE=4]2.2:[/SIZE]

In order to make it more convenient to use the advanced OBI level (introduced in version 1.2), there is now version 2.2.

The underlying operating system is upgraded to **Ubuntu version 13.10** and **Lubuntu-desktop is installed and tweaked to create a graphical desktop environment** with desktop icons for the main tasks during installation with the One Button Installer.

A USB 3 pendrive with at least 8 GB is recommended for the graphical  desktop environment. But there is also a flavour of version 2.2 with a  text desktop environment, which is suitable for very old computers. A 4  GB pendrive is big enough for the text version.

You can find some USB pendrives that are good booters in this link [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

[SIZE=4]2.3:[/SIZE]

This version is mainly a bug-fix update from 2.2 including updated pdf  documents. The operating system (13.10) is also updated/upgraded.

New feature: the OBI will share an existing swap partition, when selected at the advanced OBI level.

Use this link [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[SIZE=4]2.4:[/SIZE]

There is a new and special version of the 9w installer, the [OBI-9w installer]("https://help.ubuntu.com/community/9w#Ubuntu_14.04_LTS_text_non-pae_.27Trusty-npae124-text.iso.27_and_.27obi_Trusty-npae124-text-9w.iso.27")

This version is made for very old computers without PAE capability.  The One Button Installer in run from the 9w installer's debian system.  Now there is a super light-weight installer, that can

- install from CD, DVD and USB
- create not only single boot but also dual boot systems.

Prepare partitions with Gparted and run the One Button Installer at the advanced level to create dual boot or multi boot system.

There are special tarballs for the 9w installer, and these tarballs come with the iso file.

[SIZE=4]2.5:[/SIZE]

This version is mainly a bug-fix update  from 2.3 (and  2.4 OBI-9w) including updated pdf documents. The operating system  (14.04 LTS)  is also updated/upgraded.

New  feature: the starter menu will set the default item (command line)  in a  logical way prompting to download and select tarball, select OBI  level  and then install a system. Two-digit partition numbers  (/dev/sda10 ...)  are recognized at the advanced OBI level. 

USB 3 pendrives with at least 8 GB are recommended for this version with   Lubuntu desktop. 4 GB pendrives are still possible for the text  version.  See also this link

[SIZE=4]2.6:[/SIZE]

This version is a major improvement, implemented for ToriOS but not published here.

[LIST]
[*]dynamic focus in the starter menu 
[*]improved recognition of devices (using the function list_drives) 
[*]final warning screen with [COLOR=#ff0000]red background[/COLOR] 
[*]improved help function 
[/LIST]

[SIZE=4]2.7:[/SIZE]

This version is a bug-fix and polishing update of the starter  script. Current mkusb and mkusb-nox are installed and there are updated  pdf documents. The operating system (14.04.1 LTS) is also  updated/upgraded to the current date (2014-12-28). 
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL]

Use this link [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[SIZE=4]2.8:[/SIZE]

This version number is reserved for for ToriOS. 

[SIZE=4]2.9:[/SIZE]

This version selects tarballs depending on the version (12.04 LTS or 14.04 LTS)

[LIST]
[*]improved 'dltbl' - to download tarballs
[LIST]
[*]selecting repository for tarballs depending on the version of the system underneath the OBI (12.04 LTS or 14.04 LTS) 
[*]some bug-fixes: modified for-loops and md5check 
[/LIST]
  
[*]improved 'confirm-partition' - pre-selected root and swap partitions should *not* be mounted 
[*]a text based One Button Installer based on Ubuntu mini.iso 12.04 LTS is released 
[/LIST]

[SIZE=4]3.0:[/SIZE]

[LIST]
[*]***zmktbl***, a graphical tool to make tarballs, is added to the OBI system
[*]The host Lubuntu system is updated (2015-07-29) 
[/LIST]

[SIZE=4]3.1:[/SIZE]

This is a bug-fix version:

zmktbl, select-part2: fix for buggy(?) zenity --list in trusty: ans=${ans%|*} ... 

[SIZE=4]3.2:[/SIZE]

select-part2: fix to identify partitions to unmount: double-quotes (") removed from target in

```
umount ${line:0:10} 2>/dev/null
df|grep ${line:0:10}>/dev/null
```

[SIZE=4]3.3:[/SIZE]

[LIST]
[*]more robust syntax in the file '$partitions'
[*] in the functions confirm-partition, select-part2, autoselect 
[/LIST]

[SIZE=4]**View the pictures as a slide-show**[/SIZE]

 The pictures are screen-dumps and illustrate how to use the OBI. [View them with 100% resolution here]("https://help.ubuntu.com/community/OBI/screenshots")!

Here are a few of them attached.

---

### Post by sudodus on 2013-09-13
Update:

Three new tarballs are uploaded and easy to try with the OBI, Bodhi, Kubuntu and Xubuntu.

```

-rw-r--r-- 728648955 sep 12 08:23 tarballs/bodhi-230-nonpae.tar.gz
-rw-r--r-- 858806740 sep 12 18:16 tarballs/xubuntu-precise.tar.gz
-rw-r--r-- 927991915 sep 13 16:41 tarballs/KubuntuPrecise.tar.gz

```
And I should add that ***GnomeClassic1204.tar.gz*** also contains the ***Unity*** desktop (choose desktop at the log in screen). So there is a mixture of small, medium and big foot-print desktop environments, or in other words, more or less eye-candy. By the way, even ***KubuntuPrecise*** runs fairly well in an old IBM Thinkpad T42 with Pentium M and 1.25 GB RAM.

---

### Post by sudodus on 2013-09-20
The dialogue has been improved at 'the only really critical button' where to select device for the installation. Instead of something like this

```
Do you want to install Lubuntu_13.04? (y/n)
y
***  WARNING: the device will be completely overwritten  *******
           Use the info from another screen (less /tmp/help-mkusb.txt)
***  Unmount the device if mounted  ****************************

Model: ATA HTS548040M9AT00 (scsi) Disk /dev/sda: 40.0GB
Model: Sandisk Cruzer Blade (scsi) Disk /dev/sdb: 4005MB
Model: JetFlash Transcend 16GB (scsi)  Disk /dev/sdc: 15.8GB
Live drive: /dev/sdb

[COLOR=#0000ff]**---> 1: install to /dev/sda**
     2: install to /dev/sdc[/COLOR]
Select another device with (+/-) or the number of the list item.
Go ahead with (g) or quit with (q)

```

each line to select contains more information (cut from the output of parted -l)

```
Do you want to install Lubuntu_13.04? (y/n)
y
***  WARNING: the device will be completely overwritten  *******
           Use the info from another screen (less /tmp/help-mkusb.txt)
***  Unmount the device if mounted  ****************************

Model: ATA HTS548040M9AT00 (scsi) Disk /dev/sda: 40.0GB
Model: Sandisk Cruzer Blade (scsi) Disk /dev/sdb: 4005MB
Model: JetFlash Transcend 16GB (scsi)  Disk /dev/sdc: 15.8GB
Live drive: /dev/sdb

[COLOR=#0000ff]**---> 1: install to ATA HTS548040M9AT00 (scsi) Disk /dev/sda: 40.0GB**
     2: install to JetFlash Transcend 16GB (scsi) Disk /dev/sdc: 15.8GB
[/COLOR]Select another device with (+/-) or the number of the list item.
Go ahead with (g) or quit with (q)

```

to make it easier to select the correct target device.

See the attached screenshot from a virtual session in KVM, qemu and virt-manager, which shows the inverted video of the real OBI. [COLOR=#696969]In the text above, the inverted video is replaced with **bold** text.[/COLOR]

---

### Post by sudodus on 2013-09-27
Update:

A new tarball is uploaded at [http://phillw.net/isos/one-button-installer/](http://phillw.net/isos/one-button-installer/) and easy to try with the OBI: Lubuntu Saucy beta 2 i386 with zRAM switched off.

```

-rw-r--r-- 673950602 sep 27 18:39 saucybeta2.tar.gz

```

---

### Post by sudodus on 2013-10-13
1. The dialogue has been improved by using screens made with the linux program ***dialog***. It means a menu style similar to that of the alternate installer and the mini.iso. See the attached pictures in post #1.

2. The ***compression*** of the dd-image files and the tarballs is improved. The original compression was using ***gzip***. It is still available, but now ***xz*** compression is also available, and ***xz compression is more than 20% more efficient***, often 30% (meaning that the size of the compressed file is 20-30% smaller than a gzipped file). xz is slower and needs more memory, but not too much. During a test with low RAM, 128 MB, extracting the tarball with xz used 62 MB while extracting with gzip used 49 GB. Downloading is usually the bottleneck, so small files are preferred.

The default compression for making an own tarball is using gzip in version 1.0 and using xz in version 1.1

You must run ***mktbl*** from the bash shell to use the other kind of compression.

---

### Post by sudodus on 2013-10-30
Update:

New tarballs are uploaded at [http://phillw.net/isos/one-button-installer/](http://phillw.net/isos/one-button-installer/) and easy to try with the OBI: Lubuntu 13.10 pure and tweaked versions.

```

-rw-r--r-- 1 492883108 okt 18 15:55 tarballs/Lubuntu_13.10oct18-tweaked.tar.xz
-rw-r--r-- 1 448403032 okt 30 01:23 tarballs/Lubuntu_13.10oct30.tar.xz
-rw-r--r-- 1 494428632 okt 28 22:31 tarballs/Lubuntu_13.10oem-oct28-tweaked.tar.xz
-rw-r--r-- 1 477114724 okt 30 00:45 tarballs/Lubuntu_13.10oem-oct30.tar.xz
-rw-r--r-- 1 396702796 nov  2 12:47 tarballs/LubuntuCoreSaucy.tar.xz

```

---

### Post by sudodus on 2013-11-11
I have tied some new bits and pieces together to the OBI version 1.1
[FONT=courier new][B]
dd_blank-obi_4GB_11.img.xz[/B][/FONT]

**Own directory for tarballs (plus symlink)**

When running the OBI, you put and find the tarballs in

```
/tarballs
~/tarballs -> /tarballs
```

and when mounted in another system, you put and find the tarballs in

```
/media/OneButtonInstall/tarballs
# not /media/OneButtonInstall/home/myself/tarballs -> /tarballs

```

**Download tarball**

There is a new download system with a dialog menu, that you run from the main menu with

[COLOR=#ff0000]d[/COLOR] Download tarball

This is intended to be an easy alternative to downloading tarballs into another system and copying to the One Button Installer.

**Make tarball**

From version 1.1 ***xz*** is the default compression in ***mktbl***. You can also enter a tarball name as parameter #3 when you run ***mktbl*** from the bash shell.

See the attached pictures.

---

### Post by sudodus on 2013-11-12
**OBI quick start manual**

Users have requested a shorter manual, so I made [this OBI quick start manual file]("http://ubuntuone.com/42AIgmpo9lsz7YNfXKCROV") with a *short description* how to make a boot drive with the OBI and how to use  the OBI to install an Ubuntu based linux operating system.

---

### Post by sudodus on 2013-11-24
Update:

New tarballs created by *Federico Leoni* are uploaded at [http://phillw.net/isos/one-button-installer/](http://phillw.net/isos/one-button-installer/) and easy to try with the OBI: ***Kubuntu, Ubuntu, Ubuntu Gnome and Xubuntu 13.10*** in the final stage of an OEM installation, [COLOR=#696969]corresponding to
```

Lubuntu_13.10oct30.tar.xz

```[/COLOR]
```

Kubuntu_13.10oem-nov23.tar.xz
Ubuntu_13.10oem-nov22.tar.xz
Ubuntu_Gnome_13.10oem-nov25.tar.xz
Xubuntu_13.10oem-nov22.tar.xz

```

---

### Post by sudodus on 2013-12-16
I have realized that many of you who are active at the Ubuntu Forums need dual- or multi-boot for your linux distro/flavour. So I made version 1.2 of the OBI, that can do it, not by itself, but together with gparted.

***1 - Edit and create partitions with gparted***

***2 - Install a tarball with the OBI to partitions, that are selected automatically or manually.***

[SIZE=4]Basic and advanced OBI level[/SIZE]

Most users are recommended to use the **basic** OBI level. This means that the OBI will install a system from a tarball into a whole device, typically an internal hard disk drive or a USB 3 pendrive. This is easy and fast.

In the **advanced** level the OBI will let you select the partitions. It means that you can install a system from a tarball into two partitions, one root file partition and one swap partition. This way it is possible to create a **dual boot** device with an existing (already installed) operating system. It is also possible to create a separate **data partition**, that can be used by linux as well as Windows.

The intention with the advanced level is to edit and create partitions with **Gparted** (booted from a 'regular' boot CD/DVD/USB device). One partition is labelled 'obi-root' and one (smaller) partition is labelled 'obi-swap'. Such partitions can be identified and selected automatically in the advanced level, but manual selection is also possible.

```
[COLOR=#0000ff]cat autoselect[/COLOR]
#!/bin/bash

LC_ALL=C;LANG=C

echo "--- Use Gparted and prepare the device for the OBI ---"
echo "1. Put the label obi-root to one partition and format it to FAT32"
echo "2. Put the label obi-swap to one partition and format it to FAT32"
echo "(It is fast to format to FAT32, and it will be overwritten by the
OBI)"
echo "*. The other partitions 'can be anything else'"
echo
"----------------------------------------------------------------------"

rootpart=$(sudo blkid|grep -i obi|grep -im1 root|cut -d: -f1)
swappart=$(sudo blkid|grep -i obi|grep -im1 swap|cut -d: -f1)

echo "$rootpart $swappart" | tee partitions
read -p "Press Enter to return to the menu"

```

So please test it when you have some time. You find it here:

[http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)

[B][FONT=courier new]dd_blank-obi_4GB_12.img.xz
OneButtonInstaller_blank-noswap_12.tar.xz
[/FONT][/B]
New versions of the documents are also uploaded.

The intention is to make it easy to use. If you test the advanced OBI level, please tell me what is bad or confusing!

---

### Post by sudodus on 2013-12-20
In order to make it more convenient to use the advanced OBI level (introduced in version 1.2), there is now version 2.2.

A. Version 2.0: The underlying operating system is upgraded to ***Ubuntu version 13.10***

B. Version 2.1 release candidate: ***Lubuntu-desktop is installed and tweaked to create a graphical desktop environment*** with desktop icons for the main tasks during installation with the One Button Installer. See the attached picture file!

0. Toggle the*** touchpad*** (to prevent accidents with laptops and notebooks because the palm is touching the touchpad and causing unwanted commands).
1. Run ***Gparted*** to edit the partitions (preparing for the  advanced OBI level).
2. Run the OBI in a ***normal lxterminal*** window
3. Run the OBI in a ***maximized xterm window*** with high resolution, in other words with more lines and columns

[I]Edit:
[/I]
USB 3 pendrives with at least 8 GB are recommended (4 GB is possible, but will soon be full). See this link [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

C. Version 2.2 is released. It has the same features as 2.1 plus a few bug-fixes. The pdf documents of the version 1.2 are also updated for the usage of version 2.2.

Use this link [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)

---

### Post by sudodus on 2013-12-29
There is a new experimental tarball of Lubuntu 13.10 with a ***non-pae kernel***. You are welcome to test it, but beware, it is an early version, and you can expect that there are some problems. For example, I cannot connect to wired internet (ethernet) in Toshiba laptops with Realtek ethernet chips. But many things work as they should.

[SIZE=3][FONT=courier new]**Lubuntu_13.10oem-oct28-tweaked_nonpae.tar.xz**[/FONT][/SIZE]

Use this link [http://phillw.net/isos/one-button-installer/rc/](http://phillw.net/isos/one-button-installer/rc/)

Edit: The kernel was obtained and installed via *hyperair*'s ppa into an already installed Lubuntu 13.10 system (in a USB 3 pendrive).

```
 sudo add-apt-repository ppa:hyperair/staging
```

---

### Post by sudodus on 2014-01-12
In order to make it more convenient to use the advanced OBI level (introduced in version 1.2), there is now version 2.2.

The underlying operating system is upgraded to ***Ubuntu version 13.10*** and ***Lubuntu-desktop is installed and tweaked to create a graphical desktop environment*** with desktop icons for the main tasks during installation with the One Button Installer.

A USB 3 pendrive with at least 8 GB is recommended for the graphical desktop environment. But there is also a flavour of version 2.2 with a text desktop environment, which is suitable for very old computers. A 4 GB pendrive is big enough for the text version.

You can find some USB pendrives that are good booters in this link [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

Use this link [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer) to download the One Button Installer.

---

### Post by sudodus on 2014-01-26
[SIZE=4]**How to install and run the OBI with a *current list of tarballs* (January 2014)**[/SIZE]

**OBI quick start manual**

Please view or download [this OBI quick start manual file]("https://help.ubuntu.com/community/OBI?action=AttachFile&do=view&target=OBI-quick-start-manual.pdf") with a *short description* how to make a boot drive with the OBI and how to use  the OBI to install an Ubuntu based linux operating system.

**README**

 If you want to read more, please view or download [this README file]("https://help.ubuntu.com/community/OBI?action=AttachFile&do=view&target=README.pdf"), * which describes with more details*  how to make a boot drive with the OBI and how to use  the OBI to  install an Ubuntu based linux operating system to your  computer, to  make a portable system or to make a tarball from an  existing system for  backup or sharing. 
 
**Download the following files**

 Select one of the compressed image files

```

dd_blank-obi_4GB_22_text.img.xz
dd_blank-obi_8GB_22_LubuntuSaucy.img.xz

```

and at least one of the tarballs (check for new tarballs at the websites for downloading). ***User: *****guru*****, Password: *****changeme** if nothing else is stated, except for the One Button Installer itself, that comes with ***User: *****myself*****, Password: *****123456**

```

Bento12.04.04-oem0.tar.xz              # in OEM mode, password: 123456
Bento12.04.04-oem1.tar.xz              # OEM: ready for the end user
Bento12.04.04.tar.xz                   # user: guru, password: changeme
Bento2ToriAlpha1.tar.xz
bodhi-230-nonpae.tar.xz
GnomeClassic1204-oem.tar.xz            # in OEM mode, password: changeme
GnomeClassic1204.tar.xz
Kubuntu_13.10oem-nov23.tar.xz          # OEM: ready for the end user
KubuntuPrecise.tar.xz
[COLOR=#696969]lubuntu-10.04.tar.gz                # good for old systems but past end of life of desktop packages
Lubuntu_13.04sep1.tar.xz            # end of life in January 2014 (watch out for it)
[/COLOR]Lubuntu_13.10oct18-tweaked.tar.xz      # user: guru, password: changeme
Lubuntu_13.10oct30.tar.xz              # OEM: ready for the end user
Lubuntu_13.10oem-oct28-tweaked.tar.xz  # in OEM mode, password: changeme
Lubuntu_13.10oem-oct30.tar.xz          # in OEM mode, password: changeme
LubuntuCoreSaucy.tar.xz
lxle-2013-08-19.tar.xz
OBI_noswap_07.tar.gz
OBI_noswap_10.tar.xz
OBI_noswap_11.tar.xz
OBI_noswap_12.tar.xz
OBI_noswap_22_LubuntuSaucy.tar.xz
OBI_noswap_22_text.tar.xz
[COLOR=#696969]ubuntu-10.04.tar.gz                 # good for old systems but past end of life of desktop packages
[/COLOR]Ubuntu_13.10oem-nov22.tar.xz           # OEM: ready for the end user
Ubuntu_Gnome_13.10oem-nov25.tar.xz     # OEM: ready for the end user
Xubuntu_13.10oem-nov22.tar.xz          # OEM: ready for the end user
xubuntu-precise.tar.xz

```

plus a script file and a signed list of the md5sums

```
mkusb
md5sums.txt.asc
```

from [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer) where a complete set of files is available or from [this google drive address]("http://drive.google.com/folderview?id=0BzX-18u3W1sQblBTYXNacGVsVkk&usp=sharing") where a limited selection of files is available. If one website is slow or   unreliable when you want to download, use the other one!

---

### Post by sudodus on 2014-02-07
**[SIZE=4]Make you own tarball[/SIZE]**

[This is a link to a detailed description how to make your own tarball]("https://help.ubuntu.com/community/OBI/MakeOBItarball")

---

### Post by sudodus on 2014-02-17
There are two experimental tarballs made from Lubuntu and Xubuntu Trusty Tahr pre-beta daily builds.  You are welcome to test them, but expect that there might be problems, particularly when you try to update/upgrade.

[SIZE=3][B][FONT=courier new]LubuntuTrusty-oem-feb12.tar.xz
XubuntuTrusty-oem-feb13.tar.xz
[/FONT][/B][/SIZE]
Use this link [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)
[I]
Edit[/I]: These tarballs contain a 32-bit pae kernel and fake-pae  and can be used with most Intel/AMD CPUs including Pentium M and Celeron  M processors.
[URL="http://phillw.net/isos/one-button-installer"]
[/URL]

---

### Post by sudodus on 2014-02-17
New tarballs are created by *Jack Trice* from LXLE 12.04.4 with 32-bits non-pae kernel and OEM style installation.

[SIZE=3]**[FONT=courier new]lxle32-12.04.4-oem0.tar.xz   [/FONT]**[/SIZE][SIZE=3][B][FONT=courier new]# in OEM mode, password: 123456
lxle32-12.04.4-oem1.tar.xz[/FONT][/B][FONT=courier new]**   # OEM: ready for the end user **[/FONT][/SIZE]

Use this link [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)

These tarballs contain a 32-bit non-pae kernel and  can be used with most Intel/AMD CPUs including Pentium M and Celeron  M  processors. The non-pae kernel does not manage memory above 2 GB well (but it is seldom a problem with old hardware). LXDE is specified for minimum 512 MB RAM, so these tarballs are suitable for computers with RAM size in the interval [512 MB, 2 GB] See this link

[http://wiki.lxle.net/doku.php/requirements](http://wiki.lxle.net/doku.php/requirements)

-o-

We selected this kernel to make good tarballs for old computers. The 64-bit version of LXLE is better for newer and more powerful computers, but there is no such tarball (now).

---

### Post by sudodus on 2014-02-22
***Version 2.3*** of the One Button Installer is released. It is mainly a bug-fix update from 2.2 including updated pdf documents. The operating system (13.10) is also updated/upgraded.

New feature: the OBI will share an existing swap partition, when selected at the advanced OBI level.

USB 3 pendrives with at least 8 GB are recommended for the version with Lubuntu desktop. 4 GB pendrives are still possible for the text version. See also this link [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

Use this link [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by sudodus on 2014-02-26
There is an experimental version of the One Button Installer built on Trusty Tahr and Phill Whiteside's non-pae kernel

Compressed image name: **dd_blank-obi_7.8GB_23_LubuntuTrusty_non-pae.img.xz**

Kernel version: **3.13.2_3.13.2-1_i386**

Location:
[http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)
[http://phillw.net/isos/one-button-installer/rc/](http://phillw.net/isos/one-button-installer/rc/)
[http://phillw.net/isos/one-button-installer/dd_images](http://phillw.net/isos/one-button-installer/dd_images)

User name: **myself**
Password:  **123456**

I recommend ***mkusb*** to install the compressed image to a pendrive or a hard disk drive. If you have or can borrow a really old non-pae CPU,
please try it in ***text mode*** to keep memory requirements low! It should be happy with 128 MB in text mode.

---

### Post by sudodus on 2014-05-07
Two new tarballs are created from Lubuntu 14.04 with 32-bit non-pae and 32-bit generit (pae) kernels with OEM style installation.

[SIZE=3]**[FONT=courier new]Lubuntu_14.04oem-npae.tar.xz   [/FONT]**[/SIZE][SIZE=3]**[FONT=courier new]# in OEM mode, password: 123456, contains several tweaks[/FONT]**[/SIZE]
[SIZE=3]**[FONT=courier new]Lubuntu_14.04_eu-npae.tar.xz           # OEM: ready for the end user[/FONT]**[/SIZE], basically standard Lubuntu

Use this link [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)

These tarballs contains *PhillW*'s 32-bit non-pae kernel and  can be used with  most Intel/AMD CPUs including Pentium M and Celeron  M  processors. The  non-pae kernel does not manage memory above 2 GB well (but it is seldom a  problem with old hardware). The generic (pae) kernel is better when there is more than 2 GB RAM. See these links

[More details about the OEM tarball]("https://help.ubuntu.com/community/OBI/Lubuntu_14.04_OEM-nonPAE")

 [More details about the End User tarball ]("https://help.ubuntu.com/community/OBI/Lubuntu_14.04_EndUser-nonPAE")
[URL="http://ubuntuforums.org/showthread.php?t=2216356"]
Please help us test Lubuntu with Phill's non-pae kernel
[/URL]

---

### Post by sudodus on 2014-05-20
There is a new and special version of the 9w installer, the [OBI-9w installer]("https://help.ubuntu.com/community/9w#Ubuntu_14.04_LTS_text_non-pae_.27Trusty-npae124-text.iso.27_and_.27obi_Trusty-npae124-text-9w.iso.27")

This version is made for very old computers without PAE capability. The One Button Installer in run from the 9w installer's debian system. Now there is a super light-weight installer, that can

- install from CD, DVD and USB
- create not only single boot but also dual boot systems.

Prepare partitions with Gparted and run the One Button Installer at the advanced level to create dual boot or multi boot system.

There are special tarballs for the 9w installer, and these tarballs come with the iso file.

---

### Post by sudodus on 2014-07-05
[SIZE=4]Installer for really old computers[/SIZE]

There is a new iso file of the OBI-9w installer which is up to date with  a new version of **[[COLOR=#ff6633]phillw[/COLOR]]("http://ubuntuforums.org/member.php?u=824544")**'s non-pae kernel and updated/dist-upgraded  packages:

[B]obi_Trusty-nonpae-txt5-9w.iso

[/B]that you find at [http://phillw.net/isos/linux-tools/9w](http://phillw.net/isos/linux-tools/9w)[URL="http://phillw.net/isos/linux-tools/9w"]
[/URL]
*Edit*: See the instructions at this wiki page [http://help.ubuntu.com/community/9w](http://help.ubuntu.com/community/9w)

---

### Post by sudodus on 2014-07-08
[SIZE=4]Tarballs for old computers[/SIZE]

Two new tarballs are created for the One Button Installer. They are up to date with  a new version of **[[COLOR=#ff6633]phillw[/COLOR]]("http://ubuntuforums.org/member.php?u=824544")**'s non-pae kernel and updated/dist-upgraded  packages:

[SIZE=3]**[FONT=courier new]Lubuntu_14.04oem-npae5.tar.xz   [/FONT]**[/SIZE][SIZE=3]**[FONT=courier new]# in OEM mode, password: 123456, contains several tweaks[/FONT]**[/SIZE]

[SIZE=3][FONT=courier new]**Trusty-nonpae-txt5.tar.xz**[/FONT]**[FONT=courier new]     # user: guru, password: changeme[/FONT]**[/SIZE]

Use this link [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)

These tarballs contains *PhillW*'s 32-bit non-pae kernel and  can be used with  most Intel/AMD CPUs including Pentium M and Celeron  M  processors. The  non-pae kernel does not manage memory above 2 GB well (but it is seldom a  problem with old hardware). The generic (pae) kernel is better when there is more than 2 GB RAM. See these links

[More details about the OEM tarball]("https://help.ubuntu.com/community/OBI/Lubuntu_14.04_OEM-nonPAE")

 [URL="http://ubuntuforums.org/showthread.php?t=2216356"]Please help us test Lubuntu with Phill's non-pae kernel
[/URL]

---

### Post by sudodus on 2014-07-12
[SIZE=4]Version 2.5 of the One Button Installer[/SIZE]

Version 2.5 is released. It is mainly a bug-fix update  from 2.3 (and 2.4 OBI-9w) including updated pdf documents. The operating system (14.04 LTS)  is also updated/upgraded.

New  feature: the starter menu will set the default item (command line) in a  logical way prompting to download and select tarball, select OBI level  and then install a system. Two-digit partition numbers (/dev/sda10 ...)  are recognized at the advanced OBI level. 

USB 3 pendrives with at least 8 GB are recommended for this version with  Lubuntu desktop. 4 GB pendrives are still possible for the text version.  See also this link [URL="http://ubuntuforums.org/showthread.php?t=2196858"]

Howto help USB boot drives[/URL]

Use this link [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

-o-

*Edit*: In addition to the compressed dd image file and tarball of the OBI version 2.5 with 32-bit generic PAE kernels, there is now also a compressed dd image file with a non-pae kernel by  **[[COLOR=#ff6633]phillw[/COLOR]]("http://ubuntuforums.org/member.php?u=824544")**
[I][B]
dd_blank-obi_7.8GB_25_LubuntuTrusty_nonpae.img.xz[/B][/I]

---

### Post by sudodus on 2014-12-29
[SIZE=4]Version 2.6:[/SIZE]

This version is a major improvement, implemented for ToriOS but not published here.



[LIST]
[*]dynamic focus in the starter menu 
[*]improved recognition of devices (using the function list_drives) 
[*]final warning screen with [COLOR=#ff0000]red background[/COLOR] 
[*]improved help function 
[/LIST]

[SIZE=4]Version 2.7:
[/SIZE]
This version is a bug-fix and polishing update of the starter  script.  Current mkusb and mkusb-nox are installed and there are updated  pdf  documents. The operating system (14.04.1 LTS) is also  updated/upgraded  to the current date (2014-12-28). 
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
[/URL]Use this link [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by sudodus on 2014-12-30
[SIZE=4]Mini text based system with a menu to select installing various light desktop environments[/SIZE]

An alternative that you might want to test, is to use the One Button Installer to install a  mini system (originally made from Ubuntu 14.04 mini.iso) with a ***menu to  select installing*** various light (ultra light to medium light) desktop environments.  It installs a portable system even as a text based system.

[COLOR=#696969]The following tarball contains *phillw*'s nonpae kernel, made during last summer to be used with very old computers.

**Trusty-nonpae-txt5.tar.xz**[/COLOR]

This tarball was updated/upgraded today to the following tarball, and  the kernel was replaced with the current generic pae kernel and comes with the boot option forcepae to run with most 32-bit processors and be able to update the kernel, also with Pentium M and Celeron M.
[B]
Trusty-mini-txt6.tar.xz[/B]

The screenshots were made when Lubuntu Core was installed in a computer with Pentium M, booted without the boot option forcepae (removed). It boots from grub, but cannot update the kernel, so supplying forcepae makes it more convenient for the end user (*you*). Running in text mode needs only 39 MiB RAM in that computer, while running in the Lubuntu DE needs approximately 150 MiB.

-o-

This standard version of the One Button Installer works only from mass  storage devices (USB pendrives, but also from IDE drives and SATA  drives). And you can install in one computer and port the drive to  another computer. See the following link for more details.

[URL="https://help.ubuntu.com/community/OBI"]https://help.ubuntu.com/community/OBI
[/URL]

---

### Post by sudodus on 2015-03-29
[SIZE=4]Version 2.9:
[/SIZE]

 [TABLE]
[TR]
[TD="bgcolor: #CCFF99"] version 2.9: selects tarballs depending on the version (12.04 LTS or 14.04 LTS)[/TD]
[/TR]
[/TABLE]


[LIST]
[*]improved 'dltbl' - to download tarballs
[LIST]
[*]selecting repository for tarballs depending on the version of the system underneath the OBI (12.04 LTS or 14.04 LTS) 
[*]some bug-fixes: modified for-loops and md5check 
[/LIST]
  
[*]improved 'confirm-partition' - pre-selected root and swap partitions should *not* be mounted 
[*]a text based One Button Installer based on Ubuntu mini.iso 12.04 LTS is released 
[/LIST]


Select one of the compressed image files (in order to use the One Button Installer. See more details at the first post of this thread).

```

dd_blank-obi_4GB_23_text.img.xz                    # if you need a really small system    (324MiB)
dd_blank-obi_7.8GB_25_LubuntuTrusty_nonpae.img.xz  # if you need a non-pae kernel         (677MiB)
[COLOR=#0000cd]dd_blank-obi_7.8GB_27_LubuntuTrusty.img.xz[/COLOR]         # current main choice for most cases   (696MiB)
dd_precise-obi_4GB_29_text.img.xz                  # to install tarballs made for precise (183MiB)

```

---

### Post by sudodus on 2015-07-30
[SIZE=4]One Button Installer version 3.0[/SIZE]

***zmktbl***, a graphical tool to make tarballs, is added to the OBI system. An icon on the desktop brings you directly to the graphical tool, when you run the Lubuntu desktop.

This should work without much instructions, but

- it is recommended to save the tarballs in the directory **/tarballs**, if it has write access and there is enough free space,
- otherwise (for example in systems booted from ISO files) you should select a directory in a partition with enough free space for the tarball.

The ***host Lubuntu*** system is updated (2015-07-29)

Find more details at

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)
and
[Make your own tarball](https://help.ubuntu.com/community/OBI/MakeOBItarball)

---

### Post by sudodus on 2015-07-30
[SIZE=4]Version 3.1:[/SIZE]

This is a bug-fix version. You should download version 3.1 for zmktbl to work properly.

- zmktbl, select-part2: fix for buggy(?) zenity --list in trusty: ans=${ans%|*} ...

---

### Post by sudodus on 2015-07-31
[SIZE=4]ToriOS beta tarball[/SIZE]

There is a tarball with ToriOS (beta version) updated from the repositories yesterday (July 30, 2015).

[ToriOS-pae-OEM_prec_use-by-OBI-in-trusty.tar.xz](http://phillw.net/isos/one-button-installer/tarballs/ToriOS-pae-OEM_prec_use-by-OBI-in-trusty.tar.xz)

This tarball was made with zmktbl in the OBI version 3.1, and it can be installed with the same version. ToriOS is installed in OEM mode, and should work well in old and middle-aged computers. It is a 32-bit system and the installation method works in BIOS mode. Use another linux distro and other installation method to install in UEFI mode (for example a 64-bit version of an Ubuntu flavour and mkusb).

Edit:

This tarball was made from an OEM system, where Lubuntu Core was installed in order to help the system for final installation (ubiquity) render the graphical user interface correctly. However, you should focus on ToriOS. (Do not use the Lubuntu session, because it has passed end of life and receives no security updates).

---

### Post by sudodus on 2015-11-05
[SIZE=4]ToriOS gamma tarball[/SIZE]

There is a tarball with ToriOS ('gamma' version) updated from the repositories yesterday (Nov 4, 2015).

[ToriOS-pae-OEM_prec_use-by-OBI-in-trusty-nov.tar.xz](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs/ToriOS-pae-OEM_prec_use-by-OBI-in-trusty-nov.tar.xz)

This tarball can be installed with the OBI version 3.2. ToriOS is installed in OEM mode, and should work well in old and middle-aged computers. It is a 32-bit system and the installation method works in BIOS mode. Use another linux distro and other installation method to install in UEFI mode (for example a 64-bit version of an Ubuntu flavour and mkusb).

This tarball was made from an OEM system, where Lubuntu Core was installed in order to help the system for final installation (ubiquity) render the graphical user interface correctly. However, you should focus on ToriOS. (Do not use the Lubuntu session, because it has passed end of life and receives no security updates).

*Edit:* Notice that this 'gamma' version is 'more developed and polished than a beta version', but still not a stable released version.

```
$ md5sum ToriOS-pae-OEM_prec_use-by-OBI-in-trusty-nov.tar.xz
2b78b505d77b2cd269b6f7919efb0353  ToriOS-pae-OEM_prec_use-by-OBI-in-trusty-nov.tar.xz
```

---

### Post by sudodus on 2016-04-28
[SIZE=4]One Button Installer version 3.2[/SIZE]

This is a bug-fix version. You should download version 3.2 for selecting partitions to work properly.

- zmktbl, select-part2: fix to identify partitions to unmount: double-quotes (") removed from target in
 .  umount ${line:0:10} 2>/dev/null
 .  df|grep ${line:0:10}>/dev/null

[hr][/hr]
You find the One Button Installer at the following link: [http://phillw.net/isos/one-button-installer](http://phillw.net/isos/one-button-installer)

Get the compressed image file [dd_blank-obi_7.8GB_32_LubuntuTrusty.img.xz](http://phillw.net/isos/one-button-installer/dd_images/dd_blank-obi_7.8GB_32_LubuntuTrusty.img.xz) and install it to a USB pendrive with [mkusb](https://help.ubuntu.com/community/mkusb).

Check the md5sum:
```
[COLOR="#0000FF"]md5sum dd_blank-obi_7.8GB_32_LubuntuTrusty.img.xz[/COLOR]
e196c51aa56770a255eb99bd2abd45ca  dd_blank-obi_7.8GB_32_LubuntuTrusty.img.xz
```


There is a general description at [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by sudodus on 2016-05-02
[SIZE=4]New tarballs for ToriOS[/SIZE]

The ToriOS tarball from November 2015 with a ***Precise*** version is 'updated/dist-upgraded' in other words up to date.

A new ToriOS version is created by 'do-release-upgrade' from Precise to ***Trusty***. The Trusty version seems to work well, but is not tested much. You may find a bug. In that case, please report it (here) :-)

The two most recent tarballs (made in May 2016) have the following md5sums:

```
ead0f0ad1ecdd12d6ede036eae7f40f5  ToriOS-pae-OEM_prec_use-by-OBI-in-trusty-2016-may.tar.xz  # ToriOS Precise
8dbd99f28cce8d685f7b129641f63ff0  ToriOS-pae-OEM_trus_use-by-OBI-in-trusty-2016-may.tar.xz  # ToriOS Trusty
```

user: OEM
password: 123456

Click on the desktop icon ***Prepare for shipping to end user***. See the screenshot.

---

### Post by sudodus on 2016-05-02
[SIZE=4]New tarball for [Ubuntu flavours of] Xenial[/SIZE]

There is a new tarball for Xenial, released as [Ubuntu flavours of] version 16.04 LTS. It is based on a text only system installed with the Ubuntu mini.iso. It can easily be developed into standard Ubuntu or any of the Ubuntu flavours, or it can be used to create a custom system.

The tarball has the following md5sum:
```
c1870b61e3834941d75667c193a37019  Xenial-32-txt.tar.xz
```

See the following link to a new post in this thread:

[New systems to install [Ubuntu flavours of] Xenial alias 16.04 LTS](http://ubuntuforums.org/showthread.php?t=2172971&p=13489520#post13489520)

---

### Post by sudodus on 2016-05-06
[SIZE=4]New tarballs[/SIZE]

***Trusty mini tarball updated/dist-upgraded***

The system in the tarball **Trusty-mini-txt6.tar.xz** is made up to date and stored in the new tarball **Trusty-mini-txt7.tar.xz** with the following md5sum.

```
93a99da93736ac99c0bb5a52a1009e59  Trusty-mini-txt7.tar.xz
```

***Another ToriOS Trusty tarball***

This ToriOS Trusty version built from the system above, **Trusty-mini-txt7.tar.xz**, using the following commands and some tweaks,

[QUOTE=ToriOS developer Israel Dahl]Do your mini then run
```
wget https://raw.githubusercontent.com/Israel-/torios-from-mini/master/torios-trusty-x86.bash
chmod +x torios-trusty-x86.bash
./torios-trusty-x86.bash
```
[/QUOTE]

The script is old and originally made for Precise. I had to install the package torios-live and then overwrite it with the package torios-desktop and clean it up, but then it works well. The RAM needed should be reduced, and probably there are some bugs to squash before it is ready to be released.

```
$ md5sum ToriOS-mini_trusty_use-by-OBI-in-trusty-2016-may.tar.xz
77efef5266118c784ce0c9f5ec6db3ad  ToriOS-mini_trusty_use-by-OBI-in-trusty-2016-may.tar.xz
```

The version based on Debian Jessie is most likely to be the first ToriOS version to be released.

[hr][/hr]
You can download these tarballs from within the One Button Installer or directly from this link [phillw.net/isos/linux-tools/OBI/trusty/tarballs](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs)

user: **guru**
password: **changeme**

---

### Post by sudodus on 2016-05-09
[SIZE=4]New Lubuntu tarball with UXA acceleration for old Intel graphics[/SIZE]

The tarball **Lubuntu_16.04_oem-uxa.tar.xz** has the following md5sum

```
$ md5sum Lubuntu_16.04_oem-uxa.tar.xz
2e706871e1c193978acdd39a32479153  Lubuntu_16.04_oem-uxa.tar.xz
```

It can be used to install Lubuntu 16.04 into computers with some old Intel graphics chips, for example series 945 and 82852/855GM, where there are problems to install with the standard installer. An alterntive is to use [mkusb](https://help.ubuntu.com/community/mkusb) and the corresponding compressed image file (with the same system)

[dd_Lubuntu_16.04_oem-uxa_2016-may_7.8GB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_Lubuntu_16.04_oem-uxa_2016-may_7.8GB.img.xz)

This Lubuntu system is prepared for OEM tweaking (password 123456) and made up to date 2016-05-08.

A line can be activated in /etc/fstab to mount a floppy drive. The Xorg acceleration method is changed to UXA (which helps with old Intel graphics). Prepared with the boot option forcepae for use with Pentium M and Celeron M processors. Some useful program packages added.

The file **/etc/X11/xorg.conf** is edited as follows: (there should be a tab before each line except the first and the last).

```
Section "Device"
        Identifier "Intel Graphics"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSection
```

Intel 945 series graphics work with 'uxa' (but work better with 'intel') and 82865G graphics is not helped by 'uxa', but wants the boot option 'nomodeset' in order to display the graphical desktop (add nomodeset yourself if necessary). However, there are many Intel graphics chips, and 'uxa' might be useful for some of them. So this system is kept available, even if the first choice is 'intel' now. See the next post.

Summary of tweaks in the compressed image file and tarball:

OEM
UXA acceleration
the grub menu is shown (not hidden in a single boot system)
template in fstab to uncomment for floppy
forcepae
htop
lubuntu-restricted-extras
mkusb
mkusb-nox
pulseaudio
pavucontrol

After preparing for the end user and logging in as end user, you should install language support - via the menu option - in order to make it complete. Then the keyboard will also be the correct one, if you use a non-default language (in other words different from US English).

[hr][/hr]
You can download this tarball from within the One Button Installer or directly from this link [phillw.net/isos/linux-tools/OBI/trusty/tarballs](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs)

user: **oem**
password: **123456**

[hr][/hr]
***Edit:*** See this link, where the 'uxa' and 'intel' systems are compared: [Re: Lubuntu 16.04 flashing cursor with certain Intel video drivers](http://ubuntuforums.org/showthread.php?t=2321734&p=13486996#post13486996) concerning old Intel graphics chips, like **945** series.

---

### Post by sudodus on 2016-05-11
[SIZE=4]New Lubuntu tarballs  and compressed image files with 'xserver-xorg-video-intel' for Intel graphics[/SIZE]

Tarballs with 32-bit and 64-bit Lubuntu have the following md5sums

```
$ md5sum Lubuntu_16.04_oem-intel.tar.xz Lubuntu_16.04_oem-intl_amd64.tar.xz
fa2e6de0acac5264a7774f91b09a8ab3  Lubuntu_16.04_oem-intel.tar.xz          # 32 bits, BIOS mode
1744e008b67e179c4fb25c5f83ba7ee4  Lubuntu_16.04_oem-intl_amd64.tar.xz     # 64 bits, BIOS mode

```

They can be used to install Lubuntu 16.04 into computers with some old Intel graphics chips, for example series 945 and 82852/855GM, where there are problems to install with the standard installer. An alterntive is to use [mkusb](https://help.ubuntu.com/community/mkusb) and the corresponding compressed image files (with the corresponding operating systems)

[dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB.img.xz) (32 bits, BIOS mode)
[dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB_amd64.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB_amd64.img.xz) (64 bits, BIOS mode)

This Lubuntu system is prepared for OEM tweaking (password 123456) and made up to date 2016-05-08.

The 'intel' system is prepared by installing the package

**xserver-xorg-video-intel**

and is recommended as the first choice (before 'uxa').

A line can be activated in /etc/fstab to mount a floppy drive. The graphics is improved by installing an 'intel package'

```
sudo apt-get install xserver-xorg-video-intel
```

The system is also prepared with the boot option forcepae for use with Pentium M and Celeron M processors. Some useful programs are added.

This system works with an old IBM Thinkcentre 8187-73G  with **82865G** graphics and a not that old Lenovo T60 laptop **945 series** (Intel Corporation Mobile 945GM/GMS, and also with 943/940GML Express Integrated Graphics Controller (rev 03) prog-if 00 [VGA controller , or VGA compatible controller Intel Corporation Atom Processor D4xx/DSxx/N4xx/NSxx Integrated Graphics Controller). [noparse][edit][/noparse] This system works with old as well as middle-age and new hardware. The newest system tested is an Intel **NUC**6i3SYH with integrated i3 6100 (Sky Lake integrated graphics), and a number of laptops 'in between' also work.[noparse][/edit][/noparse]

Summary of tweaks in the compressed image file and tarball:

OEM
xserver-xorg-video-intel
the grub menu is shown (not hidden in a single boot system)
template in fstab to uncomment for floppy
forcepae
htop
lubuntu-restricted-extras
mkusb
mkusb-nox
pulseaudio
pavucontrol

After preparing for the end user and logging in as end user, you should install language support - via the menu option - in order to make it complete. Then the keyboard will also be the correct one, if you use a non-default language (in other words different from US English).

[hr][/hr]
You can download this tarball from within the One Button Installer or directly from this link [phillw.net/isos/linux-tools/OBI/trusty/tarballs](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs)

user: **oem**
password: **123456**

---

### Post by sudodus on 2016-05-15
[SIZE=4]New systems to install [Ubuntu flavours of] Xenial alias 16.04 LTS[/SIZE]

[SIZE=3]A. Tarball[/SIZE]

There is a tarball for Xenial, released as [Ubuntu flavours of] version 16.04 LTS. It is based on a text only system installed with the Ubuntu mini.iso. It can easily be developed into standard Ubuntu or any of the Ubuntu flavours, or it can be used to create a custom system.

The tarball has the following md5sum:
```
c1870b61e3834941d75667c193a37019  Xenial-32-txt.tar.xz
```

See the attached screenshots #1-2

[SIZE=3]B. Compressed image files[/SIZE]

There are also compressed image files, that work in UEFI and BIOS mode. These have no matching tarballs, because the One Button Installer does not create systems for UEFI mode. Instead, the compressed image files can be installed with [mkusb (or mkusb-nox in text mode)](https://help.ubuntu.com/community/mkusb).

[dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz)

[dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS-intel-4-pendrive-7.8GB.img.xz)

This last 'intel' file contains the package 'xserver-xorg-video-intel', which makes the system work will some old Intel graphics chips.

See the attached screenshots #3-5

[hr][/hr]
user: **guru**
password: **changeme**

---

### Post by yman on 2016-05-20
Where to download Lubuntu_16.04_oem-intel.tar.xz ?

---

### Post by sudodus on 2016-05-20
1. You can download tarballs from within the One Button Installer. This is the easiest option, and the md5sum will be checked automatically.


2. Download tarballs from the following link, [http://phillw.net/isos/linux-tools/OBI/trusty/tarballs](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs) and check the md5sum manually. 

The md5sums are in a file in the parent directory (of the tarballs directory), [md5sums-phillw.txt](http://phillw.net/isos/linux-tools/OBI/trusty/md5sums-phillw.txt)

In this case 'trusty' means 'install with the Trusty version of the One Button Installer' (which is the recommended version). So tarballs with Xenial can be found there, for example the tarball you ask for, [Lubuntu_16.04_oem-intel.tar.xz](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs/Lubuntu_16.04_oem-intel.tar.xz)

---

### Post by sudodus on 2016-06-28
[SIZE=4]Updated system to install [Ubuntu flavours of] Xenial alias 16.04 LTS[/SIZE]

The 'intel' text indicates that the system contains the package 'xserver-xorg-video-intel', which makes the system work will some old Intel graphics chips.

This system (both in the tarball and the compressed image file) has been made up to date June 28, 2016. Features of the corresponding 64-bit [UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#Mini_system_with_.27text.27_screen_user_interface) systems have been added: htop, a menu to select text mode font size, and the 'tasksel' menu for all the options of the Ubuntu Server.

[SIZE=3]A. Tarball[/SIZE]

There is a tarball for Xenial, released as [Ubuntu flavours of] version 16.04 LTS. It is based on a text only system installed with the Ubuntu mini.iso. It can easily be developed into standard Ubuntu or any of the Ubuntu flavours, or it can be used to create a custom system.

The tarball has the following md5sum:
```
3e42985053a8ea82bb87687286a45e6a  Xenial-32-txt_2016-06-28_intel.tar.xz
```

[SIZE=3]B. Compressed image file[/SIZE]

There is also a compressed image file, that works in BIOS mode. The compressed image files can be installed with [mkusb (or mkusb-nox in text mode)](https://help.ubuntu.com/community/mkusb).

[dd_Xenial-32-txt_2016-06-28_intel_7.8GB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_Xenial-32-txt_2016-06-28_intel_7.8GB.img.xz)

with the following md5sum:
```
01cc17a80dfbf7f5e484a56164ebbc8d  dd_Xenial-32-txt_2016-06-28_intel_7.8GB.img.xz
```

[hr][/hr]
user: **guru**
password: **changeme**

- You can download tarballs from within the One Button Installer. This is the easiest option, and the md5sum will be checked automatically.

- Download tarballs from the following link, [http://phillw.net/isos/linux-tools/OBI/trusty/tarballs](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs) and check the md5sum manually. 

The md5sums are in a file in the parent directory (of the tarballs directory), [md5sums-phillw.txt](http://phillw.net/isos/linux-tools/OBI/trusty/md5sums-phillw.txt)

In this case 'trusty' means 'install with the Trusty version of the One Button Installer' (which is the recommended version). So tarballs with Xenial can be found there.

---

### Post by sudodus on 2016-06-29
I have tested the system in **Xenial-32-txt_2016-06-28_intel.tar.xz** in some different computers.

***It works well in my 64-bit computers (from 2008 - 2016). ***

***It works but with some problems in my 32-bit computers***:

an IBM Thinkpad T42 with Pentium M processor and a Dell Dimension 4600 with a Pentium 4 processor.

**-** The font is selected and unselected during boot,
+ but can be selected again via the text-mode-menus.

**-** The simple graphical user interface via Fluxbox and xinit cannot be started (via startx).
+ The more advanced graphical user interface 'Lubuntu Core' works as expected, and if Fluxbox is installed, it can be selected at the log in screen.

---

### Post by sudodus on 2016-06-30
[SIZE=4]Tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS][/SIZE]

This system (both in the tarball and the compressed image file) has been debugged and made up to date June 29, 2016. More details about the bugs can be found the [this link](http://ubuntuforums.org/showthread.php?t=1958073&page=19&p=13511300#post13511300) to the Ubuntu Forums (the linked post and the following posts).

[SIZE=3]A. Tarball[/SIZE]

**X32-Txt-Startx-Intl_2016-06-29.tar.xz** contains a Xenial 32-bit (i386) mini system.

- 'Txt' indicates that the system boots into a text screen.

- 'Startx' indicates that it can use ***startx*** and start the window manager ***Fluxbox*** where ***xterm*** is available. These program packages are already installed.

- 'Intl' indicates that the system contains the package 'xserver-xorg-video-intel', which makes the system work will some old Intel graphics chips. 

The tarball has the following md5sum:
```
1d907738acfed97ac4a9009d3cf2dc5d  X32-Txt-Startx-Intl_2016-06-29.tar.xz
```

[SIZE=3]B. Compressed image file[/SIZE]

There is also a compressed image file, that works in BIOS mode. The compressed image files can be installed with [mkusb (or mkusb-nox in text mode)](https://help.ubuntu.com/community/mkusb).

[dd_X32-Txt-Startx-Intl_2016-06-29_7.8GB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_X32-Txt-Startx-Intl_2016-06-29_7.8GB.img.xz)

with the following md5sum:
```
7873e02b1cc5dcb5efe9a76569d7e2ba  dd_X32-Txt-Startx-Intl_2016-06-29_7.8GB.img.xz
```

[hr][/hr]
user: **guru**
password: **changeme**

- You can download tarballs from within the One Button Installer. This is the easiest option, and the md5sum will be checked automatically.

- Download tarballs from the following link, [http://phillw.net/isos/linux-tools/OBI/trusty/tarballs](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs) and check the md5sum manually. 

The md5sums are in a file in the parent directory (of the tarballs directory), [md5sums-phillw.txt](http://phillw.net/isos/linux-tools/OBI/trusty/md5sums-phillw.txt)

In this case 'trusty' means 'install with the Trusty version of the One Button Installer' (which is the recommended version). So tarballs with Xenial can be found there.

---

### Post by sudodus on 2016-07-04
[SIZE=4]One Button Installer version 3.3[/SIZE]

This is a bug-fix version. You should download version 3.3 for selecting partitions to work properly.

[LIST]
[*]more robust syntax in the file '$partitions'
[*] modifications in the functions confirm-partition, select-part2, autoselect 
[/LIST]

[hr][/hr]
You find the One Button Installer at the following link: [http://phillw.net/isos/linux-tools/one-button-installer](http://phillw.net/isos/linux-tools/one-button-installer)

Get the compressed image file [dd_blank-obi_7.8GB_33_LubuntuTrusty.img.xz](http://phillw.net/isos/linux-tools/one-button-installer/dd_images/dd_blank-obi_7.8GB_33_LubuntuTrusty.img.xz) and install it to a USB pendrive with [mkusb](https://help.ubuntu.com/community/mkusb).

Check the md5sum:
```
[COLOR="#0000FF"]md5sum dd_blank-obi_7.8GB_33_LubuntuTrusty.img.xz[/COLOR]
e196c51aa56770a255eb99bd2abd45ca  dd_blank-obi_7.8GB_33_LubuntuTrusty.img.xz
```


There is a general description at [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

