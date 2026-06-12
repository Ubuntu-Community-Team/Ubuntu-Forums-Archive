---
title: "Gnome problems after switching desktops"
date: 2010-08-21
forum: System76 Support
---

### Post by missLiz on 2010-08-21
Hello.

I have a nice photo of my two boys and they set it to the background of my netbook (Starling with 9.04.  I have not upgraded to 9.10).

The Ubunu desktop covers up the picture and I want to see it.  So my husband poked around and found the "Switch Desktop Mode" in the Preferences.  He switched me to "Classic Desktop" and we could see our boys.  Everything was good.  We logged off and went to bed.

This morning I started the computer, and the boys were still there, but there was no gnome panel, no tool bar.  We could only see the icons on the screen for the few files in my Desktop.  (We only have one user on this machine.)

My husband tried logging on using the different sessions (previous gnome, gnome failsafe), no luck.

So he logged on via the terminal failsafe and snooped around in the gnome config files.  He deleted the "saved_state" file in .gconfd.  This did not help.


From the forums he found a suggestion to run the "desktop-switcher" app from the command line, which he did and this brought back the Ubuntu desktop.  However, it was missing the top gnome panel (with the ubuntu home icon, power icon, etc)


More searching in the Forums and he tried to kill and then restart the gnome panel.  There was no gnome-panel process running, so he started one (with gnome-panel&) and the panel re-appeared.


However, when we shutdown and restart, the panel is gone again.   And after starting the panel from the command line,
The Ubuntu home app does not work and all the windows (terminals, firefox, etc) are missing their very top border (above the menu bar for file, edit, view, etc)


It seems like gnome thinks the screen is a few pixels taller than it really is.


Now we are officially stumped.  We just want the defaults back.


thanks for the help
Miss Liz

---

### Post by isantop on 2010-08-23
Please try this.

From a command line, run: 
```
rm -rv .gconf .gconfd .gnome .gnome2
```

This will delete the stored Gnome configuration, causing it to be rebuilt upon your next login. It will create it from the default.

I'd recommend upgrading to Ubuntu 9.10 or 10.04. These releases have removed the buggy Desktop Switcher applet. It is less direct, but more stable, to switch between different desktop versions.

---

### Post by missLiz on 2010-08-29
Many thanks, that worked.

---

