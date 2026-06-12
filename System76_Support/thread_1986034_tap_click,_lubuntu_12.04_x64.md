---
title: "tap click, lubuntu 12.04 x64"
date: 2012-05-24
forum: System76 Support
---

### Post by redonath on 2012-05-24
since installing lubuntu i have been unable to disable tap click. i have installed gpointing and changed the settings, i have placed gpointing in startup. note gpointing does not show up anywhere in the main menu, i have to navigate to /usr/share/applications and go from there. i have edited some file and changed clicks value to 0. uninstalled re-installed you name it. can't seem to get settings to stick past a reboot, thanks in advance for the help.
nath

code: synclient MaxTapTime=0 
(in terminal disables tapclick)
but how can i do this in lubuntu (is there something i am missing?(this post was for xubuntu 11.10))
If this successfully disables the tap to click, then add a new startup entry (Settings->Settings Manager->Session and Startup->Application Autostart) where the command is:
bash -c "synclient MaxTapTime=0"
this advice came from Tor on [http://ubuntuforums.org/showthread.php?t=1875057](http://ubuntuforums.org/showthread.php?t=1875057)

---

### Post by kalehrl on 2012-05-24
It is much simpler than all that.

```
sudo nano /etc/xdg/lxsession/Lubuntu/autostart
```

add at the bottom:

```
@synclient MaxTapTime=0
```

Reboot and you're fine.

---

### Post by redonath on 2012-05-24
> **kalehrl said:**
> It is much simpler than all that.

```
sudo nano /etc/xdg/lxsession/Lubuntu/autostart
```

add at the bottom:

```
@synclient MaxTapTime=0
```

Reboot and you're fine.

WORKED
everything perfect w. one restart under belt
:popcorn:
thank you

---

