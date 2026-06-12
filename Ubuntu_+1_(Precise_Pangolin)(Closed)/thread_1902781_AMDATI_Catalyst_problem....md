---
title: "AMD/ATI Catalyst problem..."
date: 2011-12-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Xgen on 2011-12-31
After only using nvidia cards, I now have an ATI/AMD one (6970). The problem is that my custom settings are still retained in the Catalyst settings manager, but upon restart the screen defaults until I change/unchange a setting in the Catalyst screen and then my custom settings are recognized again. Is there a command to add to my Startup applications (like nvidia) to correct this?

---

### Post by jfernyhough on 2011-12-31
Is this a new install? Did you recreate xorg.conf for fglrx with (e.g.) $ sudo aticonfig --initial ? Are you running amd-cccle Administrator (superuser) or normal?

I've found sometimes I have to do an --initial, then set my screen layout using cccle Admin mode, reboot, then use gnome-settings to set the display settings.

---

### Post by Xgen on 2012-01-01
Thanks for your reply...it is a new laptop with fresh installs of oneiric and precise. I regenerated xorg.conf with your command (never knew about that). I also use the Catalyst control center as superuser and normal user, but still the same annoyance. What is happening, is that upon reboot the screen gamma is very light. As soon as I bring up the control center and press cancel, it returns to my custom settings.

> ..then use gnome-settings to set the display settings

Could you please explain this?

---

### Post by jfernyhough on 2012-01-01
Sorry, I meant System Settings, Display. Sometimes I have to use a combination of both. :)

Not sure about the gamma problem - I take it you've saved the colour settings in Catalyst Control Center?

---

### Post by Xgen on 2012-01-04
Okay....still stymied by this. If starting Catalyst (amdcccle) and then canceling it works, how do I create a script to start the program hidden and then cancel it immediately at startup to temporarily correct this annoyance until I find the proper solution?

Edit: Think this is the wrong forum as it is not Precise specific. Will inquire in the Video section.

---

