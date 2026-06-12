---
title: "Can't compile vboxdrv"
date: 2009-06-22
forum: Virtualisation
---

### Post by Novasoft on 2009-06-22
Hey there Ubuntu Forums.

I've been googling around for 3 days now to no avail.

vboxdrv doesn't want to compile! It says that I don't have the linux kernel headers installed, but I do. I've also tried VMWare, but the same problem occurs; it is incapable of compiling the kernel driver.

I could post the installation log of vboxdrv if you want, but it's very long (full of errors.) 

Thanks in advance, Novasoft

---

### Post by HermanAB on 2009-06-22
Howdy,

The solution to this annoying problem, is to install the kernel source and recompile and install the kernel, reboot and then any software including VMware will compile and install properly:
Get your kernel version:

$ uname -a

Run Synaptic search for 'kernel' and install the source for your kernel version.

Now do this:

$ sudo su -
yourpassword
# cd /usr/src/linux
# make mrproper
# make oldconfig
# make bzImage
# make modules
# make modules_install
# make install
# reboot

Now run the Vmware configuration thing again.

---

