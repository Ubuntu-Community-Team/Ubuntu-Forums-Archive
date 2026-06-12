---
title: "Not-quite full screen issue with Karmic and wine dev"
date: 2009-11-02
forum: Wine
---

### Post by andrewdied on 2009-11-02
When I load a full screen program like  [geneforge]("http://www.spiderwebsoftware.com") with wine-1.1.31 on Ubuntu 9.10 (karmic koala), the top and bottom desktop bars in gnome are still on top.  Functionally, this means I can't *really* get to the bottom of the screen for things like scrolling.

I do use compiz, though I don't know if it's related.  If I use xfce instead of gnome I do get the true fullscreen by default.

Is there an option to force full screen for wine in gnome, or really push the top and bottom bars underneath wine?

---

### Post by andrewdied on 2009-11-08
Has anyone else seen this kind of behavior with full-screen wine programs and gnome?

---

### Post by beastrace91 on 2009-11-08
Its not uncommon. A quick/easy fix I have found is to run the full screened application in a different resolution than your desktop runs in. Works most of the time for me.

~Jeff

---

### Post by andrewdied on 2009-11-08
> **beastrace91 said:**
> Its not uncommon. A quick/easy fix I have found is to run the full screened application in a different resolution than your desktop runs in. Works most of the time for me.


The program itself shrinks my screen -- maybe that has something to do with it.  It runs at either 800x600, or 1024x768, I believe.

---

### Post by beastrace91 on 2009-11-08
What program is it that you trying exactly? Also have you tried loading it full screen with out compiz enabled? Also is running the app in a virtual desktop and option do you do really need it full screen? Also since your post Wine 1.1.32 has been released - be sure to give yours an upgrade and see if it helps at all.

Regards,
~Jeff

---

### Post by andrewdied on 2009-11-09
> **beastrace91 said:**
> What program is it that you trying exactly? Also have you tried loading it full screen with out compiz enabled? Also is running the app in a virtual desktop and option do you do really need it full screen? Also since your post Wine 1.1.32 has been released - be sure to give yours an upgrade and see if it helps at all.


Excellent questions.
[LIST][*]I'm running wine-1.1.31
[*]I'm trying to play "Geneforge 2", APP DB entry: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=8442]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=8442")
[*]I don't know how (haven't looked, either) how to run wine one another desktop.  I have been running it on a normal desktop workspace, not on a separate virtual terminal (Alt F5, etc).
[*]I have not turned off compiz, and I haven't researched how to do that.  X has become more complicated from my XVFWM days!
[*]There's no option to run Geneforge (I've tried versions 1 and 2) in non-full screen.
[/LIST]

For now I've been switching over to XFCE which doesn't have the problem.  So, maybe it is compiz.  It looks like I use ```
metacity --replace
``` to turn off compiz, and ```
compiz --replace
``` to turn it back on.  Theoretically there's a program called "compiz-switch" but it seems to have disappeared.

---

### Post by beastrace91 on 2009-11-09
Try upgrading your Wine to the latest 1.1.32 - this fixes random issues alot of the time.

By virtual desktop I meant opening your WineCFG (Applications->Wine->WineCFG or in terminal **winecfg**) and clicking over to the graphics tab and selecting "run in a virtual desktop". (This will force all your Wined apps to run in a window of the defined dimensions.)

To turn off compiz go to System-> Preferences->Appearance and toggle desktop effects to "none"

The program you are thinking of is called "fusion icon" not "compiz icon". Install it via ```
sudo apt-get install fusion-icon
```

Hope some of this is helpful,
~Jeff

---

### Post by joeelmex on 2009-11-09
I had the same exact problem, I went ti appearance settings and disabled all desktop effects, change the options to none.  the problem went away.

---

### Post by beastrace91 on 2009-11-09
Ahh, yes just a conflict with Compiz then - no uncommon. Glad you got it working at any rate.

~Jeff

---

### Post by andrewdied on 2009-11-09
> **beastrace91 said:**
> Try upgrading your Wine to the latest 1.1.32 - this fixes random issues alot of the time.

By virtual desktop I meant opening your WineCFG (Applications->Wine->WineCFG or in terminal **winecfg**) and clicking over to the graphics tab and selecting "run in a virtual desktop". (This will force all your Wined apps to run in a window of the defined dimensions.)

To turn off compiz go to System-> Preferences->Appearance and toggle desktop effects to "none"

The program you are thinking of is called "fusion icon" not "compiz icon". Install it via ```
sudo apt-get install fusion-icon
```

Hope some of this is helpful,
~Jeff

Thanks Jeff, it was all helpful.  I hadn't known about per-program preferences, or the stand alone "virtual desktop" window.  That's pretty cool.  It'd be nice if it could grab my mouse and use a key to ungrab it, like vmware windows, but that's just a nice to have.  [This article]("http://www.winehq.org/docs/wineusr-guide/config-wine-main") was helpful, too.

---

### Post by cronos on 2009-11-10
> **andrewdied said:**
> Has anyone else seen this kind of behavior with full-screen wine programs and gnome?

Yes. I had the same problem when playing games in fullscreen mode.  What I discovered, is that when I downgraded my Nvidia drivers from 190.x to 185.x, Wine works fine in fullscreen mode, just like it did with Ubuntu 9.04.

---

### Post by andrewdied on 2009-11-11
> **cronos said:**
> Yes. I had the same problem when playing games in fullscreen mode.  What I discovered, is that when I downgraded my Nvidia drivers from 190.x to 185.x, Wine works fine in fullscreen mode, just like it did with Ubuntu 9.04.

Ah, ok.  I'm also using the nvidia drivers.  I have some workarounds (virtual window, use xfce) so I'm going to keep the up-rev'd nvidia driver.

---

