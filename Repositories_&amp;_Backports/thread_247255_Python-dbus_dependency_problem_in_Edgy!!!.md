---
title: "Python-dbus dependency problem in Edgy!!!"
date: 2006-08-30
forum: Repositories &amp; Backports
---

### Post by tvlad on 2006-08-30
My problem is that after apt-getting from edgy repositories, i ended up with a broken package :

root@darkstar:/etc/init.d# apt-get install python-dbus
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  python-dbus
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
1 not fully installed or removed.
Need to get 0B/252kB of archives.
After unpacking 659kB of additional disk space will be used.
(Reading database ... 107604 files and directories currently installed.)
Unpacking python-dbus (from .../python-dbus_0.62-4ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python-dbus_0.62-4ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/dbus/dbus_bindings.so', which is also in package python2.4-dbus
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python-dbus_0.62-4ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

also of interest:

root@darkstar:/etc/init.d# apt-get install hal-device-manager
Reading package lists... Done
Building dependency tree... Done
hal-device-manager is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-app-install: Depends: python-dbus but it is not going to be installed
  hal-device-manager: Depends: python-dbus but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



here are the repositories i use : 
############# EDGY EFT ###################
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

############### DIVERSE ##################
Givre's repository (ntfs-3g & fuse 2.5.3)
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main
deb-src [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main

I also tried apt-get install -f, it does the same thing as apt-get install python-dbus, because it tries to install the same package, and thus generates the same error message.

---

### Post by givré on 2006-08-30
And what do you have when you try to remove python2.4-dbus and install after python-dbus?

---

### Post by tvlad on 2006-09-10
Thanks for trying to help Givre, somehow i got around that problem, i solved a few days ago, though the only thing i'm sure about is that it's solved, how exactly isn't that clear :roll:

---

### Post by DraXus on 2006-10-09
I have a similar problem. I have installed python-dbus, but a program depends of python2.4-dbus and both are in conflict. How could I fix it?

Is there any way to deceive this program in order to use python-dbus instead? :confused:

---

