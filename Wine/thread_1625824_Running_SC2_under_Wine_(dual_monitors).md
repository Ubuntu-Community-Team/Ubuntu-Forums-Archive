---
title: "Running SC2 under Wine (dual monitors)"
date: 2010-11-19
forum: Wine
---

### Post by s195640 on 2010-11-19
I have successfully installed SC2 and it runs fine under Wine.  However the issue I'm having is the mouse does not say in the window.  I would like to have a script that disables one of the monitors.  I am currently running in separate X screen.

I tryed, the following but get no result.
[FONT=monospace]sudo xrandr --output default --off
xrandr: Failed to get size of gamma for output default[/FONT]

Additional info

[FONT=monospace]lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)

xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 1: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0*    51.0  
   1360x768       52.0     53.0  
   1152x864       54.0     55.0     56.0     57.0     58.0     59.0  
   1024x768       60.0     61.0     62.0     63.0     64.0     65.0  
   960x720        66.0  
   960x600        67.0  
   960x540        68.0  
   928x696        69.0  
   896x672        70.0     71.0  
   840x525        72.0     73.0     74.0     75.0     76.0  
   832x624        77.0  
   800x600        78.0     79.0     80.0     81.0     82.0     83.0     84.0     85.0     86.0     87.0  
   800x512        88.0  
   720x450        89.0  
   720x400        90.0  
   700x525        91.0     92.0     93.0     94.0  
   680x384        95.0     96.0  
   640x512        97.0     98.0     99.0  
   640x480       100.0    101.0    102.0    103.0    104.0    105.0    106.0    107.0  
   640x400       108.0  
   640x350       109.0  
   576x432       110.0    111.0    112.0    113.0    114.0    115.0    116.0  
   512x384       117.0    118.0    119.0    120.0    121.0  
   416x312       122.0  
   400x300       123.0    124.0    125.0    126.0    127.0  
   360x200       128.0  
   320x240       129.0    130.0    131.0    132.0  
   320x200       133.0  
   320x175       134.0  


[/FONT][FONT=monospace]

[/FONT]

---

