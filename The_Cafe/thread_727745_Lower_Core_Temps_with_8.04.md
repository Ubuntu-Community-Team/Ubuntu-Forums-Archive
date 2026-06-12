---
title: "Lower Core Temps with 8.04"
date: 2008-03-18
forum: The Cafe
---

### Post by icm9768 on 2008-03-18
I just upgraded to the latest beta for 8.04 and noticed that my CPU cores are idling about 5 degrees(F) cooler (From ~113 to ~108). Has anyone else noticed this? Any explanation why this is?

I haven't done any fine tuning or anything like that. Thought it was a pretty nice surprise though.

---

### Post by Jim! on 2008-03-18
I think it has something to do with a "greener" ubuntu.. You know, making everything more environmentally friendly to help the planet...all that stuff. Lower cores temp means less power usage which = greener ubuntu!.....or something along those lines:D

---

### Post by jespdj on 2008-03-18
Are you using the 64-bit version?

Some time ago, an innovation was introduced into the Linux kernel - it was made [tickless](http://kerneltrap.org/node/6750). I don't know the details, but it basically means that the kernel does not need to wake up to handle interrupts X times a second, which it used to do. Because of this new feature, Linux doesn't need as much energy and doesn't drain the battery of your laptop so quickly.

In Ubuntu 7.10, the kernel for the 32-bit version was already tickless, but the kernel for the 64-bit version was not.

In the 64-bit version of Ubuntu 8.04, the kernel will also be tickless.

Maybe you're noticing the effect of the tickless kernel.

---

### Post by Jim! on 2008-03-19
> **jespdj said:**
> Are you using the 64-bit version?

Some time ago, an innovation was introduced into the Linux kernel - it was made [tickless](http://kerneltrap.org/node/6750). I don't know the details, but it basically means that the kernel does not need to wake up to handle interrupts X times a second, which it used to do. Because of this new feature, Linux doesn't need as much energy and doesn't drain the battery of your laptop so quickly.

In Ubuntu 7.10, the kernel for the 32-bit version was already tickless, but the kernel for the 64-bit version was not.

In the 64-bit version of Ubuntu 8.04, the kernel will also be tickless.

Maybe you're noticing the effect of the tickless kernel.

Hahahaha, couldn't help but laugh, your answer makes mine look so pathetically stupid:D Your answer sounds very professional to me and I think that it's probably right!:)

---

### Post by christianxxx on 2008-03-19
But still, tickless kernel means greener Ubuntu.. :)

---

### Post by Jim! on 2008-03-19
Yeah your right! And a greener Ubuntu is a better Ubuntu:D

---

