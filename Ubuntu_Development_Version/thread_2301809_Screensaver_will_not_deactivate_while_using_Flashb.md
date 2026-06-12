---
title: "Screensaver will not deactivate while using Flashback"
date: 2015-11-05
forum: Ubuntu Development Version
---

### Post by Smask on 2015-11-05
This bug occurs on single screen computers running Flashback (Compiz), by activating the screensaver (by waiting or running gnome-screensaver-command -a). Dual screen machines or machines running Flashback (Metacity) aren't affected. I can activate the screen from sleeping by moving the mouse or press a key, but it will not deactivate the screensaver (see picture).


Sometimes it will deactivate when I flip between virtual terminals and GUI, but not always. 
Sometimes you have to try by pressing Ctrl-alt-Del to logout and then clicking Cancel when the Logout window appear.
When both methods fail to work, I've tried by logging in on tty1 and running gnome-screensaver-command -d but "Cannot autolaunch D-bus without X11 $display"
Killing the gnome-screensaver process have no effect.

What to do?

---

### Post by Smask on 2015-11-08
Found a workaround!

Install brightside and define one corner as "Prevent screensaver starting". When you hit that corner with your mouse, brightside will put up a small window with a small progress bar and that window breaks the grip the screensaver has on the system. Don't forget to add brightside to Startup Applications. 

Note: "Start screensaver" in brightside-properties = lock screen. If you want to just start the screensaver (no lock), select "Custom action..." run "gnome-screensaver-command -a" and select terminate the application when the mouse leaves the corner.

---

### Post by Smask on 2015-11-09
The celebration of the workaround were a bit premature, since it worked on my computer driving the 47" TV at home, but failed to work on my laptop at work. (Back to logging out by killing gnome-session in tty1..)

---

### Post by Smask on 2016-01-26
Changes done to the inner workings of the system makes killing gnome-session not work any more. Kill lightdm instead.

---

