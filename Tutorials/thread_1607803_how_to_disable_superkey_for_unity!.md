---
title: "how to disable superkey for unity!"
date: 2010-10-28
forum: Tutorials
---

### Post by rinaldow on 2010-10-28
For anyone who wants to turn off the freaky superkey (windowskey) function for unity in ubuntu 10.10:

- start terminal (no root)
- type "gconf-editor" and press the enter key. 
- go to "/apps/mutter/general/overlay_key"
-->erase the "Superkey_L" from the string
- do a restart and you're ready to go :)

Your advantage hereby is that you can set up keyboard sho:

Windows Vs. Ubuntu = Function
superrtcuts in combo with superkey, and unity not interrupting it...
I am used to windows 7, so i was trying to implement the windows shortcuts into ubuntu, and that went terrible for me in UNE 10.10

---

### Post by erjoalgo on 2011-06-05
Please check my post for a workaround that enables user to keep unity, 
[http://ubuntuforums.org/showthread.php?t=1775670](http://ubuntuforums.org/showthread.php?t=1775670)

---

### Post by giancarlocp on 2011-11-23
S.O.S.
how to disable superkey for unity on 11.10?

---

### Post by giancarlocp on 2011-11-23
It wasn't so tough
on 11.10 ccsm is not default installed neither gconf-editor.

$ sudo apt-get install compizconfig-settings-manager gconf-editor.

on ccsm is in "Ubuntu Unity Plugin"
[http://www.techdrivein.com/2011/06/5-useful-compiz-tweaks-for-ubuntu-1104.html](http://www.techdrivein.com/2011/06/5-useful-compiz-tweaks-for-ubuntu-1104.html)

on gconf-editor is in *apps/metacity/global_keybindings/*, the value of “panel_main_menu” is “Alt+F1”
[http://ubuntuguide.net/ubuntu-using-windows-keysuper-key-to-launch-gnome-main-menu](http://ubuntuguide.net/ubuntu-using-windows-keysuper-key-to-launch-gnome-main-menu)
same on ccsm "Gnome Compatibility".

---

### Post by giancarlocp on 2011-11-23
There is a trap, if you change that key, launchers (Super+1,Super+2...)
are disable, even if you use another key.

i have to live with that.

---

