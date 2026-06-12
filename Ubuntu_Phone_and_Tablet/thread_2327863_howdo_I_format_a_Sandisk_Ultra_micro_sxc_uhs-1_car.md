---
title: "howdo I format a Sandisk Ultra micro sxc uhs-1 card?"
date: 2016-06-15
forum: Ubuntu Phone and Tablet
---

### Post by Old Jimma on 2016-06-15
Hi Community:

I bought a 64GB Sandisk Ultra micro sxc uhs-1 card for my tablet.

I put it in the reader slot and it would not mount.

I removed it, and tried to format it with my regular Ubuntu 14.04 desktop.... it says this card is read only.

I tried using gparted.... that doesn't work ... it says the card is read only?

How do I get that card formated and read/writable for my tablet?

Thanks,
Old Frustrated Jimma

---

### Post by ajgreeny on 2016-06-15
Does the card have a hardware switch on the side which is set to read-only and therefore stops you writing to it?

Can you try it in another card reader or computer to check it?

---

### Post by sudodus on 2016-06-15
[SD/SDHC/SDXC Specifications and Compatibility](http://kb.sandisk.com/app/answers/detail/a_id/2520/~/sd%2Fsdhc%2Fsdxc-specifications-and-compatibility)

> SD Extended Capacity (SDXC&#8482;) card is an SD&#8482; memory card based on the SDA 3.0 specification.

SDXC capacities range from 64GB to 2TB

Default Format: exFAT

Because SDXC uses a different file system called exFAT and it works differently than standard SD cards, this new format is NOT backwards compatible with host devices that only take SD (128MB to 2GB) or host devices that only take SDHC (4GB to 32GB). Most host devices built after 2010 should be SDXC compatible.

To ensure compatibility, look for the SDXC logo on cards and host devices (cameras, camcorders, etc.).

NOTE: Internal card readers on laptops from 2008 and prior may NOT support SDXC cards. SDXC cards will work in SDHC compatible readers (not SD readers) if the computer OS supports exFAT. For more information on exFat see: Operating Systems that support the exFAT File System

There may be compatibility problems with ***old hardware***, and because of the **exfat** file system.

---

### Post by mily2 on 2016-06-15
Have you tried in Vfat?
Jose108 it works well without problems: [http://ubuntuforums.org/showthread.php?t=2324480](http://ubuntuforums.org/showthread.php?t=2324480)

---

