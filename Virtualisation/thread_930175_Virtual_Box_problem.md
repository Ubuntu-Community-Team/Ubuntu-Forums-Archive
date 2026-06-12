---
title: "Virtual Box problem"
date: 2008-09-25
forum: Virtualisation
---

### Post by melp57 on 2008-09-25
I keep getting the following error when I try to start virtual box:
(trying to run DML(dam small linux)

What else do I need to install?

Here is the message I get.........

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by patrickballeux on 2008-09-25
You did not install the module kernel...  


You need to install virtualbox-ose-modules-generic.


then, you need to load it upon starting (if it does not by itself by putting

vboxdrv

in the /etc/modules file...

Manually you can do:

> sudo modprobe vboxdrv



And you need to be in the vboxusers group also...  (Log out, log in and it should work...)

---

### Post by Sef on 2008-09-25
moved to virtualization thread.

---

### Post by nusra on 2008-09-25
write uname -r in console
n now u can see your version system....
usually this problem code is not compatible in your system...
visit virtual box site n download new version(about 33Mb).....
if u finish download uninstal VBox old version n install new version...
n your problem finish...:)

---

