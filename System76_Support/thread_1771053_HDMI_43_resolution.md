---
title: "HDMI 4:3 resolution"
date: 2011-05-30
forum: System76 Support
---

### Post by Shazzner on 2011-05-30
I'm using a Lemur Ultrathin and yesterday I tried to connect it to my hdtv via hdmi.

I go to Monitor and it shows it listed, however if I clone the screen my only available resolutions are 4:3 with the max being 1024x768. The result is it changes's my laptops resolution to something small and the hdtv's image is stretched and horrible.

Any ideas on this?

Edit: looks like this has more info on it:
[https://wiki.ubuntu.com/X/Config/HDMI](https://wiki.ubuntu.com/X/Config/HDMI)

But it doesn't list any steps. I believe the text on the page is an xorg config script, but I have no idea on how to add/generate it. :(

Edit2: also I get sound just fine

Edit3: Tried a bunch of mode settings, nothing could get it to work. If I tried anything higher than 4:3 the screen would just blank.

---

### Post by isantop on 2011-06-01
I got your email today. We can continue there or here, whichever you prefer.

It looks like the monitor isn't listing 1366x768 as a supported resolution, so it has to fall back to the resolutions that both monitors support. Can you set a better resolution if you turn off the laptop monitor and use only the TV?

---

### Post by Shazzner on 2011-06-01
I'll try that today and let you know, thanks for responding.

---

### Post by Shazzner on 2011-06-01
> **isantop said:**
> It looks like the monitor isn't listing 1366x768 as a supported resolution, so it has to fall back to the resolutions that both monitors support. Can you set a better resolution if you turn off the laptop monitor and use only the TV?

Just tried it now. It wouldn't let me choose a higher resolution after turning off my laptop monitor.

Also I noticed it lists the name of the monitor as 'Phillips Consumer Electronics 29"', with the tv being 42".

---

### Post by isantop on 2011-06-03
What is the output of running the xrandr command, and what is the resolution you're trying to set.

---

