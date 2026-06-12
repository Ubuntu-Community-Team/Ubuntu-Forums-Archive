---
title: "virtualbox problem"
date: 2008-08-09
forum: Virtualisation
---

### Post by lmtraub on 2008-08-09
I have installed virtualbox on my Ubunto 7,10 box, but I'm having trouble getting it to run.

I created a Windows VM but I can't get it to start. Here is the error I get:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

According to the Synaptic Package Manager the following packages are installed on my computer:
vitualbox-ose
virtualbox-ose-modules-2.6.22

uname -r shows the following:
2.6.22-14-generic

What else do I need to do to get it to work?
all ready a member of vboxusers

---

### Post by dje on 2008-08-09
open a terminal (applications >> accessories >> terminal) and run:
```
sudo /etc/init.d/vboxdrv start
```

dje

---

### Post by tvtech on 2008-08-09
install xensource instead !

---

### Post by lmtraub on 2008-08-10
I can now get it to start, thanks. But I do get the following error:


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I am a member of the vboxusers group. Would it matter if my user name is different to the full name given during installation?

---

### Post by lmtraub on 2008-08-10
What's the easiest way to get and install xen?

---

