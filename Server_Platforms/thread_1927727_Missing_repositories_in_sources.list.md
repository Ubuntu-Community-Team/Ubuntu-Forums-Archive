---
title: "Missing repositories in sources.list"
date: 2012-02-18
forum: Server Platforms
---

### Post by Ji Ruo on 2012-02-18
I have installed 11.10 i386 server edition and went to apt-get, then realised my only source listed was the install CD. Is this normal? If not, I have misconfigured the install at some stage. I would much prefer to be able to install and update over the network, but I don't have the sources listed. Would someone be able to post the standard content of sources.list that I am looking for.

---

### Post by josephmills on 2012-02-18
> **Ji Ruo said:**
> I don't have the sources listed. Would someone be able to post the standard content of sources.list that I am looking for.

```
cat /etc/apt/sources.list
# 

# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ oneiric main restricted

#deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/main/binary-i386/
#deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
#deb http://download.webmin.com/download/repository sarge contrib
#deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib
#deb http://archive.scrapy.org/ubuntu oneiric main

```
hope this helps

---

### Post by Ji Ruo on 2012-02-18
That looks very similar to my 64-bit desktop install. So there are no differences in the names of the sources between 64-bit and 32-bit versions, and between server and desktop? (apart from the CD information at the top)

---

### Post by jailbait on 2012-02-19
> **Ji Ruo said:**
> That looks very similar to my 64-bit desktop install. So there are no differences in the names of the sources between 64-bit and 32-bit versions, and between server and desktop? (apart from the CD information at the top)
Nope.
Theirs only a difference in the **installed** packages.

---

