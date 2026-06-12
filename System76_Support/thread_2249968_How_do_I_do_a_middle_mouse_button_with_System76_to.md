---
title: "How do I do a middle mouse button with System76 touchpad"
date: 2014-10-25
forum: System76 Support
---

### Post by kencorbin on 2014-10-25
Took me a couple days to figure out that there are hidden left and right mouse buttons at the bottom of the touchpad.  But I really use the middle mouse button a lot and have not figured out how I can do it with this touchpad.  Tried enabling middle mouse button emulation, but that doesn't seem to work.  Anyone have any other ideas?

---

### Post by sudodus on 2014-10-26
I have no such computer, but it often works (by default) to click on the left and right button at the same time (within a very small interval). This often emulates the middle button. You may need to try several times, because the time interval is very tight (may be possible to increase).

---

### Post by Thalarse on 2014-10-26
By default you just have the left and right click (I think it might be one physical button, but the touchpad knows where you tap). You can use synclient in the command line to change the settings in many ways. For some reason it doesn't remember this across bootups, though, so I have it set to "synclient TapButton2=3" on startup. This means to middle click I tap three fingers. Synclient on its own will give you the current parameters.

---

### Post by jweber53 on 2015-04-14
> **Thalarse said:**
> By default you just have the left and right click (I think it might be one physical button, but the touchpad knows where you tap). You can use synclient in the command line to change the settings in many ways. For some reason it doesn't remember this across bootups, though, so I have it set to "synclient TapButton2=3" on startup. This means to middle click I tap three fingers. Synclient on its own will give you the current parameters.

This answer helped solved the middle mouse button for me, but the correct command is   
 
```
synclient TapButton3=2
```

See *man synaptics *&#8203;for all the details. It looks like there are many options for configuring the track pad.

---

