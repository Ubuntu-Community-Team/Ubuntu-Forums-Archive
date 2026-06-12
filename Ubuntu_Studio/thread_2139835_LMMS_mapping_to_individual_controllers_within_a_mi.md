---
title: "LMMS: mapping to individual controllers within a midi channel"
date: 2013-04-28
forum: Ubuntu Studio
---

### Post by morphemes on 2013-04-28
if I had a midi controller with knobs pads & keys & I figured out how to map the knobs but I wanted an A sharp to be a high hat & the next B to be a kick...  If I wanted a vocal sample mapped to a D & some other pattern mapped to a G...  if I wanted the pads to play traditional African percussion... all at the same time...  Where on earth could I find info on how to do all that in LMMS?  
I've been looking for *months.*
**it's driving me crazy!**

---

### Post by zequence on 2013-04-29
qmidiroute will allow you to remap notes, controllers, pitchbend and program changes, from one channel to another. You can also remap one type to a completely different type, like a note to a controller.
If you use multiple midi controllers, you need to set them to different channels, and qmidiroute will let you reroute the controls to anything you want.

qmidiroute is installed by default on Ubuntu Studio (at least since 12.10).

---

