---
title: "unable to delete some files despite clamtk detected them as viruses"
date: 2015-09-21
forum: Security
---

### Post by master-x on 2015-09-21
**Hi Fellow Ubuntu users,**
I ran a **clamtk** scan and it Identified about **14** Files!! to be viruses or potential ones.
How ever when I tried to delete them it did not work.
I logged is as root,yet no help.The dropdown which offers Read and write permission was
not active.I am seeing a few win32's as well.My os before ubuntu was win10. I am attaching
a scrnprnt of the concerned episode for any of you Gentlemen or Ladies to help me
get rid of the Pain.

[B]Warm Regards-
Pradeep Gour[/B]):P

---

### Post by oldos2er on 2015-09-21
I'm far from being a Wine or clamav expert, but those all look like false positives to me. I'd be very careful about deleting anything UEFI-related.

---

### Post by Habitual on 2015-09-21
Don't scan with PUA option enabled. (it's not by default, so you had to enable it.)
Disabled it and run it again. Compare results.

---

