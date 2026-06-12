---
title: "Raid 1 Grub Help"
date: 2009-02-18
forum: Server Platforms
---

### Post by bward on 2009-02-18
I have two hard drives, sda and sdb.  They are partitioned as such so that sd(a,b)1 is 250mb, sd(a,b)2 is 7GB, and sd(a,b)3 is 1GB.  I'm using mdadm to create my raid.  /dev/md0 is /dev/sd(a,b)1 and is to be mounted as /boot.  /dev/md1 is /dev/sd(a,b)2 and is to be mounted as /.  /dev/md2 is /dev/sd(a,b)2 and is to be used as swap.

For the installation of my Ubuntu system, I have boot off of a 8.04 live cd, installed mdadm, created my partitions and raid 1.  I mounted md1 as /mnt/install and md0 as /mnt/install/boot.  I installed the debootstrap and have used that to create a base system in /mnt/install.  I chroot in the system, and have set up the fstab and mtab.  I have installed mdadm and ran mdadm --assemble -s so that the /dev/md devices are created.

At this point, everything seems to be good except for grub.  I'm unable to get grub installed onto /dev/md0 which is mounted as /boot.  When I run grub-install /dev/md0 I get the following error message: 
"sync does not have any corresponding BIOS drive. You can run grub-install on your RAID device [/dev/md0], or you can define [sync] in [/boot/grub/device.map]."
Any help that could be provided at this point would be very helpful.  I have searched google, but have been unable to find an answer that doesn't require using the server or alternative install cd to accomplish this.


I know I can use the server install cd to accomplish this, but I want to be able to do this manually.  When I get this working, my next step will be to encrypt the root file system.

---

### Post by shizzy-t on 2009-02-18
Grub needs to be installed to a phyiscal drive (md0 is a not a really physical device), I would also suggest installing it to both /dev/sda and /dev/sdb and create entries in menu.lst for both drives as well. 

grub-install /dev/sda 

That way if you loose eather drive you'll be able to replace it and reboot the system.

---

### Post by bward on 2009-02-18
I'll give that a try and see if it boots.  

I did install server 8.04 on a VM to see if I could figure out how it is done with the installer.  I noticed that there is no /boot/grub/device.map.  I could not figure out how the installer does it.  Anyone have any insight on this?

---

