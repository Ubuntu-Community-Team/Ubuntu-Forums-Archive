---
title: "FireWire: Echo Audio Fire 4 not recognized"
date: 2012-11-10
forum: Ubuntu Studio
---

### Post by TheFisherman on 2012-11-10
Hi there,

my Ubuntustudio 12.04 system doesn't recognize the Echo Audio Fire 4 interface.

The FireWire controller is recognized:
lspci | grep FireWire
says:
04:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200A IEEE-1394a-2000 Controller (PHY/Link) (rev 01)

lsmod | grep -i firewire
shows the new firewire stack is loaded.

I checked with my Windows 7 system. Controller is recognized and Windows states it works properly. Echo provides a console program that should recognize the Audio Fire device. Well, it does and it doesn't. For a few seconds it's there, then it's gone again.

So, not the Linux firewire stack seems to be the problem, but somehow the connectivity between the controller card and the device.

Ideas, anyone?

Cheers,

TheFisherman

---

### Post by jejeman on 2012-11-11
Check if there are device node for it
```
ls /dev/fw*
```It should have fw0 (firewire interface) fw1 (firewire device)

---

### Post by TheFisherman on 2012-11-11
> **jejeman said:**
> Check if there are device node for it
```
ls /dev/fw*
```It should have fw0 (firewire interface) fw1 (firewire device)

That's where my firewire setup tends to erratic behaviour. Sometimes both devices are there, sometimes only the interface, sometimes none. I'm trying to detect a pattern. Maybe I missed a detail. Only wondering why Windows behaves the same way as Linux does, which would point to a general connectivity problem.
Will try BIOS properties next.

---

### Post by TheFisherman on 2012-11-28
Yes, as it turns out, it was a connectivity problem. Faulty cable (which, by the way, came with the audio interface). Replaced it and it works.

---

