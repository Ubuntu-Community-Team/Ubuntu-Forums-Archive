---
title: "Changing ubuntu server screen resolution?"
date: 2009-06-05
forum: Server Platforms
---

### Post by Vunutus on 2009-06-05
I'm running Ubuntu server in VirtualBox to set up my database test server. The only problem is, it defaults to some very small resolution. Normally this isn't an issue since it's all command line, but every time I run a mysql query from the command line, it tries to output a table and it gets all scrunched up and unreadable.

How can I change this?

EDIT: I forgot to mention that I found [this]("http://ubuntuforums.org/showthread.php?t=215566") thread. I followed it's instructions but nothing seems to have changed. Could this be because I'm using VirtualBox?

---

### Post by Kareeser on 2009-06-05
No, running it in a VM shouldn't change things. Are you sure you added the option correctly in menu.lst? I've never had to add "defoptions" to the line... just a simple "vga=773" did it.

In the meantime, you can pipe the output of the mysql command to a file, or to the command "less". That will render the output in a nice window (yes, in the command line) that is scrollable.

---

