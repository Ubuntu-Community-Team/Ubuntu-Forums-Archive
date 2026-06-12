---
title: "TV widescreen"
date: 2012-06-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-06-22
Quantal running O.K. on netbook, but 1024x600 is a squint so I hooked up a widescreen TV.  

Oof. Systems Settings Displays said unknown display, max 1024x768.

Found this site:
[http://askubuntu.com/questions/63863/unknown-monitor-intel-driver-want-to-set-vga-resolution-to-widescreen-tv/154818#154818](http://askubuntu.com/questions/63863/unknown-monitor-intel-driver-want-to-set-vga-resolution-to-widescreen-tv/154818#154818)

with magic incantations:```

#!/bin/bash
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1366x768_60.00
xrandr --output VGA1 --mode 1366x768_60.00
```Now all those funny numbers came out of a cvt command (sort of) so look at the site if you're interested.

The Coby TV is a lot sharper than I would have expected, pixel pitch .252 and 6-bit color.

Having fun, 

Jerry

---

### Post by videonaut on 2012-10-08
Worked a treat for me - thanks Jerry. I have yet to try a reboot to see if settings stick, but if they don't, instructions for getting them to stick are in the linked post.

Update: Settings did not stick consistently.

I created an .xprofile in my home directory with the settings. 

Then, I did chmod +x .xprofile. If you don't do this, .xprofile won't be run at login, and you won't be able to do it manually from the terminal either.

---

