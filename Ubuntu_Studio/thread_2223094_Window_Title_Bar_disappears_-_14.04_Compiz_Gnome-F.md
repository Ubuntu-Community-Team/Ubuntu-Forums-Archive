---
title: "Window Title Bar disappears - 14.04 Compiz Gnome-Flashback"
date: 2014-05-09
forum: Ubuntu Studio
---

### Post by cwmoser on 2014-05-09
Ubuntu 14.04 64-bit, Gnome-Flashback desktop, Compiz

Randomly I loose the Title Bar for my windows.  
Right before this happens, the Desktop flashes and blinks, then the Title Bars for all Windows disappears.
The only thing I know to do is Ctl+Alt+Backspace to log out and then log back into Ubuntu.

Is there a fix for this?

---

### Post by vermontbear on 2014-05-13
When it happens, try opening a terminal window and typing

 compiz --replace

(I tend to use Emerald Themes, so I have to type "emerald --replace," though since you have to download those from git and compile, I'm not assuming you are using Emerald)

Yes, for the rest of that session, you have to leave that terminal window open.  Minimized certainly, but open.

Else, I have noted with Ubuntu 12.04...14.04, there are problems of the system getting itself configured rightly with Compiz when you first boot. I might be a pain in the butt, but I will generally -- and immediately -- log out and log back in again after the first startup of a session. Compiz and whatever you are using for a window manager will tend to hold much better if you do that.

Try it. If it works, you're welcome.  If not, well, it's worth what you paid for it.

---

