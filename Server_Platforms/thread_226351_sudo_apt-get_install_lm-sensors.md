---
title: "sudo apt-get install lm-sensors"
date: 2006-07-31
forum: Server Platforms
---

### Post by Gris on 2006-07-31
Hi everyone

When I run:

sudo apt-get install lm-sensors

on my Ubuntu server 6.06 installation, Ubuntu asks me to insert the cd-rom - only problem is that the server is in a server room a long way away!

Is there a way to force apt-get to use the internet repositories to grab this package?

Cheers

Gris

---

### Post by Titus A Duxass on 2006-07-31
Edit your sources.list and hash (#) out the line for the CD.

---

### Post by Gris on 2006-07-31
Thanks, worked great!

---

