---
title: "OpenOffice.org 2 final installation"
date: 2005-11-05
forum: Repositories &amp; Backports
---

### Post by agro1986 on 2005-11-05
I'm not sure how this backport system works... The supplied OOo in Breezy is 1.9.something, and currently version 2 final is already released.

This is my sources.list:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://id.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://id.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## Multiverse

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
  
## Backports

deb http://ubuntu-backports.mirrormax.net/ breezy-extras main multiverse restricted universe

## Staging + extras

deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main multiverse restricted universe
deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main multiverse restricted universe

```

See, there's a backport entry there. According to my understanding, OOo version 2 will be put there. However, I did a "sudo apt-get update" and searched for "openoffice" on synaptic, and there's no OOo 2 final in sight.

Any help? (my guess is that it's not in the repository yet)

One more questions:
Suppose version 2 final is on the repository. Will my OOo gets upgraded from 1.9.x to 2.0 when I do a "sudo apt-get-update"? If not, how do I install it then?

Thanks a lot.

---

### Post by rickmans on 2005-11-05
See this topic: [http://ubuntuforums.org/showthread.php?t=80392](http://ubuntuforums.org/showthread.php?t=80392) it will help you to install open office 2

---

