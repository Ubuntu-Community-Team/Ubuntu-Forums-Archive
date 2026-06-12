---
title: "Reproducible problem with Audacity menus"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nick Payne on 2012-03-17
Just installed Audacity 2.0 from the Universe repository for Precise. If I select Preferences from the Edit menu, and then ok the dialog, all of the menus except the "Fi" of the File menu are blanked out by a white bar (see attached image). As soon as I resize the Audacity window, the menus reappear. I have global app menus disabled because they're a pain in the **** with a big monitor.

The problem doesn't happen with Audacity 1.x on Lucid, but as I can't install Audacity 2 there to check, I don't know if the problem is with Audacity 2 or elsewhere.

[IMG]http://www.users.on.net/~njpayne/scans/audacity.jpg[/IMG]

---

### Post by Irihapeti on 2012-03-17
I'm noticing the same thing.

I'm running gnome-fallback, if that affects anything.

---

### Post by stevethefiddle on 2012-03-24
The problem occurs when Audacity is built against WxWidgets 2.8.12 (which is the case for the Ubuntu repository version). The problem is known to the Audacity developers ([http://bugzilla.audacityteam.org/show_bug.cgi?id=458](http://bugzilla.audacityteam.org/show_bug.cgi?id=458) ).
As Nick Payne commented, the menus can be brought back by resizing the Audacity window.

---

