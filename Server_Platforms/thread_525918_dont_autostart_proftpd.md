---
title: "dont autostart proftpd"
date: 2007-08-14
forum: Server Platforms
---

### Post by ayu on 2007-08-14
Hello,
I've just installed gproftpd, and noticed that the ftp server is starting every time I boot the computer.  Is there a way to make it so it will only start when I explicitly start it (hopefully using the gui)?  I've noticed the conf says 'ServerType standalone' (although I'm sure I selected inetd during installation) if that is relevant at all.
Thanks!

---

### Post by netlogic on 2007-08-14
I don't use a graphical interface on the server, but there is a tool to manage all your service startup using "service settings manager."

system --> administration --> service settings.

---

### Post by ayu on 2007-08-14
Ah, there it is! Thank you so much.

---

