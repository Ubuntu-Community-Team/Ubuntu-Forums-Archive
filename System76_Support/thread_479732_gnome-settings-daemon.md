---
title: "gnome-settings-daemon"
date: 2007-06-20
forum: System76 Support
---

### Post by ncappel1 on 2007-06-20
When I log out of my session and log back in on my gazelle performance, I noticed just the other day that the keyboard indicator applet looks slightly different than normal. (I activated a dvorak layout, that's why I use the applet, to switch back and forth). When the login completes instead of displaying "USA" like it is supposed to, is just says "us." When I right click on it, a small informational window pops up and says:

Unable to start the settings manager  'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager. 

The keyboard switcher still works, and also, I put the sleep inhibitor applet switch on a panel, and upon a relogin, clicking on it does nothing, it is unresponsive. 

Other posts I have looked at suggest that it may have something to do with the theme's manager, but I haven't installed any new themes. I don't quite know what the matter is, I didn't install KDE, and when I open the system monitor gnome-settings-daemon and bonobo are both there, sleeping. It doesn't happen on a regular boot, only when I log out and back in (either from the power button on the panel or ctrl+alt+backspace).

I do admit that I was fiddleing with the sessions, but I didn't change any of the defaults. I copied /etc/share/xsessions/gnome.desktop to a new file, gnome2.desktop, and only played when logged into the gnome2.desktop. even after I deleted gnome2.desktop this still happens.

I checked the ~/.xsession-errors log, but there's no mention of gnome-settings-daemon. I can't remember the first time I noticed it, but it is consistant with the logging in and out. It hasn't really affected anything else, so far as I can tell, but it would be nice to know whats going on!

Nicola

---

### Post by thomasaaron on 2007-06-21
Hi, Nicola.

Tom, here.

Check out  this post and see if it has any relevant info:
[http://ubuntuforums.org/showthread.php?p=2852836](http://ubuntuforums.org/showthread.php?p=2852836)

---

### Post by ncappel1 on 2007-06-23
Hi Tom, 
hmmm...I didn't read anything that seemed to correlate to each other! I tried the same command, gnome-theme-manager, with out sudo, and the same error was returned, but the theme-manager comes up all the same. Don't know if this is helpful, but attached are copies of my xsession-error log on a clean boot(good), and after the logout/in(bad).

side by side they look very similar, some of the orders of the errors are shuffled, but there's no mention of anything gnome-settings-daemon related!

Nicola

---

