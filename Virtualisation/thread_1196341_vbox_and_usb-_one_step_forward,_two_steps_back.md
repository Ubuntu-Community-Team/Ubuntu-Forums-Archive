---
title: "vbox and usb- one step forward, two steps back?"
date: 2009-06-24
forum: Virtualisation
---

### Post by blur xc on 2009-06-24
So, I've made it my mission to get my usb ports to work under vista running in vbox.  I changed the fstab, 10-vboxdrv.rules to 60-vboxdrv.rules, created a usbusers group, made sure I was both in the vboxusers group and the usbusers group...  And finally, I ran 
```
sudo /etc/init.d/vboxdrv setup
```which made it look like it recompiled the vbox kernel...  So, after all that, I rebooted, and started vbox and launced my vista virtual machine.  Once it booted up it added drivers for my usb devices, so I thought all was well, except now my mouse "pointer" won't move.  Now, when I move the mouse around I can see different icons on the screen highlight as if the mouse was hovering over then, and I can click them just fine.  But the pointer just stays put where it was when I started vista.  Needless to say it's a usb mouse...  

Anyway, I'm running Ubuntu 9.04 and vbox 2.2.4.

edit- results from running "VBoxManage list usbhost"

```
Host USB Devices:

UUID:               3acecaea-7084-4864-895c-716976f5afcd
VendorId:           0x09da (09DA)
ProductId:          0x0006 (0006)
Revision:           0.1 (0001)
Manufacturer:       A4Tech
Product:            USB Optical Mouse
Address:            /proc/bus/usb/005/002
Current State:      Available

UUID:               0ff172f0-feed-4573-a02b-41e52c26b137
VendorId:           0x11b0 (11B0)
ProductId:          0x6178 (6178)
Revision:           151.54 (15154)
Manufacturer:       XM-35U
Product:            PRO Reader
SerialNumber:       A00000007
Address:            /proc/bus/usb/002/002
Current State:      Available

```
BM

---

