---
title: "Ubuntu 10.10 + Fujitsu Lifebook TH700"
date: 2011-02-14
forum: Tutorials
---

### Post by potatohead00 on 2011-02-14
I finally got the touchscreen AND stylus working on my nice new lifebook. It seems to be a bit of a kluge, but it works!
(as of 14 feb 2011)
1. Install the package xserver-xorg-input-wacom driver
2. Follow directions on this page: [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom) to get latest driver and install that as well


I'm not sure why this works, I'm just happy to get the touchscreen working :)

You may also need to have do some 'setserial' stuff, not sure how dependant everything is on that though.

---

### Post by potatohead00 on 2012-09-30
figured out screen rotation issue / touch screen cursor not being in the right place for the 3rd time or so - figured I better write it down for myself and anyone else trying to figure it out. 

This is to get the buttons to work on TH700 under Linux (i'm currently running xubuntu 12.04)

Download fjbtndrv -  [http://sourceforge.net/projects/fjbtndrv/](http://sourceforge.net/projects/fjbtndrv/)

configure/make/make install

then copy the following script into /usr/local/lib/fjbtndrv. I called it 'rotate.sh'


```

#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input tools.

case "$rotation" in
    left)
    # rotate to the left
    xrandr -o left
    xsetwacom set "Serial Wacom Tablet stylus" rotate ccw
    xsetwacom set "Serial Wacom Tablet touch" rotate ccw
    xsetwacom set "Serial Wacom Tablet eraser" rotate ccw
    ;;
    inverted)
    # rotate to inverted
    xrandr -o inverted
    xsetwacom set "Serial Wacom Tablet stylus" rotate half
    xsetwacom set "Serial Wacom Tablet touch" rotate half
    xsetwacom set "Serial Wacom Tablet eraser" rotate half
    ;;
    right)
    # rotate to the right
    xrandr -o right
    xsetwacom set "Serial Wacom Tablet stylus" rotate cw
    xsetwacom set "Serial Wacom Tablet touch" rotate cw
    xsetwacom set "Serial Wacom Tablet eraser" rotate cw
    ;;
    normal)
    # rotate to normal
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet stylus" rotate none
    xsetwacom set "Serial Wacom Tablet touch" rotate none
    xsetwacom set "Serial Wacom Tablet eraser" rotate none
    ;; 
esac


```

---

