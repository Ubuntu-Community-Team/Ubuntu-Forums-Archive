---
title: "broken dependencies 9.10 server"
date: 2009-11-03
forum: Server Platforms
---

### Post by corrosion on 2009-11-03
Hello all,

Yesterday I installed a clean 9.10 64bit on my primary server. It was running 9.04 (upgraded from 8.10) and it was running perfectly. One of its purposes is to run VMware Server2.

The problem I found now, is that, I want the machine to have a gnome desktop environment so, if I need, I can launch nautilus, brasero or other utils via remote ssh. I want all gnome environment so I have all the basic desktop apps I would like to use ocassionally. I'm using France mirror since Spanish (the one I should use) works very awful.

> crsn@gandalf:~$ sudo apt-get install gnome-desktop-environment
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-desktop-environment: Depends: gnome-core (= 1:2.22.2~4ubuntu8) but it is not going to be installed
                             Depends: deskbar-applet (>= 2.22.2.1) but it is not going to be installed
                             Depends: evolution (>= 2.22.2) but it is not going to be installed
                             Depends: fast-user-switch-applet (>= 2.22.0) but it is not installable
                             Depends: gdm (>= 2.20.6)
                             Depends: gnome-about (>= 2.22.2) but it is not going to be installed
                             Depends: gnome-netstatus-applet (>= 2.12.1) but it is not going to be installed
                             Depends: gnome-power-manager (>= 2.22.1) but it is not going to be installed
                             Depends: gnome-utils (>= 2.20.0.1) but it is not going to be installed
                             Depends: gnome-volume-manager (>= 2.22.1) but it is not going to be installed
                             Depends: vinagre (>= 0.5.1) but it is not going to be installed
                             Depends: libgnomevfs2-bin (>= 1:2.22.0) but it is not going to be installed
                             Depends: libgnomevfs2-extra (>= 1:2.22.0) but it is not going to be installed
                             Depends: libgnome2-perl (>= 1.042) but it is not going to be installed
                             Recommends: gnome-accessibility but it is not going to be installed
E: Broken packages

Any help? Any other one with the same problem?

PD: for those who want, here is sources.list:
> crsn@gandalf:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release amd64 (20091027.2)]/ karmic main restricted

#deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release amd64 (20091027.2)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


---

### Post by eldaria on 2009-11-06
No solution, but I have the same issue, it seems it does not like you to install gdm on 64 bit server.
I'm going to try 32 bit server, will see if it works better.

---

### Post by Vegan on 2009-11-06
Use the desktop version if you need it, then install the LAMP via TASKSEL.

---

### Post by eldaria on 2009-11-06
32 bit server edition also broken, this is however new, since I tried the Releas candidate before and it worked.

Using Desktop edition is not a good idea for server applications, as far as I know the kernel used in server is optimized for server tasks where as the desktop edition is for Desktop usage, why else have two different kernels?

---

### Post by eldaria on 2009-11-09
Strange, I reinstalled and tried without making any initial changes, and now it works.
The changes I had made before, were some changes to the network interfaces, and the sources.list file. I suspect this last one to be the reason.

I was using an Internal repository at IBM, but even after removing all of them and setting it back to external repositories, I got the error.

But after a reinstall and changing to the exacty same external repositories it works.

So not actually sure what was causing this.

---

