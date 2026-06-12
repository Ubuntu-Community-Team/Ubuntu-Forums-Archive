---
title: "WARNING: The following packages cannot be authenticated!"
date: 2009-04-28
forum: Server Platforms
---

### Post by irc4arab on 2009-04-28
Hi all

I just installed Fresh Ubuntu Server [9.04] and
When I try to updating my Server , I get this warning

```
WARNING: The following packages cannot be authenticated!
  update-manager-core acpid php5-mysql libapache2-mod-php5 php5-common libcups2 libfreetype6
```

is that normal! 


/etc/apt/sources.list
```
#
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://kw.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://kw.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://kw.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://kw.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://kw.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://kw.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://kw.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://kw.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://kw.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://kw.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://kw.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://kw.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://kw.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://kw.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

### Post by Namtabmai on 2009-04-28
Hi,

Do you have any other repositories enabled in

/etc/apt/sources.list.d/

?

---

