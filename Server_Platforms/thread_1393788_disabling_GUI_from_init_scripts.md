---
title: "disabling GUI from init scripts"
date: 2010-01-29
forum: Server Platforms
---

### Post by natbob1 on 2010-01-29
I have a headless Ubuntu computer which is primarily use as a server but which has Ubuntu desktop edition installed.  I use X forwarding through SSH occasionally to use GUI programs so I am not looking to remove them.  However, I would like to disable any GUI elements that would be started automatically when the computer is booted. Is the graphical login screen the only thing that would be run? or is nautilus, gnome-session etc. started as well? How would I go about removing the necessary entries from the init scripts?

---

### Post by Vegan on 2010-01-29
You can ignore the desktop, it will simply not be used when beheaded. If you have several user accounts, it will simply list a bunch in a menu.

---

### Post by sisco311 on 2010-01-29
add *text* to the kernel parameters.

---

