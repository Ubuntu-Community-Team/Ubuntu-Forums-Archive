---
title: "How do I remove the 6600/tcp connection ability from XWindow?"
date: 2011-04-15
forum: Security
---

### Post by espressobeanie on 2011-04-15
I've been reading a lot of articles on Xorg XWindow System having the ability to allow 6600/tcp for remote screen connections and I've been trying to find a way to remove the functionality without having to just dump XWindow and settle for CLI on my server. I heard it was disabled by default, but I just want to get rid of that ability completely by cutting it out of it's code and yes, I'm feeling very, very paranoid. :)

---

### Post by bodhi.zazen on 2011-04-15
I would not run X on my server, there is no need and it introduces both overhead and security risks.

If you need a graphical interface, use any of the numerous web interfaces (webmin) or better if you paranoid, ssh + keys.

---

### Post by The Cog on 2011-04-15
I don't think Ubuntu listens for X connections in a default install. Using the command ```
netstat -lntu
``` shows that port 6600 is not listening.

That said, I don't normally leave X running on my servers. I install GUI applications (or even the gnome desktop) but disable the GDM service so that X doesn't start. Then if I really want a GUI program, I can use startx locally on the server or more likely, use **ssh -X** to connect remotely and tunnel X back to my desktop. Then start the required GUI app from my desktop command line and its window appears on my desktop, not the server's (probably non-existent) screen.

---

