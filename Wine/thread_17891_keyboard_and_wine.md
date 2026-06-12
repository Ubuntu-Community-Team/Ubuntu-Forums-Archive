---
title: "keyboard and wine"
date: 2005-03-03
forum: Wine
---

### Post by thump on 2005-03-03
Hi there!

I'm new in Ubuntu and I'm triying to play starcraft trough wine.
I run winesetup and I choose "Managed" under "window mode".that lets my X window system control wine.Everything works fine, only I still see the desktop panels, and since they get bigger due to the resolution change, it's quite annoying.

If I choose "Unmanaged" the panels disapear, but the keyboard won't work (and this is unacceptable in Starcraft).When I quit Starcraft I see in an open terminal the keys I've been tipyng while trying to play Starcraft, so it looks like wine can't "get the focus" to get the keyboard signal.

Is there a way to solve this problem and use the keyboard in the Unmanaged mode??
Thank you for your help.

---

### Post by flaming_monkey on 2005-03-10
I'm having a similar problem with Counter-strike.  If anyone has any advice, please share it.

---

### Post by WirelessMike on 2005-05-24
I've tried installing previous versions of wine on my hoary final config and there doesn't appear to be any sort of solution.

Oddly, before I had to reformat I had begun with Warty and upgraded to Hoary in the developmental stage.  It worked fine, even after upgrading some apps to Breezy.

Now, after reformat with Hoary final, Wine is useless (without keyboard).

Anyone?

---

### Post by WirelessMike on 2005-05-30
Found a fix for this.  See ***[this post](http://ubuntuforums.org/showpost.php?p=193419&postcount=5)***.

I believe the settings created automatically by winesetuptk contain the source of the problem.  Best to let wine and wineutils create the proper default directories and settings for you.  You can always manually tweak the settings later if you wish.

---

### Post by magsymp on 2007-09-20
how do you uninstall only "winesetuptk" ? 

I'm running Ubuntu Feisty Fawn and my KB doesn't work in XCOM Ufo Defense.  I've tried everything and can't figure it out.

---

### Post by cogadh on 2007-09-20
Dude, this thread is over two years old. None of it actually applies to the current version of Wine anymore.

You can sometimes get the keyboard to work by selecting the "Allow window manager to control the windows" option on the Graphics tab in winecfg. Alternatively, running a game in its own X session will usually correct any keyboard input errors. Click on the "Stuff I've learned about Wine" link in my sig and go to the "Advanced Stuff" section, it explains how to do that.

---

### Post by hikaricore on 2007-09-20
Thread closed.  Make a new thread if you have an issue that isn't already covered in a **RECENT** thread.

---

