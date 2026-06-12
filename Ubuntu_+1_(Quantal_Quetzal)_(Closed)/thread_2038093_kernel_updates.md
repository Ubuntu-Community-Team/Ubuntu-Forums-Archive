---
title: "kernel updates"
date: 2012-08-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by rbrick49 on 2012-08-05
yesterday I updated it installed kernel 3.5.0.7 it didnt load on reboot I did update grub still nothing today more updates kernel3.5.0.8 same problem did update-grub  still on kenel 3.5.0.3 
any ideas folks

---

### Post by ronacc on 2012-08-05
what video driver are you using ? I'm nvidia here and had to revert to nouveau to get to desktop and I think the ati fglrx driver is borked right now also .

---

### Post by rbrick49 on 2012-08-05
Hi ronacc 
using xorgxserver amd/ati driver 
not game to touch fglrx
regards Ron
ps dektop is fine just wont load new kenel
heres my grub cfg
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-8-generic
Found initrd image: /boot/initrd.img-3.5.0-8-generic
Found linux image: /boot/vmlinuz-3.5.0-7-generic
Found initrd image: /boot/initrd.img-3.5.0-7-generic
Found linux image: /boot/vmlinuz-3.5.0-3-generic
Found initrd image: /boot/initrd.img-3.5.0-3-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Linux Mint 13 Maya (13) on /dev/sdc1
Found Ubuntu 12.04 LTS (12.04) on /dev/sdd1
done
ron@ron:~$ uname -r
3.5.0-3-generic

---

### Post by ronacc on 2012-08-06
did you try reinstalling grub-pc ?

---

### Post by SpaceCeph on 2012-08-06
Update grub from 12.04 or reinstall with 12.10.

---

### Post by jfernyhough on 2012-08-06
Have you tried the mainline kernel to see if it's kernel-related or Ubuntu-sauce related?

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/)

There were some issues with the sauce recently on some systems. I'd submit a big report.

---

### Post by fjgaude on 2012-08-06
After getting kernel 3.5.0-8, 64-bit, to install, load, the speed using **gtkperf** was 2.67. On the previous kernel it was about 6.0. Wonder what gives... it's like something is being bypassed but will come back later?

EDIT: Oh, I see: we can't for the moment at least drag and drop open windows from one Workspace to another! I'm sure it has to do with why the code is so fast, lots of stuff is left out for now.

---

### Post by rbrick49 on 2012-08-06
my desktop works ok on kernel 3.5.0.3 just couldnt understand why i got these new kernels with update but they wouldnt load just guess its som kind of bug I got reloaded quantal from alpha 2 disk ok again

---

