---
title: "Constant ticking noise from analog speakers"
date: 2019-02-28
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2019-02-28
Afer upgrading to Dingo a constant ticking noise is heard from my analog speakers at regular <1sec intervals.
Changing the volume makes the ticking go away for three seconds, and then is starts again. The volume itself does not affect te ticking - this happens even when the volume is set to mute. The only way to stop it is to unplug the speakers or turn them off.
This does not happen with my USB headphones.
What should I check? Any idea how to resolve this?

---

### Post by zika on 2019-03-01
> **Wise Ferret said:**
> Afer upgrading to Dingo a constant ticking noise is heard from my analog speakers at regular <1sec intervals.
Changing the volume makes the ticking go away for three seconds, and then is starts again. The volume itself does not affect te ticking - this happens even when the volume is set to mute. The only way to stop it is to unplug the speakers or turn them off.
This does not happen with my USB headphones.
What should I check? Any idea how to resolve this?Try „old school“
File: [COLOR=#242729][FONT=Consolas]/etc/pulse/default.pa
[/FONT][/COLOR]Line: [COLOR=#242729][FONT=Consolas]load-module module-udev-detect
[/FONT][/COLOR]change to: [COLOR=#242729][FONT=Consolas]load-module module-udev-detect tsched=0[/FONT][/COLOR]
;)

---

### Post by Smask on 2019-03-01
I were  about to start a new thread about popping sound on my machine. It's a default motherboard one connected to analog speakers and it mutes when I log in. Unmuted it pops every time I play some  some sort of sound. Playing something, then pause it, and then resume it seconds later -- POP. It only happens when I start playing something.

---

### Post by dino99 on 2019-03-01
Also check the hdd smart control (hddtemp) : if enabled it can produce such noisy disturbance via the speakers

---

