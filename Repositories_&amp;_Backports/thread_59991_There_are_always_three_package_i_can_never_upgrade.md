---
title: "There are always three package i can never upgrade..."
date: 2005-08-26
forum: Repositories &amp; Backports
---

### Post by magomago on 2005-08-26
regardless of whether i try synaptic smart upgrade or go in via apt-get terminal

it tells me of this when i try ubuntu update manager, and tells me to resolve it via synaptic or apt get
[b]
amarry@cv077078:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  firefox-gnome-support gaim gimp
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
[/b]

its ALWAYS those three pacakges...anyway i can upgrade them? (i checked my gaim its version 1.3 wheras the new one is 1.5 :()

---

### Post by Lord Illidan on 2005-08-26
Did you enable the extra repositories... check in the Ubuntu Guide...

---

### Post by magomago on 2005-08-26
[QUOTE=Lord Illidan]Did you enable the extra repositories... check in the Ubuntu Guide...[/QUOTE]
indeed i did and its how i do everything...i'll do it again for kicks, but it never updates

---

### Post by DJ_Max on 2005-08-26
Post your /etc/apt/sources.list

And do a little reading on why Ubuntu only has Gaim 1.3.

---

### Post by magomago on 2005-08-26
[QUOTE=DJ_Max]Post your /etc/apt/sources.list

And do a little reading on why Ubuntu only has Gaim 1.3.[/QUOTE]
------------------------------------------------------------------------------------------------
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## MY Test
## If I do not remove these...it complains about duplicates 24/7
## deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
## deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
------------------------------------------------------------------------------------------------

will go look for stuff about gaim ;)

---

