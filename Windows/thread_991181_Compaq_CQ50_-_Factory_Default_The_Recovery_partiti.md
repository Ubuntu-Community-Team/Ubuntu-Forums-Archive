---
title: "Compaq CQ50 - Factory Default? The Recovery partition will not load"
date: 2008-11-23
forum: Windows
---

### Post by Vakman on 2008-11-23
I am trying to restore the computer to factory default. The recovery partition is there but it will not load when you press the corresponding F# key. Is there a way to restore to factory default?

---

### Post by cmat on 2008-11-23
I don't know what's up with these laptops and ubuntu. But if the hard drive is partitioned it will not work since it assumes the disks were unmodified. What you need to do is go into your ubuntu install DVD remove the ubuntu partition and expand the NTFS partition (if you are dual booting, if not format the ubuntu partition as NTFS). Then get your hands on a vista install disk (could be anyone's you aren't installing) and use "bootrec.exe \fixMBR" and then "bootrec.exe \fixboot" in the recovery console to kill off GRUB. Vista should boot as normal.

If you don't have a dual boot. At this point you should try to use the recovery partition. If it doesn't work use the recovery DVD you should have made. If that doesn't work call tech support.

* warning, this is pretty tricky and there is no warranty for the advice I provide above. I've done this before so it worked for me.

EDIT: fixed a command switch

---

### Post by tommynz1975 on 2008-12-03
Cmat thank-you for your comment.  This would explain why on a C500 lappy using a copy of vista wont load..

I will have a friend format the non ntfs partitions for me as per your instructions and hope for the best.. Many thanks

---

### Post by fuzzyworbles on 2009-02-16
the easiest way to get access back to your factory restore is to add an entry in grub that points to it. in fact, when you installed ubuntu, it should have done that for you, but grub thinks it's just another windows installation.

---

