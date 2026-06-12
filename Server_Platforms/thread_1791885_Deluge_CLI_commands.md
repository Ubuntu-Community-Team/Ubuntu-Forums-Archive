---
title: "Deluge CLI commands"
date: 2011-06-27
forum: Server Platforms
---

### Post by Cyked on 2011-06-27
I for the life of me can not find the list of CLI/console commands for Deluge.  My googlefu is weak today. I'm trying to at least find the command to change global download speed.

Thanks in advance to anyone who can help.

---

### Post by dFlyer on 2011-06-27
Have you tried:

man deluge

---

### Post by Cyked on 2011-06-27
Yes.  There isn't much in it.  No options list.

---

### Post by Cyked on 2011-06-27
NM, just figured it out.  I need more coffee!

config --set [option] value
example - config --set max_connections_global 100 

config will give you a list of all current settings (which inherently gives you all the --set options).

---

