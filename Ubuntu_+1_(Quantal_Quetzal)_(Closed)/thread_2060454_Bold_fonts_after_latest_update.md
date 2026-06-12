---
title: "Bold fonts after latest update"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by lucazade on 2012-09-20
with the latest update all the fonts in quantal kde are bold.. 

temporary workaround:
sudo rm /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-M.ttf /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-MI.ttf

related bug-report:
[https://bugs.launchpad.net/ubuntu-fo...ly/+bug/744812](https://bugs.launchpad.net/ubuntu-fo...ly/+bug/744812)

---

### Post by dino99 on 2012-09-20
see the ubuntu-font-family changelog; its by design.

---

### Post by lucazade on 2012-09-20
going to see.. broken by design?!

---

### Post by mips on 2012-09-20
As in desktop, menus, applications or just the desktop?

I know in Xubuntu the desktop fonts became bold but there is a way to fix that in xfce.

---

### Post by lucazade on 2012-09-20
everywhere.. plasma and qt4 apps are affected.

removing the medium ttf file temporary fixes the problem.. anyway the devs seem aware of the issue.

---

### Post by mparillo on 2012-09-20
This is likely to be resolved by reverting to the KDE fonts (backing out the override to use Ubuntu fonts):
[http://irclogs.ubuntu.com/2012/09/20/%23kubuntu-devel.html](http://irclogs.ubuntu.com/2012/09/20/%23kubuntu-devel.html)

---

### Post by Mr. Picklesworth on 2012-09-20
> **mparillo said:**
> This is likely to be resolved by reverting to the KDE fonts (backing out the override to use Ubuntu fonts):
[http://irclogs.ubuntu.com/2012/09/20/%23kubuntu-devel.html](http://irclogs.ubuntu.com/2012/09/20/%23kubuntu-devel.html)

Do you know if that will help with Qt apps running under a GNOME environment? (At the moment, I see Lyx has excessively bold fonts).

---

### Post by mparillo on 2012-09-20
> **Mr. Picklesworth said:**
> Do you know if that will help with Qt apps running under a GNOME environment? (At the moment, I see Lyx has excessively bold fonts).

I am not certain, so please post your findings here, and open a Launchpad bug if not fixed.

---

### Post by funicorn on 2012-09-20
not only for kubuntu, in unity all qt fonts are bold now.

---

### Post by Mr. Picklesworth on 2012-09-20
Nah, the discussion on this bug report makes it pretty clear that these regressions are considered 'not our problem:'
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-font-family-sources/+bug/1048600](https://bugs.launchpad.net/ubuntu/+source/ubuntu-font-family-sources/+bug/1048600)

This comment is particularly disappointing to me, given that we are weeks away from release:
> Unless we add it, I don't believe those apps will ever get fixed.

Please add it and fix the bugs.

Mark

That would be lovely if there was ample time to fix the bugs, but as it is this sounds like we're totally happy to stick our users in the crossfire of some misguided attempt to accelerate a bug fix.

(Hrm, that came out maybe a little harsh. I seem to be in the grouchiest mood ever today).

---

### Post by funicorn on 2012-09-21
Intrinsically defective coordinating mechanism resulted in linux desktop fail. It's doomed.

> **Mr. Picklesworth said:**
> Nah, the discussion on this bug report makes it pretty clear that these regressions are considered 'not our problem:'
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-font-family-sources/+bug/1048600](https://bugs.launchpad.net/ubuntu/+source/ubuntu-font-family-sources/+bug/1048600)

This comment is particularly disappointing to me, given that we are weeks away from release:


That would be lovely if there was ample time to fix the bugs, but as it is this sounds like we're totally happy to stick our users in the crossfire of some misguided attempt to accelerate a bug fix.

(Hrm, that came out maybe a little harsh. I seem to be in the grouchiest mood ever today).

---

### Post by lucazade on 2012-09-22
fixed with latest updates.. thread solved.

---

