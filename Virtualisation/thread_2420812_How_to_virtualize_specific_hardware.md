---
title: "How to virtualize specific hardware?"
date: 2019-06-11
forum: Virtualisation
---

### Post by webmiester on 2019-06-11
How do we virtualize specific hardware?  For instance, I need my computer to make a virtual Core2Duo running with a Hitachi CD-rom drive?  My host computer is a core i3 with no CD drive.  Is this possible?

---

### Post by TheFu on 2019-06-11
It is highly unlikely that either of those items is important for moving physical machines into a virtual machine.  OSes just don't care about those things.

Linux systems would care about an external CNC machine or a specific RAID card, but not a CD or CPU.  Emulating a USB license key dongle can't be done, but you can setup exclusive USB passthru to the actual dongle.

Windows systems are pickier, but there's a sysprep command to tell it you'll be moving to all new hardware.

Anyway, if you use KVM and libvirt, then you can pick the CPU family you want to emulate.  For a specific optical drive, I don't know how to emulate one of those - it is have, not in 20+ yrs - been an issue.

It isn't worth the time to tell you how to accomplish these things since it is trivial to just try it and you'll know.  It isn't like you risk anything other than a copy of the storage used.

Try it. See what works and what doesn't. THEN ask questions.  I suspect you are wasting time worrying about things that won't be issues at all - there probably are other things you should worry about - like any proprietary GPU drivers. Disable/switch to F/LOSS drivers  before moving inside a VM.  Inside a VM, the real hardware doesn't get seen by the guest OSes without lots of effort.  With a Core i3, I doubt that system can handle PCI passthru, so if you need something like that, you'll likely need a higher end computer.  Same for laptops.  Passthru capabilities usually aren't part of laptop systems.

---

### Post by webmiester on 2019-06-11
Thank you.  Ill go try what you say.  But yes, it is a Windows Server 2002 machine and the application we are running only works with this OS.  Both the OS and the application are no longer supported by their vendors/developers, so I am in the dark as to how to preserve our precious data.

So far, we have been trying to make an image of the hard disk, but the image keeps failing.  I do hope we come up with a solution soon.  Thanks.

---

### Post by Skaperen on 2019-06-11
the boot images for Ubuntu and many other Linuxes these days can function as a CD-ROM, DVD-R, or a hard drive image (what you get with a USB memory stick).  if you want to boot an Ubuntu install in Linux, just make a copy of the "ISO" file, configure is as a hard drive, and boot from that device.  many virtualizers can emulate a generic CD-ROM that way, too (BTDT often). *shrug* if booting something else or running Windows on it.

---

