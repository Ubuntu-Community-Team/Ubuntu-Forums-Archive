---
title: "How can I start Hoary in text mode?"
date: 2005-03-22
forum: Server Platforms
---

### Post by gerrard on 2005-03-22
I want to config my Hoary server to start in text mode. How can I do that?

---

### Post by HungSquirrel on 2005-03-22
Most distros set the graphical runlevel to 5 and the text one to 3.  Ubuntu sets the graphical mode to 2.  I looked in /etc/rc2.d and /etc/rc3.d and the contents appear to be identical, so you can *probably* (I'm too lazy to test this) make seperate graphical and text modes by doing *sudo rm /etc/rc2.d/S13gdm* to tell GDM not to start in runlevel 2.  Then, if/when you want graphical mode temporarily, do *sudo init 3* to start GDM.  If you need to undo my instructions, do *sudo ln -s /etc/init.d/gdm /etc/rc2.d/S13gdm* .

Someone please do not hesitate to correct me if I'm wrong!

---

### Post by garyng on 2005-03-22
remove gdm under rc2.d would stop it. There are more than one way to do it though.

---

### Post by hernad on 2005-07-17
[QUOTE=HungSquirrel]Most distros set the graphical runlevel to 5 and the text one to 3.  Ubuntu sets the graphical mode to 2. ... 
[/QUOTE]

This info helped me to understand why Hoary is "ignoring" my runlevel kernel parameter on startup :).  Thank you.

What is the reason of this ubuntu's team decision (unusual runlevel for graphical mode) ?

---

