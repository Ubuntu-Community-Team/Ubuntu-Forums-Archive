---
title: "apt-get update problem"
date: 2008-08-20
forum: Server Platforms
---

### Post by fouadk on 2008-08-20
hi everyone....

i have ubuntu server 8.04 64-bit

this is the output of the the sudo apt-get update

```

Hit http://main.archive.ubuntu.com hardy Release.gpg
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://main.archive.ubuntu.com hardy/main Translation-en_US
Ign http://main.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://main.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://main.archive.ubuntu.com hardy/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://main.archive.ubuntu.com hardy-updates Release.gpg
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Get:1 http://security.ubuntu.com hardy-security/universe Packages [28.4kB]
Get:2 http://security.ubuntu.com hardy-security/universe Sources [4530B]
Hit http://security.ubuntu.com hardy-security/multiverse Packages  
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://main.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://main.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://main.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://main.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://main.archive.ubuntu.com hardy Release
Hit http://main.archive.ubuntu.com hardy-updates Release                       
Hit http://main.archive.ubuntu.com hardy/main Packages                         
Hit http://main.archive.ubuntu.com hardy/restricted Packages
Hit http://main.archive.ubuntu.com hardy/main Sources
Hit http://main.archive.ubuntu.com hardy/restricted Sources
Hit http://main.archive.ubuntu.com hardy/universe Packages
Hit http://main.archive.ubuntu.com hardy/universe Sources
Hit http://main.archive.ubuntu.com hardy/multiverse Packages
Hit http://main.archive.ubuntu.com hardy/multiverse Sources
Hit http://main.archive.ubuntu.com hardy-updates/main Packages
Hit http://main.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://main.archive.ubuntu.com hardy-updates/main Sources
Hit http://main.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://main.archive.ubuntu.com hardy-updates/universe Packages
Hit http://main.archive.ubuntu.com hardy-updates/universe Sources
Hit http://main.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://main.archive.ubuntu.com hardy-updates/multiverse Sources
Fetched 2B in 5s (0B/s)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/univer
se/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/univer
se/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used
 instead.

```

and this is my sources.list

```

#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://main.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://main.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://main.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://main.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://main.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://main.archive.ubuntu.com/ubuntu/ hardy universe
deb http://main.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://main.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://main.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://main.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://main.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://main.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://main.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://main.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
"sources.list" 58L, 3191C
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

what am i getting those error message ????

please help

thanks in advance

---

### Post by cariboo on 2008-08-20
Have you tried a different server just to make sure there isn't a proble, with the main servers?

Jim

---

### Post by fouadk on 2008-08-20
i dont think there is something wrong with the main servers....

are you facing any problems with the main servers ????

---

### Post by vandamp on 2008-08-20
hey i got the same problem here, could it be that the main server is down?

---

