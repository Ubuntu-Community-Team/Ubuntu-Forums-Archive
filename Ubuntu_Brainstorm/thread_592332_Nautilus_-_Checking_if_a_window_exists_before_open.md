---
title: "Nautilus - Checking if a window exists before opening it"
date: 2007-10-26
forum: Ubuntu Brainstorm
---

### Post by evilregis on 2007-10-26
Let's pretend I have Home and Computer icons on the desktop.  In Nautilus, if I double-click Home 5 times, it opens up Home 5 times.

It should only open one time and just get focus back if it already exists.

It's small, I know, but it's something I've run into a few times, in my case with my Music folder.  Where some time would go by, I have one opened from earlier, forgot to close it, open it again... only to start cleaning up my desktop and closing windows and seeing 3 Music folders.

---

### Post by 3rdalbum on 2007-10-26
Maybe as an option in gconf-editor. I prefer the current behaviour, actually :-)  Would your proposal include other folders that had been accessed through Nautilus?

---

### Post by evilregis on 2007-10-26
I'm down with it as a gconf option too.

Ideally, I think whenever Nautilus is about to open a window -- any window -- it should (if the option is enabled in gconf, of course :D) check to make sure that window isn't already open before opening it.

I think it'd be primarily used with home folders as I can't remember the last time I ended up with three /var/log windows open.  They're usually windows that are easily clicked.  When I'm working with /etc, /var, etc. I am generally working in Terminal.

But that's not to say it couldn't happen.  And I think at the very least an option should be there to limit a new window instance opening where one already exists.

---

### Post by Bou on 2007-10-26
> **evilregis said:**
> Let's pretend I have Home and Computer icons on the desktop.  In Nautilus, if I double-click Home 5 times, it opens up Home 5 times.

It should only open one time and just get focus back if it already exists.

It's small, I know, but it's something I've run into a few times, in my case with my Music folder.  Where some time would go by, I have one opened from earlier, forgot to close it, open it again... only to start cleaning up my desktop and closing windows and seeing 3 Music folders.

That's the way spatial mode behaves. I'd propose switching to spatial as default, really it's so much better.

---

### Post by 23meg on 2007-10-26
This is against the logic of browser mode, and already the behaviour with spatial mode. If you want it in browser mode, though, Devil's Pie or a custom script with wmctrl may help.

---

