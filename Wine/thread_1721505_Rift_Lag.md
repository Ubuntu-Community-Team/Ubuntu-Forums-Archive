---
title: "Rift Lag"
date: 2011-04-04
forum: Wine
---

### Post by Dragonorb13 on 2011-04-04
OK, I have the game Rift installed on my Ubuntu 10.10 partition. I've even gotten it to the point where I can log into world, using the newest version of Wine (the beta, not the stable). The problem I'm having is that the system seems to keep trying to buffer over and over again. It will play for about a second, then lag for about a second, lather rinse repeat until I scream and ALT-F4. I even left it run for almost 20 minutes, just to see if it needed to buffer. I really would like this running in Linux, because I hate windows.
System specs:
  AMD Athlon II X2 3.1 gHz
  4g DDR3 ram   
  NVIDIA GeForce 6150 SE (yes, on board. I'm planning to upgrade later, but if this is the issue i have a slightly better unit i can use)
  Ubuntu 10.10 x64 (if this might be the problem, I can try either an older/newer version or the x86 arch)
  Wine 1.3.17 /winetricks (all of the specs are default, though a few registry mods have been made to accommodate the game)

Any help that can be offered will be greatly appreciated. I'm not a complete newbie at Linux, but I'm also not an expert, so if I need Terminal commands, just put them in and I can CnP them, or mod any info I need to for my settings.

Thanks!

---

### Post by Kenjitamura on 2011-04-04
Wow 6150SE, I didn't even know they still used that.  I have an AM2 motherboard from like 2006 with that chipset, for future reference nvidia chipsets don't work well for amd processors and tend to run hot.  Anyway, this game doesn't support OpenGL so there is a pretty big performance hit, not sure you'll be able to run it as that video card is almost the bare minimum in spec for the game.

Anyway in the wine registry you can try a performance tweak, in HKEY_CURRENT_USER\Software\Wine create a new key and call it Direct3D.

In the new directory add the following string values with the following values: String Value/value

> 
DirectDrawRenderer/opengl
Multisampling/disabled
OffScreenRenderingMode/pbuffer
UseGLSL/disabled
VertexShaderMode/hardware

I use a radeon 4650 which even though that's a very low end card it is still way ahead in performance than your current video output and I only barely get it to run without stuttering with all settings on lowest.  The best sub $100 video card you could get that'd run this game without a hitch would probably be the radeon 5670; with that you'd be able to run it seemlessly on medium settings is my guess.  It's $75 and the sapphire model has a $10 mail in rebate (yep I'm considering getting it).

---

### Post by Dragonorb13 on 2011-04-07
Frankly, seamless run on absolute tanked settings would be acceptable to  me. Tanked settings in Ubuntu on any game seem to be better than  mid-level settings on winblows.Unfortunately, despite having applied your mods to the Wine reg, I still basically the same stutter. With in the next week, I SHOULD be getting a better vid card, so hopefully the installation of that will do. Yeah, I realize it's an old, craptastic chip set, but it was, above all else, cheap. That's was important to me, since I was trying to outfit two people for under 800.

---

### Post by Dlambert on 2011-04-08
Use nvidia for linux gaming

---

### Post by KEE on 2011-05-10
wheres the wine registry ????

---

### Post by tonyis3l33t on 2011-12-02
type at the terminal
```
wine regedit
```

---

