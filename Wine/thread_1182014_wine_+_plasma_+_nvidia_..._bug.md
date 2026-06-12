---
title: "wine + plasma + nvidia ... bug?"
date: 2009-06-08
forum: Wine
---

### Post by zapporius on 2009-06-08
Right, I'm running 64-bit kubuntu 9.04. I installed nvidia's drivers for my 9600GT.
Installed Wine, and Starcraft, set it up so that Starcraft takes whole screen (because the windowed mode is too small, you can't scale up resolution in starcraft). 

While I'm playing, its all fine, however, as soon as I exit the game one of the two things happen:

a) (rare) I'm stuck in starcrafts resolution, which is I dunno, 640x480, or maybe 800x600. That doesn't look too good on my 21" set up for 1600x1200.

b) (all the time when not the above) I'm back to 1600x1200 but Plasma has died, so I have to start it manually from the terminal.

It's no biggie technically, because I figured it out that its Plasma that dies, but I guess someone who just migrated from Windows with less linux background would be lost.

 
Anyone know a workaround for this?

---

### Post by asdfoo on 2009-06-09
a workaround for your plasma dying?

---

### Post by NightMKoder on 2009-06-09
Plasma is not known to be too happy about resolution changes at times. Make sure you disable compositing before you start (shift+alt+F12), and pray.

On the other hand, karmic has a rather stable plasma and a rather unstable ark. :D

---

