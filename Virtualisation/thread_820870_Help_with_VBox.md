---
title: "Help with VBox"
date: 2008-06-06
forum: Virtualisation
---

### Post by zalym on 2008-06-06
Hi,

My installation went through fine.  I could create an image, but when I try to start it, I get the following error:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

My kernel is 2.6.24-18-generic

When I tried to get the status of the the driver, using 
/etc/init.d/vboxdrv status
It returned  * VirtualBox kernel module is not loaded.

/etc/init.d/vboxdrv start 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.

So I got the latest from virtualbox.org, 1.6.2 and tried to install it thru the UI, but it failed.  

What should I do to get this started?

---

### Post by zalym on 2008-06-06
Hi,

My installation went through fine. I could create an image, but when I try to start it, I get the following error:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

My kernel is 2.6.24-18-generic

When I tried to get the status of the the driver, using
/etc/init.d/vboxdrv status
It returned * VirtualBox kernel module is not loaded.

/etc/init.d/vboxdrv start
* Starting VirtualBox kernel module vboxdrv
* No suitable module for running kernel found.

So I got the latest from virtualbox.org, 1.6.2 and tried to install it thru the UI, but it failed.

What should I do to get this started?

---

### Post by bodhi.zazen on 2008-06-06
zalym : In case you missed it :

Your problem is with VirtualBox and your question does not belong at the end of a long thread on VMWare.

I moved it to a more visible location.

---

### Post by zalym on 2008-06-06
Thx Bodhi.

---

### Post by Matthew Wiebelhaus on 2008-06-06
TRY THIS: > sudo /etc/init.d/vboxdrv setup in terminal.

IF IT DOESN'T WORK LOOK BELOW

Uninstall VirtualBox and then install it following my guide in my signature. Make sure you have latest Linux kernel available via updates installed before you do my guide.

---

