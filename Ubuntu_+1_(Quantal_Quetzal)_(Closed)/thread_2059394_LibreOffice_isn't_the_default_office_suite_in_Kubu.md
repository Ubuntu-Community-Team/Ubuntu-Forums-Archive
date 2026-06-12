---
title: "LibreOffice isn't the default office suite in Kubuntu 12.10"
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by vasa1 on 2012-09-17
"Calligra is the default office and graphics suite adding top class painting and database applications"
From: [https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta1](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta1)

---

### Post by bra|10n on 2012-09-17
Libreoffice has been added again,
[https://lists.ubuntu.com/archives/quantal-changes/2012-September/009160.html](https://lists.ubuntu.com/archives/quantal-changes/2012-September/009160.html)

---

### Post by vasa1 on 2012-09-17
> **bra|10n said:**
> Libreoffice has been added again,
[https://lists.ubuntu.com/archives/quantal-changes/2012-September/009160.html](https://lists.ubuntu.com/archives/quantal-changes/2012-September/009160.html)
According to that link, LibreOffice is a "full recommend" whereas Calligra is in "full", FWIW.

Someone kindly please explain the diff.

I know that if I do something like:
sudo apt-get install lubuntu-desktop I get the whole kit (~159 entries)
whereas if I do
sudo apt-get install --no-install-recommends lubuntu-desktop
I get a "lite" version with just ~30 entries.

So, assuming one **clean** installs Kubuntu, what would happen? My suspicion is that, as described above, LibreOffice may be offered as an option and if the user accepts, it will be installed.

Since the Kubuntu image is already ~ 1GB, LibO may even be part of the image?

---

### Post by vasa1 on 2012-09-17
Calligra is under "New Software Selections" [here]("https://wiki.kubuntu.org/QuantalQuetzal/Beta1/Kubuntu") with this stirring quote:
"Calligra has the best support for reading MS Office files of any open source software." ODF purists won't be amused.

---

### Post by bra|10n on 2012-09-18
Well the first thing to note is 12.10 rc has not been released yet.

When 12.10 is released LibreOffice will be the default office suite as part of kde-desktop. If you choose to install kde-full however, Calligra will also be installed as a recommends of kde-full.

---

### Post by bra|10n on 2012-09-18
> **vasa1 said:**
> Calligra is under "New Software Selections" [here]("https://wiki.kubuntu.org/QuantalQuetzal/Beta1/Kubuntu") with this stirring quote:
"Calligra has the best support for reading MS Office files of any open source software." ODF purists won't be amused.

ODF purists if they exist, would be chuffed that the .doc/x format has been ignored.

---

