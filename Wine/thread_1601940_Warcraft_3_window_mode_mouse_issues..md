---
title: "Warcraft 3 window mode mouse issues."
date: 2010-10-20
forum: Wine
---

### Post by styLz on 2010-10-20
Hey all hope you can help me out here with a little issue I'm having.

So I've decided to want to play this in windows mode now instead of full screen because the tabbing effect is very annoying. So now the issue is... my mouse leaves the window when I move it off its side. Is there a command to add in while running the game like -window and --opengl? It is very annoying when I am trying to scroll across on the map by dragging the mouse to the side of the screen then my mouse leaves the window and does nothing. Thanks

---

### Post by gufide on 2010-10-22
I see something about this, I found that:

> wine regedit


Browse to:
HKEY_CURRENT_USER\Software\Wine\DirectInput

(Create a new key called DirectInput if it doesn't exist)

Create a new string value, named "MouseWarpOverride" and set the value to "force".and you can do a "hybrid" mode between fullscreen and window mode. Just run warcraft 3 as window mode. after, open the compizconfig settings manager, go to window decoration and put "any & !(name=war3.exe)" in decoration and shadow, now go to window rule and put "name=war3.exe" in maximized. You should got it. If the screen is ugly, just add -opengl at the end of your shortcut

---

### Post by styLz on 2010-10-24
Hmm I gave that a try and it didnt work.
Mouse still leaving the window.

---

### Post by Peter7K on 2010-10-25
[http://ubuntuforums.org/showthread.php?p=5703907#post5703907](http://ubuntuforums.org/showthread.php?p=5703907#post5703907)

---

