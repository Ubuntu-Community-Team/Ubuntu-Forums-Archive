---
title: "Macbook Air Trackpad"
date: 2012-01-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nightfrost on 2012-01-21
It seems the macbook air runs nicely and smoothly with precise installed, without additional tweaks and post configs. One thing makes it unusable though, for me at least, and that's the lack of support for the trackpad. If anyone has working configuration, please share. Otherwise, I'm hoping someone can post here if a solution comes along, and I'll update this post for easy finds.

These are the various tools available, as far as I understand.

- xserver-xorg-input-mtrack
- xserver-xorg-input-multitouch
- xserver-xorg-input-synaptics
- touchegg

Of these, I haven't tried multitouch, and I have no clue what touchegg really is (I start it but notice nothing). mtrack is the only one that works alright, but not good enough. synaptics acts really weird. In fact, it's the same weirdness synaptics offers, that bugs me with mtrack, although mtrack is "less" weird.

Now, it's hard to explain exactly what's wrong with mtrack. But compared to OS X it just doesn't seem to understand what my fingers are doing. A couple of examples:

- Using my index finger to move the cursor, I'd like to rest my thumb on the trackpad (after all, there's nowhere else to rest the thumb). synaptics just doesn't handle it. mtrack handles it, but sometimes it doesn't. Furthermore, sometimes a tap with the index finger, supposed to act as a left click, turns into a right click. I presume the driver suddenly detects the thumb as one finger, making it a two finger tap.

- Resting the thumb on the trackpad, and then wanting to highlight something by clicking with the same finger and dragging with the index finger can end up in anything.

- First starting off by moving the cursor around, and then resting the thumb on the pad, causes the cursor to stop. I need to lift the index finger and then put it back on again for the cursor to move.

- When starting a two finger scroll, it take a moment before the scrollnig actually occurs.

The above issues and others continually get in the way of my work flow, leaving me to use os x when I find myself without an external mouse. 

I've tried many different xorg.conf edits but I get the feeling the problem is really with the driver, not my configs.

Finally, if anyone has any ideas, or if anyone knows any development going on anywhere (mtrack hasn't been updated for some time, it seems), I'd love to know. If anyone can shed some light on which of the drivers above one should stick for future updates, do tell. With the trackpad working, I would finally stop spending time in that other OS!

Thanks in advance!

---

### Post by kaldor on 2012-01-21
If I am not mistaken, this is one of the improvements coming in xorg 1.12. Ubuntu will use 1.11 but get multitouch backported. Unsure about how well it will work on a MacBook, though.

Maybe try the PPA [here](" http://ubuntuforums.org/showthread.php?t=1912462 ")?

---

### Post by nightfrost on 2012-01-22
> **kaldor said:**
> If I am not mistaken, this is one of the improvements coming in xorg 1.12. Ubuntu will use 1.11 but get multitouch backported. Unsure about how well it will work on a MacBook, though.

Maybe try the PPA [here](" http://ubuntuforums.org/showthread.php?t=1912462 ")?

That would be excellent! I'll try the xorg-edgers. But will multitouch be supported by the synaptics driver? Or should I be looking for something else?

---

### Post by nightfrost on 2012-01-29
Hm... it's still not good enough. The synaptics driver doesn't let me rest my thumb on the unibody trackpad while performing actions with the other fingers.

Does anyone know if the xorg multitouch driver is being developed?

---

