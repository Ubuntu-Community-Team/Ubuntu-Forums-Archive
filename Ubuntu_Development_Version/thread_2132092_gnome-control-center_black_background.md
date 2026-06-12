---
title: "gnome-control-center black background"
date: 2013-04-03
forum: Ubuntu Development Version
---

### Post by Kotrfa on 2013-04-03
The second problem is weird displaying of background in settings. My gnome-control-center and all it's "subdesktops" display black background. But only if I run them from GUI Activities->Applications. When I run them from terminal, or when I add "Terminal=true", it works fine.

[IMG]http://img18.imageshack.us/img18/3729/62333159.png[/IMG]
Is it bug or is there any known solution? I haven't find anything.

Thanks for help

---

### Post by jbicha on 2013-04-03
You should ask whoever developed the theme you're using to update their theme for GNOME 3.8.

---

### Post by Kotrfa on 2013-04-04
That's not the point - I'm using official Adwaita or High contrast theme by default. There isn't option for users theme in 3.8 yet. And changing the theme doesn't change anything. This problem is just in the settings manager.

EDIT: I've found "workaround" - the gnome-control-center displays ok, when I run it by command from terminal. It looks on the permission problem, but I don't know, what to change. Here is my /usr/share/applications/gnome-control-center.desktop (I deleted keywords for other languages for smaller output just for this thread). When I change "Terminal=false" at "Terminal=true" it works (but the terminal is lunched when I run it). Even when I manually execute it from Nautilus, it displays ok. It occurs only when I run it from applications. By the way it do much more .desktop files, for ex. gnome-notifications-accounts-panel.desktop etc. 

```
**vim /usr/share/applications/gnome-control-center.desktop**

[Desktop Entry]
Name=Settings
Icon=preferences-system
Exec=gnome-control-center --overview
Terminal=**true**
Type=Application
StartupNotify=true
Categories=GNOME;GTK;System;
OnlyShowIn=GNOME;Unity;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-control-center
X-GNOME-Bugzilla-Component=shell
X-GNOME-Bugzilla-Version=3.8.0
Keywords=Preferences;Settings;
Keywords[cs]=p&#345;edvolby;nastavení;
X-Ubuntu-Gettext-Domain=gnome-control-center-1.0

```


I will start other thread for super key.

---

