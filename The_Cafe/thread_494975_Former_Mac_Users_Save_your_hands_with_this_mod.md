---
title: "Former Mac Users: Save your hands with this mod"
date: 2007-07-07
forum: The Cafe
---

### Post by ThinkBuntu on 2007-07-07
Anyone who's used Macs and other PCs for long enough knows that Apple+Q is far more comfortable than Control+Q. I have no fact to back this up, but the placement of the Apple Key (Control Key equivalent) is just more ergonomic in my opinion. Anyway, here's a quick way to switch your Alt and Control keys on both sides of the keyboard. I thought this was a little minor to warrant its own topic in the Tutorials forum.
**Important note: Your keycodes may differ (lines 4-8 ). You can test which ones are actually yours by running *xev* and testing the four keys in question.**

1. Save this file in your home folder, as xmodmap.sh (or anything.sh):```
xmodmap -e "remove Control = Control_L";
xmodmap -e "remove Control = Control_R";
xmodmap -e "remove Mod1 = Alt_L";
xmodmap -e "remove Mod1 = Alt_R";
xmodmap -e "keycode 64 = Control_L";
xmodmap -e "keycode 109 = Control_R";
xmodmap -e "keycode 37 = Alt_L";
xmodmap -e "keycode 113 = Alt_R";
xmodmap -e "add Control = Control_L";
xmodmap -e "add Control = Control_R";
xmodmap -e "add Mod1 = Alt_L";
xmodmap -e "add Mod1 = Alt_R";
```
2. Run:
```
[username@host ~]$ sh xmodmap.sh
```
to see if you like it. If you do, put that command in your new session commands. I've also heard that you can save it as .xmodmap, and it will automatically load, but this didn't work for me.

Anyway, happy typing! I was able to switch the physical keys on my ThinkPad to mirror the change, as well.

---

