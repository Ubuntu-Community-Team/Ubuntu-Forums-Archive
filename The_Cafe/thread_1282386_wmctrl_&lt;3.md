---
title: "wmctrl &lt;3"
date: 2009-10-04
forum: The Cafe
---

### Post by etnlIcarus on 2009-10-04
I'd post this in tutorials & tips, except I really don't feel like making sure this is completely foolproof - especially since this will probably only appeal to a select few users.


*ahem*
For those of you, like myself, who are reluctant to go the full-tilt of a tiling window manager, there's a little trick to make stacking window managers a little less cumbersome.

[http://tripie.sweb.cz/utils/wmctrl/](http://tripie.sweb.cz/utils/wmctrl/)

wmctrl is probably in your distro's repos (it's in Ubuntu's). Just install it and create a shell script with the following:

```
wmctrl -r :ACTIVE: -e 0,xposition,yposition,width,height
```

Replace xposition/width/etc with numerical values. -1 will leave the property as is, so if you just want to change the position of the active window, without affecting it's size, you'll want to do something like this:

```
-e 0,40,55,-1,-1
```

Once you save your scripts, you can then either bind keyboard shortcuts to the scripts, or create panel launchers for them.

Note: at least with compiz + emerald, the window decorations aren't counted. The same may be true of other window managers, so if you're positioning a window at the top of the screen, you're going to want to allow a buffer of 20 or so pixels, to prevent the window title from being lost off the top of the screen. 40+ pixels, if you've also got a panel at the top of the screen.

I've been having a lot of fun with this little application. Manual window resizing is a clumsy affair. I've now got 9 scripts, bound to shortcuts Alt+1, through to Alt+9, with generic window sizes, that makes slotting multiple windows besides one another, an absolute breeze.

---

### Post by pt123 on 2009-10-06
I use wmctrl to slide to workspaces with script files. So I will focus the screen to a designated workspace then open a VNC connection to another computer. 

The cool part is that you run the script from Gnome-Dos Docky.

```

#!/bin/bash

wmctrl -o 0,1050  #switch to Bottom Left Viewport
xvncviewer 192.168.0.3::15600:1 -passwd ~/.vnc/passwd -ZlibLevel 6

```

---

