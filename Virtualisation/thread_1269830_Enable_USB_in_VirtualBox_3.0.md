---
title: "Enable USB in VirtualBox 3.0"
date: 2009-09-18
forum: Virtualisation
---

### Post by beatlesfan94 on 2009-09-18
I'm trying to enable USB on my VirtualBox VM, and I can't figure out how to enable it! I'm running Windows XP as the guest, I installed Guest Additions (twice, in fact), I've added myself to the vboxusers and edited text files that I don't know a clue about. And yes, I have set up filters for my devices - one Canon printer and one thumb drive.

I did hear about the open source version not having USB support, but I downloaded VB from the official website and in Synaptic, it says I have virtualbox-3.0 INSTALLED, and the virtualbox-ose package in UNINSTALLED.

Help!!

---

### Post by beameup on 2009-09-18
The way I got it to work was to plug the device in, and then in settings, added a device filter for it. Couldn't get it to work with a generic filter but it should; and I haven't tried again because my device filter worked.

---

### Post by beatlesfan94 on 2009-09-18
> **beameup said:**
> The way I got it to work was to plug the device in, and then in settings, added a device filter for it. Couldn't get it to work with a generic filter but it should; and I haven't tried again because my device filter worked.
Did you use the filter that has the name of the device? And did you enable USB 2.0?
I just can't find the problem when I got to Devices > USB Devices from the VM window, everything is grayed out.

---

### Post by beameup on 2009-09-18
Right, 2.0 enabled and the device named filter. I may have doe it before I opened the machine, but not sure.

---

### Post by beatlesfan94 on 2009-09-18
> **beameup said:**
> Right, 2.0 enabled and the device named filter. I may have doe it before I opened the machine, but not sure.
I'm going to attempt to re-install the package. For some reason, another install on my laptop somewhat supports USB. I have a filter set up for a flash drive and it appears on the USB Devices list, but it doesn't appear in My Computer. It does remove the icon from my Ubuntu desktop, though.

---

### Post by beatlesfan94 on 2009-09-18
Still doesn't work. Even tried installing 2.2.4.

---

