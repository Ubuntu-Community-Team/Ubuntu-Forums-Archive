---
title: "xfce4-settings-manager and open in terminal launchers"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-01
i made a desktop file for my script 
when i open the desktop file it works, but when i try to open it from the xfce4-settings-manager nothing happens 
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Guest User Layout
Comment=Allows you to change the default xubuntu panel layout
Exec=sudo set-guest-panel-layout
Icon=session-properties
Path=
Terminal=true
StartupNotify=false
Categories=System;Settings;
```the launcher needs to open a terminal and run sudo set-guest-panel-layout

edit:
got it :)
```
bash -c "exo-open --launch TerminalEmulator sudo set-guest-panel-layout"
```

---

