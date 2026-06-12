---
title: "K3B not installing"
date: 2005-10-02
forum: Repositories &amp; Backports
---

### Post by BdON003 on 2005-10-02
I am trying to install this and I get this error when trying to install the k3blib 
"k3blibs:
Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
Depends: libidn11 (>=0.5.13) but 0.5.2-3 is to be installed
Depends: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed
Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
Depends: libvorbisenc2 (>=1.1.0) but 1.0.1-1 is to be installed
Depends: libvorbisfile3 (>=1.1.0) but 1.0.1-1 is to be installed"
when I try to install the k3blibs from the synaptic package manager. I get a similar error message when I try to install k3b. Any help? I have the universe repository added  I have already installed the kdelib repository, but is there more that I have to?

---

### Post by aysiu on 2005-10-02
I don't know if I can help, but I'm sure someone else will be better able to help you if you post your /etc/apt/sources.list

---

### Post by BdON003 on 2005-10-02
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

 deb [http://www.planet-moll.de/debian](http://www.planet-moll.de/debian) sarge main

---

### Post by claydoh on 2005-10-02
Perhaps disable the debian sarge repo might help? I would think that the debian  repository is conflicting with Ubuntu repositories.

---

### Post by aysiu on 2005-10-02
Also, the mirrormax backports are down, I think.

[http://ubuntuforums.org/showthread.php?t=69681](http://ubuntuforums.org/showthread.php?t=69681)

---

### Post by BdON003 on 2005-10-02
[QUOTE=claydoh]Perhaps disable the debian sarge repo might help? I would think that the debian  repository is conflicting with Ubuntu repositories.[/QUOTE]
That did the trick.  So I am just curious why that was a conflict?  I don't get exactly how the sources.list file works

---

### Post by claydoh on 2005-10-02
Although Ubuntu is debian-based, there are enough differences in package versions and names to confuse things.

---

### Post by bluhound on 2005-10-08
Managed to try it on a fresh Breezy Badger Preview installation with all the repositories unlocked.
Try it and see wether it works for you.

root@ubuntu:/media/hda5/linux# apt-get install k3b
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  k3b: Depends: k3blibs (>= 0.12.2) but it is not going to be installed
       Depends: kdelibs4c2 (>= 4:3.4.2) but it is not going to be installed
       Depends: libdbus-qt-1-1c2 (>= 0.36.2) but it is not going to be installed
       Depends: libqt3-mt (>= 3:3.3.4) but it is not going to be installed
       Depends: kdelibs-data (>= 4:3.1.4-2) but it is not going to be installed
       Depends: kdebase-bin but it is not going to be installed
       Depends: kcontrol but it is not going to be installed
  libqt3c102-mt: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/media/hda5/linux# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gcc-3.3-base libstdc++5
The following NEW packages will be installed:
  gcc-3.3-base libstdc++5
0 upgraded, 2 newly installed, 0 to remove and 465 not upgraded.
1 not fully installed or removed.
Need to get 446kB of archives.
After unpacking 1077kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main gcc-3.3-base 1:3.3.6-8ubuntu1 [150kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libstdc++5 1:3.3.6-8ubuntu1 [295kB]
Fetched 446kB in 1m41s (4372B/s)

Preconfiguring packages ...
Selecting previously deselected package gcc-3.3-base.
(Reading database ... 57528 files and directories currently installed.)
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-8ubuntu1_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-8ubuntu1_i386.deb) ...
Setting up gcc-3.3-base (3.3.6-8ubuntu1) ...
Setting up libstdc++5 (3.3.6-8ubuntu1) ...

Setting up libqt3c102-mt (3.3.3-7ubuntu3) ...

root@ubuntu:/media/hda5/linux# apt-get install k3b
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  k3blibs kcontrol kdebase-bin kdebase-data kdelibs-bin kdelibs-data kdelibs4c2 libarts1c2 libdbus-qt-1-1c2 libflac++5c2
  libnetpbm10 libopenexr2c2 libpcre3 libqt3-mt libtag1c2 menu-xdg netpbm
Suggested packages:
  k3b-i18n normalize-audio toolame sox movixmaker-2 k3b-mp3 khelpcenter libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc
Recommended packages:
  vcdimager cdrdao perl-suid akode menu
The following packages will be REMOVED:
  libqt3c102-mt
The following NEW packages will be installed:
  k3b k3blibs kcontrol kdebase-bin kdebase-data kdelibs-bin kdelibs-data kdelibs4c2 libarts1c2 libdbus-qt-1-1c2
  libflac++5c2 libnetpbm10 libopenexr2c2 libpcre3 libqt3-mt libtag1c2 menu-xdg netpbm
0 upgraded, 18 newly installed, 1 to remove and 465 not upgraded.
Need to get 39.7MB/39.9MB of archives.
After unpacking 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libqt3-mt 3:3.3.4-8ubuntu5 [3290kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libarts1c2 1.4.2-0ubuntu3 [1179kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libopenexr2c2 1.2.2-3ubuntu1 [296kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main menu-xdg 0.2ubuntu1 [4026B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libnetpbm10 2:10.0-8ubuntu1 [61.4kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main netpbm 2:10.0-8ubuntu1 [1161kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main kdelibs-bin 4:3.4.2-0ubuntu7 [813kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main kdelibs-data 4:3.4.2-0ubuntu7 [6968kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main kdelibs4c2 4:3.4.2-0ubuntu7 [8067kB]
The list goes on.......

---

### Post by bluhound on 2005-10-08
Forgot to add one thing.  I am using Ubuntu, not Kubuntu.

---

### Post by claydoh on 2005-10-08
What hppens at the end?  You stopped the paste after downloading half of the dependencies, so we can't see any errors.

>  Get:1 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main libqt3-mt 3:3.3.4-8ubuntu5 [3290kB]
Get:2 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main libarts1c2 1.4.2-0ubuntu3 [1179kB]
Get:3 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main libopenexr2c2 1.2.2-3ubuntu1 [296kB]
Get:4 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main menu-xdg 0.2ubuntu1 [4026B]
Get:5 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main libnetpbm10 2:10.0-8ubuntu1 [61.4kB]
Get:6 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main netpbm 2:10.0-8ubuntu1 [1161kB]
Get:7 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main kdelibs-bin 4:3.4.2-0ubuntu7 [813kB]
Get:8 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main kdelibs-data 4:3.4.2-0ubuntu7 [6968kB]
Get:9 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") breezy/main kdelibs4c2 4:3.4.2-0ubuntu7 [8067kB]
The list goes on.......

---

