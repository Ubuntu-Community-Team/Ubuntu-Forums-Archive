---
title: "64-bit with nvidia doesn't do splash properly"
date: 2013-03-24
forum: Ubuntu Development Version
---

### Post by The Cog on 2013-03-24
Not complaining, just an observation in case the right people are reading:
It seems that Xubuntu 64bit with nvidia  GTS 250 doesn't paint the splash screen before presenting the login dialog.
Attached are 2 screenshots - from power on and after a reboot. Not a problem, just a trifle disconcerting.

---

### Post by dino99 on 2013-03-24
are you using the nvidia-313-updates package ? (which you might)

---

### Post by The Cog on 2013-03-24
> **dino99 said:**
> are you using the nvidia-313-updates package ? (which you might)

That's very odd. It turns out I was using nouveau. Odd because I saw the installer download nvidia310 (I saw wget nvidia310 in the installer process list. 
I'll install nvidia313 now.

---

