---
title: "Server to GUI (on demand)"
date: 2012-03-13
forum: Server Platforms
---

### Post by djleven on 2012-03-13
Hi everyone,

I wish to have my machine work primarily as a server but with the added ability to "launch" a user friendly GUI on demand (from the terminal). In other words, I do not want to have the GUI on all the time (from boot) but only when somebody wishes to use the box as a "regular" pc. I assume this will be a more efficient set up for a box which will serve as a web and terminal server (LTSP) most of the time, and only occasionally as a "pc". 

So i would:

1-) Install Ubuntu Server (10.04)

2-) Add GUI 

3-) Then what??!

So in other words, the question may be how to boot the machine (server) without the GUI after having installed the latter.

Is there a fundamental flaw in my reasoning or is this possible? If so, can anybody point me to any ideas/links to be able to do this?

Alternatively, maybe it is possible (and preferable) to launch a virtual machine as an LTSP client from the server command line.. I am probably getting out of my depth here but what the hey, life is for learning (Ubuntu!)

Thank you all for your time, 

Kostas

---

### Post by ajgreeny on 2012-03-13
If you simply add a gui such as gnome, lxde, xfce4, openbox or similar, and do not include a display manager (eg gdm, lightdm, xdm, etc etc) you can then probably start the gui with command ```
startx
```Simple as that!

With no display manager you will not automatically boot into a gui.

---

### Post by djleven on 2012-03-13
Thank you ajgreeny, sounds like music to my ears! :D

---

