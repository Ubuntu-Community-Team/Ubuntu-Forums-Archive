---
title: "Recording large windows"
date: 2009-05-12
forum: Ubuntu Studio
---

### Post by durand on 2009-05-12
Is it possible to record windows that are bigger than the size of the desktop you are using? I want to record a game at a resolution of 2500x1500 so that I can crop out the HUD and stuff lile that as the game doesn't seem to support disabling it. Is there a way using recordmydesktop or something like that to record stuff like that?

Or is there an easy tutorial on creating xservers with resolutions bigger than my screen?

Thanks.

---

### Post by skullmunky on 2009-05-14
What you want is "Virtual desktop size".  this gives you an X desktop larger than your actual screen dimensions; moving the mouse near the edges of the screen scrolls it around.

AFAIK you can only set this by hand in xorg.conf, but do a little searching on that.

---

### Post by durand on 2009-05-14
Yeah, I realised that I can increase the size with nvidia's settings. I'll try the xorg method as well as recordmydesktop somehow managed to blacken the edges of the desktop when I changed the size with nvidia.

---

### Post by lukeiamyourfather on 2009-05-14
> **durand said:**
> Yeah, I realised that I can increase the size with nvidia's settings. I'll try the xorg method as well as recordmydesktop somehow managed to blacken the edges of the desktop when I changed the size with nvidia.

Screen recorders pull from the video memory don't they? So if its not being actually displayed by the card then there's nothing to capture. Maybe use a VNC connection and use a VNC session recorder? Cheers!

---

### Post by durand on 2009-05-14
Hmm, yeah, you might be right. I think I'll just record in a lower resolution.

---

