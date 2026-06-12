---
title: "Auto run abcde when CD inserted"
date: 2008-05-01
forum: Server Platforms
---

### Post by Rounan on 2008-05-01
Hi,

I have a headless ubuntu 7.10 server box running as a fileserver / uTorrent server in text mode only. xubuntu was installed on the box for initial admin and the Wine install, but is not loaded by default.

I have recently begun ripping some of my music collection. I have set up abcde to do this on the server, non-interactively and ejecting the CD when finished, and it works beautifully. However, I still have to type "abcde" into an SSH terminal when I insert each CD.

I would like to set it up so that when a CD is inserted (preferably with smart detection of an audio CD), abcde is run automatically.

I looked into HAL/DBUS a bit back in the 6.06 era, but I'm not sure which of these is responsible for auto mount magic these days. I suspect DBUS, but when I try to find out with dbus-monitor, I get:

$ dbus-monitor
Failed to open connection to session message bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

none of these /var/log/ files give any output when I insert a CD:
messages, dmesg, kern.log, udev, debug, syslog

Where should I go from here? Is there any hope of getting DBUS or a similar program to alert the system that a CD has been inserted without pulling in X11 or (worse) gnome-vfs as a dependency?

--Rounan

---

### Post by ghostknife on 2008-05-03
Try setting it in "System->Preferences->Preferred Applications".

---

### Post by HornedBeast on 2008-05-06
Hi.

I'm trying to acheive the same as the OP. My server is in a stand-alone case with no monitor at all. I admin it entirely via SSH and would love to have the ability to just put a CD in, have it rip via my options in ABCDE and then eject it again (Also, preferbly only on Audio CD detection).

Anyone know how to acheive this?

---

### Post by periferral on 2008-12-08
I read this and several other forums to figure out how to do exactly this. However, I had little success finding what I really needed for a pure CLI solution. 

After plenty of reading I create this perl script that does exactly that. There isn't much to it. Just copy it, chmod 755, and execute. It waits in a loop, when you insert a CD, it starts the rip. I have my abcde to eject CD on complete and you probably should set it as well otherwise the CD will continue to rip in a loop. Or I have 4 commented lines to prompt for rip. You can enable this if needed. 

[http://dl.getdropbox.com/u/163717/abcde_autorip.pl](http://dl.getdropbox.com/u/163717/abcde_autorip.pl)

I can improve this script if people show interest. Depending on the requests I get and the time I have, I'll look into making this more useable.

---

### Post by reverber on 2008-12-08
For setting up abcde to autorip:
There are example Bash scripts in /usr/share/doc/abcde/examples.
It took me far too long to figure that one out. ;)

Cody

---

### Post by periferral on 2008-12-10
i looked into the autorip script. it really doesnt look very useful. I have all the options for my rip + encode set in the conf file and id just want to use that.

is there anyway i can pass cddb information to abcde using command line? For example, if a CD comes up with multiple results on CDDB query, abcde in non-interactive will pick the first option. Is there a way I can do -N but ask it to pick say option 5 instead? Or pass the CDDB information?

thanks

---

### Post by sudocode on 2009-06-05
Another option is to use ivman to detect CD insertion and run abcde. That's what I'm doing on my server. More info [here]("sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html").

---

### Post by MrWES on 2009-06-05
> **Rounan said:**
> Hi,

I have a headless ubuntu 7.10 server box running as a fileserver / uTorrent server in text mode only. xubuntu was installed on the box for initial admin and the Wine install, but is not loaded by default.

I have recently begun ripping some of my music collection. I have set up abcde to do this on the server, non-interactively and ejecting the CD when finished, and it works beautifully. However, I still have to type "abcde" into an SSH terminal when I insert each CD.

I would like to set it up so that when a CD is inserted (preferably with smart detection of an audio CD), abcde is run automatically.

I looked into HAL/DBUS a bit back in the 6.06 era, but I'm not sure which of these is responsible for auto mount magic these days. I suspect DBUS, but when I try to find out with dbus-monitor, I get:

$ dbus-monitor
Failed to open connection to session message bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

none of these /var/log/ files give any output when I insert a CD:
messages, dmesg, kern.log, udev, debug, syslog

Where should I go from here? Is there any hope of getting DBUS or a similar program to alert the system that a CD has been inserted without pulling in X11 or (worse) gnome-vfs as a dependency?

--Rounan

You might try incron, and set it to monitor the mount point of the cdrom and then execute the ABCDE command. However, ABCDE still prompts you to edit the track listing if I recall.

[http://www.howtoforge.com/triggering-commands-on-file-or-directory-changes-with-incron]("http://www.howtoforge.com/triggering-commands-on-file-or-directory-changes-with-incron")

Bill

---

