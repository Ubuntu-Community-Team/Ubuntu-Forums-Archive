---
title: "[SOLVED] Installing cups server on 8.04"
date: 2008-05-28
forum: Server Platforms
---

### Post by Jordanwb on 2008-05-28
I got a very good Laser printer from one of my teachers. I want to hook it up to my mini-server. I got as far as 

sudo apt-get install cupsys cupsys-client

I go to 192.168.1.2:631 to get to the Web based admin but I get the HTTP 403 error.

[Edit] I guess the cups config would be useful. I'll get that in a second.

---

### Post by Jordanwb on 2008-05-28
Okay I fixed the access.

I put after Listen localhost:631:

Listen 192.168.1.2:631

And in <Location />
Allow From All

And in <Localtion /admin>
Allow From All

---

