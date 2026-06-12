---
title: "Restoring windows mbr without recovery console"
date: 2007-12-06
forum: Windows
---

### Post by Curtisc on 2007-12-06
I had Windows and Ubuntu dual booting happily on my laptop, and then for various reasons I deleted my linux partition from the live CD.  Obviously, grub no longer works, but I expected this, so in goes the Windows CD so I can fix the MBR.  Here's where I run in to trouble: when I finally reach the screen that gives me the option to press "R", I get no response.  The CD drive isn't being accessed any more, but the fan revs up so it definitely sounds like it's trying to do something (this is before I press any of the keys).  I also can't press ENTER or F3.  I've tried this with 3 different Windows CDs with no luck.

Is there anything I can do to recover the MBR without the use of the recovery console?  My laptop cannot boot from USB keys or floppies.  My backup plan is to create a boot partition and install grub to that, but I'd rather not.

---

### Post by meierfra on 2007-12-06
Click on FixMBR in my signature. Try the 3rd method first.

---

### Post by Curtisc on 2007-12-06
Thanks, that seems to be exactly what I'm looking for!  I'll give it a shot when I get home.

---

