---
title: "If changes in gnome-keybinding-properties don't work run metacity --replace"
date: 2011-12-27
forum: Tutorials
---

### Post by vezolmi on 2011-12-27
If you have changed something with gnome-keybinding-properties (for example disabled a keyboard  shortcut, e.g. ALT+F1 -that shows the  main menu of the panel-) but the changes don't work (and F5 or CTRL+R on the desktop  don’t solve it) this command can solve the problem:
metacity --replace (you can run it from the dialog that appears holding the ALT key and pressing the F2 key)


This (re)starts the Metacity window manager.


You can also start Metacity running (but not restart it; only works to start Metacity if another window manager is in use before):
gnome-appearance-properties (also possible from ALT+F2) and setting "Visual Effects" to None

---

