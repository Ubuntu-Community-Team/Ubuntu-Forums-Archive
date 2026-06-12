---
title: "Differences between distros"
date: 2007-12-08
forum: The Cafe
---

### Post by kevindubrow on 2007-12-08
So as I am beginning to learn more about Linux (I've been a user for two years) I've noticed that many distros look and function the same. 

It seems like the major variations are the desktop (GNOME, Xfce, or KDE etc.) or the programs installed. Is this the case, or am I missing something? Thanks, I'm bored and curious!

---

### Post by prodigalson666 on 2007-12-08
Youre quite right, the base linux system is one difference, gentoo or debian are just two examples. The desktop manager is the second difference which you already know. The package manager that the distro is based on is a huge factor with distros, potage for gentoo or yast for suse etc. The package manager is an imporatnt factor is distro decision making.

---

### Post by yatt on 2007-12-08
The package management system is a major difference. There are lots of different systems available, they all work differently and they are all incompatible with each other.

Another major differences is patches. Most distros have patched a good portion of the software they ship, and they tend to use different patches. They may patch something to make it look better, add features, add hardware support, fix security holes, make the software more stable, or make the software worse (unintentionally, of course).

Then there is the default configuration. Just put Debian up against any of its derivatives, and you will see. The defaults make a huge difference.

---

### Post by kevindubrow on 2007-12-08
How do the base Linux systems differ? And are the packages incompatible with other distros only because the base systems are different?

---

### Post by yatt on 2007-12-08
> **kevindubrow said:**
> How do the base Linux systems differ? And are the packages incompatible with other distros only because the base systems are different?
Libraries tend to be one of the bigger differences. If you change a library, everything built against that library has to be recompiled too (generally). Between distros, there could be any of the following differences in a library:
Different versions.
Different patches applied.
May be in different directories.
etc

Which all effects the software that is built upon it. Then, lots of packages can be compiled with different flags that add/change functionality, usually at the cost of leanness or stability. Some distros turn on allot of flags, others are conservative and use a few, if any.

These all are sources of incompatibilities between packages of two distros. Then, a package may not contain the same stuff on different distros (eg Ubuntu's bootchart vs Debian's). Files may be in one package X in distro 1, but they are in package Y in distro 2. If you try to install distro 2's Y on distro 1 it may not work as it is missing files.

And that is only more basic stuff. A distro could decide to replace an entire subsystem with something new, and that would cause huge incompatabilities for packages that use the subsystem (ie Ubuntu uses upstart instead of sysvinit).

So, that is a start...

---

### Post by aimran on 2007-12-08
Also where certain system files are kept I believe...

---

### Post by kevindubrow on 2007-12-08
Ok, I think I understand. Thank you for your responses...I think I'll end up buying Linux for Dummies as a Christmas present for myself!

---

### Post by InfinityCircuit on 2007-12-08
Another difference is the usage of runlevels.  If you compare Ubuntu with Slackware or Red Hat you will notice that the sysv runlevels are different for graphical environments, internet, usages etc.  Gentoo is its own animal when it comes to this.

---

### Post by yatt on 2007-12-08
> **kevindubrow said:**
> Ok, I think I understand. Thank you for your responses...I think I'll end up buying Linux for Dummies as a Christmas present for myself!
Probably better off trying a bunch of tutorials in the tutorial section, then maybe a Gentoo/LFS. Books can be a) outdated, b) much to general in the areas you are interested and c) expensive.

---

### Post by kevindubrow on 2007-12-08
Ok, thank you for your advice, I'll look into that.

---

