---
title: "How I got my Refresh Rate to stick after reboot"
date: 2010-05-13
forum: The Cafe
---

### Post by zim2dive on 2010-05-13
Since the dawn of time I was never able to get the refresh rate to stick between reboots. I would have to go into nvidia settings and change it by hand, after every reboot.  After reboot, the refresh rate would be set to "auto" which produced a fuzzy picture.  Once changed to 60Hz, all was crisp and in focus.

This persisted over 3 different video cards, several versions of Ubuntu and many versions of the nvidia drivers.

many people will suggest using nvidia-settings --load-settings-only, but as far as I can tell, that method does not allow setting the Refresh Rate.

So I did some minor surgery on my xorg.conf.  In a nutshell I decided to restrict its choices.  In particular, I think the magic was to remove the auto option from the metamodes line.  I also remove the 0 and 30 Hz options, leaving only 50 and 60.

Knock wood, but so far its working.

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Philips"
    HorizSync       31.0 - 80.0
[COLOR="Red"]    VertRefresh     60.0[/COLOR]
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
[COLOR="Red"]    Option         "metamodes" "1920x1080_60 +0+0; 1920x1080_50 +0+0"[/COLOR]
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Hope this can help someone else.

---

### Post by Shakz on 2010-05-13
Gonna take a look at this when I get home. Thanks so much for sharing!

---

