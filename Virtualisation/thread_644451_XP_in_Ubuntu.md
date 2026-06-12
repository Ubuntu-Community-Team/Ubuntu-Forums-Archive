---
title: "XP in Ubuntu"
date: 2007-12-18
forum: Virtualisation
---

### Post by insert_name_here on 2007-12-18
I used VMWare Converter to convert my existing WinXP installation into a crapload of .vmdk files on my external Hard Drive.  

I'm using VirtualBox to try to load this in Ubuntu (Gutsy, if it matters).  I can't get to the Windows XP progress bar screen.  I get the "Windows didn't start normally, choose between Safe Mode, Last Known Good Config and Start Normally" screen (that's a paraphrase :D ) but none of the options work.  

How do I get it to work?  I assume I haven't given enough info, but I am obviously happy to find whatever info I need to give.

> 

General
Name
Windows XP
OS Type
Windows XP
Base Memory
256 MB
Video Memory
8 MB
Boot Order
Floppy, CD/DVD-ROM, Hard Disk
ACPI
Enabled
IO APIC
Disabled
 

Hard Disks
Primary Master
Windows XP.vmdk [Writethrough, 33.28 GB]




---

### Post by insert_name_here on 2007-12-18
Upon booting with Safe Mode, Windows stops loading at 

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS\System32\Drivers\Mup.sys

if it helps any.

---

### Post by Lord DarkPat on 2007-12-20
Try VMWare Player.

---

### Post by tech9 on 2007-12-20
> **Lord DarkPat said:**
> YOU ARE WHO YOU ARE BECAUSE OF WHAT WE ALL ARE, AND WE ARE WHAT I AM, AND YOU ARE WHAT WE ARE, WE ARE WHAT WE ARE, AND I AM......WHAT?:confused::confused::confused:

huh? :confused:

---

### Post by fjgaude on 2007-12-20
> **Lord DarkPat said:**
> Try VMWare Player.

YOU ARE WHO YOU ARE BECAUSE OF WHAT WE ALL ARE, AND WE ARE WHAT I AM, AND YOU ARE WHAT WE ARE, WE ARE WHAT WE ARE, AND I AM......WHAT?

Sure, we are dealing with Quantum Theory here, and it's been proven over and over again.

---

### Post by toobuntu on 2007-12-20
> System 32\Drivers\Mup.sys

When I have had to boot into Safe Mode, my system appears to hang when loading the mup.sys driver, sometimes for 10-15 min, but eventually will move on and boot into Windows.  Try giving it more time to load....

---

### Post by andrewoftheelves on 2007-12-20
i dont have vmware, but virtualbox. my biggest problem there was not giving the guest os enough memory. so try that maybe?

---

### Post by insert_name_here on 2007-12-20
Thanks, will try them all now (Waiting, more mem, VMware player, in that order)

---

### Post by Shazaam on 2007-12-20
This is a ACPI workaround that helps....

[http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround](http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround)

It can be done in "Safe Mode" in your XP vm. You WILL have to re-activate your Windows vm because it will re-discover hardware. Shouldn't be a problem though. As far as allocated memory for the vm I generally only allocate 1/2 of my physical ram. Any more than that will slow down the whole system (guest and host).
 If you had VMware Server I would recomend installing VMware Tools.......:)

---

### Post by fjgaude on 2007-12-20
Yes, yes, in VMware without VMware Tools things are not good, very slow with mouse and other things.

---

### Post by insert_name_here on 2007-12-20
Hey!!

Got it working in VMWare Server.  How do I install VMware-tools?  

I'm really confused - does it go on the "host" (Ubuntu) or on the "guest" (XP)?

---

### Post by Shazaam on 2007-12-20
It comes with VMware server AFAIK. You install it on the guest. Look in the main VMware window at the top.

---

