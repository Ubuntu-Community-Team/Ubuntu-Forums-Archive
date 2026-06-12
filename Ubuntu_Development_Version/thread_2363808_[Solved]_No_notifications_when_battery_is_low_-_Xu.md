---
title: "[Solved] No notifications when battery is low - Xubuntu 17.10"
date: 2017-06-14
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-06-14
Xubuntu 17.10 doesn't give a warning, when the battery is low. It gives a warning, when the battery is full, though. I had the laptop shutting itself off few times today without a warning. I have Openbox with Ubuntu base with the same Xfce4 power manager, but there notifications work well. Does anyone know, why this is happening in Xubuntu?

---

### Post by Chanath on 2017-06-21
I found the answer in XFCE forums. Its also interesting that no one here had looked into this. Only 1 view since so many days. That equals to no Xubuntu people come here.

---

### Post by #&amp;thj^% on 2017-06-21
Well the Forum views shown do not work correctly ATM
There are many XFCE users here.
```
Name            : xfce4-panel
Version         : 4.12.1-1
Description     : Panel for the Xfce desktop environment
Architecture    : x86_64
URL             : http://www.xfce.org/
Licenses        : GPL2
Groups          : xfce4
Provides        : None
Depends On      : exo  garcon  libxfce4ui  libwnck  hicolor-icon-theme
                  desktop-file-utils
Optional Deps   : None
Required By     : xfce4-battery-plugin  xfce4-datetime-plugin
                  xfce4-pulseaudio-plugin  xfce4-screenshooter
                  xfce4-sensors-plugin-nvidia  xfce4-whiskermenu-plugin
Optional For    : thunar  xfce4-power-manager
Conflicts With  : None
Replaces        : None
Installed Size  : 3.49 MiB

```
Glad you found your answer though. :p

---

### Post by Chanath on 2017-06-21
I had to add the [COLOR=#333333][FONT=Verdana]Battery Monitor Plugin to get the battery status notifications. The default Power Manager plugin didn't want to show a low battery notification. Maybe Xubuntu devs would think about that, if they come here to have a look.[/FONT][/COLOR]

---

### Post by cariboo on 2017-06-22
I'm running Xubuntu 17.10 on my laptop, the battery indicator works as it should, with no intervention from me.

---

### Post by Chanath on 2017-06-22
I don't know why this happened with Xubuntu 17.10. I have the same Power manager plugin in my Openbox install, and that works quite well. Maybe this problem would go away by itself in the process of continued upgrading. Other interesting thing I found is that, once the battery is full, the charging is cut off, even with the charger is on. Its Xubuntu that's doing it, and I like that. I had a big trouble with the battery going off without any notifications, and it happened few times while working and having a skype discussion. I couldn't pass the buck to skype all the time, so went back to using the Openbox install.

I have a laptop specific problem with my laptop ([https://ubuntuforums.org/showthread.php?t=2361898](https://ubuntuforums.org/showthread.php?t=2361898)) I never got an answer. This is happening in all kinds of Linux distros (from arch based to U ubuntu). The touchpad is Synpatic. If anyone can help out, I'd be happy. It works very well in Windows.

---

