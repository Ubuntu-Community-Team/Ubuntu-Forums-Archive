---
title: "Help with vortual box!!!"
date: 2008-05-24
forum: Virtualisation
---

### Post by mugen-R on 2008-05-24
i got this message when starting my virtual machine please tell me what to do...
[I][COLOR="Red"]VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).[/COLOR][/I]
thanks!!!

---

### Post by jrib on 2008-05-25
Did you try installing the packages the error message asks you to install?

---

### Post by bubba_169 on 2008-05-25
I wrote a short guide [IN THIS POST]("http://ubuntuforums.org/showthread.php?t=735525") about how to install virtualbox successfully. Its in the last post on the page... :D

---

### Post by mugen-R on 2008-05-25
ok i done it ... i run win98se in my virtual machine now but what about drivers(vga,audio,network)where to find which cards virtual box emulates???need help please!!!

---

### Post by 00arthuryu on 2008-05-25
You have to install the guest additions. from devices. you can't install the actual graphic drivers in your machine.

---

### Post by pizpot on 2008-05-26
I fixed it! Here is the scoop: Ubuntu upgraded its kernal from 2.6.24-16 to 2.6.24-17 and -17 is too new for virtualbox. You have to reboot and select the right kernel:

Ubuntu 8.04, kernel 2.6.24-16-generic

I tried the two above it (Ubuntu 8.04, kernel 2.6.24-17-generic, and Ubuntu 8.04, kernel 2.6.24-16-386) but they fail.

If you look in Synaptic and search for virtualbox and scroll down you will see why. I am using Virualbox-OSE. (open source edition)

If someone knows the right way, or wants to just fix the repos then thanks.

---

### Post by FoxHappy on 2008-05-28
> **pizpot said:**
> I fixed it! Here is the scoop: Ubuntu upgraded its kernal from 2.6.24-16 to 2.6.24-17 and -17 is too new for virtualbox. You have to reboot and select the right kernel:

Ubuntu 8.04, kernel 2.6.24-16-generic

I tried the two above it (Ubuntu 8.04, kernel 2.6.24-17-generic, and Ubuntu 8.04, kernel 2.6.24-16-386) but they fail.

If you look in Synaptic and search for virtualbox and scroll down you will see why. I am using Virualbox-OSE. (open source edition)

If someone knows the right way, or wants to just fix the repos then thanks.

Went through everything and needing the 2.6.24-16-generic kernel is my exact problem. So this should solve it for me, however, I am limited by my massive fail linux n00b power. Sooo.... Just how does one install that kernel?

---

### Post by FoxHappy on 2008-05-28
Actually nevermind that. I found all the answers I needed (it's actually super simple) I'll quote it over here too for anyone looking for it. This is from another thread [http://ubuntuforums.org/showthread.php?t=735525](http://ubuntuforums.org/showthread.php?t=735525) 

> **bubba_169 said:**
> The are quite a few programs available ... I like virtualbox but others like qemu (or kqemu which I think is faster)

To install virtualbox open a terminal and type

```
sudo apt-get install virtualbox-ose virtualbox-ose-modules-generic
```

then enter your password and agree to the installation. Afterwards you will need to start the vboxdrv driver by typing:

```
sudo modprobe vboxdrv
```

The last step is to add yourself to the vboxusers group. Go to System->Administration->Users and Groups, click the manage groups button, find vboxusers in the list it should be at the bottom and double click it, tick the box next to your name. Log out and back in again and you should be good to go... :)

That's all you have to do, worked great ^^ thanks a lot

---

