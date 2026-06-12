---
title: "Installed GUI now it always boots GUI"
date: 2008-10-23
forum: Server Platforms
---

### Post by amup on 2008-10-23
Hello, I installed the GUI on to the server to play with.  I was not expecting to always have to boot to the GUI.  Is there anyway to boot to just the command line or do I now have to load the GUI all the time?

---

### Post by ilrudie on 2008-10-23
change /etc/rc2.d/S30gdm to /etc/rc2.d/s30gdm (change the s to lower case)
this should prevent the gnome display manager from starting at boot.

edit:  I assumed you installed gnome but if not let us know what you installed and we can show you how to stop it from loading at boot.

---

### Post by amup on 2008-10-23
Thanks so much!

---

### Post by lykwydchykyn on 2008-10-23
It would be better to change it to K30gdm, that way the init manager knows it should be killed when entering that runlevel.

Not that it really matters.

---

