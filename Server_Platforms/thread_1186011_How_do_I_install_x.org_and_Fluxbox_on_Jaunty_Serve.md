---
title: "How do I install x.org and Fluxbox on Jaunty Server?"
date: 2009-06-12
forum: Server Platforms
---

### Post by ninja_numbnuts on 2009-06-12
I can't get Arch Linux too work. This would be the next best thing!

Thanks! :D

---

### Post by yabbadabbadont on 2009-06-12
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

That's a good place to start.

Since you have a working server install already (I assume), you only need to add a few things to it.  That guide suggests:
```
apt-get install xorg xterm gdm icewm menu firefox gksu synaptic
```
But you would replace icewm with fluxbox.  You could also leave off gdm if you don't want a graphical login and prefer to use startx (and an ~/.xinitrc that calls "startfluxbox")

---

### Post by ninja_numbnuts on 2009-06-12
> **yabbadabbadont said:**
> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

That's a good place to start.

Since you have a working server install already (I assume), you only need to add a few things to it.  That guide suggests:
```
apt-get install xorg xterm gdm icewm menu firefox gksu synaptic
```But you would replace icewm with fluxbox.  You could also leave off gdm if you don't want a graphical login and prefer to use startx (and an ~/.xinitrc that calls "startfluxbox")

Thank you!

---

### Post by ninja_numbnuts on 2009-06-13
It worked!

---

