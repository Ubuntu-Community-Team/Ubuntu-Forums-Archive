---
title: "Chrome install broke Ardour 4.7 and deleted audio/visual apps from menu"
date: 2016-05-15
forum: Ubuntu Studio
---

### Post by mwfoshee on 2016-05-15
[COLOR=#000000][FONT=Consolas]Ubuntu Studio 16.04. I've re installed using a usb drive about ten times. everything appears fine yet at some point all my audio-video-graphics menus disappear. I can find and use the Apps using alt-f2 except for ardour and qjacked which seem to be gone altogether. I first thought this was happening as a result of upgradeing Ardour, but I now think it has to do with installing google chrome (which I have to do from the terminal)[/FONT][/COLOR]

---

### Post by CrocoDuck on 2016-05-18
It shouldn't be the case, but I wonder whether you got a bug like [this]("http://ubuntuforums.org/showthread.php?t=2314622")? Are the launchers still in /usr/share/applications? Check what menu you have running, it should be alacarte:

```
dpkg -l | grep alacarte
dpkg -l | grep menulibre
```

---

