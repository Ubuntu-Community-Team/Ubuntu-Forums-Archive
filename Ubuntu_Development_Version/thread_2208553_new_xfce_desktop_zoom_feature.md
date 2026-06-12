---
title: "new xfce desktop zoom feature"
date: 2014-02-28
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2014-02-28
This is in the release notes for beta 1, anyone know how to activate it?

[LIST]
[*]Xfwm4 (4.11) brings a new accessibility feature: zoom into your desktop using Alt+Scrollwheel
[/LIST]
i checked the accessibility and window manager settings and could not find it

---

### Post by Toz on 2014-02-28
Its activated by default for me, can't seem to find a setting either. Hold down the Alt key and move the scroll wheel up to zoom in and down to zoom back out (you can also move the mouse around the screen to zoom into different areas).

---

### Post by sammiev on 2014-02-28
It's working for me but I must hold down the ( Ctrl + Scrollwheel ).

---

### Post by pqwoerituytrueiwoq on 2014-03-01
i was trying it with the live beta 1 image in virtualbox
i cant get it working

---

### Post by ajgreeny on 2014-03-01
> i was trying it with the live beta 1 image in virtualbox
i cant get it working                         Could this be something to do with running in VBox, as I can not get it to work either on a fully updated Xubuntu 64 bit in VBox, not a live system but a full VBox installation.

A Firefox window will zoom with Ctrl+Scrollwheel as normal, and I wonder if that is what sammiev was seeing.

---

### Post by sammiev on 2014-03-01
> **ajgreeny said:**
> Could this be something to do with running in VBox, as I can not get it to work either on a fully updated Xubuntu 64 bit in VBox, not a live system but a full VBox installation.

A Firefox window will zoom with Ctrl+Scrollwheel as normal, and I wonder if that is what sammiev was seeing.

It works with the file system as well and not just FF.

---

### Post by Toz on 2014-03-01
[Here]("http://blog.alteroot.org/articles/2013-12-11/xfce-xfwm4-zoom-mode.html") is a video showing the feature in action.

---

### Post by QDR06VV9 on 2014-03-01
> **sammiev said:**
> It's working for me but I must hold down the ( Ctrl + Scrollwheel ).

Also works now on GS using your same Key combo.:)

---

### Post by ionuke on 2014-05-16
But how do you disable this marvelous feature? 
I never use it and it interferes with my other programs which use CTRL+scrollwheel for zooming in (i.e. Photoshop).

[EDIT] 
After some more searching I found a partially acceptable answer here: [https://forum.xfce.org/viewtopic.php?pid=33003](https://forum.xfce.org/viewtopic.php?pid=33003)
> [COLOR=#333333][FONT=Verdana]For the record, this feature can be disabled by going to "Window Manager Tweaks" configuration panel, "Accessibility" section, and setting "none" as the "Key used to grab and move windows". But it will also disable the grab/move with [key]+mouse feature.[/FONT][/COLOR]
The problem with this is that it disables the grab key. In my case this is fortunate, as i was anyway looking to disable that feature also. Might not be desired behavior for others, though.

---

### Post by cariboo on 2014-05-16
Thread closedm as Trusty has been releasd.

---

