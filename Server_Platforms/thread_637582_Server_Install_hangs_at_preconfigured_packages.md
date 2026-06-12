---
title: "Server Install hangs at preconfigured packages"
date: 2007-12-11
forum: Server Platforms
---

### Post by Spear on 2007-12-11
Hi,

As mentioned in another post about Ubuntu Server,i found out an old Siemens Primergy B200 server in a corner, ready for the recyle bin.
It'll be perfect to replace the existing proxy (a single hard disk workastation). It holds 2 GB Ram, two Intel PIII 1 Ghz, and finally 5 disks in Raid V.

I put the Ubuntu Server 7.10 CD ... it starts ... tells me a few things about 

MP-BIOS bug 8254 timer not connected to IO-APIC
MP-BIOS ACPI : wrong _bbn value

but goes on ... i then choose language, keyboard ... then it goes to two different windows about detecting hardware, and the checkinf the CD, and ... on the third it loads additionnal components ... and hangs at 6 % or sometimes less.

I tried with the Ubuntu desktop 7.10, it goes nowhere, and i have the same problem with an Ubuntu Server 6.06 as with the 7.10.

I download a Debian 4.0 ... no problem, it installs perfectly. What's going on ?

---

### Post by bnuytten on 2007-12-15
Just a guess: the RAID controller is not properly detected/supported?

---

### Post by Spear on 2007-12-15
Might be, had not problem with the Debian 4.0 install.

I'll check how that old Adaptec 2100S is managed ; thanks :)

---

