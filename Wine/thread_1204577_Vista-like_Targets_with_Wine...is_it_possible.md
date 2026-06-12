---
title: "Vista-like Targets with Wine...is it possible?"
date: 2009-07-04
forum: Wine
---

### Post by s3a on 2009-07-04
In Windows Vista, when I make a shortcut of a game, there is a target location that I can modify. Is it possible to simulate this in Ubuntu? If so, how do I reach this with Wine?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by cogadh on 2009-07-04
The Target path in a Windows shortcut is pretty much the same as the Command path in an Ubuntu launcher (shortcut). The only difference with Wine is you need the Wine parameters in it, like this:
```
env WINEPREFIX="/home/<username>/.wine" wine "C:\Program Files\Game Directory\game.exe"
```
Wine does create shortcuts in the Applications menu when you install something, so you should just be able to modify the existing one (using the menu editor: System > Preferences > Main Menu) to suit your needs. I'm assuming that you want to be able to put command switches on the end of the command, like a "-console" to activate the in-game console. If so, you should be able to do it just like this:
```
env WINEPREFIX="/home/<username>/.wine" wine "C:\Program Files\Game Directory\game.exe" -console
```

---

