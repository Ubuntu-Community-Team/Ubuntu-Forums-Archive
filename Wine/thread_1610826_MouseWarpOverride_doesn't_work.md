---
title: "MouseWarpOverride doesn't work"
date: 2010-11-01
forum: Wine
---

### Post by FelixII on 2010-11-01
Hi,

I'm experiencing the mouse warp bug in first-person games like Crysis and Mirror's Edge. I tried the "MouseWarpOverride=force" registry entry as suggested on winehq.org but it doesn't have any effect. My mouse cursor is still working in the menus (I think it shouldn't) but i can't turn 360° in the game itself.

I tried to set the entry manually and with winetricks, none of them had any effect. I also tried to set it specifically for the application without success.

I'm running Wine 1.3.5 on Ubuntu 10.10 32-bit. Is there anything else I could try?

Thanks in advance!

Felix

---

### Post by mbradlcu on 2011-01-11
what's working for me was to install the distro version 'wine1.3' then download the source, modify dinput.dll.so, and build. The reason I used the distro version and not the source build was there was no alsa support.. I'm guessing I could have figured the config switches but it was quicker to just replace /usr/lib32/wine/dinput.dll.so ... I put it up on my server if you'd like to give it a try:
[http://qndfix.com/~daturan/dinput.dll.so](http://qndfix.com/~daturan/dinput.dll.so)

---

