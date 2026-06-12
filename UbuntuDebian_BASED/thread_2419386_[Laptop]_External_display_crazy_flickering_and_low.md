---
title: "[Laptop] External display crazy flickering and low resolution"
date: 2019-05-21
forum: Ubuntu/Debian BASED
---

### Post by totallynotfritz on 2019-05-21
Hi, I recently installed pop os. Not getting help in the Pop forums so I thought I would ask here since it sounds like an ubuntu issue :)
 
It's been a great experience so far,  everything works smoothly and out of the box EXCEPT: my 1440p external  monitor over hdmi. I have pop on my razer blade stealth, so an i7 and  i915 gpu. 

Setting the external monitor to everything below 1920x1080i  works, but 1080i and 1440 does not work, the monitor just goes black,  then shows "no signal found" and flickers repeating "no signal found".

**VIDEO: [https://youtu.be/2HaUMSDT5uM](https://youtu.be/2HaUMSDT5uM)**

What I tried: HiDPI Daemon on/off, different cables, different resolution, lots of googling :(


If that was confusing, here are some pictures:

External Monitor works on low res:
[https://imgur.com/2M7qURj](https://imgur.com/2M7qURj)


External monitor flickers, no input (can't actually see right picture since display doesn't recognize input)
[https://imgur.com/AhJ22AI](https://imgur.com/AhJ22AI)


Internal monitor in reduced resolution so scaling works
[URL="https://imgur.com/G1w2bHw"]https://imgur.com/G1w2bHw

[/URL]```
xrandr
Screen 0: minimum 320 x 200, current 5760 x 1440, maximum 8192 x 8192
eDP-1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
   3200x1800     59.98 +  59.96    59.94 
   2880x1620     59.96    59.97 
   2560x1600     59.99    59.97 
   2560x1440     59.99    59.99    59.96    59.95 
   2048x1536     60.00 
   1920x1440     60.00 
   1856x1392     60.01 
   1792x1344     60.01 
   2048x1152     59.99    59.98    59.90    59.91 
   1920x1200     59.88    59.95 
   1920x1080     60.01    59.97    59.96    59.93 
   1600x1200     60.00 
   1680x1050     59.95    59.88 
   1600x1024     60.17 
   1400x1050     59.98 
   1600x900      59.99*   59.94    59.95    59.82 
   1280x1024     60.02 
   1440x900      59.89 
   1400x900      59.96    59.88 
   1280x960      60.00 
   1440x810      60.00    59.97 
   1368x768      59.88    59.85 
   1360x768      59.80    59.96 
   1280x800      59.99    59.97    59.81    59.91 
   1152x864      60.00 
   1280x720      60.00    59.99    59.86    59.74 
   1024x768      60.04    60.00 
   960x720       60.00 
   928x696       60.05 
   896x672       60.01 
   1024x576      59.95    59.96    59.90    59.82 
   960x600       59.93    60.00 
   960x540       59.96    59.99    59.63    59.82 
   800x600       60.00    60.32    56.25 
   840x525       60.01    59.88 
   864x486       59.92    59.57 
   800x512       60.17 
   700x525       59.98 
   800x450       59.95    59.82 
   640x512       60.02 
   720x450       59.89 
   700x450       59.96    59.88 
   640x480       60.00    59.94 
   720x405       59.51    58.99 
   684x384       59.88    59.85 
   680x384       59.80    59.96 
   640x400       59.88    59.98 
   576x432       60.06 
   640x360       59.86    59.83    59.84    59.32 
   512x384       60.00 
   512x288       60.00    59.92 
   480x270       59.63    59.82 
   400x300       60.32    56.34 
   432x243       59.92    59.57 
   320x240       60.05 
   360x202       59.51    59.13 
   320x180       59.84    59.32 
DP-1 connected 2560x1440+3200+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     59.95*+
   1920x1080     60.00    60.00    50.00    59.94 
   1920x1080i    60.00    60.00    50.00    59.94 
   1680x1050     59.88 
   1600x900      60.00 
   1280x1024     75.02    60.02 
   1280x800      59.91 
   1152x864      75.00 
   1280x720      60.00    60.00    50.00    59.94 
   1024x768      75.03    60.00 
   832x624       74.55 
   800x600       75.00    60.32 
   720x576       50.00    50.00 
   720x480       60.00    60.00    59.94    59.94    59.94 
   640x480       75.00    60.00    59.94    59.94 
   720x400       70.08 
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
```[URL="https://imgur.com/G1w2bHw"]
[/URL]

---

### Post by jeremy31 on 2019-05-21
Moved to Ubuntu/Debian based

---

