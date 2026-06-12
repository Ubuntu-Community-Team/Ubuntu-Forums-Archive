---
title: "usb flash drive"
date: 2014-03-26
forum: Ubuntu Development Version
---

### Post by ronb19495 on 2014-03-26
gday folks have 14.04 and working very well under uefi mode. but I have a small problem I am trying to install 13.10 on a usb flash drive from an iso,i want to use the usb flash drive as another hard drive,but its not working as its killing my grub on 14.04,I have tried three times to load ubuntu on the usb stick alas three grub rebuilds on my computer via boot-repair.i read somewhere to unplug my hard drives does anyone know whats wrong here.I have partitioned the usb stick for uefi ok thanks for any help
regards Ron
I partitioned the usb stick for uefi via gparted

---

### Post by oldfred on 2014-03-26
Your then want a full install on flash drive not the installer.
You need to create gpt partitioning, efi partition and use Something Else or install manually like any install to a second or external drive. You must specify to install grub2 boot loader to the correct drive on the partitioning screen.

 Flash drive to boot in UEFI or BIOS 
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

 Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)

---

