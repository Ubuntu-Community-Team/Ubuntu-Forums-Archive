---
title: "Hookinh a Pangolin P7 with Ubuntu 11.10 to a TV"
date: 2012-02-06
forum: System76 Support
---

### Post by Bira on 2012-02-06
I tried looking on this forum for something similar, but I couldn't find it.

So, here's the deal: I have a Pangolin P7, which I originally bought with Ubuntu 10.04, but which has since been upgraded (in place) to 11.10. It has an ATI video card, and Catalyst drivers. When I tried to hook it up to a LCD TV (essentially an external monitor) to watch some movies, I noticed a problem that didn't happen back when I used 10.04

This TV supports a resolution of 1920x1080, which is larger than the 1600x900 that the laptop's own monitor supports. I could use this resolution just fine in 10.04, with the TV set as the only active monitor. Now, it seems to really want to stick to 1600x900! Setting the TV to the smaller resolution on the Catalyst Control Center works well, but if I try to set it to 1920x1080, it seems to enlarge my *desktop* to those dimensions, while keeping the screen itself at 1600x900. This results in the image being "cut off" or cropped, so that I lose a chunk of the left and bottom edges of the desktop.

Is this a known issue? Should I go for a clean re-install of 11.10?

---

### Post by isantop on 2012-02-06
Are you sure that it's staying at that resolution? There is a known issue with HDMI and many TVs in which the TV itself (independent of the computer) applies an effect called overscan which intentionally enlarges the image to be too big to fit on the screen. They do this because many sources expect this, and most of those that don't will show no negative consequences for doing so (games are an excellent example). 

However, a computer display will have critical portions going all the way to the edge of the screen. This usually isn't a problem because computer displays will simply not apply overscan. But when you connect a computer to a monitor, this will become apparent.

To rectify this, look for a setting on the TV to disable Overscan. This is the correct solution, and can often be done per-input (So you can leave overscan enabled on a traditional TV input).

If your TV doesn't have an overscan setting, then you can also tweak this in the Catalyst Control Center. On the Display Manager page, go to the adjustments tab, then select to use the graphics processor for scaling. Then, adjust the slider until everything lines up with the edges of the screen. This should match up pretty well and result in a clean, crisp picture.

---

