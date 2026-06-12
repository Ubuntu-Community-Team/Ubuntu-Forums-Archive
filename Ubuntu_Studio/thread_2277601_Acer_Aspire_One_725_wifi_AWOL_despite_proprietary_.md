---
title: "Acer Aspire One 725 wifi AWOL despite proprietary driver enabled."
date: 2015-05-10
forum: Ubuntu Studio
---

### Post by globetrotterdk on 2015-05-10
I am new to Ubuntu Studio 14.04 and XFCE. For some reason, I am unable to get wifi working on my Acer Aspire One 725, despite having installed the proprietary Broadcom driver. Is this a Ubuntu Studio or XFCE quirk, or both?

---

### Post by kwhitefoot on 2015-08-07
I also have this problem.  It was working in Lubuntu 14.04 but stopped when I upgraded to 14.10 and it still doesn't work in 15.04.  The network manager menu says Wireless disabled by hardware.  I've searched all over for a solution and can't find anything.

Now it works.

I booted from a usb stick with the latest Puppy (tahr).  Ran rfkill list in a terminal and discovered that now it says hard blocked no.
Rebooted in Lubuntu 15.04 and now that works too.
Very strange.

---

