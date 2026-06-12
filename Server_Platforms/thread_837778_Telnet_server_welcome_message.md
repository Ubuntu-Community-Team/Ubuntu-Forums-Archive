---
title: "Telnet server welcome message?"
date: 2008-06-22
forum: Server Platforms
---

### Post by TCLP-Daniel on 2008-06-22
Okay, so here's the deal. I installed telnetd, and I would like to know how to change the welcome screen. like this:

[img]http://img145.imageshack.us/img145/3356/tempub3.jpg[/img]

any way to change this?

---

### Post by TCLP-Daniel on 2008-06-22
oop, I found it. never mind guys

---

### Post by gtdaqua on 2008-06-23
Answer:

Edit the "/etc/motd" file:

```

sudo nano /etc/motd

```

The contents inside the file is the banner.

---

