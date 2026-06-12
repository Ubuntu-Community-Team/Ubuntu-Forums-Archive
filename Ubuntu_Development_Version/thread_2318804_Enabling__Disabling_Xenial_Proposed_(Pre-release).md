---
title: "Enabling / Disabling Xenial Proposed (Pre-release)"
date: 2016-03-29
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-03-29
16.04 Desktop / Unity

I enabled Xenial Proposed (Pre-release) and some bugs i had earlier reappeared (Gimp and Shotwell has missing filemenus).
I disabled Xenial Proposed (Pre-release) and did an update.

What does disabling the repository do? Will apt simply wait until my active repositories have a newer version. I'm petty sure it did not revert anything.

---

### Post by Cavsfan on 2016-03-29
> **izznogooood said:**
> 16.04 Desktop / Unity

I enabled Xenial Proposed (Pre-release) and some bugs i had earlier reappeared (Gimp and Shotwell has missing filemenus).
I disabled Xenial Proposed (Pre-release) and did an update.

What does disabling the repository do? Will apt simply wait until my active repositories have a newer version. I'm petty sure it did not revert anything.

You just won't get any more Proposed updates with it disabled. Nothing will be reverted.

---

### Post by grahammechanical on 2016-03-29
The proposed repository will give us updates that have not yet been pushed into the normal update channels. Think of enabling proposed as a way of early testing the packages in line to be updated. Packages in proposed will eventually come down the normal update channel. 

Regards.

---

### Post by ajgreeny on 2016-03-29
Those applications that have problems will need to be removed and then reinstalled to get back to the previous version, but only after disabling the proposed repos.

I'm not sure about the gnome-software package, or whatever it's called, but using synaptic you can force the version of a package to the lower one for installation without separately removing the currently installed newer version.

---

### Post by izznogooood on 2016-03-29
Ill ask this in a different question, i dont know which package handles the window menus... (And also i´m not pressed for time as i intend to keep this system for 5 years, so at least ill wait for the final release...)

---

