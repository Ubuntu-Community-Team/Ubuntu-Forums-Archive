---
title: "host usb not working with virtual box"
date: 2010-07-22
forum: Virtualisation
---

### Post by craig.brisbane on 2010-07-22
Hi

I am running Ubuntu 10.04, with virtualbox 3.2.6 using windows 2000 as a guest. 

I got usb in the guest working - can access my usb flash drive. When I access the flash drive in the guest os (windows 2000) it is not available on the host system. When I close virtual box or unmount the usb in the guest - the flash drive is again available on the host system.

Is there any way to have it available on both?

Tks Craig

---

### Post by craig.brisbane on 2010-07-23
Bump. any suggestions appreciated

---

### Post by mdramige on 2010-07-23
From my own experience I'm pretty sure this isn't possible. It would be pretty messy to synchronize reads/writes to the drive if both OS's were doing them at the same time. Are you trying to share files between the two OS's via the flash drive?

---

### Post by sh1ny on 2010-07-23
> **craig.brisbane said:**
> Hi

I am running Ubuntu 10.04, with virtualbox 3.2.6 using windows 2000 as a guest. 

I got usb in the guest working - can access my usb flash drive. When I access the flash drive in the guest os (windows 2000) it is not available on the host system. When I close virtual box or unmount the usb in the guest - the flash drive is again available on the host system.

Is there any way to have it available on both?

Tks Craig

Short answer : no.
Long answer : no.

:D

---

### Post by TheFu on 2010-07-23
> **craig.brisbane said:**
> Is there any way to have it available on both?

The no, no answer is true, if you use virtualbox USB methods.

But if we take a step back and think what you are really trying to accomplish, there are other options. Have you considered sharing the device from 1 of the OSes using normal file sharing methods like samba or Windows Sharing?  I can't see why that wouldn't work.  You may be able to use virtualbox folder sharing from the host side as well, just be certain to avoid the USB stuff.

---

### Post by craig.brisbane on 2010-07-23
Hello all

Tks for the assistance. I will give the sharing a go TheFu.

Have tried the sharing option as suggested by TheFu, this appears to work.

---

