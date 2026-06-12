---
title: "gdebi finishes without installing .deb"
date: 2018-03-16
forum: Ubuntu Development Version
---

### Post by monkeybrain20122 on 2018-03-16
Right click a .deb file (tried chrome an skypeforlinux) gdebi opens, click install, submit password, the progress bar goes very fast and it says installation completed. But the interface still show the install button instead of install/reinstall. Go check the menu and the file system and try to locate the supposedly installed package, it is nowhere to be found (after updatedb) Install normally with either the software centre or the cli (sudo apt install /path/to/deb) 

Ubuntu 18.04 gdebi 0.9.5.7+nmu2 Apparently there is no more gdebi-gtk in the repo, only gdebi and gdebi-core, is it a name change or am I missing something?

---

### Post by mc4man on 2018-03-17
I don't use gdebi as apt works fine on .deb packages but here all attempts to use gdebi fail with this error - 
dpkg: error: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor
A quick search of error  shows, [https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1756238](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1756238)

---

### Post by monkeybrain20122 on 2018-03-17
> **mc4man said:**
> I don't use gdebi as apt works fine on .deb packages but here all attempts to use gdebi fail with this error - 
dpkg: error: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor
A quick search of error  shows, [https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1756238](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1756238)

Not the same issue here apparently. Quite the opposite, gedbi doesn't complain about any error, but happily reports that installation completed, except that nothing is installed.

---

### Post by mc4man on 2018-03-17
gdebi installs /usr/bin/gdebi-gtk

---

### Post by mc4man on 2018-03-17
> **monkeybrain20122 said:**
> Not the same issue here apparently. Quite the opposite, gedbi doesn't complain about any error, but happily reports that installation completed, except that nothing is installed.
With what happen's here also produces error shown in syslog

---

### Post by #&amp;thj^% on 2018-03-17
If I just use "gdebi-gtk" then open any .deb all works as expected.
This: /usr/share/applications/gdebi.desktop  
Reads like:
```
[Desktop Entry]
Name=GDebi Package Installer
GenericName=Package Installer
Comment=Install and view software packages
Exec=gdebi-gtk %f
Icon=gnome-mime-application-x-deb
Terminal=false
Type=Application
Categories=System;
MimeType=application/vnd.debian.binary-package;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=gdebi
StartupNotify=true
Keywords=package;apt;dpkg;install


```
Am I missing something here?
UN-related here but I tried to set gdebi as default...but I highly stress not trying that>>>makes a mess of things currently. ;) (Just my findings here)
And for me the right click install with gdebi works also with just default Gnome DE install.

---

### Post by mc4man on 2018-03-17
> **1fallen said:**
> If I just use "gdebi-gtk" then open any .deb all works as expected.

Am I missing something here?
UN-related here but I tried to set gdebi as default...but I highly stress not trying that>>>makes a mess of things currently. ;) (Just my findings here)
And for me the right click install with gdebi works also with just default Gnome DE install.

How old is your install? Error seen here in a couple of week old one &also a  fresh install 2 days old where nothing but nvidia-driver was installed

---

### Post by #&amp;thj^% on 2018-03-17
> **mc4man said:**
> How old is your install? Error seen here in a couple of week old one &also a  fresh install 2 days old where nothing but nvidia-driver was installed

Feb 24 16:04
```
apt policy nvidia-390
nvidia-390:
  Installed: 390.42-0ubuntu0~gpu18.04.3
  Candidate: 390.42-0ubuntu1+gpu18.04.1
  Version table:
     390.42-0ubuntu1+gpu18.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages
 *** 390.42-0ubuntu0~gpu18.04.3 100
        100 /var/lib/dpkg/status

```
I do find this strange also.
BTW: This is assuming we are all talking about a X11 session.

---

### Post by DougieFresh4U on 2018-03-18
I had made thread/post about this a couple of weeks ago.
[https://ubuntuforums.org/showthread.php?t=2386043]("https://ubuntuforums.org/showthread.php?t=2386043")
Didn't get much attention, but must be affecting more installs now.

---

### Post by #&amp;thj^% on 2018-03-18
Would someone here try with on a X11 session:
```
sudo gdebi /path/to/packagename.deb
```

---

### Post by mc4man on 2018-03-18
On my fresh unadulterated install gdebi is a mess
Doesn't open from context menu, opens, then closes immediately ( but no crash reported
If used on a .deb with dependencies/recommends the deps/recos get installed but not the target.deb
If the target.deb has a same name package in repos then it substitutes the repo version

Meanwhile apt works fine in exact same scenario, dpkg also works fine on target.deb but doesn't handle deps/recos

(- sudo gdebi is known to work ok

---

### Post by #&amp;thj^% on 2018-03-18
> **mc4man said:**
> 
If used on a .deb with dependencies/recommends the deps/recos get installed but not the target.deb
If the target.deb has a same name package in repos then it substitutes the repo version

Yep; now seeing that here also.
> **mc4man said:**
> 
(- sudo gdebi is known to work ok
Thanks for the confirmation mc4man. :)

---

