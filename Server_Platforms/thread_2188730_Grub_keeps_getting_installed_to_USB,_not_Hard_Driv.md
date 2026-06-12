---
title: "Grub keeps getting installed to USB, not Hard Drive"
date: 2013-11-18
forum: Server Platforms
---

### Post by CrusaderAD on 2013-11-18
I don't know why, but I'm attempting to install Ubuntu Server 12.03.3 64bit to a 128 SSD. Everything goes smooth, but at the end, for some reason, the grub gets installed to the USB drive. So when I reboot without the USB drive plugged in, it doesn't load the operating system. I changed around the defaults in the BIOs and just can't figure this out. Can I load the setup again and choose where grub goes? Any help would be appreciated.

---

### Post by Bashing-om on 2013-11-18
CrusaderAD; Hi !

As I understand it, the default is to install grub onto the USB device in the install process; and yeah, there is an option in that process to direct where grub is to be installed.

As the system is installed, how about installing grub onto the SSD from the liveUSB ?
Boot the liveUSB -> try ubuntu mode -> terminal;
```

sudo mkdir mnt/work
sudo mount /dev/sda1 /mnt/work ##assumes the SSD is device SDA AND that "root" in in that 1st partition, adjust accordingly !
sudo grub-install /dev/sda
sudo umount /mnt/work

```
reboot into the actual install and:
```

sudo update-grub

``` just to ensure all is in order.

[INDENT][INDENT]workie great last long time ?
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-11-18
Are you using auto install? That defaults to install grub2's boot loader to sda, but some BIOS may promote the flash drive to sda. Then grub installs to flash drive.
Grub also remembers the device it installed to. You may want to check that to make sure on a major update that grub reinstall boot loader correctly or then you may have issues.

You can just install grub to sda (if that is correct drive) from inside a working install.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

   #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by CrusaderAD on 2013-11-19
> **oldfred said:**
> Are you using auto install? That defaults to install grub2's boot loader to sda, but some BIOS may promote the flash drive to sda. Then grub installs to flash drive.
Grub also remembers the device it installed to. You may want to check that to make sure on a major update that grub reinstall boot loader correctly or then you may have issues.

You can just install grub to sda (if that is correct drive) from inside a working install.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

   #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

This did it, thanks!

---

