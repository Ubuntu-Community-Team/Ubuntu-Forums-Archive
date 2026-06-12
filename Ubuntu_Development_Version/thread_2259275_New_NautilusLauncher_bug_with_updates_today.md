---
title: "New Nautilus/Launcher bug with updates today"
date: 2015-01-03
forum: Ubuntu Development Version
---

### Post by sgage on 2015-01-03
After writing in another thread that everything was working fine with GS, an update just now seems to have introduced a bug:

Launching nautilus from the launcher icon results in a second nautilus icon appearing at the bottom of the launcher. Clicking that launcher (which has the 'running' highlight') brings up the existing (running) nautilus as expected. Clicking the original launcher launches a new nautilus window, but no new icons. Subsequent clicks on the original launcher continues to bring up new instances, but no new icons.

Anyone else seeing this?

---

### Post by sgage on 2015-01-03
I solved the problem by simply deleting the existing nautilus launch icon, and making a new one.

---

### Post by sammiev on 2015-01-03
Tried to verify the bug on a fully updated Ubuntu Gnome but not having the same out come as you.

---

### Post by sgage on 2015-01-03
I don't know what caused it. It was working normally, then I did a few updates and the described behavior occured. I simply added the newly appearing icon to favorites, deleted the original one I had there, and everything is behaving normally now. Mystery!

---

