---
title: "Memory Recognition in Server"
date: 2006-04-03
forum: Server Platforms
---

### Post by dmckenna on 2006-04-03
We are running Breezy Badger Server on a Dell Server with 2 Dual Core Processors and 4Gb of RAM.

When you look at the RAM in System Monitor it only recognizes 3Gb of RAM

Is there a limit on how much RAM it will recognize or a way of making it recognize the extra RAM.

I would appreciate any assistance.

---

### Post by LordHunter317 on 2006-04-03
You may, depending on PCI configuration, have to enable a 64G HIGHMEM kernel.  On ubuntu, this means building it yourself AFAIK.

---

### Post by dmckenna on 2006-04-04
Thanks for your response. 

Do you or anyone else have instructions on how to go about doing it?

---

### Post by coolvik on 2006-04-06
Hi,

I had the same problem aswell. Check this guide: [http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

---

### Post by drakkan on 2006-04-07
look at this link, maybe you have a buggy motherboard:

[http://support.intel.com/support/motherboards/server/sb/cs-010458.htm](http://support.intel.com/support/motherboards/server/sb/cs-010458.htm)

---

### Post by LordHunter317 on 2006-04-08
No, he doesn't.  There isn't a motherboard on earth that will let you use 4 GiB of physical RAM and PCI devices at teh same time without using PAE (i.e., 64 GiB Highmem)

Why?  Because the PCI devices have to be mapped somewhere in physical memory, and if you don't have PAE enabled, they have to be mapped within the first 32-bits of the linear address space, or under 4GiB.

Now, some motherboards cannot remap the PCI devices above the 4GiB boundary, but you'd still require PAE.

---

### Post by PokerFacePenguin on 2007-11-18
> **LordHunter317 said:**
> No, he doesn't.  There isn't a motherboard on earth that will let you use 4 GiB of physical RAM and PCI devices at teh same time without using PAE (i.e., 64 GiB Highmem)

Why?  Because the PCI devices have to be mapped somewhere in physical memory, and if you don't have PAE enabled, they have to be mapped within the first 32-bits of the linear address space, or under 4GiB.

Now, some motherboards cannot remap the PCI devices above the 4GiB boundary, but you'd still require PAE.

Great thread! 

Here is my config

CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set


My Question:

Do I comment out HIGHMEM4G=y ?

Do I uncommnet and set HIGHMEM64G=y?

I am just trying to get all four gigs of my memory to show up for the party..

Will setting these options make my system run more effiiciently or will it screw up other things regarding the PCI devices.  The only card I have in this thing is a measly 256MB video card.

---

