---
title: "libapache2-mod-fastcgi"
date: 2005-12-11
forum: Server Platforms
---

### Post by iwalmsley on 2005-12-11
libapache2-mod-fastcgi -- getting from apt-get having issues:

Reading package lists... Done
Building dependency tree... Done
Package libapache2-mod-fastcgi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-fastcgi has no installation candidate

Anyone else come across this?

---

### Post by J.C. Denton on 2005-12-11
Do you have multiverse enabled in your /etc/apt/sources.list?

---

### Post by iwalmsley on 2005-12-11
I had tried that before (adding multiverse), and tried it again and got this error:

root@luther:/home/iwalmsley# apt-get install libapache2-mod-fastcgi
Reading package lists... Done
Building dependency tree... Done
Package libapache2-mod-fastcgi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-fastcgi has no installation candidate

---

### Post by J.C. Denton on 2005-12-11
[QUOTE=iwalmsley]I had tried that before (adding multiverse), and tried it again and got this error:

root@luther:/home/iwalmsley# apt-get install libapache2-mod-fastcgi
Reading package lists... Done
Building dependency tree... Done
Package libapache2-mod-fastcgi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-fastcgi has no installation candidate[/QUOTE]
You trimmed some stuff in your last edit.  Can you put it back? Can you also post your sources file?

---

### Post by iwalmsley on 2005-12-11
I trimmed the errors I recieved for not running the apt-get update command, I ran the command and the errors went away.

here is my sources file:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by J.C. Denton on 2005-12-11
Ah, you need to add multiverse to the main "breezy" repo.  Then do an update, then try to install.

---

### Post by iwalmsley on 2005-12-11
Yes! that worked!

root@luther:/home/iwalmsley# apt-get install libapache2-mod-fastcgi
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libapache2-mod-fastcgi
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 63.1kB of archives.
After unpacking 258kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse libapache2-mod-fastcgi 2.4.2-6 [63.1kB]
Fetched 63.1kB in 0s (93.6kB/s)

Preconfiguring packages ...
Selecting previously deselected package libapache2-mod-fastcgi.
(Reading database ... 16240 files and directories currently installed.)
Unpacking libapache2-mod-fastcgi (from .../libapache2-mod-fastcgi_2.4.2-6_i386.deb) ...
Setting up libapache2-mod-fastcgi (2.4.2-6) ...

Thanks a million!

---

