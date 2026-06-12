---
title: "trying to ugrade old 12.04 server, but having no new release issues"
date: 2017-07-06
forum: Server Platforms
---

### Post by Heeter on 2017-07-06
Hi all,

I have a neglected server here:

```
root@ubuntuqc:/home/rsach# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

```

I am trying to upgrade using "do-release-upgrade", but comeup with no new releases

I am also trying to update && upgrade, but the sources.list items seem to be outdated.
```

root@ubuntuqc:/home/rsach# apt-get update
Err http://archive.canonical.com precise Release.gpg
  Temporary failure resolving 'archive.canonical.com'
Err http://extras.ubuntu.com precise Release.gpg
  Temporary failure resolving 'extras.ubuntu.com'
Err http://archive.ubuntu.com precise Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://security.ubuntu.com precise-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://archive.ubuntu.com precise-security Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://archive.ubuntu.com precise-updates Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://archive.ubuntu.com precise-proposed Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://us.archive.ubuntu.com precise Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com precise-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com precise-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... 99%

```

Can I try anything else?

I have my backups done and I am ready for system wide upgrade

This is my sources.list
```

#

# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted

#deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner

```

---

### Post by darkod on 2017-07-06
12.04 is already EOL and as such the repositories have moved. That is why you can't update/upgrade anything including a release upgrade.

But even if you upgrade to 14.04 you still need one more upgrade to reach 16.04. In these cases it mght be best to do new clean 16.04 install and just migrate applications/data.

If you do decide to try the EOL upgrade this should help you:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Heeter on 2017-07-07
Great, Thank you for that link

I am almost complete the upgrade

---

