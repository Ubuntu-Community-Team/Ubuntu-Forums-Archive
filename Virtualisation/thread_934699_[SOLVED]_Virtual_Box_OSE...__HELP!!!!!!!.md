---
title: "[SOLVED] Virtual Box OSE...  HELP!!!!!!!"
date: 2008-09-30
forum: Virtualisation
---

### Post by Cyanide Cloud on 2008-09-30
When I start up my newly created Virtual Machine (Windows XP)
I get...

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

What does this mean and how do I fix this???

I really wanna get Virtual Box running so I can use Pov-Ray without hassle...

"sadface"

---

### Post by squidmaster on 2008-10-12
i've been asking this same question...

---

### Post by Sam on 2008-10-12
Run in a teminal:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
sudo adduser $USER vboxusers
```
Reboot and try again!

---

### Post by Cyanide Cloud on 2008-10-13
I fixed it...  dunno how!

---

