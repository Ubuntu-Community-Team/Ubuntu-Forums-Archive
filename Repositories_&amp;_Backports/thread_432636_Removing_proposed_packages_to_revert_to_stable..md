---
title: "Removing proposed packages to revert to stable."
date: 2007-05-04
forum: Repositories &amp; Backports
---

### Post by TPU on 2007-05-04
Recently, I had the need to use the -proposed repository on a server whose hardware was causing issues with the shipped version of one of the packages. The patched package has since been migrated to one of the standard repositories, so I've removed the proposed line from my sources.list.

My problem is that the presence of the -proposed source meant some of my *other* packages have been replaced with proposed versions, throwing that machine out of sync with the rest.

Is there any way I can revert all packages, even those which have picked up a higher version from -proposed,  back to the stable versions found in the normal repositories? I've tried and tried, and even if I remove the package and reinstall, it still reverts to the "newer" one, despite the -proposed repository being absent from the sources list.

---

### Post by mlind on 2007-05-06
You can use APT pinning to accomplish this ([http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning))

Create file **/etc/apt/preferences** with contents
```

Package: *
Pin: release a=feisty
Pin-Priority: 1001

Package: *
Pin: release a=feisty-updates
Pin-Priority: 1001

Package: *
Pin: release a=feisty-proposed
Pin-Priority: -10

```

Priority over 1000 allows downgrading. This should make apt believe that packages from feisty and feisty-updates are newer.


To simulate
```

sudo aptitude -s upgrade

```

To perform the downgrade
```

sudo aptitude upgrade

```

---

### Post by ricflomag on 2010-11-15
Thanks mlind, three years and a half later, your post helped me revert maverick from proposed to normal.

---

### Post by DrAcid on 2011-02-24
Hey, me too!
Thank You for the solution!

The proposed repository completely sucks! It has broken half of my system! :confused:
And trying to revert to stable wasted a lot of time!

WTH? Should there be some kind of warning? "If You take the Red pill, there'll be no going back" or something!
This is really frustrated! CANONICAL TAKE A LOOK AT THIS MAJOR PROBLEM!
FIX THIS PLEASE! Or at least create a button that will say:  REVERT TO STABLE REPOS
Quit trying to take Gnome Foundation's money and please fix this...

Okay? Because it's really took a go on my nerves... :(
(and I'm sure not only mine)

---

### Post by ctothej on 2011-03-18
Likewise... thanks!

---

### Post by mattubu16 on 2011-10-16
Thanks - this worked in 11.10 too!

Update: I forgot to mention that in 11.10 (and some versions previous) it's 'apt-get' instead of 'aptitude'

---

### Post by mattubu16 on 2011-10-16
> **DrAcid said:**
> 
The proposed repository completely sucks! It has broken half of my system! :confused:
And trying to revert to stable wasted a lot of time!

WTH? Should there be some kind of warning? "If You take the Red pill, there'll be no going back" or something!
This is really frustrated! CANONICAL TAKE A LOOK AT THIS MAJOR PROBLEM!
FIX THIS PLEASE! Or at least create a button that will say:  REVERT TO STABLE REPOS
Quit trying to take Gnome Foundation's money and please fix this...

Okay? Because it's really took a go on my nerves... :(
(and I'm sure not only mine)

The point of the proposed repos is for pre-release testing, which is why they are not selected by default. The Ubuntu documentation [does state]("https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Updates"): "The testing area for updates. This repository is recommended only to  those interested in helping to test updates and provide feedback."

---

### Post by herophuong on 2011-10-24
OMG!!! You've just help me get rid of the broken system after accidentally activate the proposed repo. 
Just 3 words send from 3 years later: I LOVE YOU.

---

### Post by sean on 2012-08-05
A big thank you from 2012! 

Sean

---

### Post by roudy1989 on 2012-08-06
Thank you :KS

---

### Post by Dabo Ross on 2013-03-06
Thank you! This worked for me in 12.10, using ```
apt-get upgrade
``` instead of ```
aptitude -s upgrade
```!

---

### Post by dkavraal on 2013-03-24
saves me too thanks

---

### Post by LeoMcSnarf on 2013-08-21
This helped me too, five years later... thank you :)

---

