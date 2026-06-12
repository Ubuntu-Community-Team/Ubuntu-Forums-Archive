---
title: "wine 1.3.16 dont find installed gecko"
date: 2011-03-19
forum: Wine
---

### Post by dino99 on 2011-03-19
having installed all the required default wine packages but while running winecfg from menu, i get a warning saying: wine cant find gecko.

As the changelog says that now it use the Firefox gecko, i suppose the switch has not be made somewhere or a typo exist. That mean HTML rendering is disabled (i've not installed gecko from winetricks, waiting for a fix as i've posted a bug report on bugzilla, if a quick fix is not made then i will install it from winetricks)

---

### Post by dino99 on 2011-03-19
reported bugs: [https://bugs.launchpad.net/ubuntu/+source/wine1.3/+bug/738246](https://bugs.launchpad.net/ubuntu/+source/wine1.3/+bug/738246)

---

### Post by davidsrsb on 2011-03-19
It looks like Ubuntu is installing the wrong Gecko version.
See: [http://wiki.winehq.org/Gecko](http://wiki.winehq.org/Gecko)
We should have v1.2.0, but actually have v1.1.0 in the latest package

---

### Post by cogadh on 2011-03-19
Looks like Scott needs to update the package dependency for the new gecko. This should only affect users who are using the latest and greatest Wine, not anyone using the stable Wine. 

I think (if I am reading the package info correctly) that you can install the "wine-gecko" package to get the correct version; the Wine package normally installs the "wine1.3-gecko" package as a dependency, which is definitely the 1.1 version of Gecko.

EDIT - I just tested and no joy with that package. However, when the "can't find Gecko" error occurs, it does give you the option to download the correct Gecko.

---

### Post by Dlambert on 2011-03-19
Wine 1.3.16 includes a new gecko built from firefox 4, so it might not function right away.

---

### Post by cogadh on 2011-03-19
> **Dlambert said:**
> Wine 1.3.16 includes a new gecko built from firefox 4, so it might not function right away.
The problem is the current 1.3.16 package for Ubuntu automatically installs the wrong version of the Gecko package, not that the Firefox-based Gecko doesn't work.

---

### Post by Dlambert on 2011-03-19
Ok, thanks for the info.

---

### Post by Soulcage on 2011-03-20
Heres how to get the latest until the wine1.3-gecko package is updated. [http://wiki.winehq.org/Gecko]("http://wiki.winehq.org/Gecko")

---

### Post by dankegel on 2011-03-20
> **dino99 said:**
> having installed all the required default wine packages but while running winecfg from menu, i get a warning saying: wine cant find gecko.

As the changelog says that now it use the Firefox gecko, i suppose the switch has not be made somewhere or a typo exist. That mean HTML rendering is disabled (i've not installed gecko from winetricks, waiting for a fix as i've posted a bug report on bugzilla, if a quick fix is not made then i will install it from winetricks)

I relayed your problem to Scott, who sheepishly realized he'd forgotten to upload the new gecko.  He's on it now, thanks.

If you filed a bug report, can you post a link to it here?

---

### Post by dino99 on 2011-03-20
Look post #2 above Dan

by the way Scott has built a new package 1.2.0 4 hours ago but only for maverick

---

