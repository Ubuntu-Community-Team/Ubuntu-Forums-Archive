---
title: "Hardy 8.04 ebox - Broken apt-get"
date: 2009-01-06
forum: Server Platforms
---

### Post by SleepingYoyo on 2009-01-06
Hi guys,

Running the ebox inclusive Ubuntu Server Hardy 8.04 distro and unfortuantly my apt-get keeps giving me the following error every time I attempt to do anything regarding updating, downloading or installing. 

```
sleepy@server:/etc/apt$ sudo apt-get update
E: The method driver /usr/lib/apt/methods/gttp could not be found.
E: The method driver /usr/lib/apt/methods/gttp could not be found.
```

As far as I can remember this started happening once I changed my sources.list to add a repositorie, however removing the addition didn't fix it.

Here's my sources.list also :

```

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://ppa.launchpad.net/ebox/ubuntu hardy main
deb gttp://www.openprinting.org/download/printdriver/debian lsb3.2 main


```

I've been trying to fix it for about a week now and it's driving me daft, would have just reinstalled if it were not for the fact i'd just transfered a few hundred gig of backups onto the same drive :S

Any help would be much appreciate,

Cheers,

SleepingYoyo.

---

