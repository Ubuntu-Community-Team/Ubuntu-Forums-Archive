---
title: "&quot;SOLVED&quot;  UEFI Secure Boot. Can it be deleted so to install &quot;just&quot; Linux?"
date: 2013-04-05
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2013-04-05
I am not being facetious. Is it wiped when the disk is written over with linux only installs or with Gparted first, for multiple Ext4 partitions.

If the answer is as simple as yes, than a simple yes for an answer is sufficient..

Thanks, for saving me the reading.

;p

---

### Post by coldraven on 2013-04-05
No, it is in firmware but it can be turned off if the vendor has enabled that ability.

---

### Post by arpanaut on 2013-04-05
No, uefi has replaced bios, but on most systems it can be disabled. Then the system can be installed in legacy(bios) mode.

Some OEM's implementation make that simple, others more difficult.
There may be some hoops to jump through depending of formatting of HDD, and boot loaders.
For the most part success can be had but some research and planning may be needed.

I know it's not the answer you were looking for, but there is quite a bit of information on this forum.
My best advice is to do your due diligence before buying your hardware.

HTH

---

### Post by mikodo on 2013-04-05
Thanks guys.

I'll do the reading and question asking before my next purchase then.

;p

---

### Post by grahammechanical on 2013-04-05
If a simple format of the hard drive allowed us to install and boot from any operating system, then "secure boot" would not be very secure, would it?

Its purpose is to only allow binaries that have been validated as not containing malicious code to install and be booted.

---

