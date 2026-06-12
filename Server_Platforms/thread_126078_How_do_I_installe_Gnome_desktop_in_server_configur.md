---
title: "How do I installe Gnome desktop in server configuration?"
date: 2006-02-05
forum: Server Platforms
---

### Post by VinceDee on 2006-02-05
I just installed ubuntu in server configuration following the [sourceforge ]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10")instructions, but that only installs a command line version of linux.

How can I install the gnome desktop and make ubuntu boot to it automatically?

---

### Post by moephan on 2006-02-05
I think what you want is:

$sudo apt-get install ubuntu-desktop

I never did this way before, but the description for this package is:

The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).


Cheers, Rick

---

### Post by VinceDee on 2006-02-05
Nice, it worked like a charm...thanks.:cool:

---

### Post by spartas on 2006-02-06
The method you used to install the desktop system probably saved you a fair amount of time since you didn't have to update/upgrade on top of obsoleted graphics packages.  This is the method I use for all my installs.

A further note if you want KDE or XFCE, you can install kubuntu-desktop or xubuntu-desktop respectively, as well as or in place of ubuntu-desktop if you wish.

---

### Post by wgregori on 2006-03-16
[QUOTE=moephan]I think what you want is:

$sudo apt-get install ubuntu-desktop


I tried this command and I get an error 

Couldn't find package ubuntu-desktop

Any idea why that is? 

Thanks

---

### Post by VinceDee on 2006-03-16
[QUOTE=wgregori][QUOTE=moephan]I think what you want is:

$sudo apt-get install ubuntu-desktop


I tried this command and I get an error 

Couldn't find package ubuntu-desktop

Any idea why that is? 

Thanks[/QUOTE]


I believe your problem here is that the $ in that command is supposed to represent your command line, so run the same command without the $ and you'll be good

Vince

---

