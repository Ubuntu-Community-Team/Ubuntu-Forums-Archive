---
title: "Some USB not detected in Windows 7 (guest OS)"
date: 2010-06-14
forum: Virtualisation
---

### Post by teejay17 on 2010-06-14
I am running Lucid 10.04 32-bit with the newest stable VirtualBox 3.2. My guest OS is Windows 7 32-bit.  It is working pretty well, and some of the USB devices, like the mouse and keyboard, work without a glitch in Windows 7. However, my external HD and iPod are not being detected in Windows. Is there a reason for this? Is it possible to make them "seen" in the guest OS? 
Thanks in advance.

---

### Post by belkinsa on 2010-06-27
You maybe have the open source one.  This the Closed one: [http://download.virtualbox.org/virtualbox/3.2.0/](http://download.virtualbox.org/virtualbox/3.2.0/)  That might fix your problem (and mine).

---

### Post by teejay17 on 2010-06-28
> **Mechafish said:**
> You maybe have the open source one.  This the Closed one: [http://download.virtualbox.org/virtualbox/3.2.0/](http://download.virtualbox.org/virtualbox/3.2.0/)  That might fix your problem (and mine).
Did it work?

---

### Post by pricetech on 2010-06-28
The OSE version, which would be what you installed if you used Synaptic or Software Center, doesn't support USB.  Your keyboard and mouse are different from a USB drive.

The PUEL version does support USB.

---

### Post by teejay17 on 2010-11-09
> **pricetech said:**
> The OSE version, which would be what you installed if you used Synaptic or Software Center, doesn't support USB.  Your keyboard and mouse are different from a USB drive.

The PUEL version does support USB.

I used the PUEL version (downloaded [[COLOR="Red"]here[/COLOR]]("http://www.virtualbox.org/wiki/Downloads") and not the OSE further down), but I still cannot get USB drives to show up. 10.04 32 bit is the host, and XP is the guest running on VirtualBox 3.2.10.
It would be great if I could get my USB drives to work. 
Cheers

---

### Post by wilee-nilee on 2010-11-10
With the W7 shut down and the usb plugged in, in Vbox W7 hit settings-usb then the + on the right of the screen and choose the usb device.

---

### Post by teejay17 on 2010-11-10
> **wilee-nilee said:**
> With the W7 shut down and the usb plugged in, in Vbox W7 hit settings-usb then the + on the right of the screen and choose the usb device.

Thanks. I finally figured out how to do it; I had to go to 
System>Users and Groups>Manage Groups>and select the VirtualBox properties there so that my username was recognized.

---

### Post by wilee-nilee on 2010-11-10
> **teejay17 said:**
> Thanks. I finally figured out how to do it; I had to go to 
System>Users and Groups>Manage Groups>and select the VirtualBox properties there so that my username was recognized.

Doh, forgot that part, glad your running.

---

