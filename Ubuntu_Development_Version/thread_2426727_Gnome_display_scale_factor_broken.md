---
title: "Gnome display scale factor broken"
date: 2019-09-12
forum: Ubuntu Development Version
---

### Post by Cheltspy on 2019-09-12
In the last week the scale factor is broken for most apps on Gnome, Firefox, VLC, Chrome.

All the built-in functions in Gnome are fine.

Very difficult to read on menus on 4K screen with 100%

---

### Post by #&amp;thj^% on 2019-09-12
Try  this **if your on "xorg' or X11 only.**

    You can achieve any non-integer scale factor by using a combination of GNOME's scaling-factor and xrandr. This combination keeps the TTF fonts properly scaled so that they do not become blurry if using xrandr alone. You specify zoom-in factor with gsettings and zoom-out factor with xrandr.

    First scale GNOME up to the minimum size which is too big. Usually "2" is already too big, otherwise try "3" etc. Then start scaling down by setting zoom-out factor with xrandr. First get the relevant output name, the examples below use eDP1. Start e.g. with zoom-out 1.25 times. If the UI is still too big, increase the scale factor; if it's too small decrease the scale factor.
```

    xrandr --output eDP1 --scale 1.25x1.25
```

**Wayland solution:**

Since Ubuntu 18.04, Wayland is the default display protocol.
To enable scaling:[list]

    [*]Enable fractional Scaling experimental-feature:
```

    gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
```

    [*]Restart the computer.
    [*]Open Settings -> Devices -> Displays[/list]
    Now you should see a 25 % step scales, like 125 %, 150 %, 175 %. Click on one of them and see if it works.
You can find relevant output from "xrandr -q".
Example for mine:
```
xrandr -q
Screen 0: minimum 8 x 8, current 3520 x 1080, maximum 32767 x 32767
LVDS1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 340mm x 190mm
   1600x900      60.00*+  59.95    59.82  
   1400x900      59.96    59.88  
   1368x768      60.00    59.88    59.85  
   1280x800      59.81    59.91  
   1280x720      59.86    60.00    59.74  
   1024x768      60.00  
   1024x576      60.00    59.90    59.82  
   960x540       60.00    59.63    59.82  
   800x600       60.32    56.25  
   864x486       60.00    59.92    59.57  
   800x450       60.00  
   640x480       59.94  
   720x405       59.51    60.00    58.99  
   640x360       59.84    59.32    60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
VGA1 connected 1920x1080+1600+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.95  
   1280x800      74.93    59.81  
   1152x864      75.00    59.97  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by Cheltspy on 2019-09-13
I was already using scale-monitor-framebuffer thanks anyway.

It appears that my intel bios firmware needed an update and this has resolved the issue.

---

### Post by #&amp;thj^% on 2019-09-13
> **Cheltspy said:**
> I was already using scale-monitor-framebuffer thanks anyway.



Should I have known this?
> **Cheltspy said:**
> 
It appears that my intel bios firmware needed an update and this has resolved the issue.
Glad to hear it is sorted now. ;)

---

