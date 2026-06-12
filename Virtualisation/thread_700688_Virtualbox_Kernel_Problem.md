---
title: "Virtualbox Kernel Problem"
date: 2008-02-18
forum: Virtualisation
---

### Post by snow_56767 on 2008-02-18
Hi,
    I've just installed VirtualBox and I have a Vista drive all setup but
VirtualBox Gives me the same error no matter what modules I have 
installed.
The error is:
```

VirtualBox kernel driver not installed.
The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason.
 Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```
I also Have tried many different commands to fix this but apparently 
the device /dev/vboxdrv doesn't exist.
Help please!!!!!

---

### Post by snow_56767 on 2008-02-29
Hi,
   I fixed my kernel problem by building virtualbox from the sources and got the kernel driver to work but now virtualbox can't read any of my boot mediums.
I get this message:
```
FATAL: could not read from boot medium! system halted!
```
I would really like it if you guys could help me. Thanks!!!!

---

### Post by dfmalh on 2008-06-05
Hi snow_56767,

I have had exactly the same problem... 

All of a sudden a krnel problem last night, I "re-installed" VBox and that solved the kernel problem. 

But now I cant boot my Virtual drive... I also have the same Error message. "System halted...."

Any help would be appreciated. I really need to get onto that drive!

---

### Post by dfmalh on 2008-06-05
Why does one always seem to figure out what is wrong just after you post a thread...? Hmmmm :)

Anyway, I solved the problem, and here is how/or what I had to do.

Once I opened VirtualBox, I can see my "Drive" that is "Powered off". You can select it, and then click on the Settings tab. Go to the settings for the "Hard Disks" (select on the left column). Then "Add Attachment" Now your drive is added (IDE Primary Master). That is it, you can boot into whatever OS you have on the virtual drive.

Hope this helps someone.

---

