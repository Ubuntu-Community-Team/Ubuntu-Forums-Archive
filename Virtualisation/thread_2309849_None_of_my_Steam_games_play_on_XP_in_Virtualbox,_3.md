---
title: "None of my Steam games play on XP in Virtualbox, 3D not working, how to fix."
date: 2016-01-14
forum: Virtualisation
---

### Post by MechaMechanism on 2016-01-14
Ubuntu 15.10
Virtualbox installed from Software Center.
Intel HD 530 graphics.
16 GB ram.
i5-6500 3.2

I want to run my games in Windows XP Pro running in Virtualbox that came with Ubuntu 15.10.

One game says failed to init shaders, another crashed before game even starts.  Deus Ex starts, but the mouse only sticks to the edge of the screen and can't be used.  Prey starts, but again the mouse.  Half Life works except the mouse is like hyper sensitive, not really usable.  How do I fix this?

---

### Post by Bucky Ball on 2016-01-14
Have they ever performed well in a virtual machine with XP as a guest and this has just started happening?

---

### Post by MechaMechanism on 2016-01-14
> **Bucky Ball said:**
> Have they ever performed well in a virtual machine with XP as a guest and this has just started happening?

First time gaming in Virtualbox tonight actually.  16 GB RAM.  System76 Wild Dog Pro, brand new machine.  I am wondering about the video card.  In VM I gave it 128 MB video ram.  The mouse type is PS/2.  Maybe I need to do something to VirtualBox to allow shaders?

Is there a way to post my Virtual Box settings for everyone to look at?

---

### Post by v3.xx on 2016-01-14
Did you activate 3d acceleration?

[https://www.virtualbox.org/manual/ch04.html#guestadd-video](https://www.virtualbox.org/manual/ch04.html#guestadd-video)

---

### Post by Bucky Ball on 2016-01-14
> **v3.xx said:**
> Did you activate 3d acceleration?

[https://www.virtualbox.org/manual/ch04.html#guestadd-video](https://www.virtualbox.org/manual/ch04.html#guestadd-video)

+1. And [VB guest-additions]("https://duckduckgo.com/?q=virtual+box+guest+additions+ubuntu+14")?

---

### Post by MechaMechanism on 2016-01-14
> **Bucky Ball said:**
> +1. And [VB guest-additions]("https://duckduckgo.com/?q=virtual+box+guest+additions+ubuntu+14")?I did, at least I think I did.

---

### Post by MechaMechanism on 2016-01-14
> **MechaMechanism said:**
> I did, at least I think I did.

Yes I do.  There installed according to Software Center.

---

### Post by MechaMechanism on 2016-01-14
I had to install 3D support in XP safe mode.  I now have 3D.  The games still do not mostly work, mouse is wonky at best.  All kinds of graphics glitches.

---

