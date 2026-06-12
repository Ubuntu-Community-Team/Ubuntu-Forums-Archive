---
title: "Problem installing ubuntu studio 16.04.2 from USB device."
date: 2017-02-18
forum: Ubuntu Studio
---

### Post by uwe-bungto on 2017-02-18
I am using a Dell XPS 8300 vintage 2009

I downloaded Ubuntu Studio 16.04.2 used Unetbootin 608-1 to install the distro to a USB thumb drive. Been doing this since Unetbootin came out without the slightest problem.

When I tried to boot from the USB drive I get a warning that no operating system is found. The normal boot sequence starts. I mounted the drive there is an operating system on it.
Tried the Thumb Drive on a Toshiba Satellite same warning. Next try was a Lenovo M92Z AIO this booted in text node.
It will boot from a DVD; but it takes forever and a day for each step.

I think it is worth avoiding this until the bugs are ironed out.
Paul

---

### Post by yoshii on 2017-02-21
You probably need to modify your computer's BIOS/UEFI boot settings.  This is accomplished by holding down a certain key, usually a function key, during the first several seconds of powering up.  
Check or google your computer model/manufacturer into or manual to find out how to edit the BIOS, or contact customer support of the manufacturer.  

Once in the BIOS, you'll want to browse the entire list of options and ask people questions about each feature.  Eventually you'll need to know what everything does, besides just the boot order section or USB enablement, etc.  

Don't worry, it's not really all that difficult.  However, you'll probably need to disable secureboot and enable legacy/BIOS mode.  This is usually harmless and allows the computer to boot other ways.

---

### Post by uwe-bungto on 2017-02-21
The problem is solved I think. UNetbootin seems to be the problem. I made a boot drive using Startup Disk Creator I could boot from a Thumb drive.
There must be a bug in the UNetbootin app.

---

### Post by yoshii on 2017-02-23
OK, thanks for the update.  That's good to know!

---

