---
title: "Radeon driver: Shell broken"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kaldor on 2012-03-24
Gave the daily build a go on a live USB. GNOME Shell is entirely unusable and corrupted, with major glitches and flickering. I'm using the open source Radeon driver on a 6450.

It was working the last time I tried it about a month ago. Anyone else having this problem?

---

### Post by Harry33 on 2012-03-25
> **kaldor said:**
> Gave the daily build a go on a live USB. GNOME Shell is entirely unusable and corrupted, with major glitches and flickering. I'm using the open source Radeon driver on a 6450.

It was working the last time I tried it about a month ago. Anyone else having this problem?

Nope, no problems with ATI open source drivers.
Gnome-shell works fine too.

---

### Post by tista on 2012-03-25
@kaldor,
@Harry33

No, I haven't any problems on my Thinkpad X121e (AMD Fusion E350)... Gallium 0.4 on AMD PALM works pretty well...

Then any warnings had been remained in /var/log/Xorg.0.log as graphic drivers problems causing DRI or so? Or gnome-shell might have some lack of dependencies with other libraries...;)

Regards,
Tista.

---

### Post by Mathor on 2012-03-25
Which version of gnome-shell?

---

### Post by kaldor on 2012-03-28
Sorry for the delay in replying.

The good news is that GNOME 3.4 is working fine- my corruption issue is entirely gone. 

However, the performance is really slow. Everything feels a bit jittery and like it needs to "catch up" with my mouse. Scrolling and window dragging is a good example for this- if I move a window, I can see the window chasing after the cursor, etc. Flash playback on YouTube is poorer than expected.

This is a little bit of a shame, considering Shell is my DE of choice and it's the only one that manages to not work that well :)

Edit: Just gave GIMP a try. It's *very* obvious in this. Dragging the painbrush across the canvas is extremely slow, the whole black line flashes as it's being painted, and it's just really buggy-looking in general. Maybe there's a screen redraw/refresh issue with Shell + my driver?

---

### Post by the ruler on 2012-03-29
> **kaldor said:**
> Sorry for the delay in replying.

The good news is that GNOME 3.4 is working fine- my corruption issue is entirely gone. 

However, the performance is really slow. Everything feels a bit jittery and like it needs to "catch up" with my mouse. Scrolling and window dragging is a good example for this- if I move a window, I can see the window chasing after the cursor, etc. Flash playback on YouTube is poorer than expected.

This is a little bit of a shame, considering Shell is my DE of choice and it's the only one that manages to not work that well :)

Edit: Just gave GIMP a try. It's *very* obvious in this. Dragging the painbrush across the canvas is extremely slow, the whole black line flashes as it's being painted, and it's just really buggy-looking in general. Maybe there's a screen redraw/refresh issue with Shell + my driver?

The open source driver is slower than the proprietary driver, can you install the proprietary driver?

---

