---
title: "Ubuntu-rescue-remix (formerly known as Rescubuntu)"
date: 2007-10-07
forum: The Cafe
---

### Post by az on 2007-10-07
Rescubuntu is now known as Ubuntu-rescue-remix with a brand new website:
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

Ubuntu Rescue Remix is a GNU/Linux live cd that provides the data
recovery expert with a command-line interface environment equipped
with the best free-libre, open source data recovery and forensics
tools available.

Since Ubuntu uses many filesystem and hardware detection libraries in
its live cd, it makes sense to make a remix of the live cd for data
recovery use.

The Rescue-remix is built from scratch, using the technique detailed here:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I am proud to announce the latest release of Ubuntu-rescue-remix.
Version 7.10-BETA is available here:
[http://ubuntu-rescue-remix.org/Download](http://ubuntu-rescue-remix.org/Download)

Version 7.10 of the Rescue-remix will be released once Ubuntu 7.10 is released.

As always, your help is greatly needed and appreciated.  Please
discuss development or report bugs here:
[http://ubuntu-rescue-remix.org/forum](http://ubuntu-rescue-remix.org/forum)

As well, discuss data recovery techniques or ask for data recovery help here:
[http://ubuntu-rescue-remix.org/forum/1](http://ubuntu-rescue-remix.org/forum/1)


Cheers!

az

---

### Post by southernman on 2007-10-07
Looks quite nice AZ! I'll snag the beta here in a bit and have a close up look around. 

Thanks for your efforts!

---

### Post by RAV TUX on 2007-10-07
> **az said:**
> Rescubuntu is now known as Ubuntu-rescue-remix with a brand new website:
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

Ubuntu Rescue Remix is a GNU/Linux live cd that provides the data
recovery expert with a command-line interface environment equipped
with the best free-libre, open source data recovery and forensics
tools available.

Since Ubuntu uses many filesystem and hardware detection libraries in
its live cd, it makes sense to make a remix of the live cd for data
recovery use.

The Rescue-remix is built from scratch, using the technique detailed here:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I am proud to announce the latest release of Ubuntu-rescue-remix.
Version 7.10-BETA is available here:
[http://ubuntu-rescue-remix.org/Download](http://ubuntu-rescue-remix.org/Download)

Version 7.10 of the Rescue-remix will be released once Ubuntu 7.10 is released.

As always, your help is greatly needed and appreciated.  Please
discuss development or report bugs here:
[http://ubuntu-rescue-remix.org/forum](http://ubuntu-rescue-remix.org/forum)

As well, discuss data recovery techniques or ask for data recovery help here:
[http://ubuntu-rescue-remix.org/forum/1](http://ubuntu-rescue-remix.org/forum/1)


Cheers!

az

Does this work like [Helix]("http://www.e-fense.com/helix/")?

> [IMG]http://www.e-fense.com/helix/i/HELIX-LOGO.gif[/IMG]
"Download your copy today and save a windows machine tomorrow." --zushiba

Helix is a customized distribution of the Knoppix Live Linux CD. Helix is more than just a bootable live CD. You can still boot into a customized Linux environment that includes customized linux kernels, excellent hardware detection and many applications dedicated to Incident Response and Forensics. 

Helix has been modified very carefully to NOT touch the host computer in any way and it is forensically sound. Helix wil not auto mount swap space, or auto mount any attached devices. Helix also has a special Windows autorun side for Incident Response and Forensics. 

Helix focuses on Incident Response & Forensics tools. It is meant to be used by individuals who have a sound understanding of Incident Response and Forensic techniques. That said Helix is used by the following organizations for Incident Response/Forensics Training:

e-fense: [Helix Incident Response & Computer Forensics]("http://www.e-fense.com/helix/training.php") 
NW3C: [Linux Forensics]("http://www.nw3c.org/training_courses.html") 
SANS Track 508: [System Forensics, Investigation and Response.]("http://www.giac.org/certifications/security/gcfa.php") 
InfoSec Institute: [Computer Forensics Training]("http://www.infosecinstitute.com/courses/computer_forensics_training.html") 
SEARCH: [Basic Investigators Training]("http://www.search.org/programs/hightech/courses.asp")
[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

---

### Post by az on 2007-10-08
> **RAV TUX said:**
> Does this work like [Helix]("http://www.e-fense.com/helix/")?

[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

No.  The rescue remix is a data recovery toolkit.  It's purpose is to allow you to recover lost files, not gather evidence.  Some forensics tools (like sleuthkit) are very useful for finding deleted or otherwise lost files so those tools are there for that purpose.

Other differences include the small footprint (the Rescue-remix is console-only) and the six-month release schedule - you get the latest supported versions of libraries and it can run on very old or very new hardware.

---

