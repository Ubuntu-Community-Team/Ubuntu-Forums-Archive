---
title: "Swap Fn and Ctrl keys on Starling?"
date: 2010-02-22
forum: System76 Support
---

### Post by Schrollini on 2010-02-22
I have a star1 Starling.  I've mostly gotten used to the slightly smaller keyboard, except that my left pinkie continues to insist that the key in the bottom left should be Ctrl, not Fn.  Is there anyway to swap those two keys?  I fear that this may be a BIOS setting, as pressing the Fn key doesn't seem to produce any keypress events. A little snooping around in BIOS didn't reveal any obvious things to change.

Thanks.

---

### Post by jdb on 2010-02-22
> **Schrollini said:**
> I have a star1 Starling.  I've mostly gotten used to the slightly smaller keyboard, except that my left pinkie continues to insist that the key in the bottom left should be Ctrl, not Fn.  Is there anyway to swap those two keys?  I fear that this may be a BIOS setting, as pressing the Fn key doesn't seem to produce any keypress events. A little snooping around in BIOS didn't reveal any obvious things to change.

Thanks.

I have a Daru2 with that key layout.
After a few years I still have the problem.
I think the little finger just heads for that corner key :lolflag:

jdb

---

### Post by thomasaaron on 2010-02-22
You might play around with xkeycaps.

```
sudo apt-get install xkeycaps
xkeycaps
```

---

### Post by Schrollini on 2010-02-23
> **thomasaaron said:**
> You might play around with xkeycaps.


I gave it a brief try, but didn't notice anything lighting up when I pressed the Fn key.  I'm not that hopeful, as [FONT="Courier New"]xev[/FONT] doesn't report anything when I press or release Fn.  (All of the other modifiers do get reported.)  This doesn't particularly surprise me, as I would expect the Fn key to be handled very close to the hardware.  This is why I was wondering if there was a BIOS setting to tweak.

Thanks anyway.

---

