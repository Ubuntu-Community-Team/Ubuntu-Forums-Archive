---
title: "GShutdown 0.2RC1 Released !"
date: 2007-02-01
forum: The Cafe
---

### Post by Maxime81 on 2007-02-01
Hello,

GShutdown is an utility which allow you to shutdown, reboot and logout by setting a date or a countdown. Even it has been developed using Gtk+, it's independent from the GNOME's libraries and works as much under KDE than under GNOME using either KDM or GDM.
The interest of this software is that it doesn't need to be run as root due to a communication with the desktop manager. GShutdown wants to be easy to use.

To sum up, its features are :
  * A good integration with GNOME/GDM.
  * Compatible with KDE/KDM.
  * Shutdown, reboot or close the current session, without being root (KDE and GNOME only).
  * The ability to choose a command to stop the computer (like "sudo poweroff").
  * Systray icon with visual notifications.
  * Three different ways to schedule the action : « at time and date », « after a delay », « now ».

The aim to this message is to announce the 0.2RC1 release which is a first step to a stable version of gshutdown.

This new version doesn't bring a lot of news but we can notice :
  * Command line options
  * GShutdown has been translated in more than 10 languages
  * Bug fixes of very few bugs
  * And more...

The official website : [http://gshutdown.tuxfamily.org](http://gshutdown.tuxfamily.org)

Ubuntu Edgy package : [http://gshutdown.tuxfamily.org/release/ubuntu/edgy/gshutdown_0.2rc1-1_i386.deb](http://gshutdown.tuxfamily.org/release/ubuntu/edgy/gshutdown_0.2rc1-1_i386.deb)

If you find any bug, please contact us by mail or use the wiki : [http://gshutdown.tuxfamily.org/en/wiki/doku.php?id=contributionmisc](http://gshutdown.tuxfamily.org/en/wiki/doku.php?id=contributionmisc)

Thanks.

---

### Post by Ghil on 2007-02-01
nice one, thanks!

---

### Post by weatherman on 2007-02-01
so it's basically a graphical frontend for shutdown? :)

---

### Post by Maxime81 on 2007-02-01
"so it's basically a graphical frontend for shutdown? "

No :). gshutdown doesn't use by default the shutdown command.
gshutdown doesn't need to be run as root.

---

### Post by Kuoi on 2007-04-21
Gshutdown does "log out" my computer instead of turning it off.

I've used the command "sudo poweroff" too , but then the program is only working when I'm real lucky. Can't figure out why it does work one time , and does not the other .

Kuoi

---

### Post by karellen on 2007-04-21
I give it now a try in feisty :D

---

### Post by MGStreak on 2007-04-24
> **Kuoi said:**
> Gshutdown does "log out" my computer instead of turning it off.
Kuoi

I have the exact same problem... anyone have any thoughts?

---

### Post by Bou on 2007-04-24
Gshutdown is great, but I wish it would let me run apps -or even close them- instead of just shutting down my computer.

Of course then it should be rechristened to something else.

---

### Post by DoctorMO on 2007-04-24
you mean a 1 time schedule linked to kill or arbitrary? there are cron jobs to run commands at a set time but this is something different I think.

---

