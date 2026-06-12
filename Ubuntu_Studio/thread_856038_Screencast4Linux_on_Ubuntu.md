---
title: "Screencast4Linux on Ubuntu?"
date: 2008-07-11
forum: Ubuntu Studio
---

### Post by Shaythong on 2008-07-11
I downloaded "screencast4linux-0.2" and in the terminal I typed "make" and "make install", then I ran "sudo ./screencast".

For some reason I got a segmentation fault error. I need this application for uStream.
```
Registering driver.
Starting screencast.
Using device: /dev/video1
Video resolution: 320x240
Frame rate: 10
Select source with mouse:
  Left Click: Window (supports resizing)
  Left Drag: Rectangle area (free size, does not support resizing)
  Right Click: Rectangle area (fit size to video resolution, does not support resizing)
target: Point(216, 519)
size: 549x145
CTRL-C to exit
Segmentation fault
Unregistering driver.

```

Is there a way to get this program to work?

Edit: I got it to work, but it only works if you select a small area, not a big area. Plus it won't show up in Ustream.tv's broadcaster interface.

---

### Post by heathenx on 2008-07-12
I take you didn't favor screencast apps like recordmydesktop or xvidcap?

---

### Post by Shaythong on 2008-07-12
Those applications don't work for Ustream.tv or any flash program.

---

