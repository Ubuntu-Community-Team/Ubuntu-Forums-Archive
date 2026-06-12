---
title: "Wine Starcraft II dual monitors"
date: 2011-02-08
forum: Wine
---

### Post by DanielJackins on 2011-02-08
Has anyone had any success running Starcraft 2 with dual monitors (twinview)? My mouse won't keep focus on the monitor it's running in, so the only way I can play is by disabling the other monitor at the moment.

Anyone know any fixes to this?

Thanks

---

### Post by slvr42 on 2011-04-05
Bump

Same Problem.  Confine Mouse Cursor not working in windowed or fullscreen mode.

---

### Post by Soulcage on 2011-04-05
Have you tryied "MouseWarpOverride"? [http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

---

### Post by slvr42 on 2011-04-05
My Registry doesn't look like that could it be because im running an older version of wine?

---

### Post by slvr42 on 2011-04-05
I added that key in to my registry and have tried all variations of it.  The mouse cursor still does not stay confined to the game when I am in it.

---

### Post by IMNOboist on 2011-05-07
Same issue, fresh copy and install of SC2. If I disable one monitor everything works fine but no beans if both monitors are on.

Maverick 64-bit with nVidia 9500GT driver version 270.41.06 and Wine 1.3.19

---

### Post by IMNOboist on 2011-05-07
I found a fix for this. Add a metamode in xorg.conf that matches the resolution you set for Starcraft. For me, I changed:
```
Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1440+0"
```
to this:
```
Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1440+0;DFP-0:1440x900,DFP-1:NULL"
```

This makes it so my other monitor automatically disables when Starcraft starts up. There is one issue, however. It stays disabled even after closing Starcraft... I'll see if I can fix that.

---

### Post by Tweak42 on 2011-05-08
I had the problem with the wayward mouse using twinview when I first installed SC2, as well as the video resolution was squished into the center of view 1.  It went away some where between reinstalling the game, patching and launching with only 1 monitor enabled and later re-enabling twinview after exiting the game.  I use windowed full screen mode, and a dedicated wineprefix for sc2.

Specs: Nvidia latest proprietary drivers on GTX460, wine 1.3.19

---

### Post by andymcca on 2011-06-09
If anyone is still having trouble with this, using "Windowed (Fullscreen)" mode will work. Not sure if it affects frame rates like running games in Windowed mode used to?

If you edit Variables.txt (it was in my "~/StarCraft II" directory, which was automatically generated when I ran the game):
displaymode=1

If you don't see displaymode, you can add a line with it. (My file did not contain displaymode, and the game must default to fullscreen)

Also, for those who care: Variables.txt appears to be similar to World of Warcraft's config.wtf. Oh, and WoW appears to have the same mouse-mapping bug when fullscreen.

---

