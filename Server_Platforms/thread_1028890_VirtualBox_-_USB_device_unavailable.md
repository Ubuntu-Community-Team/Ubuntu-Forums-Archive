---
title: "VirtualBox - USB device unavailable"
date: 2009-01-02
forum: Server Platforms
---

### Post by vze4p6c2 on 2009-01-02
Hello,

I've installed VirtualBox and I see all of my attached devices on the VirtualBox, yet as I attempt to attach a new filter, it says indicates that the status is Unavailable (see attachment).  And obviously, the devices aren't working/available when I attempt to run virtual winXP.

I've followed a bunch of steps to get this thing working, but have no luck.  Any Help is greatly appreciated.

---

### Post by verlyn13 on 2009-03-28
I have the same issue.  I just recently installed Vbox 2.1 with windows XP and the USB devices are unavailable.  It worked just fine a couple months ago with an older version of Vbox.

Ubuntu host
XP guest

---

### Post by papatrpt89 on 2009-04-05
> **vze4p6c2 said:**
> Hello,

I've installed VirtualBox and I see all of my attached devices on the VirtualBox, yet as I attempt to attach a new filter, it says indicates that the status is Unavailable (see attachment).  And obviously, the devices aren't working/available when I attempt to run virtual winXP.

I've followed a bunch of steps to get this thing working, but have no luck.  Any Help is greatly appreciated.

I third this, with an identical setup.  Specifically, Virtualbox 2.1.4, Intrepid 8.10.

Oddly, my printer (an HP Officejet 5600) shows up as available.  All other USB devices show an unavailable state as in the screenshot provided by the OP.

Anyone have any similar experience or solutions?

Thanks!

---

### Post by papatrpt89 on 2009-04-06
I found a solution: adding the following to /etc/fstab and restarting did the trick.

```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

However, I don't understand what this is doing.  I'm relatively low on the Linux learning curve.  I have the conception that /etc/fstab is some configuration file having to do with lots of different kinds of hardware.  If anyone would care to point me to a guide about /etc/fstab and/or explain the function of that line, I would appreciate it!

Thanks.

---

