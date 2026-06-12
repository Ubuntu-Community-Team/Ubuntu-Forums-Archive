---
title: "Uninstall Apparmor problem"
date: 2007-11-02
forum: Server Platforms
---

### Post by sandman652001 on 2007-11-02
I'm running gutsy and I am having a strange problem.
 I stop app armor with

sudo /etc/init.d/apparmor kill

then

sudo update-rc.d -f apparmor remove

I then i remove apparmor and apparmor-utils with synaptic and when I reboot I get an 

Unable to start the settings manager 'gnome-settings-daemon' 

error message and my theme does not load. the problem persists even after various reboots.

It is fixed as soon as I reinstall apparmor
the problem is I need to load the  dazuko module  that is not compatible with the apparmor module.
Any Ideas?

---

### Post by sandman652001 on 2007-11-03
bump
Anyone?

---

### Post by sandman652001 on 2007-11-03
Should anyone be interested it has nothing to do with apparmor it is related to dazuko what I had not realized was that the moment I uninstalled apparmor the dazuko module would load and cause the problem. this still is strange because I had everything working fine in Festy  but even with the latest version of Dazuko in gutsy I get this annoying problem so my only choices at the moment are to have a working antivirus and a broken desktop or a working desktop with no antivirus.

---

### Post by Mr_Freez3 on 2007-11-03
> **sandman652001 said:**
> Should anyone be interested it has nothing to do with apparmor it is related to dazuko what I had not realized was that the moment I uninstalled apparmor the dazuko module would load and cause the problem. this still is strange because I had everything working fine in Festy  but even with the latest version of Dazuko in gutsy I get this annoying problem so my only choices at the moment are to have a working antivirus and a broken desktop or a working desktop with no antivirus.

I assume you already have dazuko and apparmor properly installed on your system.  I have dazuko working with apparmor installed and have no desktop problems.  But there is a consequence, apparmor does not load after dazuko starts in the boot process.  For me this is ok, I'd rather have on access scanning rather than apparmor.

Try doing this in the terminal:

sudo gedit /etc/modprobe.d/dazuko

Paste in this ( if you have something already in this file, comment it out or delete it first, then paste. ) :

install dazuko modprobe -r apparmor;\
modprobe -i dazuko; \
modprobe -i apparmor

Save it.

Reboot and  try this in the terminal to see if dazuko loaded:

lsmod | grep dazuko

If you get something similar to this:

dazuko                 58596  2 
commoncap               8320  2 capability,dazuko

then it's working.  If you get nothing, then we'll have to try something else.

---

### Post by sandman652001 on 2007-11-03
Sorry maybe I did not explain my self properly. If I disable or uninstall apparmor I am able to load the dazuko module the problem is that with the dazuko module loaded on reboot the gnome settings demon does not load any more. If I unload the dazuko module then the settings demon loads perfectly.
I too would rather have an antivirus loaded  than apparmor, my problem is that if I have an antivirus loaded I can not have a normal desktop.

---

### Post by Jose Catre-Vandis on 2007-11-03
Maybe uninstall apparmor _and_ dazuko and then reinstall dazuko wihtout apparmor being there?

---

### Post by sandman652001 on 2007-11-04
OK I tried uninstalling everything then reinstalled dazuko And I get the same gnome demon problem, what I did notice is that I can load dazuko manually after I am in gnome with no trouble, the other thing I noticed is that if I kill X ctrl+alt+backspace when I log back in the demon has started normally.
Anymore ideas?

---

### Post by Jose Catre-Vandis on 2007-11-04
I think this is an xgl-xserver issue rather than anything else as i get it too, when switching from an XGL session to a normal Gnome session (no compiz)

If after fiddling and restarting x what happens when you restart again and again without fiddling?

---

### Post by sandman652001 on 2007-11-04
just keep getting the same error, I tried both with and without the desktop effects enabled

---

