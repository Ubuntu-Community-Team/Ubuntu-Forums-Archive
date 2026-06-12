---
title: "Virtualbox 5.0.22 Seamless mode shows windows as black boxes"
date: 2016-06-20
forum: Virtualisation
---

### Post by Separ on 2016-06-20
I'm having a little trouble with Virtualbox and seamless mode with a Windows 7 guest VM. Fullscreen mode works fine but whenever I switch to seamless mode, the windows are just black boxes, though they can be moved. The preview window in Virtualbox shows things as expected. If I switch back out of seamless mode, the entire virtual monitor is black and I have to save the VM and start it again before it displays normally. Attached is an example of the black box where a window is.

Environment:
Dell Latitude E6540
Ubuntu Gnome 16.04
Virtualbox 5.0.22 r108108
Windows 7 Professional guest

[ATTACH=CONFIG]269669[/ATTACH]

EDIT: So it seems that turning off 3D acceleration solves the issue but I'd still like to know if I can get it working with 3D turned on.

---

### Post by ajgreeny on 2016-06-20
> **Separ said:**
> <snip>

EDIT: So it seems that turning off 3D acceleration solves the issue but I'd still like to know if I can get it working with 3D turned on.
I suspect not.

There are a number of graphics bugs with VBox when 3D is enabled.

I found that flash in firefox, using the** browser-plugin-freshplayer-pepperflash** package showed black spaces in flash windows but works perfectly when 3D turned off.

I've searched the VBox forum about this (see [https://forums.virtualbox.org/search.php?keywords=3d+acceleration](https://forums.virtualbox.org/search.php?keywords=3d+acceleration))  but so far not found a solution other than disabling 3D.

---

### Post by Separ on 2016-06-20
Thanks for the reply. Maybe one of these days things like this will work, eh? :P

---

### Post by ajgreeny on 2016-06-21
We can hope, but don't hold your breath!

---

