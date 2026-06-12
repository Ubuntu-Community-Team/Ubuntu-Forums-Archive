---
title: "Really basic sources.list question"
date: 2005-10-13
forum: Repositories &amp; Backports
---

### Post by PaganHippie on 2005-10-13
I upgraded from Hoary to Breezy a couple of weeks ago over the network, rather than using the install CD.  Of course, this meant that I had to set up sources.list by hand.  What should the 'official' contents of sources.list look like?

Thanks....  :smile:

---

### Post by Anchovie on 2005-10-14
I'm not sure if this is what you are asking for but mine looks like this...

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse

---

### Post by PaganHippie on 2005-10-14
Yep, that looks like exactly what I'm after.  Thanks!

---

