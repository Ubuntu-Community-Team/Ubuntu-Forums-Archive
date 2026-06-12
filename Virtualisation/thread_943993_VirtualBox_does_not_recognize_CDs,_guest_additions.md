---
title: "VirtualBox does not recognize CDs, guest additions, or flash drives"
date: 2008-10-10
forum: Virtualisation
---

### Post by zephyrcat on 2008-10-10
I am using VirtualBox on Ubuntu 8.04 to run 8.10. I need to get a (fairly large) file out of the virtual machine. I first tried putting in a DVD. Unfortunately, I cannot get it to recognize that a DVD has been put in (although the host does recognize it). Then I tried to use my USB flash drive, which caused an error:

```
Failed to attach the USB device Patriot Memory [0110] to the virtual machine

Not permitted to open the USB device, check usbfs options.

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

Finally, when I tried to install the guest additions (by going to the devices menu), nothing happened.

What do I do?

---

### Post by overdrank on 2008-10-10
Moved :)

---

### Post by zephyrcat on 2008-10-17
Anyone?

---

### Post by Shazaam on 2008-10-18
Go to the Settings menu for the guest. Then go to CD/DVD-ROM and make sure the drive is mounted. Try burning the cd/dvd again.

---

### Post by zephyrcat on 2008-10-19
Thanks! That solved the problem. For anyone who is trying to do the same thing, the trick is to check the box that says Enable Passthrough.

---

