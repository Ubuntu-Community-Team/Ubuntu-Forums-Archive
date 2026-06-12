---
title: "Install Ubuntu"
date: 2019-12-21
forum: Ubuntu, Linux and OS Chat
---

### Post by P-I H on 2019-12-21
A week ago I wrote this thread about Ubuntu 18.04 update.
 [https://ubuntuforums.org/showthread.php?t=2433000](https://ubuntuforums.org/showthread.php?t=2433000)
My main problems was that an update of grub made the installation unbootable and that ubiquity don't allow you to select the installation disk for grub, see this bug 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I will update my computer with a new motherboard and use NVme disks that are fixed to the motherboard with screws and I want to be in control of booting the computer.
I think I'm able to use rEFind Boot Manager as a solution to my problems.
To verify I made an installation of Ubuntu 19.10 on an 16 GB USB memory by following this instruction in the Linux Mint forum.
 [https://forums.linuxmint.com/viewtopic.php?f=42&t=287353#p1590696](https://forums.linuxmint.com/viewtopic.php?f=42&t=287353#p1590696)

The USB memory booted fine on my main system and showed a menu similar to the picture below from the rEFind web page
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

I'm able to select which system to boot, the 19.10 system on the USB memory (/dev/sdc), the 18.04 system on /dev/sda, the 20.04 system on /dev/sdb. 
The main 19.10 system on /dev/nvme0n1 is available from the grub menu when booting to /dev/sda. I suppose this is because I played around with  the installation and had to use Boot-Repair from the 18.10 system to rescue the main 19.10 system.

---

### Post by oldfred on 2019-12-21
The issue is Ubiquity, not grub2. 
You can reinstall grub to any drive. This is why many need or use Boot-Repair as it just lets you choose where to reinstall grub. Or you can do it manually.

Some like rEFInd. I use it for emergency boot.
But again you are selecting where to install it. Ubiquity & its bug then are not involved.

Most UEFI systems that support UEFI & NVMe drives have a UEFI setting somewhere to turn off a hard drive. Mine has [disabled] as a drive option. Then ubiquity will not see another drive. Still another work around as Ubiquity in BIOS mode lets you choose where to install & it works.

I have installed Debian & Fedora and both let me choose to install grub to my sdb drive's ESP, so my main working install in sda was not used, even though originally mounted to boot ISO using grub's loop mount.

---

### Post by P-I H on 2019-12-22
Thanks for the information.
It's hard to understand how to create the boot or repair the boot partitions.
As I understand the only way to to install an Ubuntu Gnome installation is to use Ubiquity. Perhaps it's possible to use the server installer, but then you face a lot of customization.
I have tried to use Gparted to clear the boot flag and to physical disconnect hard drives and both aren't always successful.
My present motherboard, MSI Tomahawk B350, don't have the feature to turn off hard drives.

---

### Post by oldfred on 2019-12-22
Then you can use the work around posted in the bug report. I found I can unmount the ESP at the screen where you put in password and mount whatever ESP you want, and then after install update fstab with correct ESP.
 
Or you can not install grub at all during install and manually install from live installer.
Or use Boot-Repair advanced mode to install or reinstall grub to drive you specify. 
Or use chroot to install grub.

---

