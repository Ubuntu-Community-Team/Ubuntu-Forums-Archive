---
title: "VMWare 1600x900 resolution on Ubuntu 12.04"
date: 2013-04-23
forum: Virtualisation
---

### Post by hippiechic on 2013-04-23
I have loaded Ubuntu 12.04 onto a system in VMWare 7. The default resolution listing does not include an option for 1600x900.

If using *gtf* or *cvt*, then I get the output as follows:
```

$ gtf 1600 900 60
# 1600x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 119.00 MHz
Modeline "1600x900_60.00"  119.00  1600 1696 1864 2128  900 901 904 932  -HSync +Vsync

$ gtf 1600 900 75
# 1600x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 152.28 MHz
Modeline "1600x900_75.00"  152.28  1600 1704 1880 2160  900 901 904 940  -HSync +Vsync

$ cvt 1600 900 60
# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

$ cvt 1600 900 80
# 1600x900 79.85 Hz (CVT) hsync: 75.46 kHz; pclk: 163.00 MHz
Modeline "1600x900_80.00"  163.00  1600 1712 1880 2160  900 903 908 945 -hsync +vsync

```

I then tried each modeline, one at a time, to try and get the 1600x900 resolution working.
They all have identical results:
```

$ xrandr --newmode "1600x900_60.00" 118.25 1600 1696 1856 2112 900 903 908 934 -hsync +vsync
xrandr: Failed to get size of gamma for output default

$ xrandr --addmode default 1600x900_60.00
xrandr: Failed to get size of gamma for output default

$ xrandr --output default --mode 1600x900_60.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```

Here is the before and after of my *xrandr* output:

_before:_
```

$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 3200 x 1600
default connected 1440x900+0+0 0mm x 0mm
   800x600        60.0     85.0     75.0     72.0     56.0      0.0  
   2048x1536      85.0     75.0     60.0      0.0  
   1920x1440      85.0     75.0     60.0      0.0  
   1856x1392      75.0     60.0  
   1792x1344      75.0     60.0  
   1600x1200      85.0     75.0     70.0     65.0     60.0      0.0  
   1680x1050      85.0     75.0     70.0     60.0      0.0  
   1400x1050      85.0     75.0     70.0     60.0      0.0  
   1280x1024      85.0     75.0     60.0      0.0  
   1440x900       60.0*     0.0  
   1280x960       85.0     60.0      0.0  
   1360x768       60.0  
   1152x864      100.0     85.0     75.0     70.0     60.0      0.0  
   1024x768       85.0     75.0     70.0     60.0      0.0  
   832x624        75.0  
   640x480        85.0     75.0     73.0     60.0      0.0  
   720x400        85.0  
   640x400        85.0      0.0  
   640x350        85.0  
   320x240         0.0  
   400x300         0.0  
   512x384         0.0  
   854x480         0.0  
   1280x720        0.0  
   1366x768        0.0  
   1920x1080       0.0  
   1280x800        0.0  
   1920x1200       0.0  
   2560x1600       0.0  
   720x480         0.0  
   720x576         0.0  
   320x200         0.0  
   800x480         0.0  
   1280x768        0.0  
   3200x1600       0.0  

```

_after:_
```

$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 3200 x 1600
default connected 1440x900+0+0 0mm x 0mm
   800x600        60.0     85.0     75.0     72.0     56.0      0.0  
   2048x1536      85.0     75.0     60.0      0.0  
   1920x1440      85.0     75.0     60.0      0.0  
   1856x1392      75.0     60.0  
   1792x1344      75.0     60.0  
   1600x1200      85.0     75.0     70.0     65.0     60.0      0.0  
   1680x1050      85.0     75.0     70.0     60.0      0.0  
   1400x1050      85.0     75.0     70.0     60.0      0.0  
   1280x1024      85.0     75.0     60.0      0.0  
   1440x900       60.0*     0.0  
   1280x960       85.0     60.0      0.0  
   1360x768       60.0  
   1152x864      100.0     85.0     75.0     70.0     60.0      0.0  
   1024x768       85.0     75.0     70.0     60.0      0.0  
   832x624        75.0  
   640x480        85.0     75.0     73.0     60.0      0.0  
   720x400        85.0  
   640x400        85.0      0.0  
   640x350        85.0  
   320x240         0.0  
   400x300         0.0  
   512x384         0.0  
   854x480         0.0  
   1280x720        0.0  
   1366x768        0.0  
   1920x1080       0.0  
   1280x800        0.0  
   1920x1200       0.0  
   2560x1600       0.0  
   720x480         0.0  
   720x576         0.0  
   320x200         0.0  
   800x480         0.0  
   1280x768        0.0  
   3200x1600       0.0  
   1600x900_60.00   59.9  

```

When I try loading the mode with *xrandr* and then using the display utility, I get a CTRC 311 error, then another message showing a module name.

---

### Post by hippiechic on 2013-04-24
This issue has been resolved. It seems as though I had not installed the open-vm-tools package and upon doing so I was able to force the resolution I desired with Autofit Guest. Here is what I followed to install the open-vm-tools package: [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

