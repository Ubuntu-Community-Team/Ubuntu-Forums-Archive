---
title: "Lxappearance and Lxkeymap doesn't show even though they are installed"
date: 2015-08-04
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-08-04
This is a Wily question. I have installed Wily with Openbox, then installed Lxappearance and Lxkeymap. I see the icon, but neither of them won't open when clicked. This could be a Trusty problem too. I didn't try to install Openbox on Trusty, but only on Wily. It appears that all dependencies are installed, checked with synaptic. Does anyone know why this is happening?

---

### Post by Portaro on 2015-08-04
Try to launch the tools by terminal , and see if works.

If works maybe you need edit the launch icon o tint or on openbox menu with the commands.

---

### Post by Chanath on 2015-08-04
> **Portaro said:**
> Try to launch the tools by terminal , and see if works.

If works maybe you need edit the launch icon o tint or on openbox menu with the commands.

Lxkeymap,
> lxkeymap
Traceback (most recent call last):
  File "/usr/bin/lxkeymap", line 28, in <module>
    import dbus
ImportError: No module named dbus
dbus is installed, though.

Lxappearance,
> lxappearance
Segmentation fault (core dumped)

---

### Post by sudodus on 2015-08-04
> **Chanath said:**
> This is a Wily question. I have installed Wily with Openbox, then installed Lxappearance and Lxkeymap. I see the icon, but neither of them won't open when clicked. This could be a Trusty problem too. I didn't try to install Openbox on Trusty, but only on Wily. It appears that all dependencies are installed, checked with synaptic. Does anyone know why this is happening?

There is a bug report about Lxappearance, See [http://launchpad.net/bugs/1468529](http://launchpad.net/bugs/1468529)

See a list of several bugs in the qa-tracker at [Live Session in Lubuntu Desktop i386 for Wily Daily](http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/99303/testcases/1303/results)

If you hover over a bug symbol, you will get a short description. If you click on it you will get to the bug report.

---

### Post by Chanath on 2015-08-04
> **sudodus said:**
> There is a bug report about Lxappearance, See [http://launchpad.net/bugs/1468529](http://launchpad.net/bugs/1468529)

See a list of several bugs in the qa-tracker at [Live Session in Lubuntu Desktop i386 for Wily Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/99303/testcases/1303/results")

If you hover over a bug symbol, you will get a short description. If you click on it you will get to the bug report.

Thanks sudodus. I got Lxapperance working. Uninstalled lxappearance-obconf and it worked. I still have to find a way to get Lxkeymap working.

---

### Post by Chanath on 2015-08-06
In Lxkeymap, put importing dbus off, and it worked. Problem solved.

---

