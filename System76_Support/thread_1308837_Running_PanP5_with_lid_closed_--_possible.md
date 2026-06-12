---
title: "Running PanP5 with lid closed -- possible?"
date: 2009-10-31
forum: System76 Support
---

### Post by samalex on 2009-10-31
Hi,

I thought I posted this already, but I don't see it.  I wanted to see if it's possible to boot-up a PanP5, connect an external monitor or HDMI device, then close the lid where the laptop keeps running. Is this possible?

Thanks ..

Sam

---

### Post by HotShotDJ on 2009-11-01
> **samalex said:**
> Hi,

I thought I posted this already, but I don't see it.  I wanted to see if it's possible to boot-up a PanP5, connect an external monitor or HDMI device, then close the lid where the laptop keeps running. Is this possible?

Thanks ..

Sam
I run my PanP5 dual-headed when I'm home, but I figured I'd test this out for you.

Yep! I'm now running on my external monitor with the laptop lid closed.  (Ok, I just switched it back... I like my dual-head setup ... all without even a log-in/log-out)

[LIST=1]
[*]Open a terminal.  Run gconf-editor as a regular user (not sudo, in other words)
[*]Go to apps -> gnome-power-manager -> buttons
[*]Change "lid_ac" to "nothing" (without the quotes) -- you used to be able to set this via the Power Manager applet, but the "do nothing" option is gone.  EDIT: After I made the change in gconf-editor, the "do nothing" option returned to Power Management applet... spooky!
[*]Close the Configuration Editor.
[*]Go to System -> Administration -> NVIDIA X Server Settings
[*]Click on X Server Display Configuration
[*]Set it the way you like it (I'm assuming you know how to do what you want here)
[*]Click Apply when you're done.
[*]Close your laptop lid.
[/LIST]

EDIT2: You might need to use the Fn + F7 combination a couple times to get both displays turned on before configuring NVIDIA X Server Settings.

---

### Post by samalex on 2009-11-01
Nice... thanks for testing this out.  Are there any heat issues though with doing it this way?  I know that some laptops actually use the keyboard as part of the ventilation, so with the lid closed and the laptop running will it stay cool enough?

Thanks again for the reply.

Sam

---

### Post by flukeairwalker on 2009-11-01
My Panp4 ran hot enough to cause the screen to lock up when I did this (75C). I now keep a piece of hard foam between the keyboard and screen when I close the lid to make sure it stays open. So I wouldn't recommend it from my personal experience. Also, getting one of those cooling racks doesn't seem to do much since there's only one vent at the bottom. Your mileage may vary.

---

### Post by HotShotDJ on 2009-11-01
> **samalex said:**
> Nice... thanks for testing this out.  Are there any heat issues though with doing it this way? I honestly didn't run it long enough with the lid closed to be able to answer this.

---

