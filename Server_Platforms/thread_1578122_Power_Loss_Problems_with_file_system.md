---
title: "Power Loss Problems with file system"
date: 2010-09-19
forum: Server Platforms
---

### Post by Z.K. on 2010-09-19
Is there anyway to prevent damage to a file system should the device loose power?  I have had several instances where the power was either pulled manually or the power went out from some power problem.  In each case, Ubuntu 10.04 would no longer boot and I was unable to fix the file system with the fsck command, but it did not help.  Once I got the system to boot, but some of the applications would not run properly.  In the end I had to reinstall the entire operating system.  So, I was just wondering if there was anything that could be done aside from installing a battery backup system, because even a battery backup would not help in case the 12V power plug was pulled.  

What I would like is something, some kind of hardware that could be used to keep the device's 12V up for a small amount of time and the operating system would detect that the power had been removed and do a normal shutdown.  I don't know if such a thing actually exists, but I thought I would ask.

---

### Post by BkkBonanza on 2010-09-19
You shouldn't have problems with power outage on ext3 and ext4 file systems. They both do journalling so that rebuilding any corruption caused by power failure should be fast and automatic. 

The device you ask for is called a "UPS" - Uninteruptible Power Supply and they are readily available at most computer stores. Get the kind with a serial/usb port and they can send a signal to the computer that will trigger a shutdown while it keeps the power up using a battery system. Any serious server application really should have a UPS and all data centers will have big diesel backup versions of this.

They're not expensive, about $50 for one that will get you around 10-30 minutes backup power.

---

### Post by CharlesA on 2010-09-19
I would recommend APC UPSes, since you can use apcupsd to monitor it and let it shutdown the machine after a power failure.

---

### Post by Z.K. on 2010-09-20
> **CharlesA said:**
> I would recommend APC UPSes, since you can use apcupsd to monitor it and let it shutdown the machine after a power failure.

That would only cure half the problem.  If someone were to pull the 12V power plug, I would still see the same problem.

As for the file system, I have trashed the file system at least twice now when the power went out and I was unable to repair it.  I was using the default file system when it was installed which I believe is ext4 in Ubuntu 10.04.  Would a flash file system like on a flash card rather than a rotating drive be more forgiving?

---

### Post by CharlesA on 2010-09-20
> **Z.K. said:**
> That would only cure half the problem.  If someone were to pull the 12V power plug, I would still see the same problem.

As for the file system, I have trashed the file system at least twice now when the power went out and I was unable to repair it.  I was using the default file system when it was installed which I believe is ext4 in Ubuntu 10.04.  Would a flash file system like on a flash card rather than a rotating drive be more forgiving?

ext4 has a delayed write, which is why a power failure causes corruption. If you have that many power interruptions, you might want to look into a different file system.

Normally a UPS would be fine if you have blackouts/brownout, but if someone/thing just yanks the power cord out, you are pretty much out of luck.

---

### Post by Z.K. on 2011-03-26
Well, I fixed the file trashing problem by installing acpi.  I am still looking for a battery backup solution and there is a board on [http://www.mini-box.com]("http://www.mini-box.com") that looks promising.

):P

---

