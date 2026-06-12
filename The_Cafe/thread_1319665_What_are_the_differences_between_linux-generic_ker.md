---
title: "What are the differences between linux-generic kernel and linux-server kernel?"
date: 2009-11-08
forum: The Cafe
---

### Post by wulfgang on 2009-11-08
I was just curious, What are the differences between linux-generic kernel and linux-server kernel?

---

### Post by NoaHall on 2009-11-08
One is for general use, the other is optimized for servers.
You get five points if you correctly guess which one is which.

---

### Post by wulfgang on 2009-11-08
well I already know that much. ;)

---

### Post by markp1989 on 2009-11-08
> **NoaHall said:**
> One is for general use, the other is optimized for servers.
You get five points if you correctly guess which one is which.

op had already guest that lol, i would also like to know what optimizations the server version has that desktop doesnt, and vice versa?

---

### Post by wojox on 2009-11-08
I'm guessing the difference is mostly in the fact that the server kernel is not preemptive, like the desktop kernel is.

Preempting means kicking process A from the CPU in favor of process B, in simple terms. End-users expect a responsive system. Therefore, a desktop will run a preemptive kernel, which can favor user interaction above running programs. This means that the kernel can 'kick' a background program, favoring a user program by granting it runtime on the CPU, even before the background program's timeslice is over and before the background program yields the CPU.

A server on the other hand, is built to run a couple of programs in the background (like Apache) and not to interact with a user. Therefore, a server will not run a non preemptive kernel, and so be optimized for running programs in the background.

---

### Post by wulfgang on 2009-11-08
Thanks, wojox.

---

### Post by NoaHall on 2009-11-08
Not to mention PAE. This enables 32 bit computer to sort of become 36 bit computers, so they can support more RAM without being 64 bit. However, since karmic(I think) this is also included in the generic version.

---

### Post by wojox on 2009-11-08
Not absolutely sure, haven't gotten to far into kernel hacking. Another is generic will run on any system and optimize itself.

---

### Post by ronocdh on 2009-11-30
Canonical provides a list of [server-specific optimizations]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel"). They include lack of pre-emption, as noted by wojox above, as well as the Deadline scheduler over CFQ, sped up interrupt cycle, and so on.

Found this post on a search, wasn't happy with the results, so kept looking and found the above link. =) Sorry to revive a dead post, but I thought it would help someone.

---

