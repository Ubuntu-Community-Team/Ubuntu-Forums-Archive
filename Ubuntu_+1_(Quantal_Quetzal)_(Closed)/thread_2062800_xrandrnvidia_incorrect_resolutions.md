---
title: "xrandr/nvidia incorrect resolutions"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by eyecreate on 2012-09-25
xrandr or nvidia driver seems to be report the wrong display resolutions. Even though on boot my screens are at native resolution, all programs the query for available resolutions will only find up to 1024x768. What do you think is causing this?

Below is xrandr output:

```
Screen 0: minimum 8 x 8, current 3600 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1024x768       75.0 +   70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
   640x400        70.1  
HDMI-0 connected 1920x1080+1680+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1024x768       75.0 +   70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        75.0     72.8     59.9  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
  1680x1050 (0x27e)  146.2MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1920x1080 (0x292)  148.5MHz
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz

```

EDIT:A workaround for now is adding nomodeset on kernel boot.

---

