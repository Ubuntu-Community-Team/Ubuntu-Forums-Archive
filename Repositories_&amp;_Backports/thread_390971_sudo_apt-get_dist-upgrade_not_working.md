---
title: "sudo apt-get dist-upgrade not working"
date: 2007-03-22
forum: Repositories &amp; Backports
---

### Post by lvleph on 2007-03-22
Not sure if I should put this here or in feisty discussion...

I tried to use 
```
sudo apt-get dist-upgrade
```
but I got
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
I am currently using Edgy Eft, so I should be able to upgrade

my /etc/apt/sources.list
```
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
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

#deb http://security.ubuntu.com/ubuntu edgy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#I added the following lines
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen
deb http://ubuntu.beryl-project.org/ edgy main

#The following is for ntfs-3g 
deb http://flomertens.free.fr/ubuntu/ edgy main main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
deb http://flomertens.keo.in/ubuntu/ edgy main main-all

```

Anyone have a clue why this is not working?

---

### Post by dougfractal on 2007-03-22
did you try

sudo apt-get dist-upgrade

N.B.  the hyphen between dist upgrade

---

### Post by lvleph on 2007-03-22
> **dougfractal said:**
> did you try

sudo apt-get dist-upgrade

N.B.  the hyphen between dist upgrade
That was a typo in my post. I fixed it.

---

### Post by bapoumba on 2007-03-22
@ lvleph: all your repositories are edgy's, you wont dist-upgrade to feisty that way ;)
Are you sure you want to do that ? Feisty is not stable yet, may be difficult to handle sometimes. It's probably wise to wait, unless you have a reason for it.

---

### Post by lvleph on 2007-03-22
I have a few things that I use that have been fixed in Feisty that don't work in Edgy and that is why I am not patient. I don't mind so much if it is not stable.

EDIT: Thank you for letting me know why I am stupid. I have everything straightened out now.

---

