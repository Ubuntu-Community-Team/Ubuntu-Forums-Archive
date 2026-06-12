---
title: "warcraft and my toolbar"
date: 2009-03-05
forum: Wine
---

### Post by mongoose_za on 2009-03-05
Hi there,
I've just installed Warcraft The Frozen Throne 1.22.
I'm using Hardy Heron 8.04 
I'm using wine that I installed last night.
My toolbars are always visible in game which is kinda irritating. How can I fix this? I took a look at [http://ubuntuforums.org/showthread.php?t=1052109](http://ubuntuforums.org/showthread.php?t=1052109) but it didn't really help me. I am not or have never manually installed or heard of compiz.




Thanks,

---

### Post by cogadh on 2009-03-05
Technically, you have heard of Compiz, it just has a different name in current versions of Ubuntu: Desktop Effects. When you install the restricted drivers for your video card, I believe it automatically activates basic desktop effects, like drop shadows, menu fade, etc. (I am certain it does this with 8.10, not as sure on 8.04). Check under System > Preferences > Appearance > Visual Effects to confirm if any desktop effects are enabled.

If they aren't enabled, then fire up winecfg and uncheck the option to allow the window manager to control the windows, it should correct the panel problem.

---

### Post by mongoose_za on 2009-03-06
Hey there,
cogadh I also went to System > Preferences > Appearance > Visual Effects and turned the option to none, however the toolbar was still there. I sorted it out just by setting my toolbar to *autohide*:-P

---

