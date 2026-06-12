---
title: "Check Raid status"
date: 2011-01-20
forum: Server Platforms
---

### Post by xirochanh on 2011-01-20
Sorry if I post is in wrong place.
I've installed Ubuntu 10.10 on my server box with RAID1 configured, I'm sure it's hardware raid, not software raid.
My machine's running fine now. My concern is: how to check the configuration of my RAID1, how to check status of it?

Thank you,

---

### Post by xirochanh on 2011-01-20
I'm kind of confusing about raid knowledge now, don't know if mine is hardware one.
Basically, it's an on-board embedded  megaraid, I create the raid array in BIOS with megaraid utility, then installed ubuntu normally on the array(without any further driver installation)

#lspci show me this:
 Intel Corporation 82801 SATA RAID Controller

I'm supposing that my raid1 array is configured well, then how can I monitor/check its status now?

---

### Post by psusi on 2011-01-20
Unless you paid like $300+ for a hardware raid controller, then it isn't hardware raid.  The cheaper cards and motherboard built in raids are fake.  Add a -v to the lspci and see what driver is bound to the device.

---

### Post by kgatan on 2011-01-21
Im not 100% sure on this but if its hardware raid the "raid" is done outside linux.
Linux just recognise the raid as a device.

You often configure and check status of the raid during bios boot.

But maybe thats just mb built in fake hw raids?

---

### Post by paulisdead on 2011-01-21
Do you see anything from LSI in your lspci?  They're the ones with the Megaraid series, so maybe that's it.  There are some motherboards that have used their chips, so it could be in there.

If this an LSI RAID card built onto the mobo, then you'd need their MegaCli (MegaRaid) utility to check the status, or make changes on the fly from inside the OS.  I think you can find it on the LSI site, just be sure to get the right one, 32 or 64bit.

The context for it is a real bitch to use, though.  There was a java GUI to manage LSI cards that I've used in the past on a linux box, too.

If it's on the builtin intel chipset, ya it's fakeraid.  It'll still use your CPU to handle RAID operations.  Fakeraid is generally on motherboards, but a lot of add in cards have it too.  It's basically just a bios to configure a raid set, and a driver that windows uses just to install onto there, the CPU still has to do all the heavy lifting.

---

### Post by Vegan on 2011-01-21
I like those PCI Express x8 RAID cards, super fast and never load a CPU more than a DMA to send it data.

Cheap cards and motherboard based RAID are useless. You need a specialized device to speed up RAID6.

---

### Post by xirochanh on 2011-01-26
Hi bros,
lspci -v shows this:
------------------------------------------------------------------------------------
RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev0 5)
        Subsystem: Super Micro Computer Inc Device 0605
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 53
        I/O ports at c400 [size=8]
        I/O ports at cc00 [size=4]
        I/O ports at c880 [size=8]
        I/O ports at c800 [size=4]
        I/O ports at c480 [size=32]
        Memory at fb4f8000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] SATA HBA v1.0
        Capabilities: [b0] PCI Advanced Features
        Kernel driver in use: ahci
        Kernel modules: ahci
------------------------------------------------------------------------------------
From your comments, I believe mine is fakeraid.
I tried megacli tool, every commands I type just return "Exit Code: 0x00"

I can configure the raid array (MegaRaid Menu), see the status well on BIOS, but the thing is I put my machine in a data center, so, can not see BIOS screen. And also, I like to monitor the hard disk status without stopping the machine, it hosts some web sites.

---

### Post by psusi on 2011-01-26
Yep, you have a fake raid.  Linux will see the individual disks and should create a raid device to combine them in /dev/mapper/ with the dmraid utility.  Unless you need to dual boot with windows, you should not use the fake raid support since it is not as robust; use mdadm Linux software raid instead.

---

