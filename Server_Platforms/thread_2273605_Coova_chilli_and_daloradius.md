---
title: "Coova chilli and daloradius"
date: 2015-04-14
forum: Server Platforms
---

### Post by j3r3my2 on 2015-04-14
Hi,
I installed on my ubuntu server coova chilli and daloradius. I can access at the web interface of daloradius, but if I launch chilli, i can't anymore. But I am able to use the captive portal and the database from the freeradius, but to use my captive portal i have to launch chilli .
Someone have any clue(s), why I can't use daloradius interface when chilli is started ?

---

### Post by j3r3my2 on 2015-04-15
I finally find my mistake, if you dont uncomment into the coova configuration file the line HS_TCP_PORTS="80 443 1812 1813 22", once chilli is up, the server doesn't listen other ports

---

