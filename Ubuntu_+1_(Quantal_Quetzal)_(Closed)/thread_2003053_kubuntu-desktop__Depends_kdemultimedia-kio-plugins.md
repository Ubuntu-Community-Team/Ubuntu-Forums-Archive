---
title: "kubuntu-desktop : Depends: kdemultimedia-kio-plugins but it is not going to be instal"
date: 2012-06-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by caryb on 2012-06-13
Have had a broken KDE session for about 3 days, am I in isolation or is this wide spread? I (with brain out of gear) applied a update the other day that removed kubuntu-desktop when I try to install it I get
"kubuntu-desktop : Depends: kdemultimedia-kio-plugins but it is not going to be installed"


Cary

---

### Post by PaulW2U on 2012-06-13
As far as I can ascertain, KDE 4.8.80 (4.9 beta 1) was abandoned as some packages failed to build.

KDE 4.8.90 (4.9 beta 2) should be uploaded in the next few days and hopefully the dependency problems will disappear.

---

### Post by 67GTA on 2012-06-13
Yeah, it hit me too. I knew better than to update using synaptic. Usually apt will catch this kind of package mismatch. Waiting for 4.8.90 to build and hit the mirrors. Using gnome 3 now just to get logged in, but a gnome-settings-daemon problem is keeping me from using any theme except the "windows 95" look. Welcome to the world of testing!

---

### Post by caryb on 2012-06-13
Yep can relate, am using LXDE just for laughs :lolflag:


Cary

---

### Post by PaulW2U on 2012-06-14
> **67GTA said:**
> Waiting for 4.8.90 to build and hit the mirrors.

The upload has started but I'm going to wait until it is more or less complete before upgrading KDE.

It's worth keeping an eye on the #kubuntu-devel IRC channel to see if there are any packages that are giving the developers problems.

---

