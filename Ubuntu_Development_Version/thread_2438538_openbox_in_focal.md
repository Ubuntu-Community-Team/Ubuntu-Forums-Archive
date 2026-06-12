---
title: "openbox in focal?"
date: 2020-03-14
forum: Ubuntu Development Version
---

### Post by Irihapeti on 2020-03-14
When I want a lightweight installation, I've been in the habit of installing Ubuntu-standard and then installing xorg and openbox on top of that. However, in focal there seems to be some issue with python2, which is not getting upgraded. I believe it's because Python2 is being phased out.

Does anyone know what's likely to happen here? Is openbox now deprecated? If so, what other equivalent lightweight/minimal WM is recommended?

---

### Post by zika on 2020-03-14
i3, sway, ratpoisson, stumpwm, list is long... ;)
openbox is still very good eventhough a bit old...
It's just a WM... ;)

---

### Post by sudodus on 2020-03-14
I often use (and recommend) the window manager Fluxbox for that purpose. I  tried it in Ubuntu Server Focal right now, and it works, at least the basic features that I tested works as expected.

JWM is another window manager, that is worth testing.

---

### Post by guiverc on 2020-03-14
Lubuntu uses `openbox` and thus I can confirm it works fine (a Lubuntu install allows you to select openbox as a session at login).

I do recall discussions in #lubuntu-devel about specific parts (*menu related maybe*) of openbox that did rely on `python2` and a number of (fix) alternatives were discussed, but I remember little of it now (I didn't need to know so didn't really take any notice).  Most of `openbox` though is good, or at least everything Lubuntu uses is.

---

### Post by Irihapeti on 2020-03-14
Thanks for the replies.

I've taken a closer look using aptitude (which I should have done earlier, sorry) and it seems that it's obmenu - the menu editor - that's the issue. I've removed it plus the python2 dependencies and the system is happy. I suppose I'll just need to get used to editing the menu XML file directly. :|

---

