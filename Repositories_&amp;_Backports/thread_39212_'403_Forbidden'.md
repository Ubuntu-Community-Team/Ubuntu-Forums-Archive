---
title: "'403 Forbidden'"
date: 2005-06-03
forum: Repositories &amp; Backports
---

### Post by Hydrant on 2005-06-03
Apt-get has been working great for a few days now, then suddenly today, this happens:
```
hikaru79@navi:~/usbdisk$ sudo apt-get update
Ign http://us.archive.ubuntu.com hoary Release.gpg
Ign http://ca.archive.ubuntu.com hoary Release.gpg
Ign http://us.archive.ubuntu.com hoary-updates Release.gpg
Ign http://ca.archive.ubuntu.com hoary-updates Release.gpg
Ign http://us.archive.ubuntu.com hoary Release
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ca.archive.ubuntu.com hoary Release
Ign http://us.archive.ubuntu.com hoary-updates Release
Ign http://ca.archive.ubuntu.com hoary-updates Release
Hit http://security.ubuntu.com hoary-security Release
Hit http://archive.ubuntu.com hoary Release
Ign http://us.archive.ubuntu.com hoary/main Packages
Ign http://ca.archive.ubuntu.com hoary/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://us.archive.ubuntu.com hoary/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://ca.archive.ubuntu.com hoary/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://us.archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/multiverse Packages
Ign http://ca.archive.ubuntu.com hoary/main Sources
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://us.archive.ubuntu.com hoary/restricted Sources
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ca.archive.ubuntu.com hoary/restricted Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Ign http://us.archive.ubuntu.com hoary/universe Packages
Ign http://ca.archive.ubuntu.com hoary-updates/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://us.archive.ubuntu.com hoary/universe Sources
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Ign http://ca.archive.ubuntu.com hoary-updates/restricted Packages
Ign http://us.archive.ubuntu.com hoary-updates/main Packages
Ign http://ca.archive.ubuntu.com hoary-updates/main Sources
Ign http://us.archive.ubuntu.com hoary-updates/restricted Packages
Ign http://ca.archive.ubuntu.com hoary-updates/restricted Sources
Ign http://us.archive.ubuntu.com hoary-updates/main Sources
Err http://ca.archive.ubuntu.com hoary/main Packages
  403 Forbidden
Ign http://us.archive.ubuntu.com hoary-updates/restricted Sources
Err http://ca.archive.ubuntu.com hoary/restricted Packages
  403 Forbidden
Err http://us.archive.ubuntu.com hoary/main Packages
  403 Forbidden
Err http://ca.archive.ubuntu.com hoary/main Sources
  403 Forbidden
Err http://us.archive.ubuntu.com hoary/restricted Packages
  403 Forbidden
Err http://ca.archive.ubuntu.com hoary/restricted Sources
  403 Forbidden
Err http://us.archive.ubuntu.com hoary/main Sources
  403 Forbidden
Err http://ca.archive.ubuntu.com hoary-updates/main Packages
  403 Forbidden
Err http://us.archive.ubuntu.com hoary/restricted Sources
  403 Forbidden
Err http://ca.archive.ubuntu.com hoary-updates/restricted Packages
  403 Forbidden
Err http://us.archive.ubuntu.com hoary/universe Packages
  403 Forbidden
Err http://ca.archive.ubuntu.com hoary-updates/main Sources
  403 Forbidden
Err http://us.archive.ubuntu.com hoary/universe Sources
  403 Forbidden
Err http://ca.archive.ubuntu.com hoary-updates/restricted Sources
  403 Forbidden
Err http://us.archive.ubuntu.com hoary-updates/main Packages
  403 Forbidden
Err http://us.archive.ubuntu.com hoary-updates/restricted Packages
  403 Forbidden
Err http://us.archive.ubuntu.com hoary-updates/main Sources
  403 Forbidden
Err http://us.archive.ubuntu.com hoary-updates/restricted Sources
  403 Forbidden
Fetched 2B in 3s (1B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Is something wrong with the ubuntu repo? Here's my sources.list:
```
deb http://ca.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
Thanks in advance :)

---

### Post by michael376071 on 2005-06-03
Having similar probs, it seems the us repo is down  :-(

---

### Post by AndyAWS on 2005-06-03
Browsing through the official repos with firefox...they appear to be empty...

I would have expected to see some official announcement somewhere, if this were planned...

---

### Post by Hydrant on 2005-06-04
Eek, that's quite a problem :( Can anyone in some sort of position of authority confirm/deny this, or give some details?  :neutral:

---

### Post by dmccarney on 2005-06-04
I'm getting 404's for aproximately 9 of the Repisitories using Synaptic. If anyone has a fix I'd love to know it :) 

```
http://ca.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz: 404 Not Found
http://ca.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz: 404 Not Found
http://ca.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz: 404 Not Found
http://ca.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz: 404 Not Found
http://ca.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz: 404 Not Found
http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz: 404 Not Found
http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz: 404 Not Found
http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz: 404 Not Found
http://ca.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz: 404 Not Found
```

---

