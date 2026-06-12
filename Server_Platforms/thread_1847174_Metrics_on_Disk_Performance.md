---
title: "Metrics on Disk Performance"
date: 2011-09-20
forum: Server Platforms
---

### Post by jnorthr on 2011-09-20
Can anyone suggest a monitor prgram that i can use to find out which of my i/o storage devices is the fastest ? I'm looking to relocate the swap partition of my 11.04 system to another drive or usb key in order to reduce contention on bus interface and/or drive heads. Have maxed out my system at 512MB  ram but need to do something else to boost thruput.

thanx

---

### Post by Entilza on 2011-09-20
Try:

hdparm -t /dev/xxx

---

### Post by rubylaser on 2011-09-20
hdparm is okay, but more of a quick guideline.  I'd use dd to write / read some files to the disk in varying sizes and block sizes and see which one is the fastest.

---

### Post by jnorthr on 2011-09-20
ok, will look at hdparm. was thinking there was something more utility-like as part of system tools or like that. thanx

---

