---
title: "Dependency problems with common (dev-)libraries"
date: 2007-05-23
forum: Repositories &amp; Backports
---

### Post by Zibri on 2007-05-23
I'm getting weird dependency problems, especially on libraries, and even more especially on development libraries.

I can't install any development-packages, and the problem does not seem to be in my source.list. As you can see, i have the src-packages activated, so that's not it. Ideas? Downloading the packages from packages.ubuntu.com works... sort of. Only i get stuck in an almost endless labyrinth.

Any ideas? 

```
## Main
deb http://se.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Universe
deb http://se.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty universe

## Multiverse
deb http://se.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty multiverse

## Backports
deb http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

## Security
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY
deb http://archive.canonical.com/ubuntu feisty-commercial main

##KDE
deb http://kubuntu.org/packages/kde-latest edgy main
deb-src http://kubuntu.org/packages/kde-latest edgy main

##Amarok
deb http://kubuntu.org/packages/amarok-latest edgy main
deb-src http://kubuntu.org/packages/amarok-latest edgy main

##Wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main
```

---

### Post by WW on 2007-05-23
You have "feisty-updates", but not "feisty".  Add these lines:
```

deb http://se.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty main restricted

```

---

### Post by Zibri on 2007-05-23
Thank you. I believe I just copied a premade sources.list, that was my mistake :)

Thanks!

---

