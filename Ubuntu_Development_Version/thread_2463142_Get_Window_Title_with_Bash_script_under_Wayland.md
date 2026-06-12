---
title: "Get Window Title with Bash script under Wayland"
date: 2021-06-04
forum: Ubuntu Development Version
---

### Post by crcarson on 2021-06-04
Have a bash script that gets the window title under X11 but now that Ubuntu is running Wayland this doesn't work.  Any hints in getting a window title from Wayland with bash?

---

### Post by TheFu on 2021-06-04
What tool does the bash script use so we don't waste our time trying to test?

---

### Post by crcarson on 2021-06-05
Prior to 21.04 Ubuntu used X11 to manage desktop and I used an bash script using xprop to gather the information I wanted (in this case the window title).  With Wayland trying to find a similar tool to xprop to get the title.  You can get it with Looking Glass but that is not a command line tool.

---

### Post by TheFu on 2021-06-05
Wayland is supposed to be a simpler and more secure windowing environment.  Many of the capabilities we use/abuse with X tools worked by using some of the non-secure "features" of X11.

I was going to suggest xdotool but it doesn't work with Wayland.  There is ydotool, but it doesn't have the same capabilities and needs to run as root to steal access to input devices. [https://github.com/ReimuNotMoe/ydotool](https://github.com/ReimuNotMoe/ydotool)  May have enough to accomplish what you need, but probably can't get the window title. ;(

---

### Post by crcarson on 2021-06-18
Something change in my 21.10 system.  The script using xprop is again returning the window title under Wayland.

---

### Post by TheFu on 2021-06-18
21.10 isn't released - not until late October. Post about it all belong in the "Ubuntu Development Release" sub-forum.

Support for 20.10 will end in a few weeks, so moving to 21.04 is mandatory at this point.

Call me confused.

---

### Post by ajgreeny on 2021-06-18
*Thread moved to **Ubuntu Development Version**.* which is more appropriate and a better fit for this thread about 21.10.

---

