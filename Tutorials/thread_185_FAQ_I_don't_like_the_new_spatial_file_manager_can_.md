---
title: "FAQ: I don't like the new spatial file manager can I turn it off?"
date: 2004-10-11
forum: Tutorials
---

### Post by ubuntu-geek on 2004-10-11
Gnome uses the new spatial file manager layout many people don't like this. You should at least give it a try :) However if you cannot stand it follow these steps.
> 
1. Open a terminal window
2. Run the following command: gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true
3. Log out and log in again, and the file manager will be back to the way it used to be in previos gnome releases.

If you wish to enable spatical mode again follow these steps:
> 1. Open a terminal window
2. Run the following command: gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser false
3. Log out and log in again, and the file manager will be back to spatical mode.

---

### Post by jdong on 2004-10-24
The less-complicated way:

1. Pull down the Computer menu, goto Desktop Prefs->File Management.
2.Choose Behavior tab.
3.Check "always open in browser windows"

---

### Post by TheMTtakeover on 2011-11-12
Does this still work?

---

