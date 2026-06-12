---
title: "Removing Leftover Files"
date: 2009-06-07
forum: Wine
---

### Post by loweehahn on 2009-06-07
I've uninstalled WINE but then the icon under Applications is still there. Later on I found out that I've to manually remove the hidden files so I revealed all hidden files and tried to remove them but they are protected and requires me as a root owner. How do I enable myself as a root owner to remove these files?

---

### Post by izizzle on 2009-06-07
```
sudo rm -rf PathToFile
``` Be careful with this tool. Only use it when you know what you are doing.

---

### Post by Bucky Ball on 2009-06-07
[http://wiki.winehq.org/FAQ#head-2e99ab665e3b15d1880eff2bcbb640b2d5839586](http://wiki.winehq.org/FAQ#head-2e99ab665e3b15d1880eff2bcbb640b2d5839586)

That should help. Be VERY careful with the instruction given in the last post. I advise you follow a guide for completely uninstalling Wine rather than slash through the jungle removing things you're not too sure about. With that command, there is no going back once something is removed.

Yes, Wine is a hassle to remove. Normal. :)

---

### Post by hikaricore on 2009-06-07
> **loweehahn said:**
> I've uninstalled WINE but then the icon under Applications is still there. Later on I found out that I've to manually remove the hidden files so I revealed all hidden files and tried to remove them but they are protected and requires me as a root owner. How do I enable myself as a root owner to remove these files?


How many times does this question have to be asked?
There are no left over files, WINE doesn't always remove itself from the gnome/kde menus.
Disable them via the menu edit functions..

---

### Post by loweehahn on 2009-06-08
Bucky Ball, I've followed the instructions given in the link you provided and now the WINE icon under Applications is gone. But when I searched for WINE files under File System there are still quite a few left and because I'm not the root owner so I can't remove them. How can I remove them?

---

### Post by Bucky Ball on 2009-06-08
You could open a terminal and type/paste:

sudo nautilus

That will open a window with you as root and you should be able to remove them.

But that could be risky, I don't know if you could remove something you shouldn't. I installed Wine, never used it and have had a heap of files sitting there for months, even though it is effectively uninstalled. No issues. I figured a fresh install will clean things up when I eventually get round to it.

---

### Post by loweehahn on 2009-06-10
Thanks a lot! This solved my problem. :D

---

