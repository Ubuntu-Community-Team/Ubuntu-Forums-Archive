---
title: "VLC media player keeps moving itself under top panel"
date: 2018-04-13
forum: Ubuntu Development Version
---

### Post by &amp;KyT$0P# on 2018-04-13
Xubuntu 18.04 with Openbox window manager.  I like to position VLC media player at the top right of my screen.  Every time I open VLC, it moves upward a bit, often placing itself underneath my top panel.

As a test, I tried moving the panel to the bottom, but that doesn't help - then VLC just goes off screen.  I also tested with xfwm4 instead of Openbox, but VLC still places itself a little bit further up the screen every time it's opened.

How to get VLC to properly restore its window position?

---

### Post by ajgreeny on 2018-04-13
Have a look in **Settings Manager -> Window Manager Tweaks** and try changing the settings in the **Placement** tab.

---

### Post by &amp;KyT$0P# on 2018-04-13
That's for xfwm4.  I'm using Openbox.  But thanks for the suggestion to try window manager settings!  I added the config to Openbox, and VLC now gets positioned where I want it! :D

---

### Post by ajgreeny on 2018-04-13
Brilliant!
I didn't notice you're using openbox, but at least it gave you a clue about where to look.

---

