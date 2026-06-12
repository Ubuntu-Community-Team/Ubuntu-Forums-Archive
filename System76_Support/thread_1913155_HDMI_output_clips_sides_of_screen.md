---
title: "HDMI output clips sides of screen"
date: 2012-01-22
forum: System76 Support
---

### Post by mgolden on 2012-01-22
I have a Gazelle Pro with the Nvidia GeForce GTX 560M Graphics card.  The DVI output works fine, but when I use the HDMI output, the edges of the screen are clipped.  A few pixels on all 4 sides are missing from the external monitor.

I used the NVidia X Server settings manager, set it to TwinView, and set the extermal monitor to be a clone of the LCD.

Is anyone else experiencing this?  Is there some setting I am missing?

---

### Post by jschall1 on 2012-01-22
> **mgolden said:**
> I have a Gazelle Pro with the Nvidia GeForce GTX 560M Graphics card.  The DVI output works fine, but when I use the HDMI output, the edges of the screen are clipped.  A few pixels on all 4 sides are missing from the external monitor.

I used the NVidia X Server settings manager, set it to TwinView, and set the extermal monitor to be a clone of the LCD.

Is anyone else experiencing this?  Is there some setting I am missing?

If the monitor you're using is a TV, this is called "overscan" and I'm not certain there's anything you can do about it, other than be happy that it's only "a few pixels" and not "a few hundred pixels." My TV falls in the realm of "a few hundred pixels."

I can't imagine the actual HDMI output would clip, since it's essentially the same as DVI. You can even get a simple adapter from HDMI to DVI.

---

### Post by jschall1 on 2012-01-22
nvidia-settings
On the left, underneath GPU0, click the name of the screen with the overscan.
At the bottom, overscan compensation.

---

### Post by mgolden on 2012-01-23
It is a TV and I am sure you are right.  Thanks for pointing this out.

---

