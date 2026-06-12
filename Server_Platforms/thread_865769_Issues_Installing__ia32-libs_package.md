---
title: "Issues Installing  ia32-libs package"
date: 2008-07-21
forum: Server Platforms
---

### Post by sil3nt on 2008-07-21
Hi Guys,
       I am troubleshooting some issues on a new server build with 8.04 LTS. I have installed Vmware server and I am having issues getting it going because it cant find the above package.

I am specifically missing libXi.so.6, when I try using 

```
sudo apt-get install ia32-libs
```

I get the following :

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ia32-libs

``` 

I have the correct repo's available (needs universe), but just in case here is my sources.list

```

#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

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

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

```

For background I am using the 32Bit version of Ubuntu on a Core 2 Duo Machine (64Bit)

I have updated apt a number of times and I have the latest linux-headers installed.

I am pretty much completely lost and I would love to get vmware server (1.06) up and running but until I get this installed I fear I have no hope.

If you need anymore system info please let me know any details pointers or tips would be greatly appreciated.

---

### Post by windependence on 2008-07-21
Isn't ia32 an Itanium package? I think you have the wrong architecture.

Try these tutorials:

[http://ubuntuforums.org/showthread.php?t=788169](http://ubuntuforums.org/showthread.php?t=788169)

[http://www.howtoforge.com/vmware-server-on-ubuntu8.04](http://www.howtoforge.com/vmware-server-on-ubuntu8.04)

[http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04)

-Tim

---

