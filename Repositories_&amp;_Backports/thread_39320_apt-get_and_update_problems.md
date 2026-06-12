---
title: "apt-get and update problems"
date: 2005-06-04
forum: Repositories &amp; Backports
---

### Post by btumpps on 2005-06-04
hello ppl. i have two problems, one with apt-get install and one with automatic updates. 

the apt-get problem is: whenever i want to install something with the command "apt-get install sth" i got these warnings and errors:

bsevindi@ubuntu:~$ sudo apt-get install amule
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libpng10-0 libwxbase2.4 libwxgtk2.4
Recommended packages:
  amule-utils
The following NEW packages will be installed:
  amule libpng10-0 libwxbase2.4 libwxgtk2.4
0 upgraded, 4 newly installed, 0 to remove and 22 not upgraded.
Need to get 5060kB of archives.
After unpacking 7094kB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  amule
Install these packages without verification [y/N]?
E: Some packages could not be authenticated

note: it's not only about the program amule. i got this error on every program i want to install.

the second problem is about updates. i am using ubuntu with gnome and on the bottom right part of the toolbar there is an icon that says "there are 22 updates avaible". i clicked that and the updates are installed but the icon still stands there. BTW, i also got the warning "not authenticated" while the updates are being downloaded, but the download process continued.

maybe my sources.list file will be useful. here is the copy of it:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

thanks already

---

### Post by DJ_Max on 2005-06-04
Try changes your sources to another mirror. Maybe those packages in that mirror are signed.

---

