---
title: "recomeneded repositries sources.list for gutsy x64 ???"
date: 2007-11-03
forum: Repositories &amp; Backports
---

### Post by mincho on 2007-11-03
please paste here the recomeneded sources.list for gutsy amd64 edition.. please

with medibuntu repo please...

---

### Post by 1337455 10534 on 2007-11-05
Bump

---

### Post by LavianoTS386 on 2007-11-13
My sources list look like this...

```
# deb cdrom:[APTonCD for ubuntu gutsy - amd64 (2007-10-21 18:54) CD1]/ /
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# Bleeding edge wine packages
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main

# Seveas&#8217; packages (GPG key: 1135D466)
# GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl gutsy-seveas all
deb-src http://mirror.ubuntulinux.nl gutsy-seveas all

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ gutsy free non-free
deb-src http://packages.medibuntu.org/ gutsy free non-free

#syzygy42 repository: avant-window-navigator, exaile, closure&#8230; (GPG key: 8434D43A)
# GPG key-file: http://download.tuxfamily.org/syzygy42/8434D43A.gpg
deb http://download.tuxfamily.org/syzygy42/ gutsy all
deb-src http://download.tuxfamily.org/syzygy42/ gutsy all

# Le dépomaniak repository (GPG key: 1D59E694)
# GPG key-file: http://ubuntu.davromaniak.eu/1D59E694.gpg
deb http://ubuntu.davromaniak.eu gutsy-depomaniak all
deb-src http://ubuntu.davromaniak.eu gutsy-depomaniak all

# Ryan Kavanagh&#8217;s packages (GPG key: 02544D0E)
# GPG key-file: http://packages.ryanak.ca/02544D0E.gpg

# Iuculano&#8217;s debian packages (GPG key: AE3BE9AA)
# GPG key-file: http://ubuntu.iuculano.it/AE3BE9AA.gpg

# Virtualbox PUEL
# GPG key-file: http://www.virtualbox.org/debian/innotek.asc
deb http://www.virtualbox.org/debian gutsy non-free

## uPure 64 Repository
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 main-amd64
deb http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental-amd64
deb-src http://download.tuxfamily.org/upure64/ gutsy-upure64 experimental-amd64

## lprod packages: many audio/video apps: avidemux, cinelerra&#8230;

# Morgoth Repository (GPG key: 7E2E4741)
# Provides Monkey&#8217;s Audio, xmms pugins, vlc plugins, gqview, audacius, audacity&#8230;
# GPG key-file: http://morgoth.free.fr/files/morgoth-signkey.gpg.asc

deb http://ppa.launchpad.net/bruce89/ubuntu gutsy main
deb-src http://ppa.launchpad.net/bruce89/ubuntu gutsy main

```

Skip the upure64 if you don't use 64-bit Ubuntu

---

### Post by lancerocke on 2008-03-14
thanks.
any updates?

---

### Post by bruce89 on 2008-03-15
You really ought to use the default sources.list and only add other repositories if you know what you need from them.

---

