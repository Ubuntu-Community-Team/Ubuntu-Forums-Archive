---
title: "How to check webcam?"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Double.J on 2012-01-16
Hi all after testing for a couple of hours, I have only minor bugs thus far - software centre crashes when I close it, bluetooth isn't detected, little things.

However, I don't know how to test the camera - it's listed under lsusb, and has worked out of the box since karmic on ubuntu, no problems, I noticed it wasn't working during install, and cheese freezes when it opens - I also ran "system testing" on it and found that it wasn't recording. However, none of these things have told me anything along the lines of it's not installed, or not compatible or what not, so I'm not sure if it's a driver bug, or system one?

Thanks :)

---

### Post by Derek Karpinski on 2012-01-16
Cheese is broken for me too. It's not your webcam.
 
Try installing ffmpeg, and creating an avi with it:
 
```
ffmpeg -f video4linux2 -s vga -i /dev/video0 ~/Desktop/test.avi
```
 
Change video0 to where your webcam is mounted.....most likely 0.

---

