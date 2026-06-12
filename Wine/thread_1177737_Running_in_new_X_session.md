---
title: "Running in new X session"
date: 2009-06-03
forum: Wine
---

### Post by PTSnoop on 2009-06-03
In the latest Full Circle Magazine ([Issue 25]("http://fullcirclemagazine.org/issue-25/")) there was an article about how to get better performance on games running on Wine, by starting them in a new X session. It describes how to change the Xwrapper.config parameter from "allowed_users=console" to "allowed_users=anybody", then write a shell script to start a program in a new X session.

Well, I tried this with Starcraft, and Dawn of War: Dark Crusade (both games that work normally in Wine). Now, at this point I'd best explain that I've not installed either of them onto my Linux partition; I'm just running them from my Windows partition, with wine E:\ set to /media/disk/ . Normally it works fine.

Well, for Starcraft everything works fine. I can load up into the new X, flick between them using CtrlAltF7/F9, do things on both X sessions, and the new F9 session closes down when I click "Quit" in Starcraft.

But for some strange reason, when I load Dawn of War in the same way, X starts up, I get the black-and-white alternating pixels wallpaper and a black X mouse pointer for a few seconds, then it quits and I'm back in normal Gnome.

Can anyone explain this? What do I need to change to get Dawn of War working in another session?

Useful information: I'm using Wine 1.1.22 on Ubuntu Hardy, on a [Samsung X22 laptop]("http://www.samsung.com/uk/business/b2b/products/notebooks/business_class/x22.htm"), and flgrx drivers on an ATI Radeon 2400 graphics card.

The shell script I'm using is:

```
#!/bin/bash
X :2 -ac -terminate & sleep 2
DISPLAY=:2 nice -20 env WINEPREFIX="/home/andrew/.wine" wine "E:\Program Files\THQ\Dawn of War - Dark Crusade\DarkCrusade.exe"
```

By the way, yes, the E:\Program Files\THQ\etc. is the right file path (I've checked it a few times), and it's the only thing different to the working Starcraft script. And the same thing happens whether you use backslashes or forwardslashes for the E:/Program Files/etc.

Can anyone help?

---

