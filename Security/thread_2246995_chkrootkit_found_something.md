---
title: "chkrootkit found something"
date: 2014-10-04
forum: Security
---

### Post by jamal5 on 2014-10-04
Hi all,

I'm fairly new to ubuntu and I noticed some irregularities with my system lately. Comodo AV only scans for about 30 secounds and freezes (despite uninstall and reinstall), and when my computer is locked but not shut down the screen lights up randomly without me touching it... Before Ubuntu I know my Win7 system on the same computer had something nasty that no AV could catch, so I installed Ubuntu selecting wipe disk during setup so theoretically nothing from the old system could survive but who knows...

So today I installed chkrootkit and got these results:



[ATTACH=CONFIG]256945[/ATTACH]




Hope you can read it- it says that there is a suspicious file usr/bin/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noint   and Suckit rootkit is active

Does anybody know what these are and what they could be doing? Should I completely reinstall my OS or is there a way to get rid of it?


Thanks in advance

---

### Post by skompier on 2014-10-04
This has been around for years and has been a false positive for that long. You could try rkhunter and see what it shows, but I'm pretty sure there's nothing to worry about.

---

### Post by bashiergui on 2014-10-05
+1 to the false positive. Here's a bug report about it: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694860](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694860)

---

### Post by John_Ten on 2014-10-06
Unless you are running Linux Kernel 2.4.X it's a false positive 100%, suckit is long dead.

---

