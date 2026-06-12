---
title: "Edgy server, /var/run/*/*.pid"
date: 2006-11-08
forum: Server Platforms
---

### Post by corvy on 2006-11-08
Hello, I have an edgy server running a few transports for a jabber server. Since I run many of these off svns and such I have installed them manually and also crafted some simple runscripts for init.d.

All works fine until I reboot, because I saved the pid files in /var/run/jabber/* and at every reboot the jabber dir gets deleted :confused:. Why is this? I haven't seend this behaviour on any other of my linux servers (none ubuntu flavor). 

I know I can put them directly in /var/run, but I like my jabber dir and I started to wonder about this.

---

### Post by corvy on 2006-11-20
*bump*

No-one knows why this dir gets deleted?

---

