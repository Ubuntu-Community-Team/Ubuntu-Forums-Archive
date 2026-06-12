---
title: "Lightweight Ubuntu LAMP install"
date: 2010-12-10
forum: Server Platforms
---

### Post by LinkMJB on 2010-12-10
Hello all,

I am running an installation of 10.04 Ubuntu LTS as a virtual machine that I would like to make more application restrictive/lightweight. I manage it via ssh (loopback) and have already disabled gdm which improved performance significantly, but I would like a lighter footprint and a tighter security profile. Less apps to patch, less security worry.

Is there a recommended package list I can model my system after and still stay stable? 

Is it as easy as 'dpkg --list | egrep -i "game|bluetooth|gtk|gnome" | awk '{print $2}' | xargs dpkg -r' ?

Is avahi REQUIRED on Ubuntu at this point? Or can I safely remove it?

Or do I need to completely start over and move to something like 'lubuntu' or 'xubuntu' to have a supported lightweight server installation?

Any input would be appreciated :)

---

### Post by James78 on 2010-12-10
Did your 10.04 LTS virtual machine have Gnome? The regular Ubuntu Server distribution has no Gnome, no desktop environment, and is really lightweight by default (because it has no desktop environment, and no unneeded applications).
[http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download)

---

### Post by andriansah on 2011-04-19
> **LinkMJB said:**
> Hello all,

I am running an installation of 10.04 Ubuntu LTS as a virtual machine that I would like to make more application restrictive/lightweight. I manage it via ssh (loopback) and have already disabled gdm which improved performance significantly, but I would like a lighter footprint and a tighter security profile. Less apps to patch, less security worry.

Is there a recommended package list I can model my system after and still stay stable? 

Is it as easy as 'dpkg --list | egrep -i "game|bluetooth|gtk|gnome" | awk '{print $2}' | xargs dpkg -r' ?

Is avahi REQUIRED on Ubuntu at this point? Or can I safely remove it?

Or do I need to completely start over and move to something like 'lubuntu' or 'xubuntu' to have a supported lightweight server installation?

Any input would be appreciated :)

if you were instakking ubuntu-server there's no window manager, just plain cli. if you were installing fr om alternate/ live cd maybe you have window manage manager.

just remove the window managesudo apt-get remove ubuntu-desktop

---

