---
title: "TV-Out and Bluetooth on PanV3?"
date: 2008-01-12
forum: System76 Support
---

### Post by EmptyCinema on 2008-01-12
I'm probably becoming all too frequent of a poster of questions in here -- normally I'm able to solve my own problems, but this one has me stumped (and the other is just hardware).

How can I enable the tv-out (S-Video) on the PanV3?  I've tried xrandr but can only get a completely green screen.  I've done video out with nvidia and ati before, but never intel (and the intel documentation seems to indicate the following should work):
```

xrandr --display TV --mode 800x600
xrandr --display TV --left-of LVDS
```

Second question:  I'm curious if it's possible to add bluetooth to a PanV3 after the fact.  I didn't order it with bluetooth, but am about to get a new cellphone with BT and would like to be able to sync.  I know I can get a USB dongle, but internal is so much cleaner.

Also, as an aside, do you all know about what battery life I could get if I bought a 9-cell for the PanV3?

Sorry for the flood of questions, though you all have great support and I really do appreciate it!

---

### Post by thomasaaron on 2008-01-14
The S-Video is unsupported. It may be possible to get it working, but we've not figured it out yet.

As for the bluetooth, you can just buy and install the module yourself. Send me an email (support<at>system76<dot>com) and I'll give you the specifics of the card we use.

Battery life should be between 4.5 and 5hrs, depending on usage.

---

### Post by Zxaos on 2008-01-15
I'd say thomas is being politely pessimistic with the battery life - I have a 9-cell on my panv3 and  it gives me about 5.5 hours with the screen all the way up - and I'm running compiz too. The battery life is really quite impressive.

You should be aware that the 9-cell does stick out of the back of the machine a bit though - but I haven't had any problems getting it to fit in a standard 15 inch laptop bag even with the battery sticking out.

---

### Post by EmptyCinema on 2008-01-15
I really am quite tempted to get a 9 cell for it, when I get some money.  :)  Batteries are so quite expensive, especially for a college student.  :)

---

### Post by thomasaaron on 2008-01-15
Zxaos, 

:lolflag::lolflag::lolflag::lolflag::lolflag:
Under-promise, Over-deliver!!

Best,
Tom

---

### Post by Zxaos on 2008-01-15
What can I say? I was really impressed and happy when I saw how long the battery was lasting.

---

### Post by rumblered on 2008-01-16
> **EmptyCinema said:**
> 
```

xrandr --display TV --mode 800x600
xrandr --display TV --left-of LVDS
```

(I think you meant --output, not --display)

I don't think setting the mode on an output actually enables it (though documentation somewhere might say it does). I always enable multi-output with the following:
```
xrandr --auto
```

That detects and enables all connected devices. Then if you don't want clone mode, give the command to position the displays.

---

### Post by EmptyCinema on 2008-01-16
I did mean output, sorry.  I was typing off the top of my head.

I have tried --auto as well.  I used to use the first two lines on an old ATI Radeon 7500-based notebook and it worked fine (yeah, ATI working fine, I was shocked).

I would've though intel hardware would do better.  I've filed a bug hoping for a future improvement.

---

