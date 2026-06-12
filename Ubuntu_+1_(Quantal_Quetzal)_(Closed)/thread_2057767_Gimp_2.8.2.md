---
title: "Gimp 2.8.2"
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by thotz on 2012-09-14
GIMP 2.8.2 is out.

Hopefully we get it for quantal.

Made a bug report: [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1050831](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1050831)


Thomas

---

### Post by ranger1021994 on 2012-09-14
:cool:

---

### Post by Harry33 on 2012-09-14
There is always a PPA (Otto06217) for Gimp_2.8.2:

[https://launchpad.net/~otto-kesselgulasch/+archive/gimp/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal](https://launchpad.net/~otto-kesselgulasch/+archive/gimp/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal)

---

### Post by thotz on 2012-09-14
Thank you for the info Harry :)

---

### Post by Andrew_P on 2012-09-14
Will this install on Lucid Lynx (10.04)?  If not, I'd be interested to learn of a PPA where one could get a backport i386 .deb installer file.

Edit:  Just found related thread [#1982183]("http://ubuntuforums.org/showthread.php?t=1982183").

---

### Post by Rallg on 2012-09-14
I compiled 2.8.2 on QQ. It's much better than 2.8.0 (which I also compiled, months ago). If you are happy with compiling, try 2.9.1 which has high bit depth, and put it into /opt. Caution: As usual with leading edge, there will be critical bugs.

---

### Post by Harry33 on 2012-09-14
> **Andrew_P said:**
> Will this install on Lucid Lynx (10.04)?  If not, I'd be interested to learn of a PPA where one could get a backport i386 .deb installer file.

Edit:  Just found related thread [#1982183]("http://ubuntuforums.org/showthread.php?t=1982183").

The Otto PPA is for Precise and Quantal.
It is very likely that trying to install the Precise version on a Lucid system would end up in trouble with certain dependencies.
This means packages depend on other packages that are not found on Lucid system.
This will certainly be the case with Quantal version.

---

### Post by Harry33 on 2012-09-19
As this forum is only for Quantal Quetzal (12.10) it is worth mentioning,
that Gimp_2.8.2 is already in the QQ repos.

Here:
[https://launchpad.net/ubuntu/quantal/+source/gimp/2.8.2-1ubuntu1](https://launchpad.net/ubuntu/quantal/+source/gimp/2.8.2-1ubuntu1)

---

### Post by funicorn on 2012-09-19
in Ubuntu 12.10, libgdk-pixbuf2.0-0 has bug: Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed. This error shows every time when opening any gtk application.
I wonder if it's related to gimp.

---

### Post by thotz on 2012-09-19
Great News :D

---

