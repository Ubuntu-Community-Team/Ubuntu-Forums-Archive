---
title: "apt suddenly fails to update sources"
date: 2010-02-26
forum: Server Platforms
---

### Post by dragos2 on 2010-02-26
On Ubuntu 8.04 64 bit.

Today I tried to install libgtk2.0-dev 
```

apt-get install libgtk2.0-dev

```

but I did non updates the sources before with apt-get update and it failed because it
could not fetch sources.

Then I did an 

```

apt-get update

```

and it can't fetch the sources:

```

root@ubu02:/home/dragos# apt-get update
Err http://cz.archive.ubuntu.com hardy Release.gpg
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Err http://cz.archive.ubuntu.com hardy/main Translation-en_US
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Err http://cz.archive.ubuntu.com hardy/restricted Translation-en_US
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Err http://cz.archive.ubuntu.com hardy/universe Translation-en_US
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Err http://cz.archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Err http://cz.archive.ubuntu.com hardy-updates Release.gpg
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Err http://cz.archive.ubuntu.com hardy-updates/main Translation-en_US
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Err http://cz.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Err http://cz.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Err http://cz.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Reading package lists... Done
W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Failed to fetch http://cz.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to cz.archive.ubuntu.com:80 (217.31.205.123). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

Any ideas of what happened ? 

This is the sources.list

```

root@ubu02:/home/dragos# cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 8.04.2 _Hardy Heron_ - Release amd64 (20090121.1)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04.2 _Hardy Heron_ - Release amd64 (20090121.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://cz.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://cz.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cz.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://cz.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://cz.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://cz.archive.ubuntu.com/ubuntu/ hardy universe
deb http://cz.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://cz.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cz.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://cz.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://cz.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://cz.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cz.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://cz.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
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

This server is hosted in Czech republic as you can see, the system was untouched
at the admin level before this error.

Is there anything with the local caches from Czech republic ?

---

### Post by dragos2 on 2010-02-26
Czech repositories back online and working.

---

