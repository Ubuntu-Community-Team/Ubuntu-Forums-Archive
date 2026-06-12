---
title: "Turning Wine off"
date: 2010-11-14
forum: Wine
---

### Post by Ranko Kohime on 2010-11-14
I've only used Wine once on a system other than my Netbook, and I didn't use it long enough to figure out this behavior, so pardon me if it's a silly question.  :P

Anyway, when I did run it, I noticed it left running, or started as a service, several processes that I assume mimic Windows functions.  This wasn't an issue on the other machine I used it on, as I had swap available.

On my Netbook, I have no swap, due to the SSD.  I want to run a Windows program on it that I use very infrequently, but I'm concerned about the memory usage of the extra bits that Wine runs.  This program is AutoTap, and it requires USB hardware, which does not function correctly in a Virtual Box running XP (I've already tried that).

Does Wine clear out it's processes on a reboot, or, if not, is there a way to turn Wine off when I don't need it?

---

### Post by Soulcage on 2010-11-14
When you close all the windows programs all of wine's exes close right after. If this doesn't happen you can type ```
wineserver -k
```

---

### Post by Ranko Kohime on 2010-11-14
> **Soulcage said:**
> When you close all the windows programs all of wine's exes close right after. If this doesn't happen you can type ```
wineserver -k
```
Thank you, that's good information to know.  :)

---

