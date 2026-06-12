---
title: "Ubuntu_Xenial Xerus (Nov. 13th build) Alongside Threshold_2"
date: 2015-11-13
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-11-13
Friday November 13, 2015

Testing Xenial Installer (2nd attempt)

It's now possible to install Ubuntu 16.04 alongside Windows Ten.  This option was reintroduced in the Xenial installer.  No need to pass by Gparted, Partition Wizard nor Something Else.  It's all cooked in the plate. 
The Xenial installer splits default the HDD into 2 equal partitions.  It can be resized by dragging one of the partition.   I chose a 233 GB partition to mount Xenial in it (see screenshot). 

Results are similar to my previous attempt:
[http://ubuntuforums.org/showthread.php?t=2299825](http://ubuntuforums.org/showthread.php?t=2299825)

There was only one error at the end: I was not asked to remove the media and the installer starts a second installation.  In an issue like this one, it's better to shut-down the computer instead of choosing restart (no end loop). 

That's improvement!  Thanks to those who worked on the Xenial Xerus installer.


P.S. There was no error nor integrity violations under Windows after the installation: sfc /SCANNOW in command prompt admin.  System File Check / Scannow

All the best,

**Proposed enable**

```
xenial@hp:~$ grub-install --version 
grub-install (GRUB) 2.02~beta2-31
xenial@hp:~$ uname -r
4.2.0-19-generic
xenial@hp:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
xenial@hp:~$ ubuntu-drivers list
intel-microcode
xenial@hp:~$ ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free


xenial@hp:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for xenial: 
NAME   FSTYPE   SIZE MOUNTPOINT                     LABEL
sda           698.7G                                
&#9500;&#9472;sda1 ntfs     500M                                System Reserved
&#9500;&#9472;sda2 ntfs   480.8G /media/xenial/A6D2CFA0D2CF72DB 
&#9500;&#9472;sda3            1K                                
&#9500;&#9472;sda5 ext4   213.5G /                              
&#9492;&#9472;sda6 swap     3.9G [SWAP]                         
sr0            1024M                                
xenial@hp:~$ sudo fdisk -l
.
.
.
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048    1026047    1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2          1026048 1009213457 1008187410 480.8G  7 HPFS/NTFS/exFAT
/dev/sda3       1009215486 1465147391  455931906 217.4G  5 Extended
/dev/sda5       1009215488 1456943103  447727616 213.5G 83 Linux
/dev/sda6       1456945152 1465147391    8202240   3.9G 82 Linux swap / Solaris

```

Ubuntu 16.04 LTS Dual Boot Windows 10 P / 10586.3.amd64fre.th2_release_sec.151104-1948

---

### Post by jerrylamos on 2015-11-13
I use the easy way out.  Ubuntu on USB SSD hard drive.  Actually, three partitions of Ubuntu - LTS, Xenial, Xenial.  
Plus an Archive partition with documents, pictures, .iso's, etc. etc.
I alternate Xenial installs in case something screws up.  During Development things do screw up.
Internal hard drive has two Win 10's, one from Win 7 update and the other from Win 10 Preview.  I could ditch one but haven't needed to.  Yes the two partitions were made with gparted.
Currently the internal hard drive does have a Grub boot.  Works O.K.
Do note after booting Win 10 it can be a fiddle to get Ubuntu to boot even with the USB as first choice on boot-up.  Win 10 shutdown saves a Win 10 image, not really shutting down, and tries to restart the image on power on.....
The Xenial partitions are at the moment 10 GB each, using a bit less than  6 GB.  I use these for testing.

Choices.

---

### Post by MikeMecanic on 2015-11-15
Only have good news: It runs like a Swiss clock

---

