---
title: "virtual box problem"
date: 2008-04-12
forum: Virtualisation
---

### Post by kursacl on 2008-04-12
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 but l install virtualbox-ose-modules package
Please Help

---

### Post by Jon Monreal on 2008-04-12
> **kursacl said:**
> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 but l install virtualbox-ose-modules package
Please Help

This usually occurs if you haven't changed your settings so you are a vboxuser.

To do this, go to System>Administration>Users and Groups.

Click on your user account, and then click properties. Then go to the Advanced Tab. Change the Main Group setting to vboxusers.

This should fix the problem unless you are getting that error for another reason.

I hope this works for you.

---

### Post by kursacl on 2008-04-13
thank you but it is unsuccesfully.
and l dont find vboxdrv in /etc/init.d/vboxdrv

---

### Post by kursacl on 2008-04-13
l install this
virtualbox-ose modules for linux-image-2.6.22-14-generic
VirtualBox is a free PC virtualization solution allowing you to run a wide
range of PC operating systems on your Linux system. This includes Windows,
Linux, FreeBSD, DOS, OpenBSD and others.

This package provides the virtualbox-ose module (vboxdrv.ko) for the
2.6.22-14-generic kernel.

---

### Post by kursacl on 2008-04-13
l complete this problem thanks jon

---

### Post by cach0rr0 on 2008-05-01
gday gents

I had this problem on gentoo and managed to get around it. Thought I'd share. 

I got this when powering on the virtual machine - id already build the virtualbox-ose modules and all of that...didn't have the init script, same as mentioned here

the "fix" ?

modprobe vboxdrv

sure enough, the VM started right up. I went ahead and added it to /etc/modules.autoload.d/kernel-2.6 (not sure what the equivalent is in Ubuntu)

That should sort it. Hope this is helpful to someone else, couldn't find anyone asking about this on the gentoo forums.

---

