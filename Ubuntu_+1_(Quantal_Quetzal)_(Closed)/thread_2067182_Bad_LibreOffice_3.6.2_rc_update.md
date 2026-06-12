---
title: "Bad LibreOffice 3.6.2 rc update"
date: 2012-10-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-10-06
The LibreOffice_3.6.2 rc2 update in QQ proposed repos seems to of low quality.

Two main issues are these:

1. Regression - menus are gone again when using Gnome-shell DE.

2. The LibreOffice crashes immediately when any odt file is opened.

The LibreOffice 3.6.1 rc2 works fine.
So I downgraded back to it.

---

### Post by Harry33 on 2012-10-06
Here is the bug report (# 1062757):

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1062757](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1062757)

---

### Post by dino99 on 2012-10-06
same trouble here on i386 with gnome-classic: 3.6.2 load but without menu again, and crash when i try to load an .ods calc file :(

---

### Post by Wise Ferret on 2012-10-06
<vent>
This happened before, and it really becomes ridiculous. When messing with a vital desktop component like LibreOffice, the developers should be much more careful.
</vent>

---

### Post by cariboo on 2012-10-06
> **Wise Ferret said:**
> <vent>
This happened before, and it really becomes ridiculous. When messing with a vital desktop component like LibreOffice, the developers should be much more careful.
</vent>

Then it's a good thing you still have a stable 12.04 install. :)

---

### Post by Wise Ferret on 2012-10-06
My problem is not exactly with the inherent instability of development releases. I have been using development releases of ubuntu since 2005, and encountered many interesting crashes and malfunctions. It is the growing trend within ubuntu that worries me: to concentrate on Canonical's own projects (unity, ubuntu one) to an extent that harms the basic functioning of the system.

---

### Post by alphacrucis2 on 2012-10-06
An attempted fix for this has just landed from the intertubez. The menu is back but it goes AWOL again when you open a doc.

Edit: Maybe it is ok now. Might have been a glitch

---

### Post by vasa1 on 2012-10-06
> **Wise Ferret said:**
> My problem is not exactly with the inherent instability of development releases. I have been using development releases of ubuntu since 2005, and encountered many interesting crashes and malfunctions. It is **the growing trend** within ubuntu that worries me: to concentrate on Canonical's own projects (unity, ubuntu one) to an extent that harms the basic functioning of the system.
Then that is a sort of topic better written about elsewhere.

---

### Post by Harry33 on 2012-10-08
This bug is fixed now.

New update is available (1:3.6.2~rc2-0ubuntu2).

> **Changelog**

          libreoffice (1:3.6.2~rc2-0ubuntu2) quantal-proposed; urgency=high    *
do not build extensions on armel, armhf for bug 1062448
* update to unitymenus patch Change-Id
Ia8f82024e56ad83c8979d60df3c94e8209fe2552 (LP: [#1062757]("https://launchpad.net/bugs/1062757")) (LP: [#1062812]("https://launchpad.net/bugs/1062812"))

libreoffice (1:3.6.2~rc2-0ubuntu1) quantal-proposed; urgency=low
* update to unitymenus patch to 7ffc24eb76325afef89c25e8a7fe13124ed5a041
* lo-menubar is obsolete with this (C/P/R needs to stay there until 14.04 LTS)

libreoffice (1:3.6.2~rc2-0ubuntu1~ppa2) quantal; urgency=low
* update to Antonios fixes for today

libreoffice (1:3.6.2~rc2-0ubuntu1~ppa1) quantal; urgency=low
* ttf-sil-gentium-basic has been renamed to fonts-sil-gentium
* new upstream release 3.6.2.2
* update unitymenus patch to 767bae2cefd4cfcaa852c2c39e651bab81e4e134

libreoffice (1:3.6.1~rc2-1ubuntu6~ppa1) quantal; urgency=low
* update unitymenus to commit 22774aff3f1d4b2a09d713555e0180a3eded3155
* make metapackage explicit in short description (LP: [#1045165]("https://launchpad.net/bugs/1045165"))
* drop ttf-sil-gentium-basic and filter-mobiledev to suggests on
metapackage (LP: [#1045165]("https://launchpad.net/bugs/1045165"))
-- Bjoern Michaelsen <email address hidden>   Sun, 07 Oct 2012 10:18:24 +0200      


---

