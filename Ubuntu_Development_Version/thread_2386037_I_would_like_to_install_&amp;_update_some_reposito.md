---
title: "I would like to install &amp; update some repositories. Why can't I do so?"
date: 2018-02-28
forum: Ubuntu Development Version
---

### Post by cavina on 2018-02-28
This is my source list:
```
# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Alpha amd64 (20180126)]/ bionic main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic main restricted
deb-src [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic restricted main universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic-updates main restricted
deb-src [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic-updates restricted main universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic universe
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic-updates universe
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic-updates multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic-security main restricted
deb-src [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic-security restricted main universe multiverse #Added by software-properties
deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://ubuntu.mirror.garr.it/ubuntu/](http://ubuntu.mirror.garr.it/ubuntu/) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb-src [http://ppa.launchpad.net/numix/ppa/ubuntu](http://ppa.launchpad.net/numix/ppa/ubuntu) bionic main
```

Something its wrong because have problem with update and cannot install new repositories like  Unity 8 from UBports

---

### Post by kerry_s on 2018-02-28
the have a script for newest ubuntus-> [https://github.com/ubports/unity8-desktop-install-tools](https://github.com/ubports/unity8-desktop-install-tools)

---

### Post by coffeecat on 2018-02-28
18.04 is still in development.

*Thread moved to **Ubuntu Development Version**.*

---

### Post by kc1di on 2018-02-28
You have 18.04 which changes daily because it's still in development not all things will work not all repositories will be tracking the development release.  It will be final on April 26 or there abouts. 
You should be receiving many updates during the development and some may break the system.  That why it's not advised to install development releases on production machines.

---

