---
title: "sources.list setup to use local mirror, need a new one for US mirrors"
date: 2008-08-20
forum: Server Platforms
---

### Post by maxim99 on 2008-08-20
I found that the Synaptic Package Manager is able to restore a lost/deletec sources.list. However, with the server editiont his application is not available. I'm faced with this issue because I installed Ubuntu using PXE and pointing the installer to a local http server where I have the ISO mounted onto a directory. This works fantastically, however, the sources.list is setup to use that as it's main repository, which is of course not going to work for updates.

I'm looking for a reliable source where I can download an "official" copy of sources.list for a US mirror, or some how generate a new one on the server itself. I'm curious if the installer application gets the list of mirrors from a list somewhere that I could derirve a new sources.list from.

---

### Post by maxim99 on 2008-09-05
Any idea's on this one?

---

### Post by windependence on 2008-09-06
```
# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
```

This is the default US source list. If you are not in the US, you should probably use a closer mirror.

-Tim

---

### Post by maxim99 on 2008-09-08
Is there any way to generate this list automajically?

It seems that Synaptic Package Manager is able to do this. Maybe it downloads it from somewhere? Will this list that you have given me always be valid and up to date?

---

### Post by maxim99 on 2011-09-13
Disappointingly, this is still an issue 3 years later.

I found another user asking the same question here:
[http://askubuntu.com/questions/9148/how-can-i-change-repository-mirror-from-commandline](http://askubuntu.com/questions/9148/how-can-i-change-repository-mirror-from-commandline)

A bug reported by a user in 2003 where it was decided that "dpkg-reconfigure apt" shouldn't run a mirror selection menu:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=178818](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=178818)

I've installed Ubuntu Server from a local repository so I didn't have to download everything over again. The installer sets the repository to the one manually set at install time. Ubuntu doesn't offer any means of changing it outside of having another computer handy, editing sources.list and typing in the addresses by hand.

---

