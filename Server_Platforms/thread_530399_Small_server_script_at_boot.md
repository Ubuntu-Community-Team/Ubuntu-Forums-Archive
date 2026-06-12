---
title: "Small server script at boot"
date: 2007-08-20
forum: Server Platforms
---

### Post by koma77 on 2007-08-20
I would like to start a WebShell server when I boot my computer.

The WebShell server is a python script that listens for https connections.

Which is the best way to make it start when I boot my computer without even having to log in?

---

### Post by jakev383 on 2007-08-20
I use Redhat for my servers, and to do something like this I would put the command(s) in my /etc/rc.d/rc.local file (the path will be /etc/init.d/rc.local for Ubuntu).

---

