---
title: "GS use baobab instead of nautilus"
date: 2013-03-14
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-03-14
As the old "fallback" DE is now fully broken (latest mutter job), i've started GS as a substitute (not so huge difference after all).
But when i've clicked on Places -> Home, i was expected to get nautilus loaded, but got baobab instead ;)
Well, the menus are a bit confuse (looks a mess compared to the old gnome-classic aka fallback), and have not yet found how to change the app's preferences.
Need to start Alacarte from the terminal.

Have you also got that mess ?  (the 2 gnome3-team ppas activated)

---

### Post by mc4man on 2013-03-14
Possibly caused by the desktop-file-utils upgrade & maybe the same as this thread
[http://ubuntuforums.org/showthread.php?t=2125567](http://ubuntuforums.org/showthread.php?t=2125567)
No ill effect, (or any effect) here though don't quite get the purpose of the change, possibly there is one
> * debian/defaults.list:
    - use current glade version as default
    - default to nautilus-folder-handler, which doesn't use --new-window,
      that way we correctly focus open view rather duplicating those


---

