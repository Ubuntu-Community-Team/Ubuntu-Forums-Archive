---
title: "qemu on Gutsy - FATAL: not a bootable disk"
date: 2007-10-31
forum: Virtualisation
---

### Post by nicolasdiogo on 2007-10-31
hello folks,

i am using QEMU to run a gutsy server, or rather trying to.
to start the server i installed all those components required by qemu and qemu launcher.
i have used qemu launcher to install the server without any problems.
however, when trying to boot the server i get the following message:

Boot from hard diks 0 failed
FATAL: not a bootable disk

and Nothing happens. i am setting hard disk 0 to be the boot disk in qemu launcher, and this where i have installed the OS.

but i am puzzled by this error.

PC spec:
AMDx2
2gb RAM


i would really appreciate some assistance.

many thanks

---

### Post by bodhi.zazen on 2007-10-31
hard to say, but I would start by booting (qemu) with a live CD and checking it out. 

Suggestions :

1. Boot the server install CD, go to recovery mode, and install the generic kernel (rather then the server kernel).

2. Install / configure GRUB.

---

### Post by nicolasdiogo on 2007-11-20
hi,

i have tried your suggestion but it did not work after a number of attempts i am using VMware again.

thanks

---

### Post by vouzico on 2008-04-04
Hello nicolasdiogo,

try this one : 

sudo kvm -m 256 -boot d -cdrom /path/to/your/iso.iso /path/tou/your/img.img

It seems that the virtualized BIOS tries to boot first from the non-existing hard drive without taking the CD ROM in account.

It worked for me, it should work for you ;)

---

### Post by dilbert_side on 2008-09-13
well, I found a solution, and my 2 cents it is related to the MBR win try to boot from.

the previous tip is interesting to tweak the command line, but has been useless unfortunately.
After multiple trials and errors, I retrace my workaround:

1) download [http://www.ibiblio.org/pub/Linux/system/recovery/tomsrtbt-2.0.103.ElTorito.288.img.bz2](http://www.ibiblio.org/pub/Linux/system/recovery/tomsrtbt-2.0.103.ElTorito.288.img.bz2), uncompress, 

2)attach it as an iso floppy to your VM

3) boot on that floppy 
4) run fdisk /dev/xxx on the main disk you want to boot winxxx
5) activate dos mode (command c)
6) activate boot on the (command a)
7) halt your virtual machine
8 ) "remove" your virtual floppy

you should be able to start your iso/cdrom and reboot on it to end the process install

this worked for me after trying to install JeOS and failing with grub pointing to a win partition

---

