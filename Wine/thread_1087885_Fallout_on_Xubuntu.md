---
title: "Fallout on Xubuntu"
date: 2009-03-05
forum: Wine
---

### Post by fugazi32 on 2009-03-05
Hi, i've got Fallout 1 installed & running okay ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=43&iTestingId=33795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=43&iTestingId=33795)) except for 2 problems:

1) In full-screen mode, when I start the game & it changes the screen resolution I can still see the XFCE panels.

2) If I run the game in windowed mode & with *winecfg* set the mouse cursor to NOT leave the window, it still does in-game...??!

Any help would be much appreciated! Again, i'm glad it works straight out of the box for me, save for these two problems.

---

### Post by cogadh on 2009-03-05
If you uncheck the option to allow the window manager to control the windows in winecfg's graphics options, it should correct the panel problem. Not sure about the mouse issue, though.

---

### Post by fugazi32 on 2009-03-05
Cheers, works okay in full screen now, although a little skewed to the left, though it might be my X set-up as it does this alot when running apps in full screen.
The in-game mouse response seems a little slow, any way to speed this up? I seem to recall someone mentioning a few extra command parameters could speed the game up.

**UPDATE:** Installed *Fallout 2* as well, seems to be okay; apart from same problem - slow mouse cursor response.

---

### Post by NightMKoder on 2009-03-05
[http://bugs.winehq.org/show_bug.cgi?id=6033](http://bugs.winehq.org/show_bug.cgi?id=6033) has some solutions.

---

### Post by fugazi32 on 2009-03-08
> **NightMKoder said:**
> [http://bugs.winehq.org/show_bug.cgi?id=6033](http://bugs.winehq.org/show_bug.cgi?id=6033) has some solutions.

Phew! Cheers for that link, seems there's a major big issue with the mouse speed, but once in the game I cranked up the mouse sensitivity and it seems fine & playable now, really getting into it! Peace.

---

