---
title: "Wine doesn't obey virtual desktop overrides"
date: 2008-12-27
forum: Wine
---

### Post by soluphobe on 2008-12-27
Hi,

I've had this problem with wine for a long time, over two computers, from 7.04 to 8.10 and from 0.9.30-something to 1.1.10.  I like the virtual desktop, and I want a lot of my more intensive games to run there, so that if/when they crash, my desktop isn't screwed.  But there are some small applications that I don't want a virtual desktop to open for.  So I go into winecfg, add the applications, and uncheck the 'emulate a virtual desktop' setting for those applications.

Does anyone else have the problem that this does **absolutely nothing**?  I don't really mind, because when Oblivion throws me for a loop I'd like my resolution normal.  But when I'm just running Progress Quest I'd just like for it to act like a normal linux game without a monstrous blue screen behind it.

So I disabled the virtual desktop for the default configuration and started setting a 1240x768 VD as the overridden configuration for individual programs.  On some applications this works fine (well, some of the time).  On others (*cough* Steam! *cough*) there are issues that invariably leave my 1920x1200 resolution stuck at 800x600.  And if I set the default back to a VD, my well-behaved programs that I don't want to lock into a virtual desktop get stuck there anyway, which probably shouldn't be happening.

TLDR:

Trying to set the Virtual Desktop for individual applications doesn't work.  Is there a quick-fix I'm missing?

---

### Post by darklegion on 2008-12-27
If the option fails for you (worked for me when I needed to use it), you can instead use a different wine prefix fo load the apps that you don't want to use a virtual desktop with .Like this:
```

WINEPREFIX=~/.wine.novirt wine [app]

```
You can call the wineprefix whatever you want, btw.

Another way to workaround crashed apps is to make a script that recovers whenever a game fails.I use xrandr to switch back to my native resolution when this happens.You can also use "nvidia-settings -l" if brightness gets messed up (and you have a nvidia card).I don't use the brightness fix anymore, though, as it haven't needed to for a while.
Here's an example of a script I use for oblivion:
```

#!/bin/bash
# Runs Oblivion under wine
ORIGINAL_RES=`xrandr -q | grep \* | cut -c4-12`
cd "/xdata/games/oblivion" && WINEPREFIX=~/.wine.oblivion WINEDEBUG=-all wine oblivion.exe "$@" ; xrandr -s $ORIGINAL_RES

```

You won't need the ORIGINAL_RES code if your desktop resolution is the maximum used, you can just use "xrandr -s 0" in this case.You can also instead use "xrandr -s [resolution]" to force a specific resolution.
This isn't tested with ubuntu or any normal window manager (I use ratpoison) but it should work.

---

### Post by soluphobe on 2008-12-29
Thanks for your reply.  I don't think the WINEPREFIX will work - I just looked it up now, so all my programs are in one .wine .  The screen resizing looks promising, though, so I'll give that a try once I can isolate the causes of crashing.  I've got a fairly stable setup now, through lots of -w and -vidmode.  That extra WINEPREFIX looks very promising, and my hard drive can take it...

---

