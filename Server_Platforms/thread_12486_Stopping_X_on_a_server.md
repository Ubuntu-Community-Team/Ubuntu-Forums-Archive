---
title: "Stopping X on a server"
date: 2005-01-24
forum: Server Platforms
---

### Post by MrBojangles on 2005-01-24
Hi all,

I've just installed ubuntu, intending to run it as a web development server on an oldish machine. Everything is set up and running - apache2, php, mysql, samba, all is humming along nicely (thanks to all the excellent documentation etc available for ubuntu).

This is an oldish machine - a PII 400 w. 128mb ram - so I want to leave as much ram free for apache & mysql as possible. According to `top`, the top two memory users are gdmgreeter and XFree86.

I'm more familiar with Redhat & Fedora distros, where to stop this I'd just set the default init level to 3 (rather than 5), which stops the graphical login stuff from starting. However, the defaul init level in ubuntu is 2, so I'm not sure how to proceed now. How can I stop X (and gdmgreeter etc) from starting up?

---

### Post by mendicant on 2005-01-25
You could uninstall ubuntu-desktop--as long as you used something like aptitude to install packages (aptitude keeps track of automatically installed dependencies), this should uninstall everything you don't need.   If you installed other apps that depend on X, you'll also have to uninstall those.  If the latter is your case, you can uninstall x-window-system-core which should break everything that depends on X.  Alternatively, you could edit the /etc/X11/default-display-manager to contain the text "/dev/null" (or anything except /usr/bin/gdm).

---

### Post by ebrowne on 2005-01-25
Hey,  With redhat fedora you can use chkconfig and turn off X for that run level well in debian/ubuntu like distros I found that you can simply remove the link in /etc/rcx.d where the x corecponds to the runlevel your in.  In the case of X you remove the link S99gdm from /etc/rcx.d and the good thing is the orgional script is still in I believe /etc/init.d/rc.d so you can alway put it back.

---

### Post by mendicant on 2005-01-25
The equivalent in debian/ubuntu is to use update-rc.d

---

### Post by kulaki on 2005-01-25
you may install rcconf  and turned off gdm from there.

---

### Post by MrBojangles on 2005-01-28
Thanks kulaki. I installed rcconf (I love apt :) ) and switched gdm off. I stopped it via `sudo /etc/init.d/gdm stop` as well, and it's not running now. thanks lots, much appreciated.

---

