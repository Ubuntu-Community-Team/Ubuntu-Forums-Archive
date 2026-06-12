---
title: "window size?"
date: 2011-10-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by scradock on 2011-10-23
Does anyone know how to set the window size these days? Specifically for the gnome Mahjongg game - which now always appears at a size that's far too small for my elderly eyes, so I have to fiddle with the (single-pixel) grab lines to expand it.

I've checked in gconf-editor and dconf-editor, the ...schema.xml file, and all, but can't find anywhere that refers to the window size.

Is this another example of Canonical deciding how my computer should work, and removing any way for me to change this? If so, I'm annoyed. If it's an oversight, maybe someone will notice that 

IT OUGHT TO BE POSSIBLE TO DO STUFF LIKE THIS

This is Ubuntu - not a proprietary walled-garden like AOL used to be in the old days.

Yes, this isn't exactly PP-specific - it happened a few weeks back in OO - but it still annoys me in PP...

---

### Post by cariboo on 2011-10-23
For Mahjong click either Settings->Fullscreen, or press F-11

---

### Post by scradock on 2011-10-23
> **cariboo907 said:**
> For Mahjong click either Settings->Fullscreen, or press F-11

Thanks - I don't need full-screen - just bigger than three inches square.

---

### Post by VinDSL on 2011-10-23
I've been going borderless (on certain windows - browsers and so forth) these days.

I resize these borderless windows using the "Love Handles" in Compiz.  I think you have to enable them in CCSM, e.g. they aren't enabled by default.

Heh!  I'd give you the real name for them, but I'm in GS right now.

Anyway, if you're running Unity, you might give love handles a whirl...  ;)

---

### Post by mc4man on 2011-10-23
You can adjust mahjong' opening window siz in compiz > window rules

I'm not up on all the in's & outs of window rules, in this case it seems simple but you may want to hear from someone that spends some time in there.
There are likely several ways you could mess things up by doing the wrong thing in window rules - if you don't get explicit intr. or want to fool around/test then I'd highly recommend creating a new user & doing so in there.

screen shows setting mahjong to open @ 700X600,  based on window name

---

### Post by scradock on 2011-10-23
> **mc4man said:**
> You can adjust mahjong' opening window siz in compiz > window rules

I'm not up on all the in's & outs of window rules, in this case it seems simple but you may want to hear from someone that spends some time in there.
There are likely several ways you could mess things up by doing the wrong thing in window rules - if you don't get explicit intr. or want to fool around/test then I'd highly recommend creating a new user & doing so in there.

screen shows setting mahjong to open @ 700X600,  based on window name

Thanks! That's where it's gone, is it?

But no luck so far - I enabled Windows Rules, and set as you showed, but no change - still opens far too small for me. I tried logging out and back in too...

Maybe I'll have to re-boot....No, that didn't do it, either.

Ah - but "compiz --replace" in a terminal did change the window size (mahjongg was open, small window - display has seizures, and mahjongg window is bigger).

---

### Post by mc4man on 2011-10-24
The window rules in ccsm are only for sessions using  compiz (unity 3d & gnome-fallback with  compiz enabled

---

### Post by scradock on 2011-10-24
> **mc4man said:**
> The window rules in ccsm are only for sessions using  compiz (unity 3d & gnome-fallback with  compiz enabled

Good point - so how would I set window size if I was using Unity-2d?

---

