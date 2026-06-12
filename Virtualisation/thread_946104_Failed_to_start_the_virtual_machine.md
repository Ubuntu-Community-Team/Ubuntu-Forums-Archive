---
title: "Failed to start the virtual machine"
date: 2008-10-13
forum: Virtualisation
---

### Post by johnmata on 2008-10-13
On my notebook computer I have Virtual Box running quite well. On my desktop the results are quite different at this point. On attempting to start up a virtual machine the following pop up error occurs:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..

VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code:	0x80004005
Component:	Console
Interface:	IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

The error message tells me to install the virtualbox-ose-modules package for my kernel. To identify my computers kernel I will open the terminal and execute the following code:

    * $ uname -r

And when I do I get the following reply: 2.6.24-19-generic

In the Synaptic Package Manager I search for VirtualBox and select to download and install the following:

    * virtualbox-ose-guest-modules-2.6.24-19-generic

Despite the fact that I have the driver installed now, the same error remains.  Any advice greatly appreciated.

Cheers,
John

---

### Post by b0b138 on 2008-10-13
try these commands.

sudo /etc/init.d/vboxdrv restart

and if that doesnt help

sudo /etc/init.d/vboxdrv setup

---

### Post by Peter09 on 2008-10-13
I don't think its asking for the guest modules, more the virtualbox-ose-modules.

PC

---

