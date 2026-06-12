---
title: "Removing Sketchup7 in Wine 1.1.23"
date: 2009-06-06
forum: Wine
---

### Post by fester225 on 2009-06-06
I'm attempting to install Sketchup7 in Ubuntu 9.04 under Wine 1.1.23. During the process, I managed to install Sketchup, but now find it would be in my best interests to remove it, completely. I run Wine GoogleSketchUpWEN.exe, and even after using the remove tool, on the next run of Wine GoogleSketchUpWEN.exe, I still get a choice of removing or repairing the program rather than doing a complete fresh install. I am forced to assume Sketchup wasn't entirely removed during the last remove.

I even removed Wine using apt-get. When I re-installed Wine, Sketchup was still there the way it was after I had removed it.

How do I COMPLETELY remove Sketchup so I can do a fresh install?

---

### Post by NightMKoder on 2009-06-07
rm -Rf ~/.wine

that will remove all the files/programs in your wine folder. As for removing the menu entries...I think you need a menu editor or something. Search the forum, there's been a ton of topics on removing wine gnome menu items.

---

