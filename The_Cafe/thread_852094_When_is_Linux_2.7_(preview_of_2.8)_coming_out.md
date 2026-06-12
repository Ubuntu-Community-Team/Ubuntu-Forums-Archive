---
title: "When is Linux 2.7 (preview of 2.8) coming out?"
date: 2008-07-07
forum: The Cafe
---

### Post by ryaxnb on 2008-07-07
Linux 2.6 has been out for a long time for there to have not been any on 2.7,the "pre-beta" 2.8 builds, one would presume. What new kernel features will they have with 2.7? And when is the first 2.7 coming out?

---

### Post by zachtib on 2008-07-07
AFAIK, 2.7 hasn't even been started yet.  They've yet to encounter something that can't be done with 2.6, so there's no reason to create a new release line

---

### Post by Canis familiaris on 2008-07-07
What happened which spurred Linux from 2.5.x to 2.6.x?

---

### Post by fatality_uk on 2008-07-07
@ 2.6.24-19 now there's a lot that needs tidying up here first before they go releasing beta 2.8!

---

### Post by Lostincyberspace on 2008-07-07
The latest stable is 2.6.25.10but most distro releases are still using the 24 line because it is still being updated. but the 25 has  more features that have been fixed that are not quite compatible with the 24 line so are not included.

Oh and the just number them consecutively now the odd even doesn't matter any more.

---

### Post by keiichidono on 2008-07-07
> **Anurag_panda said:**
> What happened which spurred Linux from 2.5.x to 2.6.x?
[Wikipedia is your friend]("http://en.wikipedia.org/wiki/Linux_kernel").

---

### Post by Lostincyberspace on 2008-07-07
> **CalvinB said:**
> [Wikipedia is your friend]("http://en.wikipedia.org/wiki/Linux_kernel").
Wikipedia is on the fritz to day.

---

### Post by Canis familiaris on 2008-07-07
I get this now.

[QUOTE=Wikipedia]Version 1.0 of March 1994 supported only single-processor i386 machines.
Version 1.2 of March 1995 added support for Alpha, Sparc and MIPS.
Version 2.0 of June 1996 included SMP support and added support for more types of processors.
Version 2.2 of January 1999 (The Wonderful World of Linux 2.2).
Version 2.4.0 of January 2001[37] 
CPU support: Hewlett-Packard's PA-RISC processor, Axis Communications' ETRAX CRIS ("Code Reduced Instruction Set") processors
added ISA Plug-and-Play
added USB and PC Card support
2.4.6: added Bluetooth support
Filesystem and data storage 
added Logical Volume Manager (LVM) version 1
support for RAID devices
2.4.15: support for InterMezzo filesystem were added.
2.4.15: support for ext3 filesystem
Version 2.6 - current (December 17, 2003 to the present)[38] 
integrated µClinux (for microcontrollers)
CPU support: with support for Hitachi's H8/300 series, the NEC v850, and Motorola's embedded m68k processors, NUMA support, support for NCR's Voyager architecture, support for Intel's hyperthreading and Physical Address Extension (PAE)
integrated the ALSA sound driver
OS support: 
Improved APIC support.
Increased the maximum number of users and groups each from 65,536 (= 216) to 4,294,967,296 (232).
Increased the maximum number of process ids from 32,768 (= 215) to 1,073,741,824 (230).
Increased the maximum number of device types (major device) from 255 to 4095 and the maximum number of devices of each type (minor device) from 255 to more than a million.
Improved 64-bit support and filesystems of up to 16 terabytes on common hardware.
Improvements to the "overall responsiveness" for interactive processes (the kernel became fully pre-emptible and the I/O scheduler was rewritten).
Support for futexes, a rewrite of threading infrastructure to allow the Native POSIX Thread Library (NPTL) to be used.
An improved module loader.
User-mode Linux integration.
2.6.11 Infiniband support
Vendor neutral virtualisation API
Storage Support: 
LVM version 2
support for SGI's XFS filesystem.
A new "system filesystem" called sysfs, destined to relieve procfs of its system related information.
2.6.2 ATA over Ethernet support
2.6.12 (17 June 2005) iSCSI support
2.6.13 inotify support
2.6.14 9P support
2.6.14 FUSE support
2.6.17 Online reshaping of software raid5/6
2.6.19 support for ext4dev[/QUOTE]

---

### Post by Foster Grant on 2008-07-07
> **Lostincyberspace said:**
> Wikipedia is on the fritz to day.

F5 is also your friend. :)

---

### Post by eragon100 on 2008-07-07
linux 2.6 is almost 5 years old now, isn't it time for a new (major) version?

---

### Post by FuturePilot on 2008-07-07
I remember reading somewhere that there really isn't a need to bump the version number with 2.6. The way the kernel is currently structured allows the addition of large changes without the need to do a whole overhaul on the code.

Also I think they dropped the even-stable odd-development version numbering.

---

### Post by smartboyathome on 2008-07-07
2.6.27 isn't a preview of 2.6.28. 2.6.27 is a stable release, much line 2.6.26 is.

---

### Post by BrokeBody on 2008-07-07
> **ryaxnb said:**
> And when is the first 2.7 coming out?

> even numbers indicate a stable release, i.e. one that is deemed fit for production use, such as 1.2, 2.4 or 2.6. Odd numbers have historically been development releases, such as 1.1 or 2.5. 

[Version numbering](http://en.wikipedia.org/wiki/Linux_kernel#Version_numbering)

---

### Post by Xanatos Craven on 2008-07-07
Artificial version bumps are the domain of distributions, if they so choose to. Joe Blow doesn't care that his kernel went from 2.6 to 2.8, he just cares that he upgraded his Ubuntu to Year.Month Adjective Animal.

---

