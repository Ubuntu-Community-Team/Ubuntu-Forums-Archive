---
title: "Rack Mounted Servers"
date: 2009-02-15
forum: Server Platforms
---

### Post by Vegan on 2009-02-15
I was looking at building a prototype server based on a Supermicro 16 disk SATA chassis with a generic motherboard and a Promise 16 channel SATA controller (PCIe x8) to run the disks. The controller I am looking at suports RAID 6 so it is less likely to piss off the user when a disk croaks.

The controller is the EX16650 and fits a PCIe x8 slot. It supports SATA and SAS disks.

Can Ubuntu server manage on such a platform idea, I want to be able to have an eagle eye on disks so I can detect problems and report to an administor as well as log SMART data.

I wanted to get some background before I spend my hard earned cash.

:guitar:

---

### Post by songshu on 2009-02-17
as usual check all you hardware components for linux compatibility and simply check what others have to say about it.

otherwise i see no problem

Technical Details for Promise SuperTrak EX16650
System Requirements	Microsoft Windows 2000, FreeBSD, Red Hat Linux, SuSe Linux, Microsoft Windows XP, Microsoft Windows Server 2003, Red Hat Fedora Core, Microsoft Windows Vista, Microsoft Windows Server 2008, Miracle Linux, VMware ESX Server 3.0.2, VMware ESX Server 3.5

---

### Post by Vegan on 2009-03-18
What can't Ubuntu seem to support this any many other RAID cards? I can also finds lots of NICs it does not like too.

---

### Post by BkkBonanza on 2009-03-18
If your'e asking "why"? Then it's because many hardware manufacturers don't see a big market in linux and don't write drivers for it. The ones we do have often come from volunteer open source efforts. Ask yourself when was the last time you dedicated months of time to doing something for free and you'll know why the driver coverage is incomplete. I'm amazed people actually do develop drivers for free.

---

### Post by windependence on 2009-03-19
> **Vegan said:**
> What can't Ubuntu seem to support this any many other RAID cards? I can also finds lots of NICs it does not like too.

Just because the box specifically doesn't say it supports a distro certainly does not mean it won't work. The kernel is what matters and if it supports all of those, it most likely will support Ubuntu.

Are you using this box as a SAN? What will you be serving on it?

-Tim

---

### Post by Vegan on 2009-03-19
> **windependence said:**
> Just because the box specifically doesn't say it supports a distro certainly does not mean it won't work. The kernel is what matters and if it supports all of those, it most likely will support Ubuntu.

Are you using this box as a SAN? What will you be serving on it?

-Tim

I was looking at AMD based boards (low power) and Promise SATA or Supermicro SATA RAID6 controllers in a 16 bay Supermicro chassis which needs 3U per chassis.

I was going to use Ubuntu to make a rack of storage for the LAN. I simply wanted to see if it could scale to racks as far as the eye can see and row after row etc. Far as I can see, that is possible, only issue is RAID and NIC choices.

This would become SAN system with the scaling some corporations seem to indulge in.

---

