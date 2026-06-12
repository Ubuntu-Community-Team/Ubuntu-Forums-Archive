---
title: "Nautilus 3.8 files appear progressively"
date: 2013-07-12
forum: Ubuntu Development Version
---

### Post by TiCPU on 2013-07-12
I don't know when this was changed, but right now with Files 3.8.2 on Ubuntu 13.10, when opening a folder, files appear progressively until all files are in view. This causes a serious problem, each file is a moving target until the folder is ready, this makes the folder view useless until it is loaded anyway.

It seems this behaviour was stolen from Windows Vista which was the first OS I used to exhibit such moving target behaviour.

One solution to this problem would be to not auto-sort the files progressively but append them to the end then when fully loaded, sort them. This will move the files around only once, and not a couple of times.

Edit: After testing, /usr/lib or /usr/bin will block until all files are ready to be shown and only additional information is added progressively, which is much better! However, when a folder was sorted by "Date" for example, it will exhibit this behaviour on re-entry.

---

### Post by markbl on 2013-07-12
> **TiCPU said:**
> I don't know when this was changed, but right now with Files 3.8.2 on Ubuntu 13.10, when opening a folder, files appear progressively until all files are in view.
I'm running gnome-shell on a stock Ubuntu 13.04 with GNOME 3 ppa and I have noticed this change also, since the last few days. Looks crappy doesn't it?

---

