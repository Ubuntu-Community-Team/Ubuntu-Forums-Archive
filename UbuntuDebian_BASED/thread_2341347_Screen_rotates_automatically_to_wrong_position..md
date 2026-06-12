---
title: "Screen rotates automatically to wrong position."
date: 2016-10-27
forum: Ubuntu/Debian BASED
---

### Post by kiina on 2016-10-27
Tested with Ubuntu 16.04 & 16.10. Now I have Elementary OS installed. Bottom of screen turns always to left side. How to fix to correct screen position or disable automatic rotation?

---

### Post by howefield on 2016-10-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by kiina on 2016-10-27
```

$ sudo xrandr
Screen 0: minimum 8 x 8, current 1536 x 2048, maximum 32767 x 32767
eDP1 connected primary 1536x2048+0+0 (normal left inverted right x axis y axis) 160mm x 120mm
   1536x2048     60.60*+
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   768x1024      61.00  
   1024x768      60.00  
   800x600       60.32    56.25  
   640x480       59.94  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

```
sudo xrandr --output eDP1 --rotate normal
``` fixes screen orientation, but everytime I turn screen problem comes back. :(

What does Ubuntu use for autorotation? Is it magick rotation?

---

