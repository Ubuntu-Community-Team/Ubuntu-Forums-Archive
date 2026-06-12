---
title: "package python3 3.2.3-2 failed to install/upgrade"
date: 2012-07-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by paul_in_london on 2012-07-12
```
 ...
Unpacking replacement libxatracker1:amd64 ...
Setting up python3 (3.2.3-2ubuntu1) ...
running python rtupdate hooks for python3.2...
Usage: py3clean [-V VERSION] [-p PACKAGE | DIR_OR_FILE]

py3clean: error: only one action is allowed at the same time (cleaning directory
 or a package)
error running python rtupdate hook screen-resolution-extra
dpkg: error processing python3 (--configure):
 subprocess installed post-installation script returned error exit status 4
Setting up libgbm1:amd64 (8.1~git20120712.fe911c1d-0ubuntu0sarvatt3) ...
```

There's a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1024016](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1024016)

---

### Post by mcellius on 2012-07-12
Same thing here.

---

### Post by kuvanito on 2012-07-12
me 3

---

### Post by mc4man on 2012-07-12
Had no issue here with the 3 recent python upgrades though always use synaptic & generally break a set up into several groups of related packages.
So as it was python was done by itself & presented no issue

---

### Post by scradock on 2012-07-12
I tried the fix suggested in the bug report (editing one line in /usr/share/python3/runtime.d/ubuntu-drivers-common.rtupdate, but it did not remove the Broken Package flag, or allow the install of the latest python3 to complete properly.

To achieve that I had to downgrade python3 and python3-minimal (first) to the straight 3.2.3.2 version (not the 0ubuntu1 or 2 version), then update/upgrade again from there. It looks as if one version of the python3 package required exactly version 3.2.3.2 of python3-minimal, and 3.2.3.2-0ubuntu2 wasn't recognized as a match.

Anyway, now it's fixed...

---

### Post by mc4man on 2012-07-12
there will be some more updates to that source in the near future
[https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3](https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3)

---

### Post by paul_in_london on 2012-07-13
> **mc4man said:**
> there will be some more updates to that source in the near future
[https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3](https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3)

Seems to be fixed now:

```
Setting up libxatracker1:amd64 (8.1~git20120712.fe911c1d-0ubuntu0sarvatt3) ...
Setting up python3-minimal (3.2.3-3ubuntu1) ...
**Setting up python3 (3.2.3-3ubuntu1) ...**
running python rtupdate hooks for python3.2...
running python post-rtupdate hooks for python3.2...
Setting up firefox-trunk (16.0~a1~hg20120712r98952-0ubuntu1~umd1) ...
```

---

### Post by mcellius on 2012-07-13
It doesn't appear to be solved yet, or if it was it left another problem in its wake:

```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python3 : Depends: python3-minimal (= 3.2.3-2ubuntu1) but 3.2.3-3ubuntu1 is installed
 python3-software-properties : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-gtk : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 ubuntu-drivers-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.
mdk@savina:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-champlain-0.12 gir1.2-clutter-1.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-gtkchamplain-0.12 gir1.2-gtkclutter-1.0
  libchamplain-0.12-0 libchamplain-gtk-0.12-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python3
Suggested packages:
  python3-doc python3-tk
The following packages will be upgraded:
  python3
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
6 not fully installed or removed.
Need to get 0 B/33.0 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of python3:
 python3 depends on python3-minimal (= 3.2.3-2ubuntu1); however:
  Version of python3-minimal on system is 3.2.3-3ubuntu1.

dpkg: error processing python3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-common:
 nvidia-common depends on ubuntu-drivers-common; however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing nvidia-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        dpkg: error processing python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.
 software-properties-common depends on python3-software-properties; however:
  Package python3-software-properties is not configured yet.

dpkg: error processing software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.
 software-properties-gtk depends on python3-software-properties; however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not confNo apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            igured yet.

dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3
 ubuntu-drivers-common
 nvidia-common
 python3-software-properties
 software-properties-common
 software-properties-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Salane on 2012-07-13
> **paul_in_london said:**
> Seems to be fixed now:

```
Setting up libxatracker1:amd64 (8.1~git20120712.fe911c1d-0ubuntu0sarvatt3) ...
Setting up python3-minimal (3.2.3-3ubuntu1) ...
**Setting up python3 (3.2.3-3ubuntu1) ...**
running python rtupdate hooks for python3.2...
running python post-rtupdate hooks for python3.2...
Setting up firefox-trunk (16.0~a1~hg20120712r98952-0ubuntu1~umd1) ...
```

Not on my system 


```
dpkg: dependency problems prevent configuration of python3-aptdaemon.pkcompat:
 python3-aptdaemon.pkcompat depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.

dpkg: error processing python3-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because MaxReports is reached already
                                                              ldconfig deferred processing now taking place
Errors were encountered while processing:
 python3
 ubuntu-drivers-common
 nvidia-common
 python3-software-properties
 software-properties-common
 software-properties-gtk
 software-properties-kde
 printer-driver-foo2zjs
 python3-aptdaemon.pkcompat
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing software-properties-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3:
 python3 depends on python3-minimal (= 3.2.3-2ubuntu1); however:
  Version of python3-minimal on system is 3.2.3-3ubuntu1.

dpkg: error processing python3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.

dpkg: error processing ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-common:
 nvidia-common depends on ubuntu-drivers-common; however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing nvidia-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.
 software-properties-gtk depends on python3-software-properties; however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.

dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.pkcompat:
 python3-aptdaemon.pkcompat depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.

dpkg: error processing python3-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-foo2zjs:
 printer-driver-foo2zjs depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing printer-driver-foo2zjs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 software-properties-kde
 software-properties-common
 python3
 ubuntu-drivers-common
 nvidia-common
 python3-software-properties
 software-properties-gtk
 python3-aptdaemon.pkcompat
 printer-driver-foo2zjs

```

---

### Post by pressureman on 2012-07-13
On my system, apt-get had got its panties in such a bunch that I resorted to simply downloading the .deb and installing it with 'dpkg -i --force-all'.

Problem fixed.

Sometimes apt-get is too smart for its own good.

---

### Post by Salane on 2012-07-13
> **pressureman said:**
> On my system, apt-get had got its panties in such a bunch that I resorted to simply downloading the .deb and installing it with 'dpkg -i --force-all'.

Problem fixed.

Sometimes apt-get is too smart for its own good.

Well at least that worked. Thanks :guitar:

---

### Post by paul_in_london on 2012-07-13
> **Salane said:**
> Not on my system 


```
dpkg: dependency problems prevent configuration of python3-aptdaemon.pkcompat:
 python3-aptdaemon.pkcompat depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.

dpkg: error processing python3-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because MaxReports is reached already
                                                              ldconfig deferred processing now taking place
Errors were encountered while processing:
 python3
 ubuntu-drivers-common
 nvidia-common
 python3-software-properties
 software-properties-common
 software-properties-gtk
 software-properties-kde
 printer-driver-foo2zjs
 python3-aptdaemon.pkcompat
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing software-properties-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3:
 python3 depends on python3-minimal (= 3.2.3-2ubuntu1); however:
  Version of python3-minimal on system is 3.2.3-3ubuntu1.

dpkg: error processing python3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.

dpkg: error processing ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-common:
 nvidia-common depends on ubuntu-drivers-common; however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing nvidia-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.
 software-properties-gtk depends on python3-software-properties; however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.

dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.pkcompat:
 python3-aptdaemon.pkcompat depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.

dpkg: error processing python3-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-foo2zjs:
 printer-driver-foo2zjs depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing printer-driver-foo2zjs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 software-properties-kde
 software-properties-common
 python3
 ubuntu-drivers-common
 nvidia-common
 python3-software-properties
 software-properties-gtk
 python3-aptdaemon.pkcompat
 printer-driver-foo2zjs

```

My setup is derived from a mini.iso and one difference here is:

```
Current status: 0 updates [-7].
paul@quantal:~$ apt-cache policy python3-aptdaemon.pkcompat
[B][COLOR="Red"]python3-aptdaemon.pkcompat:
  Installed: (none)[/COLOR][/B]
  Candidate: 0.45+bzr846-0ubuntu1
  Version table:
     0.45+bzr846-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
paul@quantal:~$
```

---

### Post by dino99 on 2012-07-13
this one is needed now:  python3-aptdaemon.pkcompat

---

### Post by mcellius on 2012-07-13
To  that command, I get:

```
mdk@savina:~$ apt-cache policy python3-aptdaemon.pkcompat
python3-aptdaemon.pkcompat:
  Installed: 0.45+bzr846-0ubuntu1
  Candidate: 0.45+bzr846-0ubuntu1
  Version table:
 *** 0.45+bzr846-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
mdk@savina:~$ 
```

---

### Post by paul_in_london on 2012-07-13
> **mcellius said:**
> To  that command, I get:

```
mdk@savina:~$ apt-cache policy python3-aptdaemon.pkcompat
python3-aptdaemon.pkcompat:
  Installed: 0.45+bzr846-0ubuntu1
  Candidate: 0.45+bzr846-0ubuntu1
  Version table:
 *** 0.45+bzr846-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
mdk@savina:~$ 
```

Spoke too soon! Back on my main box now and after apt-get upgrade:

```
paul@quantal-64:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 python3 : Depends: python3-minimal (= 3.2.3-2ubuntu1) but 3.2.3-3ubuntu1 is installed
 python3-software-properties : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-gtk : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.
paul@quantal-64:~$ 
```

Synaptic output:

```
dpkg: dependency problems prevent configuration of python3:
 python3 depends on python3-minimal (= 3.2.3-2ubuntu1); however:
  Version of python3-minimal on system is 3.2.3-3ubuntu1.

dpkg: error processing python3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.
 software-properties-common depends on python3-software-properties; however:
  Package python3-software-properties is not configured yet.

dpkg: error processing software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.
 software-properties-gtk depends on python3-software-properties; however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.

dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3
 python3-software-properties
 software-properties-common
 software-properties-gtk
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3:
 python3 depends on python3-minimal (= 3.2.3-2ubuntu1); however:
  Version of python3-minimal on system is 3.2.3-3ubuntu1.

dpkg: error processing python3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.

dpkg: error processing python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3 (>= 3.2.3-3~); however:
  Version of python3 on system is 3.2.3-2ubuntu1.
 software-properties-gtk depends on python3-software-properties; however:
  Package python3-software-properties is not configured yet.
 software-properties-gtk depends on software-properties-common; however:
  Package software-properties-common is not configured yet.

dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 software-properties-common
 python3
 python3-software-properties
 software-properties-gtk
```

---

### Post by mc4man on 2012-07-13
Have any of you with issues tried synaptic/ had no issue at all with the upgrade
```
$ apt-cache policy python3   python3-all  python3-minimal
python3:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
python3-all:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
python3-minimal:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
doug@doug-XPS-M1330:~$ apt-cache  python3   python3-all  python3-minimal
E: Invalid operation python3
doug@doug-XPS-M1330:~$ apt-cache policy python3   python3-all  python3-minimal
python3:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
python3-all:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
python3-minimal:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status[
```

---

### Post by paul_in_london on 2012-07-13
> **mc4man said:**
> Have any of you with issues tried synaptic/ had no issue at all with the upgrade
```
$ apt-cache policy python3   python3-all  python3-minimal
python3:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
python3-all:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
python3-minimal:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
doug@doug-XPS-M1330:~$ apt-cache  python3   python3-all  python3-minimal
E: Invalid operation python3
doug@doug-XPS-M1330:~$ apt-cache policy python3   python3-all  python3-minimal
python3:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
python3-all:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
python3-minimal:
  Installed: 3.2.3-3ubuntu1
  Candidate: 3.2.3-3ubuntu1
  Version table:
 *** 3.2.3-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status[
```

Synaptic won't play ball for me at the moment. :(

---

### Post by zenarcher on 2012-07-13
Same here for me.  Synaptic can't fix it when trying to fix broken packages.

---

### Post by mcellius on 2012-07-13
Synaptic finds the broken packages but won't fix them.

---

### Post by mc4man on 2012-07-13
I think I managed to break it so it's similar or the same, is this about right

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python3 : Depends: python3-minimal (= 3.2.3-2ubuntu1) but 3.2.3-3ubuntu1 is installed
 python3-software-properties : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-gtk : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 ubuntu-drivers-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```
And synapic shows something like screen

---

### Post by paul_in_london on 2012-07-13
> **mc4man said:**
> I think I managed to break it so it's similar or the same, is this about right

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python3 : Depends: python3-minimal (= 3.2.3-2ubuntu1) but 3.2.3-3ubuntu1 is installed
 python3-software-properties : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-gtk : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 ubuntu-drivers-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```
And synapic shows something like screen

You seem to be in the same boat!

---

### Post by dino99 on 2012-07-13
Just made the upgrade on Lubuntu. Was having this kind of python issue too. So i've chosen the hard way:

- purged python & python3 packages, they removed other packages too but accepted
- then reinstalled the meta package (lubuntu-desktop)

that way this issue is gone now  ):P

---

### Post by mcellius on 2012-07-13
McMan,

Pretty close!  Here's what I get:

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python3 : Depends: python3-minimal (= 3.2.3-2ubuntu1) but 3.2.3-3ubuntu1 is installed
 python3-distupgrade : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 python3-software-properties : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-gtk : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 ubuntu-drivers-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by cecilpierce on 2012-07-13
I finally tried fix broken in synaptic and it took out alot of good stuff, even firefox but I just reinstalled some after it fixed python junk.

---

### Post by mc4man on 2012-07-13
> **mcellius said:**
> McMan,

Pretty close!  Here's what I get:

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python3 : Depends: python3-minimal (= 3.2.3-2ubuntu1) but 3.2.3-3ubuntu1 is installed
 python3-distupgrade : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 python3-software-properties : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 software-properties-gtk : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
 ubuntu-drivers-common : Depends: python3 (>= 3.2.3-3~) but 3.2.3-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.
```

Well i was able to fix eastly by just putting the new python3* trio in a folder & using dpkg on.
The small diff may be that I'd already had the other (python3-software-properties, software-properties*, ubuntu-drivers-common, ect) already upgraded

But what you could try - 
get these 3 packages, place in a folder, cd to the folder * run 
```
sudo dpkg -i *.deb
```
As long as they install then it won't matter if there are any other broken, synaptic or apt-get should handle

python3_3.2.3-3ubuntu1_all.deb  
python3-all_3.2.3-3ubuntu1_all.deb  
python3-minimal_3.2.3-3ubuntu1_all.deb

Can be downloaded from here if not already in /var/cache/apt/archives, just use those 3 to start
[https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3ubuntu1/+build/3652904](https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3ubuntu1/+build/3652904)

Example - 
```
~/Documents/fix1$ sudo dpkg -i *.deb
[sudo] password for doug: 
(Reading database ... 265556 files and directories currently installed.)
Preparing to replace python3 3.2.3-2ubuntu1 (using python3_3.2.3-3ubuntu1_all.deb) ...
running python pre-rtupdate hooks for python3.2...
Unpacking replacement python3 ...
Preparing to replace python3-all 3.2.3-2ubuntu1 (using python3-all_3.2.3-3ubuntu1_all.deb) ...
Unpacking replacement python3-all ...
Preparing to replace python3-minimal 3.2.3-2ubuntu1 (using python3-minimal_3.2.3-3ubuntu1_all.deb) ...
Unpacking replacement python3-minimal ...
Setting up python3-minimal (3.2.3-3ubuntu1) ...
Processing triggers for man-db ...
Setting up python3 (3.2.3-3ubuntu1) ...
running python rtupdate hooks for python3.2...
running python post-rtupdate hooks for python3.2...
Setting up python3-all (3.2.3-3ubuntu1) ...
doug@doug-XPS-M1330:~/Documents/fix1$
```

Or you could do basically what dino99 did, just purge pthyon3, then put everything back - just don't log out or restart till you've set things right

---

### Post by cariboo on 2012-07-13
I managed to use synaptic to fix the problem. I first removed python3, which removed quite a few other packages. Once all the packages had been removed, I re-installed python3, the re-installed all the packages in the residual config to be removed list.

I knew I had a problem with the graphics driver, so I wasn't surprised to boot to a command prompt. I used ppa-purge to remove the xorg-edgers ppa, which installed nvidia-current, which doesn't seem to work well with my graphics adapter. I rebooted to an 800X600 desktop, and used synaptic to remove nvidia-current, and install nvidia-current-updates. After a final reboot, I'm back at an 1920X1080 desktop, with no broken packages.

---

### Post by mcellius on 2012-07-13
> But what you could try - 
get these 3 packages, place in a folder, cd to the folder * run 
 	Code:
 	sudo dpkg -i *.deb


So far, so good.  It may have worked!  (I'm not sure this helps those fixing the bugs, though.)

---

### Post by mc4man on 2012-07-13
" python3 depends on python3.2 (>= 3.2.3); however:
  Package python3.2 is not installed."

Not sure how you've got yourself without python3.2, try installing it

---

### Post by mcellius on 2012-07-13
I revised my answer as I think it actually did work. Please don't ask for an explanation: I made a stupid error.  I'll just say that I hope I didn't mess up my 12.04 installation.  (Actually, that's all good.)

I should add, however, that the error was only in applying McMan's fix to the wrong partition.  That was not at all the source of all of the errors reported earlier.

---

### Post by extremeGreen on 2012-07-13
> [INDENT]get these 3 packages, place in a folder, cd to the folder * run 
```
sudo dpkg -i *.deb
```As long as they install then it won't matter if there are any other broken, synaptic or apt-get should handle

python3_3.2.3-3ubuntu1_all.deb  
python3-all_3.2.3-3ubuntu1_all.deb  
python3-minimal_3.2.3-3ubuntu1_all.deb
[/INDENT] 
Thank you so much, mc4man!  You solved the problem on my system.

---

### Post by paul_in_london on 2012-07-13
> **mc4man said:**
> ...
But what you could try - 
get these 3 packages, place in a folder, cd to the folder * run 
```
sudo dpkg -i *.deb
```
As long as they install then it won't matter if there are any other broken, synaptic or apt-get should handle

python3_3.2.3-3ubuntu1_all.deb  
python3-all_3.2.3-3ubuntu1_all.deb  
python3-minimal_3.2.3-3ubuntu1_all.deb

Can be downloaded from here if not already in /var/cache/apt/archives, just use those 3 to start
[https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3ubuntu1/+build/3652904](https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3ubuntu1/+build/3652904)
...

Thanks. All sorted - just downloaded and installed the 3 debs.

So now (because of the PPAs I'm using) I just have:

```
paul@quantal-64:~$ sudo apt-get upgrade                                                                                                                                                                                                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gir1.2-clutter-1.0 indicator-applet indicator-applet-session libclutter-1.0-0
```

---

### Post by Curtis6767 on 2012-07-14
I borked things up so I had to do a fresh install and now I'm in the process of updating that install. On the launchpad site there is now a fix for the problem, which I don't have at the moment and I'd prefer not to get it. I can wait on updating until this issue gets sorted out, or maybe it already has.

Here is what I'm currently being offered as updates/upgrades. If I go ahead with the update, am I just installing the problem? 

Thanks

---

### Post by mcellius on 2012-07-14
Curtis,

That looks good, so maybe it's all good now.  I'll be interested to see how it goes.

---

### Post by Curtis6767 on 2012-07-14
> **mcellius said:**
> Curtis,

That looks good, so maybe it's all good now.  I'll be interested to see how it goes.

Seems to be okay.

Thanks

---

### Post by shaneo1 on 2012-07-16
THIS FIXED MY ISSUE. Never even uninstalled python from synaptic.

> **mc4man said:**
> Well i was able to fix eastly by just putting the new python3* trio in a folder & using dpkg on.
The small diff may be that I'd already had the other (python3-software-properties, software-properties*, ubuntu-drivers-common, ect) already upgraded

But what you could try - 
get these 3 packages, place in a folder, cd to the folder * run 
```
sudo dpkg -i *.deb
```As long as they install then it won't matter if there are any other broken, synaptic or apt-get should handle

python3_3.2.3-3ubuntu1_all.deb  
python3-all_3.2.3-3ubuntu1_all.deb  
python3-minimal_3.2.3-3ubuntu1_all.deb

Can be downloaded from here if not already in /var/cache/apt/archives, just use those 3 to start
[https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3ubuntu1/+build/3652904](https://launchpad.net/ubuntu/+source/python3-defaults/3.2.3-3ubuntu1/+build/3652904)

Example - 
```
~/Documents/fix1$ sudo dpkg -i *.deb
[sudo] password for doug: 
(Reading database ... 265556 files and directories currently installed.)
Preparing to replace python3 3.2.3-2ubuntu1 (using python3_3.2.3-3ubuntu1_all.deb) ...
running python pre-rtupdate hooks for python3.2...
Unpacking replacement python3 ...
Preparing to replace python3-all 3.2.3-2ubuntu1 (using python3-all_3.2.3-3ubuntu1_all.deb) ...
Unpacking replacement python3-all ...
Preparing to replace python3-minimal 3.2.3-2ubuntu1 (using python3-minimal_3.2.3-3ubuntu1_all.deb) ...
Unpacking replacement python3-minimal ...
Setting up python3-minimal (3.2.3-3ubuntu1) ...
Processing triggers for man-db ...
Setting up python3 (3.2.3-3ubuntu1) ...
running python rtupdate hooks for python3.2...
running python post-rtupdate hooks for python3.2...
Setting up python3-all (3.2.3-3ubuntu1) ...
doug@doug-XPS-M1330:~/Documents/fix1$
```Or you could do basically what dino99 did, just purge pthyon3, then put everything back - just don't log out or restart till you've set things right

---

