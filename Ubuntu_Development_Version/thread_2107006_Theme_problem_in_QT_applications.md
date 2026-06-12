---
title: "Theme problem in QT applications"
date: 2013-01-20
forum: Ubuntu Development Version
---

### Post by darkhole on 2013-01-20
Hi guys, yesterday I made an upgrade to 13.04 from 12.10,  I got a problem today with Compiz and libunityshell.so, so I removed (and purge) almost all applications (compiz, unity and beyond... firefox, chrome, libreoffice, lightdm)...

After that I reinstalled all the applications (ubuntu-desktop) and now it is working fine everything (BTW Ubuntu 13.04 is really fast :) )

But now I have a problem with some apps (qt apps) like qbittorrent, VirtualBox, etc. All of them looks weird and with KDE icons... When I installed all this applications they just works using the GTK theme, but now they looks ugly.

Do you know how can I recover this aspect? I already tried using qtconfig-qt4 (as normal user and as sudo) but that didn't work.


Attached is an image from one dialog window in qBittorrent.

---

### Post by cariboo on 2013-01-20
I see the same thing here.

---

### Post by mc4man on 2013-01-20
There was an issue seen here a few weeks ago in an ubuntu session, (ambiance theme) with qt4, may or may not be your issue
(I only saw on installs of recent history, mid Dec or so thru now.

resolved by installing libgnome2-common or editing a certain schema file
So it wouldn't hurt to try - 
```
sudo apt-get install libgnome2-common
```
(& maybe a log out/in

---

### Post by cariboo on 2013-01-20
> **mc4man said:**
> There was an issue seen here a few weeks ago in an ubuntu session, (ambiance theme) with qt4, may or may not be your issue
(I only saw on installs of recent history, mid Dec or so thru now.

resolved by installing libgnome2-common or editing a certain schema file
So it wouldn't hurt to try - 
```
sudo apt-get install libgnome2-common
```
(& maybe a log out/in

Thanks mc4man, that fixed it for me.

---

### Post by mc4man on 2013-01-21
> **cariboo907 said:**
> that fixed it for me.
Here's the bug on, qt4(x11) issues generally take their time being resolved
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1094360](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1094360)

---

