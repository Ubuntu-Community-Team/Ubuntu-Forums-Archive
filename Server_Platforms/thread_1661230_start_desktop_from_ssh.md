---
title: "start desktop from ssh"
date: 2011-01-06
forum: Server Platforms
---

### Post by kfleten on 2011-01-06
Hi 
I have a thin client environment where the thin clients (HP t5325) is capable of Citrix, RDP and ssh. No PXE. I want to connect to a running Ubuntu 10.04 server. I have managed to do so by using ssh and writing "gnome-session" in the "run command" option of the thin client.

Unfortunately, this gnome desktop is quite bare compared to the ubuntu desktop I get when I log in from gdm or from a LTSP session. Also, there is no graphical login, so the gnome session is esthablished after a dull login prompt. Is there a way of invoking gdm from ssh ? Or even better: Is there a way to invoke the same graphical login I have on my LTSP clients from ssh ?

---

