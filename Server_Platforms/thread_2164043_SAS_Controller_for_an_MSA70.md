---
title: "SAS Controller for an MSA70?"
date: 2013-07-20
forum: Server Platforms
---

### Post by MakOwner on 2013-07-20
This really is linux related - I'm running a couple of other external storage enclosures off a quad port SAS card, and recently aquired an HP MSA70 enclosure.
This is the 25 2.5" SAS disk enclosure.  
I'm not as familiar with this hardware as I am the other ones I have.

The SAS card I'm using is an LSI SAS1068E quad port card in a Dell server.  

I attached the MSA 70 to the free port on the LSI card and the first boot after installation, the boot sequence compeltes, but in dmesg I see the port resets.
I powered everthing down and reseated everything on the MSA70 and when rebooting the Dell, the boot porcess goes into endless modeprobe killing udev processes.


Anyone everworked with one of these?

---

