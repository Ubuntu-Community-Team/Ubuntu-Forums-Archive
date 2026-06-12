---
title: "Is there anything missing from this source list?"
date: 2007-05-27
forum: Repositories &amp; Backports
---

### Post by darknightuk on 2007-05-27
Is there anything missing from this source list, i cant find realplay or msttcorefonts

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) feisty main restricted multiverse


## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) feisty-updates main restricted multiverse
deb-src [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) feisty-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) feisty-backports main universe restricted multiverse

deb [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) feisty-security main restricted multiverse

deb [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) feisty-proposed main universe restricted multiverse
deb [ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive](ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive) feisty-updates universe

deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

---

### Post by Kobalt on 2007-05-30
It doesn't seem so. Here is mine, if you'd want to test : > # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

---

### Post by ChrisNiemy on 2007-05-30
you could probably expand the mlind repository with "fonts" and "experimental"
(EDIT: seems like there are no packages available with "fonts" and "experimental")

```
deb http://www.telemail.fi/mlind/ubuntu feisty main fonts experimental
```
(see: [http://www.telemail.fi/mlind/ubuntu/dists/feisty/](http://www.telemail.fi/mlind/ubuntu/dists/feisty/)
for edgy: [http://www.telemail.fi/mlind/ubuntu/dists/edgy/](http://www.telemail.fi/mlind/ubuntu/dists/edgy/))

However one should be careful with non-standard repositories. By the way, thanks for the repository, was searching it. :)

---

