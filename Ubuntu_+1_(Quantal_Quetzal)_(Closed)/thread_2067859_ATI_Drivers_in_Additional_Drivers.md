---
title: "ATI Drivers in Additional Drivers"
date: 2012-10-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cromat on 2012-10-07
Hey I tried an upgrade and it seems there isn't any more additional drivers module? I am unable to install ATI graphics card, does anyone know when this will be added back in or will the new drivers be available elsewhere?

---

### Post by jfernyhough on 2012-10-07
If you have an HD5000 or after, you can:

$ sudo apt-get install fglrx
$ sudo aticonfig --initial

If you have an earlier card the drivers may work, but may not; YMMV as HD2000-4000 are not officially supported by the Catalyst 12.9 drivers on which our fglrx 9.00 are based. Reports on Launchpad and elsewhere suggest they will not; at least one person has posted in the fglrx thread to say they do (or seem to).

---

### Post by lincoln32 on 2012-10-07
if you upgraded to ubuntu 12.10 they moved it to software sources and added a new tab

open software center ---top left edit---- software sources-- right tab is addl drivers

---

### Post by cromat on 2012-10-07
Thanks all, I see it now.

---

