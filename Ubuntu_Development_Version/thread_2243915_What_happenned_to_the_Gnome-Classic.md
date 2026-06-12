---
title: "What happenned to the Gnome-Classic?"
date: 2014-09-12
forum: Ubuntu Development Version
---

### Post by Chanath on 2014-09-12
What happenned to the Gnome-Classic in Ubuntu-Gnome 14.10? You can choose it in the Login, but all you get is Gnome-shell.

---

### Post by LYXDhE3 on 2014-09-12
Are you talking about the one that looks like this:
[ATTACH=CONFIG]256394[/ATTACH]
with Applications and Places at the top, and a task bar on the bottom?
You have to install it separately.

---

### Post by Chanath on 2014-09-12
Ubuntu-gnome 14.10 has two to choose from at login, Gnome, and Gnome-Classic, but whatever you choose, you get only the Gnome-shell. Checking at the /usr/share/xsessions, the desktops are there. They are even in the /usr/share/gnome-session/sessions, but they don't work. 
One can install, either gnome-flshback or gnome-fallback from Ubuntu repos, and they appear in the login screen, but clicking on them won't bring in any desktop.

---

### Post by Cavsfan on 2014-09-12
All you need to do is **sudo apt-get install gnome-session-flashback** in terminal and after it updates install **compiz** along with all of it's other parts including **compizconfig-settings-manager**.
Then reboot and select if from the session before you enter your password. It will appear as Gnome Flashback (with compiz). You can have the cube, cairo dock and the whole gamut. :)

The package **gnome-session-fallback** is just a transitional package so it is not needed.

Here is Gnome Flashback (with compiz) on Utopic Unicorn 14.10:

[[IMG]http://www.zimagez.com/miniature/screenshotfrom2014-08-24133934.png[/IMG]]("http://www.zimagez.com/zimage/screenshotfrom2014-08-24133934.php")

Here another screenie:

[[IMG]http://www.zimagez.com/miniature/screenshotfrom2014-04-25152212.png[/IMG]]("http://www.zimagez.com/zimage/screenshotfrom2014-04-25152212.php")

---

### Post by Cavsfan on 2014-09-12
Then there is Ubuntu Utopic Mate Remix 14.10. The remix uses a fork of the GNOME 2-era desktop and its associated applications on top of an Ubuntu 14.10 base.

[http://www.omgubuntu.co.uk/2014/09/ubuntu-mate-remix-14-10-beta-1-released](http://www.omgubuntu.co.uk/2014/09/ubuntu-mate-remix-14-10-beta-1-released)

There is no Unity on Mate currently but things could change. It's a little more difficult to set up but it's worth it.

Here is what my setup looks like:

[[IMG]http://www.zimagez.com/miniature/screenshot-1464.png[/IMG]]("http://www.zimagez.com/zimage/screenshot-1464.php")

---

### Post by grahammechanical on 2014-09-12
Gnome Classic is a Gnome shell extension. So, we do not actually lose Gnome shell. It could be that there has been an update to Gnome 3 shell and that has broken the Gnome classic extension. You could try removing the extension and re-installing it. Or another update might fix what is broken. Is there a bug report for this?

Regards.

---

