---
title: "Expand disk space of Ubuntu in vmplayer"
date: 2010-01-15
forum: Virtualisation
---

### Post by vivalost on 2010-01-15
Hi,
I use vmplayer 3 ([http://www.vmware.com/de/products/player/](http://www.vmware.com/de/products/player/)) to run Ubuntu ([http://gisvm.com](http://gisvm.com)).
The Ubuntu guest system has 8GB, I need more. In vmplayer I expanded disk space of this vm to 15 GB. In Ubuntu i can see the 7 GB added with the gparted tool as unassigned disk space. I would like to add them to the existing hard drive in the vm.

So far I tried formating the available space with gparted, but than I can not mount it (following the Ubuntu Help for "Mounting and Unmounting Devices")

I appreciate your help. I am not confident with terminal commands.
Than you

---

### Post by fouadatmeh on 2010-01-15
Hello,
to guide you in the right direction, you can use:

> resize2fs /dev/sda1 15G

*where sda1 is the partition you want to resize (you have to unmount it first)
**the extra space after the partition has to be unpartitioned..

I haven't used this in a production system yet, so be careful..

---

### Post by vivalost on 2010-01-21
sda1 is the boot partition and therefor I can not unmount it

---

### Post by fjgaude on 2010-01-21
Boot from a liveCD and then run the commands of the drive.

---

