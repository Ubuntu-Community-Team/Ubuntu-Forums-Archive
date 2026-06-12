---
title: "Window movement is not smooth"
date: 2017-09-12
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-12
Moving windows is not smooth in default Ubuntu, Wayland or Xorg. The movement is like a collection of slight jumps. The maximizing and minimizing happens the same way. Is this a Gnome problem or Ubuntu problem? Autohiding of the panels are jerky too. In comparison, in Ubuntu Unity 17.10, the movements are very smooth.

---

### Post by dino99 on 2017-09-12
no a such problem here with lightdm login and intel igp

---

### Post by Perfect Storm on 2017-09-12
could it be a video driver problem?
No problem here with the latest nvidia driver here.

---

### Post by Chanath on 2017-09-12
Both are Lenovo laptops, and both have Unity only and Ubuntu default 17.10 installed in separate partitions. Both have Intel integrated video.

---

### Post by ventrical on 2017-09-12
> **Chanath said:**
> Moving windows is not smooth in default Ubuntu, Wayland or Xorg. The movement is like a collection of slight jumps. The maximizing and minimizing happens the same way. Is this a Gnome problem or Ubuntu problem? Autohiding of the panels are jerky too. In comparison, in Ubuntu Unity 17.10, the movements are very smooth.

This is what happened to me when I installed dash2dock  a while back and then removed it.  its probably different issue.

---

### Post by Chanath on 2017-09-12
> **ventrical said:**
> This is what happened to me when I installed dash2dock  a while back and then removed it.  its probably different issue.

Ubuntu Dock is a fork of Dash to Dock, so problems come through...

---

### Post by mc4man on 2017-09-12
See what happens if you disable animations in gnome-shell (should be easily found in the tweak tool

---

### Post by Chanath on 2017-09-12
> **mc4man said:**
> See what happens if you disable animations in gnome-shell (should be easily found in the tweak tool

Yes, it stopped the jumps.
Gnome is getting buggier?

---

### Post by mc4man on 2017-09-12
If it was up to me, (not even close), I'd default disable animations & let those that see some value in it enable themselves. Maybe I'll file a bug, maybe not.
It will also cause a poor look in video players when using hwdec & going to & from fullscreen. 
Personally I think it's worthless..

---

### Post by Chanath on 2017-09-12
> **mc4man said:**
> If it was up to me, (not even close), I'd default disable animations & let those that see some value in it enable themselves. Maybe I'll file a bug, maybe not.
It will also cause a poor look in video players when using hwdec & going to & from fullscreen. 
Personally I think it's worthless..

I disabled animations to have a peace of mind, while using Gnome.
But, everything is enabled in Unity, a full blast of Compiz, and window movements are quite smooth. A long way to catch up with Unity.

---

### Post by mc4man on 2017-09-12
Removed link as I invalidated report, will only file on elements of this concerning video playback...

---

