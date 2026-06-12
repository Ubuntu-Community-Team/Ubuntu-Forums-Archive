---
title: "Secret Power Management?"
date: 2016-08-04
forum: Ubuntu Studio
---

### Post by hathalud on 2016-08-04
Problem #2 with my system... Not nearly as annoying as the audio stuff in my prior thread, but annoying all the same for me. The system is powering off the screen after a few minutes of inactivity. On a laptop that would seem like a good thing, but this is my desktop and it's not something I want... much less for the short duration that it is set to. Normally I can just go into Power Management and disable it there. I did that. I also checked the settings in the following areas: 
Displays
Desktop
Window Manager
Window Manager Tweaks
None of these have any power management settings that disables the monitor.

Under LightDM GTK+ Greeter Settings (which probably only controls the login screen, not my XFCE session) I have the "Timeout until the screen blanks" set to "Never."

That said, the screen still is being timed out and blanked after maybe 10 minutes of inactivity... And I don't know what is doing it or where to go to set it to a longer time at the very least.

---

### Post by CrocoDuck on 2016-08-05
To my reckoning (I used XFCE few years ago) the problem is due to the fact that under XFCE based Ubuntu OSes both XfcePowerManager and XScreenSaver are active. Probably the blanking is given by XScreenSaver and you should configure that one. [Have a look]("https://wiki.archlinux.org/index.php/Xfce#Display_blanking"). Probably this will fix it:

```

xset s off 

```

See [here]("https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling#Modifying_DPMS_and_screensaver_settings_using_xset"). I think that what I did back then was to drop that line in a startup script. Look also at [this]("http://superuser.com/questions/644804/disable-screensaver-screen-blank-via-command-line#644829").

---

### Post by hathalud on 2016-08-05
> **CrocoDuck said:**
> To my reckoning (I used XFCE few years ago) the problem is due to the fact that under XFCE based Ubuntu OSes both XfcePowerManager and XScreenSaver are active. Probably the blanking is given by XScreenSaver and you should configure that one. [Have a look]("https://wiki.archlinux.org/index.php/Xfce#Display_blanking"). Probably this will fix it:

```

xset s off 

```

See [here]("https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling#Modifying_DPMS_and_screensaver_settings_using_xset"). I think that what I did back then was to drop that line in a startup script. Look also at [this]("http://superuser.com/questions/644804/disable-screensaver-screen-blank-via-command-line#644829").


Thank you for that. Based on this info I installed XScreensaver and disabled it. Hopefully that will work. Either way I'll update this thread.

---

### Post by hathalud on 2016-08-06
That seems to have done it. Thanks! Closing this thread.

---

