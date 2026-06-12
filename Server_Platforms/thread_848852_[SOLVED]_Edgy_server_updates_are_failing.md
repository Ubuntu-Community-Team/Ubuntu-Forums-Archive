---
title: "[SOLVED] Edgy server updates are failing"
date: 2008-07-03
forum: Server Platforms
---

### Post by r0ydster on 2008-07-03
I have a box running Edgy 6.10 server - no X, no desktop.

When I run apt-get update this is what I get:

```

Ign http://us.archive.ubuntu.com edgy Release.gpg
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security Release.gpg
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates Release.gpg
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-backports Release.gpg
Ign http://us.archive.ubuntu.com edgy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-backports/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security Release
Ign http://us.archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy Release  
Ign http://us.archive.ubuntu.com edgy-updates Release
Ign http://security.ubuntu.com edgy-security/main Packages
Ign http://us.archive.ubuntu.com edgy-backports Release
Ign http://us.archive.ubuntu.com edgy/main Packages
Ign http://us.archive.ubuntu.com edgy/restricted Packages
Ign http://us.archive.ubuntu.com edgy/main Sources
Ign http://security.ubuntu.com edgy-security/restricted Packages
Ign http://security.ubuntu.com edgy-security/main Sources
Ign http://security.ubuntu.com edgy-security/restricted Sources
Ign http://us.archive.ubuntu.com edgy/restricted Sources
Ign http://us.archive.ubuntu.com edgy/universe Packages
Ign http://us.archive.ubuntu.com edgy/universe Sources
Ign http://us.archive.ubuntu.com edgy-updates/main Packages
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages
Ign http://us.archive.ubuntu.com edgy-updates/main Sources
Ign http://us.archive.ubuntu.com edgy-updates/restricted Sources
Ign http://security.ubuntu.com edgy-security/universe Packages
Ign http://security.ubuntu.com edgy-security/universe Sources
Err http://security.ubuntu.com edgy-security/main Packages
  404 Not Found
Ign http://us.archive.ubuntu.com edgy-backports/main Packages
Ign http://us.archive.ubuntu.com edgy-backports/restricted Packages
Ign http://us.archive.ubuntu.com edgy-backports/universe Packages
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com edgy-backports/main Sources
Ign http://us.archive.ubuntu.com edgy-backports/restricted Sources
Err http://security.ubuntu.com edgy-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/main Sources
  404 Not Found
Ign http://us.archive.ubuntu.com edgy-backports/universe Sources
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Sources
Err http://us.archive.ubuntu.com edgy/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com edgy-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-backports/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-backports/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-backports/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-backports/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-backports/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com edgy-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```


Here is my /etc/apt/sources.list file:

```

#deb-src http://http.us.debian.org/debian stable main contrib non-free 
#deb-src http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
# 
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


#deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```


Is this repo still available?  Do I need to pick another one?

I want to do an in-place upgrade from 6.10 to 8.04 Server.  I have this box configured as a LAMP and Email server, and I don't want to rebuild/reconfigure everything.

Thanks for the help.

Mike

---

### Post by ibutho on 2008-07-03
Its my understanding the Ubuntu Edgy is no longer supported, so maybe thats why you are experiencing these problems. Try upgrading to a newer release.

---

### Post by r0ydster on 2008-07-04
I thought 6.10 wan an LTR, but maybe not.

I was going to try to upgrade to 7.X, then upgrade to 8.04 LTR.

Just thought that maybe someone had a similar experience.

Mike

---

### Post by sjwk on 2008-07-04
Yep, I ran into that the other day.  Bit of a pain, but meant I had to spend time upgrading an old machine shortly before it gets scrapped...

It was 6.06 that was the previous LTS version, not 6.10.

Steve.

---

### Post by r0ydster on 2008-07-05
Thanks for the update.

I will try the upgrade to 7.x then to 8.4 route.

Mike

Update:

I was able to update the box from 6.10 to 8.04.1.

Here is what I did:

as root:

1) change from edgy to feisty:
sed -e 's/\edgy/feisty/g' -i /etc/apt/sources.list

2)apt-get update && apt-get upgrade && apt-get dist-upgrade
took about an 90 minutes.

rebooted to 7.04 server

as root: 
3) do-release-upgrade
this took about an hour as it took me from Feisty to Gutsy.

rebooted to 7.10 server

as root:
4) do-release-upgrade
about another hour to take me from Gutsy to Hardy

rebooted to a working 8.04.1 server

I kept most of my conf files the same, and so far everything seem to be working.

Mike

---

