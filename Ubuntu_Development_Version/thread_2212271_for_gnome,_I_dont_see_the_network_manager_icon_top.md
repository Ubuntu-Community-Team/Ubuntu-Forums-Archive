---
title: "for gnome, I dont see the network manager icon top right?"
date: 2014-03-20
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-20
sound and off functions only.
My other trusty gnome pc does show that?
Settings?

---

### Post by varunendra on 2014-03-21
Maybe nm-applet crashed during startup for some reason? Can you bring it back with "nm-applet" command?

If it crashes again, it should leave some hints in the terminal. If it comes up and stays there, you can run the command from "Alt-F2" rather than terminal.

Also, check the "nm-applet.desktop" file in "/etc/xdg/autostart" directory to make sure it is set to autostart. If the same file also exists in the ".config/autostart" directory in your Home, *I believe* it will override the settings of the one in /etc/xdg/autostart. So check that one also if there is one. If unsure, post back its/their contents here -
```
cat /etc/xdg/autostart/nm-applet.desktop
cat .config/autostart/nm-applet.desktop
```

---

### Post by sdowney717 on 2014-03-21
one is empty.

I have seveal PC and cant recall if this is the one that did that.

Looking at the wireless, I dont see all available networks, might be this one

```
scott875@scott875-desktop:~$ cat /etc/xdg/autostart/nm-applet.desktop
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=nm-applet
X-GNOME-UsesNotifications=true
X-Ubuntu-Gettext-Domain=nm-applet


scott875@scott875-desktop:~$ cat .config/autostart/nm-applet.desktop
cat: .config/autostart/nm-applet.desktop: No such file or directory
scott875@scott875-desktop:~$ 

```

---

### Post by varunendra on 2014-03-21
Not being able to see all available networks is usually a driver related problem, not related to NetworkManager or nm-applet as far as I know.

The file seems normal to me. Although this line -
> **sdowney717 said:**
> ```

X-GNOME-Bugzilla-Component=**nm-applet**
```
says "general" in my file here (12.04.1) instead of "nm-applet" as above. But I don't think it should matter in its execution.

So it seems like it does crash during startup, and the driver may be a factor, probably the cause of the crash. The inability to show all networks being a symptom of the problem in the driver.

Maybe take a look at logs in /var/log directory to find some hints about why it didn't start or why it crashed. I'm not sure which logs, but syslog should be the one.

---

