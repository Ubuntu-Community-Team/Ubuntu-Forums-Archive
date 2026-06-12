---
title: "odd problems with apt-get (wont connect)"
date: 2011-02-20
forum: Server Platforms
---

### Post by TechSupportx86 on 2011-02-20
I have been having some problems with apt-get in that it won't update and i can't install anything. When i run sudo apt-get update i get loads of errors saying "Failed to fetch http://..." and "canot initiate connection to blah blah blah". I haven't done anything to sources.list or modified my network setup. I am running ubuntu 10.10 server, if you need anything else just ask. i am connected via ssh and ready to go.

```

# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

``````

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0

```

---

### Post by wilee-nilee on 2011-02-20
So blah blah blah, then yadda yadda yadda.:)

Specificity will get you quick answers.

---

### Post by lkjoel on 2011-02-20
> **TechSupportx86 said:**
> I have been having some problems with apt-get in that it won't update and i can't install anything. When i run sudo apt-get update i get loads of errors saying "Failed to fetch http://..." and "canot initiate connection to blah blah blah". I haven't done anything to sources.list or modified my network setup. I am running ubuntu 10.10 server, if you need anything else just ask. i am connected via ssh and ready to go.

```

# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

``````

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0

```
I can't find any problems for now.
Could you post the complete output of apt-get update?

---

### Post by TechSupportx86 on 2011-02-20
This is all i can get:

```
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/multiverse Sources
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/main i386 Packages
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/restricted i386 Packages
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/universe i386 Packages
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]
Err http://uk.archive.ubuntu.com maverick Release.gpg
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates Release.gpg
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Ign http://uk.archive.ubuntu.com maverick Release
Ign http://uk.archive.ubuntu.com maverick-updates Release
Ign http://uk.archive.ubuntu.com maverick/main Sources
Ign http://uk.archive.ubuntu.com maverick/restricted Sources
Ign http://uk.archive.ubuntu.com maverick/universe Sources
Ign http://uk.archive.ubuntu.com maverick/multiverse Sources
Ign http://uk.archive.ubuntu.com maverick/main i386 Packages
Ign http://uk.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://uk.archive.ubuntu.com maverick/universe i386 Packages
Ign http://uk.archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://uk.archive.ubuntu.com maverick-updates/main Sources
Ign http://uk.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://uk.archive.ubuntu.com maverick-updates/universe Sources
Ign http://uk.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://uk.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://uk.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://uk.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://uk.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://uk.archive.ubuntu.com maverick/main Sources
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick/restricted Sources
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick/universe Sources
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick/multiverse Sources
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick/main i386 Packages
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick/restricted i386 Packages
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick/universe i386 Packages
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick/multiverse i386 Packages
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates/main Sources
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates/restricted Sources
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates/universe Sources
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates/multiverse Sources
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates/main i386 Packages
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates/restricted i386 Packages
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates/universe i386 Packages
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
Err http://uk.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)
W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (91.189.92.166). - connect (101: Network is unreachable) [IP: 91.189.92.166 80]

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

W: Failed to fetch http://uk.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to uk.archive.ubuntu.com:80 (194.169.254.10). - connect (101: Network is unreachable)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```


::EDIT::
Im also reading some other guides, some said trying the uk servers, that's why it's uk.archive

---

### Post by TechSupportx86 on 2011-02-20
This may also be helpfull:

```
nas@nas:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  cups linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  apparmor apparmor-utils bind9 bind9-doc bind9-host bind9utils bsdutils cups-bsd cups-client cups-common dnsutils dpkg fuse-utils hpijs ifupdown initscripts libapparmor-perl libapparmor1
  libbind9-60 libblkid1 libc-bin libc6 libcairo2 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbus-1-3 libdns66 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1
  libdrm2 libfreetype6 libfuse2 libgssapi-krb5-2 libhpmud0 libisc60 libisccc60 libisccfg60 libk5crypto3 libkrb5-3 libkrb5support0 liblcms1 libldap-2.4-2 liblwres60 libpam-modules libpam-runtime
  libpam-smbpass libpam0g libparted0debian1 libplymouth2 libpoppler7 libsqlite3-0 libssl0.9.8 libudev0 libuuid1 libwbclient0 libxml2 linux-firmware linux-headers-2.6.35-22
  linux-headers-2.6.35-22-generic-pae linux-image-2.6.35-22-generic-pae mount openssh-client openssh-server openssl parted plymouth plymouth-theme-ubuntu-text poppler-utils python python-apt
  python-minimal samba samba-common samba-common-bin samba-doc smbclient sudo sysv-rc sysvinit-utils tar tzdata udev update-inetd update-manager-core upstart util-linux uuid-runtime winbind
93 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 117MB of archives.
After this operation, 655kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dpkg mount tar libc-bin libc6 tzdata sysvinit-utils sysv-rc initscripts libdbus-1-3 libudev0 ifupdown upstart util-linux bsdutils python-minimal python libpam-modules
  linux-image-2.6.35-22-generic-pae libssl0.9.8 libuuid1 libblkid1 libpam-runtime libpam0g libsqlite3-0 libdrm2 libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 fuse-utils libfuse2 udev plymouth
  libplymouth2 apparmor libapparmor1 libapparmor-perl apparmor-utils libk5crypto3 libgssapi-krb5-2 libkrb5-3 libkrb5support0 libxml2 dnsutils bind9-host bind9 libisc60 libisccc60 libisccfg60
  libldap-2.4-2 liblwres60 bind9utils libdns66 libbind9-60 libfreetype6 libcairo2 libparted0debian1 openssh-server openssh-client parted plymouth-theme-ubuntu-text python-apt update-manager-core
  uuid-runtime bind9-doc libcups2 update-inetd cups-common cups-bsd libcupsimage2 cups-client hpijs libhpmud0 libcupscgi1 libcupsdriver1 libcupsmime1 libcupsppdc1 liblcms1 libpoppler7 smbclient
  samba-common-bin samba libpam-smbpass winbind samba-common libwbclient0 linux-firmware linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic-pae openssl poppler-utils samba-doc sudo
Install these packages without verification [y/N]?

```

---

### Post by TechSupportx86 on 2011-02-20
well i'm not 100% sure why, but i got apt-get to work. The only thing i can think that may have fixed it was generating a new sources.list (using a website), or adding the gateway IP to my interfaces file (Which should have been there in the first place). either way it just downloaded and installed torrentflux, so :confused:

---

### Post by volkswagner on 2011-02-21
> **TechSupportx86 said:**
> well i'm not 100% sure why, but i got apt-get to work. The only thing i can think that may have fixed it was generating a new sources.list (using a website), or **adding the gateway IP to my interfaces file **(Which should have been there in the first place). either way it just downloaded and installed torrentflux, so :confused:

Thank you for posting your solution.  I had the same problem.  For some reason I also originaly neglected to add the gateway address to my interfaces file.  Odd thing is I saw no other networking issues such as host command worked fine for internet domains.

---

### Post by mciverza on 2011-02-22
If you have no gateway address, your computer will not "know how" to access anything outside your LAN.
The gateway address is the address your computer will send network requests to, when the destination traffic is not on your network.

(probably archive.ubuntu.com is outside your LAN).

---

