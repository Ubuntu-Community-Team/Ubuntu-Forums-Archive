---
title: "Unable to connect to update server in Ubuntu Server 9.10"
date: 2010-02-16
forum: Server Platforms
---

### Post by dilaang on 2010-02-16
Hi, i'm installed Ubuntu Server in VMWare Server.

I trying to update the system using aptitude, but the system say that is unable to contact security.ubuntu.org.

But i just ping the server and i have a positive response.

Can anyone help me ?

I copy here the /etc/apt/sources.list

# 
# deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)]/ karmic main restricted

#deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by Satoru-san on 2010-02-17
> **dilaang said:**
> Hi, i'm installed Ubuntu Server in VMWare Server.

I trying to update the system using aptitude, but the system say that is unable to contact security.ubuntu.org.

But i just ping the server and i have a positive response.

{snip}
Pinging does not tell you if the site is up ;) It just tells you there is connectivity. I went to that site and it is indeed down. infact ** server can't find security.ubuntu.org: NXDOMAIN

that is not a good server. [s]You will have to find out why, it may be that you are using an old version of ubuntu that is no longer supported.[/s]

there is nothing in your sources.list that says .org it is all .com which does resolve and does have a working server. It must be from a ppa repo or somthing that is causeng that.

---

