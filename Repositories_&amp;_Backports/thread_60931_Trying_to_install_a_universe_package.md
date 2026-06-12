---
title: "Trying to install a universe package"
date: 2005-08-29
forum: Repositories &amp; Backports
---

### Post by daledude on 2005-08-29
I understand this forum is for main and restricted and there is a forum for backports but I dont see anything for universe specifically so please forgive.

Im trying to install request-tracker3.4 which I see at [http://archive.ubuntulinux.org/ubuntu/pool/universe/r/request-tracker3.4/](http://archive.ubuntulinux.org/ubuntu/pool/universe/r/request-tracker3.4/). When I try apt-get/cache it only displays request-tracker3.2.

[http://archive.ubuntulinux.org/ubuntu/indices/override.hoary.universe](http://archive.ubuntulinux.org/ubuntu/indices/override.hoary.universe) doesnt contain the request-tracker3.4 line. Is that the issue?

Is there something I should be doing outside manually downloading and installing? 

Im using the sources.list straight from the FAQ:
```
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
```

---

### Post by UbuWu on 2005-08-30
3.4 is for breezy, hoary has 3.2, so yes if you want to upgrade, you will have to install it manually or wait for breezy (october 13th)

---

