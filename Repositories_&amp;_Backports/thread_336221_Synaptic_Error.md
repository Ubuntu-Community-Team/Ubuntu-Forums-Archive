---
title: "Synaptic Error"
date: 2007-01-11
forum: Repositories &amp; Backports
---

### Post by yosef on 2007-01-11
I am getting this error when I try to run synaptic:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

What's goiiing on and how can I fix it?

---

### Post by bapoumba on 2007-01-11
Hi, are you running some other package manager ? (update manager, adept, apt-get or aptitude) ?

---

### Post by yosef on 2007-01-11
no

---

### Post by yosef on 2007-01-11
This is what happens when I try this:

yosef@rlyeh ~> sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?


And this is what happens when I try that:

yosef@rlyeh ~> sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by bapoumba on 2007-01-12
Hi,
Are you using GNOME or KDE ?

> E: Couldn't lock list directory..are you root?
This message is strange as you did the update using sudo. Do you have some sudo problems ? Can you open nano for ex (a small text editor) as root ? Try **sudo nano** (CTRL +X to exit if working okay). Do you have any error messages ?

> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
This could also be due to your internet connection. Update-notifier checks for updates when booting. If you have some kind of delay or time-out, it will be checking for updates, and thus locking the lock file (just one package manager can work at a time). What kind of router do you have ?
**ps -U root** and **ps -U <your_actual_login>** will show you the current processes owned by root and by your user (replace <your_actual_login> in the previous command). Anything particular regarding package managers ?

You can alos check that thread :
[http://ubuntuforums.org/showthread.php?t=31854]("http://ubuntuforums.org/showthread.php?t=31854")

---

### Post by yosef on 2007-01-24
thanx! now it all works great except for:

Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  404 Not Found

whats up with that?

---

### Post by bapoumba on 2007-01-24
Freecontrib repositories are not available anymore. You can comment them out from your sources.list and run **sudo aptitude update** again.

---

### Post by yosef on 2007-01-24
are there any new repositories which I should be aware of?

---

### Post by yosef on 2007-01-24
... and btw, how can I check the architecture of a computer from the commandline?

---

### Post by bapoumba on 2007-01-24
Yes, medibuntu ;)
It's maintained by a french team, I wrote a translation there :
[http://bapoumba.free.fr/?p=13]("http://bapoumba.free.fr/?p=13").

---

### Post by bapoumba on 2007-01-24
> **yosef said:**
> ... and btw, how can I check the architecture of a computer from the commandline?
**uname -a** will tell you what ubuntu version is installed
**cat /proc/cpuinfo ** will tell you about your processor.

---

### Post by yosef on 2007-01-24
Thank you

---

### Post by bapoumba on 2007-01-24
Your'e welcome :)

edit : I just checked medibuntu web site, they have an English translation now :
[http://medibuntu.sos-sts.com/www/repository.php]("http://medibuntu.sos-sts.com/www/repository.php").

---

### Post by yosef on 2007-01-24
Very cool, I appreciate it
:guitar:

---

