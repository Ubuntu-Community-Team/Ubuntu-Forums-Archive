---
title: "Fatal Server error no screens found"
date: 2008-03-18
forum: Sun Sparc Users
---

### Post by mabsalon on 2008-03-18
I have installed Ubuntu 7.10 on a Sunfire T2000 server which has the Matrox G550 graphics card. Installed Ubuntu desktop, did a reconfigure xorg.conf and when I type startx, i get the following error

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux asiaminor 2.6.22-14-sparc64-smp #1 SMP Sun Oct 14 22:55:24 GMT 2007 sparc64
Build Date: 18 January 2008
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 18 16:02:48 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 54 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

PLEASE HELP!!

---

### Post by linuxtoindia on 2008-03-20
''sudo dpkg-reconfigure xserver-xorg''

wait for some seconds ,, configure manually ..


then type gdm
or get to root and type reinstall gdm
sudo /etc/init.d/gdm restart

hope this should solve

---

