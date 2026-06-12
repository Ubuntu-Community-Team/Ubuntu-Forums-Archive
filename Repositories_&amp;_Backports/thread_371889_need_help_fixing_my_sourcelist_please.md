---
title: "need help fixing my sourcelist please"
date: 2007-02-27
forum: Repositories &amp; Backports
---

### Post by maddbaron on 2007-02-27
I can update but these four programs refuse to update, I have tried sudo apt-get upgrade/adept and nothing upgrades for these four. Someone suggested dist-upgrade and I still get the error.
> sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  audacity bmp-mp4 k3b libk3b2
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


Here is my sourcelist. Can someone please help me fix it?

> # If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

## Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

## Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse 

## Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse 

## Ubuntu supported packages (sources, GPG key: 437D05B5)
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted 
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse 
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse 

## Ubuntu commercial packages
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 

## RareWares/Debian Multi-Media Repository for Unstable

deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

## RareWares/Debian Multi-Media Repository for Unstable - Experimental Staging

deb [http://www.rarewares.org/debian/packages/experimental/](http://www.rarewares.org/debian/packages/experimental/) ./

#Debuntu Repo
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse 
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse 
#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse 
#AUTOMATIX REPOS END

---

### Post by MepisReign on 2007-02-27
Try this please

[http://www.ubuntuforums.org/showthread.php?t=345166](http://www.ubuntuforums.org/showthread.php?t=345166)

Regards,

MepisReign

---

### Post by MepisReign on 2007-03-01
It would be nice if you let us know if the link above helped you to fixed the problem ;)

Regards,

MepisReign

---

