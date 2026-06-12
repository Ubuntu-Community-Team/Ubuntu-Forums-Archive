---
title: "request : XQF"
date: 2005-06-16
forum: Ubuntu Backports
---

### Post by ubuntu_demon on 2005-06-16
Hi,

> 
XQF is a game server browser and launcher for Unix/X11 for many popular games such as the Quake series, Unreal Tournament series, Half-Life etc. XQF is a front-end to QStat, a program by Steve Jankowski and uses the GTK+ toolkit.



1.0.3  can also search for ET 2.60 games

This should be a simple backport. If you decide to do this you have to backport qstat as well. But you have to backport this from debian unstable I think (I've installed the debian unstable packages)  because this is what the breezy ones do :

dpkg: dependency problems prevent configuration of qstat:
 qstat depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.

---

### Post by Seth on 2005-06-16
The version of qstat is the same in Debian unstable and in Breezy, so I just backported both these from Breezy. Please let me know how they work.

XQF: [http://sethkinast.com/ubuntu/hoary/backports/xqf_1.0.3-1~5.04upb1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/xqf_1.0.3-1~5.04upb1_i386.deb)
QStat: [http://sethkinast.com/ubuntu/hoary/backports/qstat_2.8-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/qstat_2.8-1~5.04ubp1_i386.deb)

---

### Post by ubuntu_demon on 2005-06-16
[QUOTE=Seth]The version of qstat is the same in Debian unstable and in Breezy, so I just backported both these from Breezy. Please let me know how they work.

XQF: [http://sethkinast.com/ubuntu/hoary/backports/xqf_1.0.3-1~5.04upb1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/xqf_1.0.3-1~5.04upb1_i386.deb)
QStat: [http://sethkinast.com/ubuntu/hoary/backports/qstat_2.8-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/qstat_2.8-1~5.04ubp1_i386.deb)[/QUOTE]

great! This will make ET players happy :)

works fine for ET 2.60

a bit offtopic : I believe their next release should also support nexuiz

---

### Post by skoal on 2005-06-16
I've been using XQF for over 3 months now.  I didn't realize it was a Debian package I had been using all along.  Been working great tho.

\\//_

---

### Post by JimboJoe on 2005-06-25
Works like a charm. Thanks!

---

