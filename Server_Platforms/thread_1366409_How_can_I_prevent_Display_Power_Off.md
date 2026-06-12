---
title: "How can I prevent Display Power Off???"
date: 2009-12-28
forum: Server Platforms
---

### Post by FlapBags on 2009-12-28
Ok, I got Ubuntu Hardy here. and Ive tried 
 
setterm -blank 0 -store 
 
And I have tried 
 
apci=off <--I added this to my kernel line in the grub boot loader
 
And neither have prevented the display from shutting down. well ACPI kept it from shutting off completely, but it does STILL go to a blank screen.
 
I like running htop and having a display up and would like to know how to prevent the display from shutting off, this is a pure command line system.
 
If any of you pros might be willing to share a small nugget or tip with me I would be smiling about it all day, thank you

---

### Post by FlapBags on 2009-12-28
Shameless bump

---

### Post by KiLaHuRtZ on 2009-12-28
[https://bugs.launchpad.net/ubuntu/+source/kbd/+bug/381517](https://bugs.launchpad.net/ubuntu/+source/kbd/+bug/381517)

---

### Post by FlapBags on 2009-12-28
According to that thread, this is a known bug that has not been adressed.

---

### Post by KiLaHuRtZ on 2009-12-28
True, there are many more important issues that need to be resolved first.  However, the more people that confirm the issue, the sooner it gets attention towards a fix.  That said, feel free to chime in on the bug report. :)

---

