---
title: "put wine system tray on top system bar"
date: 2010-09-07
forum: Wine
---

### Post by xzinkx on 2010-09-07
Hi there, how do I put the wine system tray program on the top taskbar in lucid lynx? So i can just click on the program icons to interact with them instead of having to navigate to the system tray app? Regards

---

### Post by 0004tom on 2010-09-07
I see your using a windows build of spotify.. You are awear there are native linux builds?

What version of wine are you running?

```
wine --version
```

I run several win apps, which have system tray icons, unlike your's tho, mine do actually sit in the gnome-panal notification area thing.

---

### Post by xzinkx on 2010-09-07
wine-1.1.42

Oh, I didn't know there was a native linux version of spotify, I'll give that a go at a later date.
I really just want to get to the root of this problem. I have ubuntu 9 netbook remix running on my O2 joggler with wine installed on it (don't know which version of wine), I use the device pretty much as a dedicated spotify streaming device and have never encountered this problem on it.

infact the ubuntu build on the joggler goes one step ahead as it automatically sets the spotify icon .ico file (which is contained within the .exe) to the badge of the .exe file and the badge of the .exe desktop shortcut in which clearly isn't happening in my desktop build of ubuntu 10. I don't whether that's due to differences in wine versions or something else.

On a side note, the first time I ran spotify on the desktop, it initially  ran perfectly with the system tray applet in the right place. It was after I minimized spotify for the first time that the wine system tray program became displaced and I haven't been able to get it back onto the gnome panel.

Hope that helps
xzinkx

EDIT:
I solved this btw, just turns out you need to enable the indicator applet for the top panel.

---

### Post by gurkesaft on 2012-06-25
I solved this by adding a "notification area" to the gnome classic top bar:

1. <super>-Alt-<right click> the top bar.
2. Select "Add to Panel"
3. Select "Notification Area" and click "Add"

It won't obviously appear unless you have something running in the system tray (such as a wine icon).

Cheers!

---

