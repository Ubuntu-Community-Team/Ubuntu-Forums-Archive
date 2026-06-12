---
title: "internel volume icons  in launcher options"
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-22
It would appear that currently in unity 0.6.6 there are now only 2 avail. options, applied individually per volume
Always
Never (blacklisted

Unfortunately missing atm is 'Only when mounted'

(removal media gets 'when mounted' or never on a per session basis, (a removal media blacklist isn't persistent.

On a positive note all launcher icons can now be re-positioned except BFG & trash.

---

### Post by arpanaut on 2012-09-22
Pardon my French but, WTF?

This is a mistake/bug I hope.
I had to remove 11 instances of volumes from the launcher individually. Floppy won't remove.
and mounted volumes don't show, Yikes No more selection avail. in ccsm.
I see it as a regression, I'm off to work today will check back later.
Hopefully a bug has been filed?

---

### Post by mc4man on 2012-09-22
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1053704](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1053704)

---

### Post by cariboo on 2012-09-22
Thanks I've added myself to the bug, as yesterday I unlocked the icons from the Launcher, and now they don't reappear when I mount a partition via nautilus.

---

### Post by mc4man on 2012-09-22
> **cariboo907 said:**
> Thanks I've added myself to the bug, as yesterday I unlocked the icons from the Launcher, and now they don't reappear when I mount a partition via nautilus.

As it stands now the only way to return a volume(s) to the launcher is to remove it from the blacklist in dconf (dconf-editor is one way.

com.canonical.Unity.Devices > blacklist

Then of course it never leaves the launcher.
Hopefully an oversight or wip

---

### Post by arpanaut on 2012-09-22
Thanks mc4man!
If this is intentional, I fail to see the logic.
If I want to find an unmounted volume, I go to the file manager.

If the reason for having icons in the launcher not show in dash > recent
to reduce redundancy, this is really off target.

---

### Post by GreatDanton on 2012-09-24
After latest updates, anyone noticed unmounted devices in unity bar?
I don't even have floppy in my computer, and all other partitions are unmounted, but I can see them in unity bar.

Regards.

---

### Post by grahammechanical on 2012-09-24
Me too. Not only that but my 12.04 has been showing all my partitions in the Launcher for sometime.

The floppy disk icon appearing in the 12.10 launcher is indeed weird. I do not have one installed and it lacks the option to remove it from the Launcher. As do the disk icons in my 12.04 launcher.

Regards.

---

### Post by mc4man on 2012-09-24
[http://ubuntuforums.org/showthread.php?t=2061234](http://ubuntuforums.org/showthread.php?t=2061234)

---

### Post by GreatDanton on 2012-09-24
Unfortunately I didn't see that thread. Thanks mc4man. I added myself to the bug report.

Regards.

---

### Post by philinux on 2012-09-24
Merged.

---

### Post by arpanaut on 2012-10-05
Anyone have any links to the logic of and discussion of this change?
I just don't get it, and find it very irritating to have lost the "only mounted" option.

Wishlist>>> bah-humbug!  It's a regression!

---

### Post by mc4man on 2012-10-05
> **arpanaut said:**
> Thanks mc4man!
If this is intentional, I fail to see the logic.

I don't think 'logic' has played a significant role in unity design, too simple a 'concept'

---

### Post by arpanaut on 2012-10-05
> **mc4man said:**
> i don't think 'logic' has played a significant role in unity design, too simple a 'concept'
very funny?

):P

---

