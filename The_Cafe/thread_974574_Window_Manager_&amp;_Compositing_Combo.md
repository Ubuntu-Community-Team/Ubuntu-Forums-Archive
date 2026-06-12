---
title: "Window Manager &amp; Compositing Combo"
date: 2008-11-07
forum: The Cafe
---

### Post by BGFG on 2008-11-07
Hi all,
In 8.04 I found that a combination of A Gnome-Openbox Session and xcompmgr significantly speed up window response time.
In Intrepid, much like in hardy i find myself waiting seconds for a response when i select any of my "PLACES"

Can any one who know the code explain why metacity and compiz respond so slowly ? I tried Gnome-openbox in Intrepid but i can't get it to work yet.

---

### Post by Joeb454 on 2008-11-07
Try XFCE - that has a built in compositor, it's pretty decent too :)

---

### Post by loell on 2008-11-07
that's probably because metacity and compiz are not just compositors they also do window management

---

### Post by BGFG on 2008-11-10
> **loell said:**
> that's probably because metacity and compiz are not just compositors they also do window management

If they both do window management and compositing, that seems redundant. Run slow as hell here. I'll keep trying with openbox. Not as pretty but much faster.

---

### Post by aaaantoine on 2008-11-10
> **BGFG said:**
> If they both do window management and compositing, that seems redundant. Run slow as hell here. I'll keep trying with openbox. Not as pretty but much faster.

No redundancy.  Your system will run one (Metacity) or the other (Compiz), not both at once.

---

### Post by BGFG on 2008-11-10
In my system processes i see both metacity and compiz decorator running. Also,which is faster ?

---

### Post by chris4585 on 2008-11-10
Compiz should be faster on the right machine.  Compiz utilizes your gpu to manage all the nice effects and opening windows, etc.. leaving your cpu to do the real work.  This is what I've been told before.

thus why on my system with compiz things fly, and with just gnome things are slow as crap with 2gb of ram!

---

