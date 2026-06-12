---
title: "SDL faster than x11/xWindows?"
date: 2005-07-13
forum: The Cafe
---

### Post by sapo on 2005-07-13
Ever since i started to use a custom dark theme here i was noticing that my pc became a little slow.. even using gedit it was giving me some slowdowns... and as i have a 9800pro, i tried to change to SDL..

I dont know if its just Psychologic... but my desktop seens faster now... i ve noticed specially in azureus that the rendering of the imagens on the screen is faster...

Is it true or its just my imagination? 

whats the main difference between xWindows and SDL on the desktop?

---

### Post by Gnobody on 2005-07-13
[QUOTE=sapo]Ever since i started to use a custom dark theme here i was noticing that my pc became a little slow.. even using gedit it was giving me some slowdowns... and as i have a 9800pro, i tried to change to SDL..

I dont know if its just Psychologic... but my desktop seens faster now... i ve noticed specially in azureus that the rendering of the imagens on the screen is faster...

Is it true or its just my imagination? 

whats the main difference between xWindows and SDL on the desktop?[/QUOTE]
 how do you use SDL for your desktop?

---

### Post by sapo on 2005-07-13
[QUOTE=Gnobody]how do you use SDL for your desktop?[/QUOTE]

Just click in:

System -> Preferences -> Multimedia System Selector -> video -> SDL

But i dont understand about it.. i dont know if the desktop drawing is using SDL or just when i play videos... i m confused  ](*,)

---

### Post by Gnobody on 2005-07-13
It's the video output sync which is only applicable to Gnome/GStreamer video apps. SDL runs on top of X11.

---

