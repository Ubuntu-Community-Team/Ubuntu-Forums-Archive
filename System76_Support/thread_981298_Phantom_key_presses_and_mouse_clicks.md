---
title: "Phantom key presses and mouse clicks"
date: 2008-11-13
forum: System76 Support
---

### Post by Dave_Wesnoth on 2008-11-13
I recently bought a System76 Pangolin. It mostly works well, except on occasion there seem to be "phantom" mouse clicks and key presses -- i.e. sometimes the computer acts like I pressed a key or clicked the mouse, even when I didn't. Sometimes windows will get selected, or a bunch of characters inserted (always one or more of the same character) or (worst of all!) text I had selected gets pasted into a window (presumably because of a middle-click event, even though there is no middle mouse button, so it'd have to be the lmb and rmb at the same time, which I definitely didn't press).

Anyone else have these problems? Anyone know the cause? I assume it's some kind of hardware problem, but don't really know.

Any help appreciated.

-David.

---

### Post by thomasaaron on 2008-11-13
You know, no matter how long I do this job, it stays fun! :lolflag:

> text I had selected gets pasted into a window (presumably because of a middle-click event, even though there is no middle mouse button

Yes there is... sort of. If you tap the mousepad with two fingers at the same time, it emulates a middle-mouse button.

I'm betting most (if not all) of these symptoms is being caused by brushing against your touchpad.

---

### Post by Dave_Wesnoth on 2008-11-13
> **thomasaaron said:**
> 
I'm betting most (if not all) of these symptoms is being caused by brushing against your touchpad.

I don't think this is the cause. It happens even if I'm not touching my touchpad, and as I said, it sometimes happens with keypresses. For instance, sometimes I'll have a terminal window open, and suddenly a string like "BBBBBBBBB" will be inserted.

-David.

---

### Post by thomasaaron on 2008-11-14
I'm not sure.

If it is truly a hardware problem, it'll be the first one that I've seen quite like it.

I'd try to monitor where your hands are when it happens. Or see if you are holding keys down too long (causing them to repeat), etc...

We had one customer who's touchpad would act up whenever the palms of his hands got close to it. If memory serves, this guy couldn't wear a digital watch either.

Try this:
Connect a USB mouse to your computer for a while and use that. Turn off your touchpad by going to a terminal and entering this command:

```
sudo modprobe -r psmouse
```

Does the problem still occur?

BTW: You can re-enable your touchpad by running:

```
sudo modprobe psmouse
```

---

### Post by ScottyP on 2008-12-20
Dave. You're not alone. I'm having this problem on my desktop (no touchpad to brush). I'm searching for an answer now.

Update: Found my problem. it was mixing a USB keyboard with a 4 year old daughter. Doh!

---

