---
title: "Getting Devices And Such Working in Virtual Box"
date: 2007-01-26
forum: The Cafe
---

### Post by Fingerz91 on 2007-01-26
Hey All,

Im sure you've all heard about the GNU virtualization software Virtual Box ([www.virtualbox.org](www.virtualbox.org))

I set up my virtual XP without an issue, but need a little guidance at this point....

I have an external LightScribe drive, and an external USB hard disk, and a printer, all of which need to be utilized in the virtual machine, if possible....

Anyone figured out devices yet?

---

### Post by Fingerz91 on 2007-01-27
Im guessing no?:D 

I guess Ill try some USB filters or something and play around a little

---

### Post by RChickenMan on 2007-01-27
In VMware, running "sudo mount -t usbfs none /proc/bus/usb" in a terminal (and restarting the virtual machine) does the trick.  Not sure if this fix would carry to other virtualization software.

---

### Post by Fingerz91 on 2007-01-27
No good.

This threads still here for anyone who has figured out how to add devices in VirtualBox....

---

### Post by AndyCooll on 2007-01-27
Have you tried the main thread? [ New GPL virtualization software: Virtualbox]("http://www.ubuntuforums.org/showthread.php?t=338931")

:cool:

---

### Post by Fingerz91 on 2007-01-28
I've posted there, yes. Nobody seems to know exactly how to get devices working with VirtualBox....

---

### Post by Fingerz91 on 2007-01-29
> **Fingerz91 said:**
> I've posted there, yes. Nobody seems to know exactly how to get devices working with VirtualBox....

I know how to now!

Just check out this thread..... issue the VBoxManage list usbhost command and you're all set to setup a USB filter

VIRTUALBOX IS AMAZING! No more dual booting for me:D 

[http://www.ubuntuforums.org/showthread.php?t=341740](http://www.ubuntuforums.org/showthread.php?t=341740)

---

