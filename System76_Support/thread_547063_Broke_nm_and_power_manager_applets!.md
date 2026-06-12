---
title: "Broke nm and power manager applets!"
date: 2007-09-09
forum: System76 Support
---

### Post by KoRnholio on 2007-09-09
I accidentally removed the network manager and power manager applets.  How do I restore them?  I went to System->Administration->System76 Driver, and restored the system with the Restore System tab, but still nothing.  I can't connect to wireless networks without it :(

edit:  I have a panv2 (old Pangolin), running 7.04, if it matters.

---

### Post by palintheus on 2007-09-10
I know the network manager is 

nm-applet --sm-disable

just add that to system > Preferences > sessions. for it to start at boot. To get it running now just to Alt-F2 and enter it there

I do not have my laptop with me to look and see what the power management one is.

---

### Post by thomasaaron on 2007-09-10
For the power manager, add gnome-power-manager to System>Prefs>Sessions.

---

### Post by KoRnholio on 2007-09-10
Neither of those work.  nm-applet --sm-disable just hangs and doesn't pop anything up.

Here's the thing:
Network manager and power manager both still are in sessions, and they boot up too (they both show up in 'Current Session').  The network manager will even connect to wireless networks that I've connected to before (meaning everything the applet usually does without user input works).  But they don't show up in the panel - this means I can't find wireless networks, or monitor my power usage.

When I accidentally removed both of them, it happened in one fell swoop.  At least on my panv2, you can't directly remove either the nm-applet or power-manager.  What I right-clicked on was an unmarked space just to the left of both of them, and removed that (which removed both)  System76 seems to install a 'meta-applet' that contains both of them (and maybe a third, but if anything else was on there it wasn't important enough for me to notice its absence), and *that* is what I removed.

System76's system restore to defaults doesn't seem to re-add these, because it doesn't replace the panel settings at all.

If nobody has any idea what I'm talking about, then could you at least give me your copy of whatever file contains your panel configuration?  I don't know what Gnome config file contains panel settings, but I'm sure that is all I need to get this working.

---

### Post by palintheus on 2007-09-10
did you remove the panel area (system tray for lack of a better work) where the applet icons are? I don't have my laptop with me or I could probably help more.

---

### Post by thomasaaron on 2007-09-10
OOOOOOOOOOHHHHHHHHHHHHH! I see.

OK, right-click on the panel and select "Add to Panel."
Now find the little icon that says "Notification Area.".
Click it and then click OK.

That should do it.

---

### Post by KoRnholio on 2007-09-10
Thanks, that worked!  Now I have two wireless applets and no power applet, but that could be fixed when I restart it.

---

### Post by thomasaaron on 2007-09-10
If your battery is fully charged, you may not see your battery applet.
See System->Prefs->Power Management ("General" Tab).

---

