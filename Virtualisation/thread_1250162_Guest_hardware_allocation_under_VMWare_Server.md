---
title: "Guest hardware allocation under VMWare Server"
date: 2009-08-26
forum: Virtualisation
---

### Post by batfastad on 2009-08-26
Hi everyone

I'm planning to convert 2 physical servers onto a single VMWare Server and I'm wondering about it works with regard to allocating cores/memory/storage between the VMs.
I've only ever used VMWare workstation under windows so don't know too much about VMWare Server under Linux. I'm just about to start testing this.

One VM will be a new mail (Zimbra) server.
The other will be our NAS/LAMP intranet system.

Here's the specs of the new box:
Tyan s5211 i3210W motherboard
Intel quad core Xeon x3360
8GB ECC memory
120GB SATA drive for OS/boot
3Ware 9690SA-8i RAID card with the following arrays:
- 5x1TB in a RAID 6 for the NAS/intranet VM
- 2x1TB in RAID 1 for the mail VM
- 1x1TB as a hot-spare

Obviously the 3Ware card deals with all the RAID stuff so they just appear to the system as sdb1 sdb2 etc.
And I guess I specify the size each VM should occupy on the main boot 100GB boot drive.

But does it let me allocate 5GB memory to one VM and 3GB to the other?
How much should I leave for the VMWare Server host machine? Or does it not really work like that?

For the 2 guests I was planning on using JeOS 64bit. And Ubuntu  8.04 Server LTS 64bit as the host OS.

Or should I just leave our LAMP intranet/shared files system running on the host OS alongside VMWare Server, and only have our mail server running as a guest VM?

Any comments/suggestions on this?

Cheers, B

---

### Post by batfastad on 2009-08-28
Anyone?
Any comments/suggestions?

Cheers, B

---

