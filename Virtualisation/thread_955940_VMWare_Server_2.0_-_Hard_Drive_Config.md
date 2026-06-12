---
title: "VMWare Server 2.0 - Hard Drive Config"
date: 2008-10-22
forum: Virtualisation
---

### Post by Spitphire on 2008-10-22
Ok,

Let me start out by explaining what I'm trying to accomplish.  I have 5 computers in the house which all can access a NAS located on a headless ubuntu 8.04 box.  The ubuntu box is used for backing up all the pertinent info from the other 5 computers.

The ubuntu box has two hard drives, one holds the operating sys, and the other holds the shared space drive (which is shared utilizing samba).

the ubuntu box also runs VMWare 2.0 (among other things).  With a session of windows xp running which can be remotely accessed.  I would like to add the shared space drive to the virtual machine.  However, I would like to add it as a separate hard drive and not as a network drive.  I figure the virtual machine has access to all the hardware on the host system, so it should be possible?

Is this possible?

-Spit

---

### Post by dcstar on 2008-10-22
> **Spitphire said:**
> Ok,
.........
the ubuntu box also runs VMWare 2.0 (among other things).  With a session of windows xp running which can be remotely accessed.  I would like to add the shared space drive to the virtual machine.  However, I would like to add it as a separate hard drive and not as a network drive.  I figure the virtual machine has access to all the hardware on the host system, so it should be possible?

Is this possible?

-Spit

There is a separate Virtualization forum where questions like this have a better chance of being answered.

---

### Post by bodhi.zazen on 2008-10-22
It should be possible. In VMWare, add a new hard drive, and point it to the physical partition.

FYI: I use KVM and this KVM uses physical partitions smooth as butter.

---

### Post by Spitphire on 2008-10-23
That worked, thanks.  I appericiate it.

---

### Post by arvliet on 2008-11-05
Could someone elabourate on this a little please?  

I'm running VMWare Server 2.0 Build 122956 under Windows and I am able to create/add only virtual drives.  

Please confirm - the Linux version of VMWare Server 2.0 /is/ able to attach to physical drives?  

Thanks

---

