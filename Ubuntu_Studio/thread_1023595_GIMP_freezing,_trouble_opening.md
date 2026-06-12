---
title: "GIMP freezing, trouble opening"
date: 2008-12-28
forum: Ubuntu Studio
---

### Post by niemaodpowiedzi on 2008-12-28
I've been having trouble running GIMP. I couldn't get it to open earlier (ETA: through Applications>Graphics>GIMP or by right-clicking on an image and instructing it to "Open With". When I went through Applications, it acted like it was starting by displaying "Starting GIMP" in the bottom panel, but never actually opened it), so searched the forums and came across [this thread]("http://http://ubuntuforums.org/showthread.php?t=1021934&highlight=GIMP+open") (ETA, part deux: didn't know how to follow the "revert to an  old kernel" or the "open GIMP via Terminal" suggestions in that thread). By Alt+F2, I opened GIMP and was on my merry photoediting way, and the program froze the computer. I tried to click to a different desk/workspace to no avail, and Ctrl+Alt+D didn't do anything either. I had to hold down the power button to shut down and restart my machine.

Any ideas what could be going wrong? I'm a n00b (installed Ubuntu less than a week ago), so you'll need to walk me through any instructions.

I'm running Ubuntu 8.10 on a Dell Inspiron e1505 laptop, and GIMP 2.6 with GIMPshop added. I'll install Photoshop Elements into Wine until I figure out what's going on, but I would prefer to use GIMP (for one thing, GIMP has better curve function!). 

Thanks!

---

### Post by paeltz on 2009-01-05
I'm having the same problem.  I've tried uninstalling then reinstalling but still doesn't work.  I am also running Ubuntu on a laptop.

---

### Post by paeltz on 2009-01-06
OK, It looks like I fixed my problem.  Try this and see if it works.

1. Applications -> Add/Remove
  a. search for gimp and remove it.
2. System -> Administration -> Synaptic Package Manager
  a. uninstall every package that has gimp in it. (don't uninstall every package that displays only the ones that it appears that Gimp uses. I uninstalled Gimpshop.)

3. open a terminal and type "sudo apt-get remove gimp"

4. restart

5. open terminal and type "sudo apt-get install gimp"  (this should install the latest version of gimp)

Hope this works, Let me know!

---

### Post by chili555 on 2009-01-06
To start GIMP in a terminal, open Applications -> Accessories -> Terminal. In the terminal, type gimp and press enter. It will probably spit out warnings and errors that you can use to debug, figure out what dependencies to install or post here for more help.

This technique is useful whenever any application won't start or run cleanly.

---

### Post by niemaodpowiedzi on 2009-01-14
It did, thanks!

---

