---
title: "Help With Virtual Box Module"
date: 2008-04-30
forum: Virtualisation
---

### Post by seiya5 on 2008-04-30
im useing ubuntu studio, and was trying to get virtual box to work.
last night it did no problem; with the exception that it wouldnt recognize the mouse. But today it wont work at all. I installed Windows XP as a virtual machine in virtual box. Ive looked around the forum, and tried several things, with nothing getting better:(

i get this message:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 i reinstalled :
virtualbox-ose-modules-generic
linux-image-2.6.24-16-generic
over again from synaptic still nothing.

---

### Post by bluefrog on 2008-04-30
a good chance you have not followed what the installation told you.

you must add your user to the vboxusers group then log out/log on

---

### Post by seiya5 on 2008-04-30
> **bluefrog said:**
> a good chance you have not followed what the installation told you.

you must add your user to the vboxusers group then log out/log on

i've added the my user name to vboxusers group, but dont think ive done that.

would you recommend uninstall and do it over?
or would there be a better way?


re-installed, working now. Thanks bluefrog!!!

---

