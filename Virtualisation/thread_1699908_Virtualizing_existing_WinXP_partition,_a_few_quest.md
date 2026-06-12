---
title: "Virtualizing existing WinXP partition, a few questions"
date: 2011-03-04
forum: Virtualisation
---

### Post by Arightwizard on 2011-03-04
Hey,
I have windows xp installed on my laptop's built-in 120gb harddrive. I now installed the latest Ubuntu Studio on a separate, external 1TB drive for music-related things.

What I want to know is, since the hard drive holding ubuntu is significantly larger than Windows XP, is there any way I could "copy" the whole harddrive holding windows into an iso file, then convert it to vmdk and run it in virtualbox?

Problem right now is I have no internet on ubuntu, so everything related to the internet has to be done through windows xp...like downloading virtualbox.

Any ideas?

Thanks!

---

### Post by Hedgehog1 on 2011-03-04
This is possible.

The idea is you would install XP in Vbox, with enough disk space to hold your current XP system and data.

Then, in the 'real' XP, do a backup of the entire system.

Finally, in the Vbox XP, do a full restore of the backup.

While Win 7 has built in functionality for this, I think in XP you would need to use 3rd party software (which you may already own).

*It **may** also be possible to use the free clonezilla and backup a partition to a file, then inside the Vbox restore the partition using clonezilla again.*

***The Hedge***

:KS

---

