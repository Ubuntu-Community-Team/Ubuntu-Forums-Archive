---
title: "Where's &quot;Boot&quot; in Ubuntu (Hoary)?"
date: 2005-07-03
forum: The Cafe
---

### Post by ZephyrXero on 2005-07-03
Where did Ubuntu hide the "Boot" tool that normally comes with Gnome (since 2.8)? This is a graphical tool that allows you to configure your bootloader, like Grub for example...but it's no where to be found in the current release of Ubuntu? I checked to see if "Gnome-System-Tools" was installed, and it is...but I can't find it anywhere. Is it in there at all? If not, why?

---

### Post by TravisNewman on 2005-07-03
there's a tool called grubconf that does this:
[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)

---

### Post by ZephyrXero on 2005-07-04
Ok, thanks...but I'm still curious as to what happened to the Gnome one... ;)

---

### Post by ZephyrXero on 2005-07-08
Grubconf is not listed in Synaptic anywhere.... I've got the universe and multiverse repositories added as well as backports. Is it listed under a different name?

---

### Post by poofyhairguy on 2005-07-08
[QUOTE=ZephyrXero]Grubconf is not listed in Synaptic anywhere.... I've got the universe and multiverse repositories added as well as backports. Is it listed under a different name?[/QUOTE]

the deb only exists in one place:

[http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb)

you have to install it yourself (has no depebdancies):

sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb

---

