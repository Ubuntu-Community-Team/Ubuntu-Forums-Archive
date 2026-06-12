---
title: "HowTo: Compiz with no flash on fullscreen virtualbox when spinning cube"
date: 2008-05-16
forum: Virtualisation
---

### Post by 00arthuryu on 2008-05-16
Heya
If you're using compiz with virtualbox, do you get a flash with virtualbox when you turn to another screen/desktop/spin the cube? It also happens when you go back to the desktop with the fullscreen virtualbox. Has anyone got this problem?? I think I've found a sneaky unorthadox solution :D you'll see what I mean

first of all, you need compiz configuration manager (ccsm) installed, I do not think the distro matters that much as it seemed to happen with all flavours of ubuntu so far.
Anywho, If you go to General Options on ccsm and move along the top tabs until you get to 'Opacity Settings' add a new to 'Window Opacities' with
```

role=consoleWnd

```
With Opacity window value as '99'

this should do the trick
but like I said, i'm sure theres a much better way of doing it but I'm a nOOb and this is the nOObie way of doing it
:lolflag:

---

### Post by 00arthuryu on 2008-05-17
only me eh? heh heh

---

### Post by el-mar01 on 2008-08-29
> **00arthuryu said:**
> only me eh? heh heh

LOL I had the same problem as well !! thankyou very much arthuryu !! That solution worked perfectly !! Its weird though I thought I had it set up perfectly so it didn't do that but when I restarted it began to do it again so I applied your fix and it worked !!

Damn I can't give you a thanks .. hrrmm I will just thank one of your most recent posts.

---

### Post by el-mar01 on 2008-09-04
This also works for VMWare fullscreen .. instead of role=consoleWnd in the opacity settings just put in vmware and vmplayer.

---

### Post by el-mar01 on 2008-11-17
*bump* I was hoping that I wouldn't have to use this workaround on Compiz 0.7.8 but it seems I still have to use it.

---

