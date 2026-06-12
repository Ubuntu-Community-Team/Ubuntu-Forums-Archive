---
title: "A small doubt regarding kpackagekit"
date: 2009-09-26
forum: The Cafe
---

### Post by praveesh on 2009-09-26
From a thread in this forum, I got the following information :
. The packagekit is not going to be the backend of Ubuntu app center. It is because of some incapacilities of the packagekit to deal with some features of the apt . Without that features, some softwares including some stuffs of sun won't be able to install. 

But the KUBUNTU uses kpackagekit . Is the backend of kpackagekit the packagekit ? If yes, doesn't that implies that KUBUNTU won't be able to install some softwares that can be installed on the Ubuntu ?.

---

### Post by Slug71 on 2009-09-26
> **praveesh said:**
> From a thread in this forum, I got the following information :
. The packagekit is not going to be the backend of Ubuntu app center. It is because of some incapacilities of the packagekit to deal with some features of the apt . Without that features, some softwares including some stuffs of sun won't be able to install. 

But the KUBUNTU uses kpackagekit . Is the backend of kpackagekit the packagekit ? If yes, doesn't that implies that KUBUNTU won't be able to install some softwares that can be installed on the Ubuntu ?.

Packagekit is very likely going to be the backend to Ubuntu Software Center for Karmic +1. Work is in the planning stage to make Packagekit deal with debconf and conf files.

Please see,

[http://ubuntuforums.org/showthread.php?t=1251708](http://ubuntuforums.org/showthread.php?t=1251708)

---

### Post by Xbehave on 2009-09-26
> If yes, doesn't that implies that KUBUNTU won't be able to install some softwares that can be installed on the Ubuntu ?.
No, you can always drop to apt-get/aptitude to install stuff that needs a dialog. I'm not saying you will have to KpackageKit may be able to deal with the license dialog, but because packagekit uses the underlying apt/yum framework you can always fallback if you need to.

---

### Post by praveesh on 2009-09-26
> **Xbehave said:**
> No, you can always drop to apt-get/aptitude to install stuff that needs a dialog. I'm not saying you will have to KpackageKit may be able to deal with the license dialog, but because packagekit uses the underlying apt/yum framework you can always fallback if you need to.

Oh yes . I forgot it.

---

