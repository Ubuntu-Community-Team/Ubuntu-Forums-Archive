---
title: "Crash report cannot be processed"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jasonsmith01 on 2012-03-28
Can anyone help with why my packages appear to newer than required. What may have caused this? I update regularly, maybe too frequent?


libgtk-3-common version 3.3.20-0ubuntu1 required, but 3.4.0-0ubuntu1 is available
libdconf0 version 0.11.7-0ubuntu1 required, but 0.12.0-0ubuntu1 is available
outdated debug symbol package for libdconf0: package version 0.12.0-0ubuntu1 dbgsym version 0.11.7-0ubuntu1
gnome-settings-daemon version 3.3.92-0ubuntu2 required, but 3.4.0-0ubuntu1 is available
outdated debug symbol package for gnome-settings-daemon: package version 3.4.0-0ubuntu1 dbgsym version 3.3.92-0ubuntu2
nautilus-data version 1:3.3.92-0ubuntu2 required, but 1:3.4.0-0ubuntu1 is available
libglib2.0-0 version 2.31.22-0ubuntu1 required, but 2.32.0-0ubuntu1 is available
outdated debug symbol package for libcolord1: package version 0.1.16-2 dbgsym version 0.1.12-1ubuntu2.1
dconf-service version 0.11.7-0ubuntu1 required, but 0.12.0-0ubuntu1 is available
outdated debug symbol package for dconf-service: package version 0.12.0-0ubuntu1 dbgsym version 0.11.7-0ubuntu1
gnome-desktop3-data version 3.3.92-0ubuntu1 required, but 3.4.0-0ubuntu1 is available
libgnome-desktop-3-2 version 3.3.92-0ubuntu1 required, but 3.4.0-0ubuntu1 is available
outdated debug symbol package for libgnome-desktop-3-2: package version 3.4.0-0ubuntu1 dbgsym version 3.3.92-0ubuntu1
libgtk-3-0 version 3.3.20-0ubuntu1 required, but 3.4.0-0ubuntu1 is available
gsettings-desktop-schemas version 3.3.92-0ubuntu1 required, but 3.4.0-0ubuntu1 is available
dconf-gsettings-backend version 0.11.7-0ubuntu1 required, but 0.12.0-0ubuntu1 is available
outdated debug symbol package for dconf-gsettings-backend: package version 0.12.0-0ubuntu1 dbgsym version 0.11.7-0ubuntu1
outdated debug symbol package for librsvg2-common: package version 2.36.0-0ubuntu1 dbgsym version 2.35.2-0ubuntu1

---

### Post by dino99 on 2012-03-28
Please post your sources.list

sudo gedit /etc/apt/sources.list
ls -l  /etc/apt/sources.list.d/

---

### Post by jasonsmith01 on 2012-03-28
> **dino99 said:**
> Please post your sources.list

sudo gedit /etc/apt/sources.list
ls -l  /etc/apt/sources.list.d/

Thanks for the help, here they are. 

sudo gedit /etc/apt/sources.list
```
# 

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ precise main restricted

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120301)]/ precise main restricted

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
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

ls -l /etc/apt/sources.list.d/

```
-rw-r--r-- 1 root root 134 Mar 21 20:33 atareao-atareao-precise.list
-rw-r--r-- 1 root root 132 Mar 21 20:33 eugenesan-java-precise.list
-rw-r--r-- 1 root root 132 Mar 21 20:33 eugenesan-java-precise.list.save
-rw-r--r-- 1 root root 175 Mar 21 20:33 google-earth.list
-rw-r--r-- 1 root root 175 Mar 21 20:33 google-earth.list.save
-rw-r--r-- 1 root root 182 Mar 21 20:33 google-musicmanager.list
-rw-r--r-- 1 root root 182 Mar 21 20:33 google-musicmanager.list.save
-rw-r--r-- 1 root root 168 Mar 21 20:20 indicator-multiload-stable-daily-precise.list
-rw-r--r-- 1 root root 154 Mar 21 20:33 unity-team-lenses-testing-precise.list
-rw-r--r-- 1 root root 154 Mar 21 20:33 unity-team-lenses-testing-precise.list.save
-rw-r--r-- 1 root root  71 Mar 21 20:33 virtualbox.list
-rw-r--r-- 1 root root  71 Mar 21 20:33 virtualbox.list.save

```

---

### Post by dino99 on 2012-03-28
All seems ok there

some cleanings:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

---

### Post by jasonsmith01 on 2012-03-28
> **dino99 said:**
> All seems ok there

Thank goodness, I thought I broke something. I will get to the cleaning asap. 

Thank you, much appreciated.

---

### Post by jasonsmith01 on 2012-03-28
All done. Hopefully this end result was okay. Should that correct the initial incompatibility you think? 

sudo dpkg-reconfigure -phigh -a

```

Package `gtk2-engines-oxygen' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gtk2-engines-oxygen is not installed

```

---

### Post by dino99 on 2012-03-28
gtk2-engines-oxygen is not a genuine Precise package, meaning that one of your used ppa is outdated.
As you dont use ppa actually, those listed inside sources.list.d need to be removed

sudo rm /etc/apt/sources.list.d/*

---

### Post by dcstar on 2012-03-28
> **jasonsmith01 said:**
> Can anyone help with why my packages appear to newer than required. What may have caused this? 
............

This can happen when the repository you are using is only part way though being updated and the packages and catalogue are no longer in sync.

With so many 12.04 updates appearing at the moment this is always a chance of happening.

---

### Post by jasonsmith01 on 2012-03-28
That makes sense. I sure have been doing a lot of updates lately. I guess this is just part of the beta process. Never been in a beta OS process before, fun but sure is a learning experience.

---

