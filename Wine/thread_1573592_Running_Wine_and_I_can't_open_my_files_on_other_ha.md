---
title: "Running Wine and I can't open my files on other harddrives."
date: 2010-09-12
forum: Wine
---

### Post by Tian102983 on 2010-09-12
Situation is this.
I have 2 hard drives. One where I keep all my programs and OSs and another where I keep my media or games and such.

I can mount both my harddrives and I see them on the desktop. I can go into my media harddrive and play videos and such.

Now when I run WINE. I cannot find my harddrive where I keep my media or games and such.

For instance I want to run ZSNES on WINE, and my games are in my media hard drive, but it won't show up.

What can I do? Any solutions?

---

### Post by hikaricore on 2010-09-13
Is there a reason you can't run the native release of zsnes?

> sudo apt-get install zsnes

As for being able to find things these drives need to be mounted in Linux then mapped in winecfg before you'll be able to access them.

---

### Post by cwwilson721 on 2010-09-13
If you INSIST on running ```
Windows ZNES > Wine >NES Games
```rather than just the Linux native znes (Look above on how to install it), and your data is on another drive, just run ```
Applications > Wine > Configure Wine 
``` And assign a drive letter to where your data is stored.

Personally, I'd run Linux ZNES. Much simpler/faster.

The way you're doing it is ALMOST like an emulator inside an emulator running non-native code. (Yes, I KNOW...***W***ine ***I***s ***N***ot an ***E***mulator. But for the sake of this post...). You're killing whatever performance you MIGHT think you'll have.

Running native znes is just running ONE emulator. Much, much faster

---

