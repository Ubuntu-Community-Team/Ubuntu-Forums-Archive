---
title: "Why does System Monitor hang?"
date: 2010-08-15
forum: System76 Support
---

### Post by Eyore15 on 2010-08-15
My Starling is about 8 months old.  I recently upgraded to UNR 10.04.I discovered that the system monitor function doesn't work.  When I click on the ICON, I get the dialogue box saying "opening" and a different graphic for the function.  The whole system grinds to a halt in about 15 seconds after selecting system monitor and requires a hard restart.

Any ideas?

mcm

---

### Post by dlavi1976 on 2010-08-15
Not sure why it hangs but see this thread for a discussion of the issue

 [http://ubuntuforums.org/showthread.php?t=1476897](http://ubuntuforums.org/showthread.php?t=1476897) 

I use KSysguard instead and it works fine.

---

### Post by thomasaaron on 2010-08-16
Yes, there is something about the ifconfig command (which System Monitor evidently uses) that causes a kernel panic. Definitely a driver issue.

---

