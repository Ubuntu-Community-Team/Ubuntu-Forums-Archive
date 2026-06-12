---
title: "Missing menus on fresh boots or restarts on ubuntu sessions"
date: 2016-04-06
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-04-06
This has been occurring for several months to varying degrees per user in _ubuntu sessions_. (more likely to occur quite often on recent fresh install
A check on whether affected by currently open bug is to log out/in. If the menus return then the bug it is. 
orig. report - [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1532226](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1532226)

If affected quite often & desiring an auto workaround while awaiting a proper fix this can be done as described below. If doing so one should subscribe to the report so they know when fixed. Then the below autostart can be disabled/removed.

```
mkdir -p .config/autostart
```
```
gedit .config/autostart/menus.desktop
```

copy & paste below in gedit, save. The startup delay line has no value, in some cases it may benefit to use a delay of a sec. or two, if so just add 1 or 2 to the line.
```
[Desktop Entry]
Type=Application
Exec=initctl restart unity-panel-service
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=menus
Comment=Show me the menus
X-GNOME-Autostart-Delay=
```

---

### Post by parker-hugh on 2016-04-11
Thanks [**[COLOR=#DD4814][B]mc4man**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=320715"),  for the workaround. The menu is missing most days, but I just logout and in again and it returns ok. If it persists past this week, I will use your autostart solution.

---

### Post by jasonmili on 2016-04-25
This hasn't been yet fixed on the released version. I have this problem since I upgraded (yesterday).

---

### Post by angusk on 2016-05-04
I found the desktop entry didn't work on startup (on 16.04). I found this to work for me:

[INDENT][Desktop Entry]
Name=menus
GenericName=Menus Startup
Comment=Show me the menus
Exec=initctl restart unity-panel-service
Terminal=false
Type=Application
StartupNotify=false[/INDENT]

---

### Post by cariboo on 2016-05-05
Thread closed, not about Yakkety.

---

