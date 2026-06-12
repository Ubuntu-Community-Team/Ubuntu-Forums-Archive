---
title: "Vista missing from grub - Windows 7 not missing."
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by coffeecat on 2012-09-22
Two (Vaio) laptops, Vista/Quantal on one, Windows 7/Quantal on the other, Quantal on both fully updated as of a few minutes ago. Both have Windows recovery partitions on sda1 and boot into Windows itself from sda2. (7 has the usual separate small boot partition on sda2).

Apart from Quantal, the grub menu on the Vista machine only has an entry for the recovery partition, not for Vista itself. The W7 Machine still has entries for both the recovery partition and for Windows. The Vista machine did have a grub option for Windows a few days ago, but I can't recall when it disappeared. There was a grub update today, and I only noticed the missing entry today, do perhaps it was today's update that did it.

Anyone else notice this with a Vista dual-boot?

Running update-grub didn't pick up the sda2 Windows. I've done a quick and dirty edit of grub.cfg and Vista boots up OK from that, so there's nothing wrong with the Vista partition boot sector. Running update-grub a subsequent time removes my edit (as expected) but still doesn't pick up Vista.

I'll add a Vista stanza in 40_custom in the unlikely event I need to boot into Vista, but I'm curious about this.

---

### Post by DougieFresh4U on 2012-09-22
After update of grub my Win7 is not showing.But I do see partition in 'shortcuts' menu.
Haven't had an issue like this in years

---

### Post by ronacc on 2012-09-23
the new grub isn't even finding all my linux installs .

---

### Post by DougieFresh4U on 2012-10-16
After updateing yesterday, grub has found my Win7 install and now in grub all proper.
So glad it sorted itself out, may have taken a couple of weeks but it got there.

---

### Post by Hairy_Palms on 2012-10-16
a few days ago there was a version of grub in the repos that only added partitons that were mounted when grub-install was run, but the new version is fine here at least, if your still having problems try mounting the OS partitons and running grub-install from a terminal

---

