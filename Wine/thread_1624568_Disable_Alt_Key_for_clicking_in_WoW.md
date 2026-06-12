---
title: "Disable Alt Key for clicking in WoW"
date: 2010-11-17
forum: Wine
---

### Post by dardack on 2010-11-17
Just remembered how to do this after googling (yes I changed my movement key to super, and yes I tried that unchecking let the window manager handle wine crap, first didn't work, second made it so my keyboard didn't work in wow after tabbing out).

System -> Preferences -> Keyboard -> Layouts -> Options... -> alt/win key behavvior -> click Add the standard behavior to Menu key.

This now allows wow in wine to properly interpret alt+right clicking for addons and such.

---

### Post by kneeki on 2011-11-07
I've tried this using Ubuntu 11.10 and it doesn't seem to be working after shutting down all Wine applications and restarting them. Is there something I'm missing?

[img]http://i.imgur.com/2nH5r.png[/img]

---

### Post by dsanta on 2012-08-31
The trick is to install "CompizConfig Settings Manager".
Under "Window Management" click on the "Move Window" icon.  I change "Initiate Window Move" from <alt>Button1 to <alt><super>button1.  Changing in in this one place seemed to fix the other alt function behaviors.

---

