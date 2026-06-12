---
title: "Cannot Move panels in Ubuntu 13.10 Fallback &quot;Flashback&quot; Desktop Environment"
date: 2013-10-07
forum: Ubuntu Development Version
---

### Post by linuxguru43 on 2013-10-07
Hello there. I have a quick question. I have just installed Ubuntu 13.10 and I then installed gnome-fallback desktop environment. I cannot move the top panel to the bottom of the screen. It is stuck... Usually, what I would do to move a panel in Ubuntu classic fallback "flashback" desktop environment in Ubuntu 13.04 is, I would simply hold down the ALT key and then click with my mouse and hold to move the panel and put it where I want it (either top of the screen or the bottom of the screen) ... Does anyone here know what I am describing in 13.04? Well, for whatever strange reason when I try this Ubuntu 13.10 the panels are fixed to the screen and will not move. Nothing happens when I hold down the ALT key and try to click to move the panels from top to bottom, and bottom to top. It is like I can't change the position of the top and bottom panels in gnome "flashback" classic desktop environment in 13.10, but it works totally fine in Ubuntu 13.04.. Is there is setting somewhere in 13.10 that will allow me to position the panels in classic fallback flashback desktop environment in Ubuntu 13.10 anymore?

Thanks for your help with this 

:guitar:

---

### Post by muktupavels on 2013-10-08
1) Win+Alt and than move panel.
2) Win+Alt+Right click, click on Properties and change Orientation from Top to Bottom

This is what works for me. I am using flashback session with compiz.

---

### Post by Doug S on 2013-10-08
Here are my the login options and the results of trying the OP method on each:

GNOME                                - OP method does not work
GNOME Classic                      - OP method does not work
GNOME Flashback                  - OP method works fine
GNOME Flashback (No effects) - OP method works fine
Ubuntu (default)                    - NA (and doesn't work)

---

### Post by linuxguru43 on 2013-10-09
Okay, I figured it out. I'm running Ubuntu 13.10 in Virtualbox and it won't emulate the keyboard and the mouse action simultaneously through my KVS switch. Thanks for your help. Closing thread.

---

### Post by Doug S on 2013-10-09
For what it's worth...

My 13.10 Desktop is also a virtual machine, running on an Ubuntu 12.04 server, and I am connected to the DeskTop via VNC (tight VNC Viewer) from a Microsoft Windows computer.

---

