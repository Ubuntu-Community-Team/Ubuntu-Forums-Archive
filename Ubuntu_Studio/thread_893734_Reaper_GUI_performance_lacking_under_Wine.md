---
title: "Reaper GUI performance lacking under Wine"
date: 2008-08-18
forum: Ubuntu Studio
---

### Post by uboontoo on 2008-08-18
I have Ubuntu set up for audio production work (alsa/jack/wine/wineasio/etc), and the low-latency audio performance is commendable, albeit not nearly as good as running under Windows, but still very usable.

The GUI, on the other hand, is in a much worse state in Wine.  Scrolling and zooming are horrendously slow (even with the UI set to unbuffered).  Are there any tricks to faster GUI performance?

---

### Post by uboontoo on 2008-08-22
*bump*

---

### Post by ThrashJazzAssassin on 2008-08-22
For some reason the grid slows down scrolling so go to **Options > show grid** and turn it off.

To speed up zooming go to **Options > Preferences... > Appearance** and at the bottom where it says **Track buffered (recommended)** change it to **Unbuffered (flickery)**

Another option I just found is under **Options > Preferences... > Buffering** for running under WINE it recommends to **untick** the very bottom box: **Use native events for synchronising** This cleaned up my audio significantly.

---

### Post by eric71 on 2008-08-26
You've probably already done this, but make sure desktop effects are switched off.

---

