---
title: "build-essentials"
date: 2007-05-24
forum: Repositories &amp; Backports
---

### Post by darknightuk on 2007-05-24
whats happened to build-essentials, aint listed in any repo?

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main universe restricted multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe

deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

---

### Post by sergiodlc on 2007-05-24
Yes, but you have misstyped it. The proper spelling is "build-essential" (without the trailing "s"). This should work for you:```
sudo apt-get install build-essential
```
By the way, this meta-package is so common that is included in the install CD.

---

### Post by darknightuk on 2007-05-24
thanx can't belive i missed that:(:redface:
> **sergiodlc said:**
> Yes, but you have misstyped it. The proper spelling is "build-essential" (without the trailing "s"). This should work for you:```
sudo apt-get install build-essential
```
By the way, this meta-package is so common that is included in the install CD.

---

### Post by spandanj on 2009-06-17
So many times I have come across a situation where a program won't build from source. I am a newbie, even after using ubuntu for a year. Something or other would lack. I didn't have time to go through what it was ie. what it prints in the terminal. 

Anyway, my point it is that it would be much easier if, during, or after, installation of ubuntu, it would have given me an option to install this "build-essential". Or when it would not build, it would LET ME KNOW that this is what I need to do. 

any thoughts?

---

