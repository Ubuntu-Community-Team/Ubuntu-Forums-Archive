---
title: "Photoshop in Wine Link Error"
date: 2011-02-28
forum: Wine
---

### Post by webler707 on 2011-02-28
After following the instructions found on this page:
[http://maketecheasier.com/install-photoshop-cs5-in-ubuntu-maverick/2010/11/02](http://maketecheasier.com/install-photoshop-cs5-in-ubuntu-maverick/2010/11/02)
To install Photoshop CS5 in Wine under 10.10 I have found that I cannot like to the .exe file to launch it. 
I want to put a shortcut into my Cairo Dock but when I try to make a link, holding shft+ctrl and dragging to the desktop I get this error "Photoshop.exe was not found in 
Z:\home\david\desktop\App\PhotoshopCS5"
Same when I right click and select "Make Link"
Getting it into Cairodock produces no errors, but nothing happens when I click it either. 

Also, the .exe is marked to "Allow executing file as a program"

As well as when I put a link into the shortcut bar at the top a problem seems to occur with the space in "Program Files" I've tried %20, \\, $, and % but none of these characters seem to be able to fix the path. 

As it turns, installing it into a non "Program Files" directory did the trick.

---

