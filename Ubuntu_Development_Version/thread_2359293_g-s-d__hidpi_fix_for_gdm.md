---
title: "g-s-d  hidpi fix for gdm"
date: 2017-04-22
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-04-22
Is this going to be included in 17.10 & if so why not in 17.04's  new proposed package
For reference,  
[https://bugzilla.gnome.org/show_bug.cgi?id=780208](https://bugzilla.gnome.org/show_bug.cgi?id=780208)

---

### Post by jbicha on 2017-04-22
That fix was not included in the current zesty gnome-settings-daemon Stable Release Update (SRU) because it wasn't committed to the upstream git repository until after the SRU was accepted. So let's verify the current SRU and once that's done, we can get this other fix in.

Would you be interesting in applying the [SRU template]("https://wiki.ubuntu.com/StableReleaseUpdates#Procedure") to [bug 1685035]("https://launchpad.net/bugs/1685035")?

---

### Post by mc4man on 2017-04-24
> **jbicha said:**
> That fix was not included in the current zesty gnome-settings-daemon Stable Release Update (SRU) because it wasn't committed to the upstream git repository until after the SRU was accepted. So let's verify the current SRU and once that's done, we can get this other fix in.

Would you be interesting in applying the [SRU template]("https://wiki.ubuntu.com/StableReleaseUpdates#Procedure") to [bug 1685035]("https://launchpad.net/bugs/1685035")?
I'm not really in position to do that atm as I've lent my 4k laptop to someone else in  need of a laptop with Windows & that's the only one I have with it. Not expecting to see it back for a few months or so.

---

