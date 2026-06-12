---
title: "IDEA: Terminal Prefs, include option to change it's default window size."
date: 2008-07-14
forum: Ubuntu Brainstorm
---

### Post by philinux on 2008-07-14
I would like to suggest this change to Terminal Prefs.

At the moment the Hardy guide has this to say.

 > Change the default Terminal window size

The default size of the Terminal window is around 80 columns wide and 24 columns high. To alter this, edit the file /usr/share/vte/termcap/xterm. You can use the following command:

 sudo gedit /usr/share/vte/termcap/xterm

Just a few lines from the top will be the line reading:

 :co#80:it#8:li#24:\

Change the number right after co# to change the width. Change the number right after li# to change the heigh

---

### Post by xebian on 2008-07-14
> **philinux said:**
> I would like to suggest this change to Terminal Prefs.

At the moment the Hardy guide has this to say.

In KDE, configure your terminal the way you want it - size, scheme, colors, etc.., and then 'save as default' .  Or define as many profiles you want.:guitar:

---

### Post by philinux on 2008-07-14
Sorry should have said. This is for gnome.

---

### Post by knarf on 2008-07-14
...or, instead of changing the default/while waiting for the default to be changeable in the prefs. pane change the command you use to start a gnome-terminal. Add --geometry=80x50 to get an 80 col/50 row terminal, etc. I use this to start terminal-based apps from Gnome, eg. Mutt:
```
gnome-terminal --geometry=120x50 -t Mutt -e mutt
```
This gives you mutt (*-e mutt*) in a 120 col/50 row terminal (*--geometry-120x50*) with a window title of 'Mutt' (*-t Mutt*). Feed it to a launcher or put it under a command key for quick access.

Adding a new preference should not be necessary I think. Saving the current state of a terminal window as default for a given profile (like the above-mentioned KDE terminal does) sounds like the better way of doing this. This might necessitate the addition of a new context menu option or checkbox: 'save current state as default for profile'

---

