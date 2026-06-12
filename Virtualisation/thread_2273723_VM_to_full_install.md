---
title: "VM to full install?"
date: 2015-04-15
forum: Virtualisation
---

### Post by pantera989 on 2015-04-15
At the moment I'm running ubuntu as a VM to see if it is possible to get all the software I want working. If it works out, is there a way to take my VM and and use it without a VM, or at-least sync all my settings to a fresh install?

---

### Post by TheFu on 2015-04-15
Yes to both.  There are many different ways to accomplish it.  It isn't like Windows where you get to fight with licenses tied to BIOS on specific hardware.  

[http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) explains a few ways.  

To move a HVM Linux install to a physical install, here's the high-points:
* remove any "guest additions" from the VM
* create the partitions you want on the new HDD - probably want some for /, /home and swap as a min. Read a few how-to guides to see of you want /boot and/or /var separate too.
* replicate all storage in the VM to the physical disk(s) and partitions using a live-boot of your favorite distro.  Some tools that can do this are partimage, ddrescue, clonezilla, or any backup tool - rdiff-backup, rsync. There are many other options. I'd probably use **rsync**
* Still using the live-boot, mount the partition which contains /etc. Then edit the following files for the new partition locations:
** /etc/fstab  # you'll want to understand this well. The manpage and many how-to guides exist
** delete /etc/udev/rules.d/70-persistent-net.rules  # it will be recreated automatically at boot
* Still using the live-boot, run grub-install /dev/sd-----whatever the device name is for the whole HDD that will boot Ubuntu from the BIOS settings
* Still using the live-boot, run update-grub  # this will find all the installed OSes on all the attached disks and create grub menu items

Reboot into your new install.

That should be it for a BIOS/MBR system.  EFI/UEFI has a few more steps. There is a EFI how-to for Ubuntu, google finds it.

Besides copying all the data, this should take less than 15 min including reboot times.

---

### Post by slickymaster on 2015-04-15
*Moved to the ***Virtualisation*** sub-forum*

---

