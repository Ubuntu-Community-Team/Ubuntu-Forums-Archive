---
title: "XMir and custom refresh rates."
date: 2013-09-19
forum: Ubuntu Development Version
---

### Post by yaji on 2013-09-19
I have problem with setting custom refreshrate while using XMir. I'm doing it just like before XMir:

```
xrandr --newmode "1680x1050_75" 149.24 1680 1728 1760 1840 1050 1053 1059 1080
xrandr --addmode XMIR-2 1680x1050_75
xrandr --output XMIR-2 --mode 1680x1050_75
```

And the resoult is:

```
xrandr
Screen 0: minimum 320 x 320, current 1680 x 1050, maximum 32767 x 32767
XMIR-0 disconnected (normal left inverted right x axis y axis)
XMIR-1 disconnected (normal left inverted right x axis y axis)
XMIR-2 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 490mm x 320mm
   1680x1050      60.0 +
   1280x1024      59.9  
   1440x900       59.9  
   1280x960       59.9  
   1152x864       60.0  
   1024x768       59.9  
   832x624        59.8  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   1680x1050_75   75.1* 
```

It looks like it worked, but all I got is short screen flash, and the refreshrate is stuck at 60hz. Is there any way to fix this?

---

