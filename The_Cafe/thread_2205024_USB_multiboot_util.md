---
title: "USB multiboot util?"
date: 2014-02-11
forum: The Cafe
---

### Post by mips on 2014-02-11
I know there is a util out there to write several linux distros to the same usb stick and boot from it but for the life of me I cannot remember the name. I need to write three distros to one usb stick shortly.

---

### Post by sudodus on 2014-02-11
I know two multibooters.

1. Multisystem
2. Yumi

(and my own OBI - One Button Installer, but it uses tarballs, not iso files)

---

### Post by oldfred on 2014-02-11
I make my own. Just install grub to USB flash drive, create new grub.cfg with loop boot entry for each ISO you want to boot.

Its similar to this except for the manual install of grub to flash drive.
 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

To install grub to flash drive it really is one command:

 Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

If you want automatic, I have these links, not checked them recently:

 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Uses grub4dos to boot many ISO and other bootable files
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by C.S.Cameron on 2014-02-11
My favorite is MultiBootUSB.
It is a script that works in Ubuntu, (with grub2).
Once set up it is easy to modify and add distros, etc

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)


Edit:
I have been using it on one 4GB flash drive since it first came out.
Twice a year I drop the new Ubuntu iso on to the drive and edit the grub file to suit.
I do reset the casper-rw persistence partition with each new iso.

---

### Post by monkeybrain20122 on 2014-02-11
multisystem
[http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

---

### Post by SuperFreak on 2014-02-11
I use [Easy2Boot]("http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1") which seems to work with my EFI PC unlike some of the others. It boasts 133 compatible distros and several Windows OSs that can be used on a USB. I presently have about a dozen distros on a USB. Only issue I have had is the ISOs have to be contiguous on the USB and I believe the easiest and perhaps the only way to ensure that is using the associated RMPrepUSB on a Windows PC. It is possible though to load ISOs onto the USB so they are contiguous by downloading them to one's hard drive and then copying them to the USB, I think

---

