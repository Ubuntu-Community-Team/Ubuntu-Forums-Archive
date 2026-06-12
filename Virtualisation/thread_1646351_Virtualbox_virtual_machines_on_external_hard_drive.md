---
title: "Virtualbox: virtual machines on external hard drive die next reboot"
date: 2010-12-15
forum: Virtualisation
---

### Post by fcarramate on 2010-12-15
hi,

I am currently running ubuntu 10.10 clean installation and installed VirtualBox from repo to run windows as guest system.

I can create, install and run windows guest machines but only to the next host system reboot.
If I completely shutdown the host the virtual machines will never be able to boot VMs whose virtual drivers reside on external hard drive again.

In the VM boot process various error messages saying that system32 could not be found or is corrupted.

tha same symptom does  n o t  happen on internal hard drive. So i am guessing that something is dynamic/changes when ubuntu (host system) tries to mount the external USB hard drive, even if I plug it on the same USB port without any other devices connected to other USBs.

I already googled  but this issue seams unique and is happening only to me, not that i am special of course!! LoL

any help, method of debugging, link to other page,... please shoot!

thanks in advance

---

### Post by fcarramate on 2010-12-18
the same symptoms are verified with VMware. 
so i am guessing this a ubuntu related issue.

does anyone knows how VirtualBox looks for USB devices and how are they identified in ubuntu?

---

### Post by Don1500 on 2010-12-18
> **fcarramate said:**
> the same symptoms are verified with VMware. 
so i am guessing this a ubuntu related issue.

does anyone knows how VirtualBox looks for USB devices and how are they identified in ubuntu?

I am having the same type problem:
[LIST=1]
[*]I have a USB drive and it can not be seen in the VirtualBox
[*]I have 2 CD drives, the Virtual box shows only 1 and it doesn't recognize that I have a disk in it.
[/LIST]
Do I need to add drivers? (My virtual box is Windows XP SP3) And I am in the Virtual box now.

---

### Post by Don1500 on 2010-12-20
> **Don1500 said:**
> I am having the same type problem:
[LIST=1]
[*]I have a USB drive and it can not be seen in the VirtualBox
[*]I have 2 CD drives, the Virtual box shows only 1 and it doesn't recognize that I have a disk in it.
[/LIST]
Do I need to add drivers? (My virtual box is Windows XP SP3) And I am in the Virtual box now.

I was able to get the CDs working, but I still cant see the USB drives.
Funny though, I have a HP C4180 printer and I can see the SD card slots just fine. But no action  on the Pen Drives or my SS USB 120 Gig hard drive. IT also doesn't show my MP3 Player when plugged into the USB.

---

### Post by fcarramate on 2010-12-23
my issue is not like yours, in fact is very different!
you might wanna give a look in shared folders feature just as an workaround to you problem.

My problem is that all the VMs i have installed in a USB external hard disk will fail next time the system is shutdown and started.

---

