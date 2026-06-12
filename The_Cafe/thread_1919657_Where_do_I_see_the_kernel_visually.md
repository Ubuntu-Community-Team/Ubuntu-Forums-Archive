---
title: "Where do I see the kernel visually?"
date: 2012-02-03
forum: The Cafe
---

### Post by brawnypandora0 on 2012-02-03
So whenever I open the terminal, do I "see" the shell?

Can the kernel be seen on the screen or is it abstract and unseen?

---

### Post by haqking on 2012-02-03
> **brawnypandora0 said:**
> So whenever I open the terminal, do I "see" the shell?

Can the kernel be seen on the screen or is it abstract and unseen?

sure you can see it, it is the file on the far right called vmlinuz in my attachment ;-)

When you open the terminal you are at the command line/CLI, shell etc.


The kernel is the core/brain of the OS

---

### Post by forrestcupp on 2012-02-03
> **brawnypandora0 said:**
> So whenever I open the terminal, do I "see" the shell?

Can the kernel be seen on the screen or is it abstract and unseen?

The kernel the low-level thing that makes everything work with your hardware. It's not something that you see with your eyes in your day to day work. Everything you see directly or indirectly depends on the kernel, but you only actually see the upper level stuff running.

And no, the command line is not the visual representation of the kernel.

---

### Post by Smilax on 2012-02-03
don't know about seeing it,

but you can here it here...


[http://www.linux.fm/](http://www.linux.fm/)


Use the Source, Luke!

:guitar::guitar::guitar:

---

### Post by odiseo77 on 2012-02-03
I guess that if you can somehow actually "see" the (compiled) kernel, everything you will see is a bunch of ones and zeroes... unless you see its source files, which should have a more human-readable aspect (C code, if I'm not mistaken).

---

### Post by JDShu on 2012-02-03
One possible interpretation of the question, is how do I know what the kernel is doing?

Well the kernel is always doing something, but you can see what the kernel sees fit to tell you by running

```
dmesg
```

in the terminal, which would give you the latest logs from the kernel. That is, what the kernel feels is important that you know. If you wanted to look at it more actively, you could run

```
watch 'dmesg|tail'
```

which would give you the same thing except it updates immediately whenever the kernel sends a new message to the log. It might not be terribly interesting though!

---

### Post by Lars Noodén on 2012-02-03
There's a Linux Kernel Map which gives a very general overview of its functionality:

[http://upload.wikimedia.org/wikipedia/commons/5/5b/Linux_kernel_map.png](http://upload.wikimedia.org/wikipedia/commons/5/5b/Linux_kernel_map.png)

---

### Post by Lucradia on 2012-02-03
> **Lars Noodén said:**
> There's a Linux Kernel Map which gives a very general overview of its functionality:

[http://upload.wikimedia.org/wikipedia/commons/5/5b/Linux_kernel_map.png](http://upload.wikimedia.org/wikipedia/commons/5/5b/Linux_kernel_map.png)

Check out class shooting across the map there. It's like a bloody warzone in there.

---

### Post by Gremlinzzz on 2012-02-03
The kernel is a myth it doesn't exist :popcorn:
I thought i seen one but i didn't have a camera.

---

### Post by Gremlinzzz on 2012-02-03
Had a kernel in a deb package once but when i opened it nothing was there !
:popcorn:

---

### Post by forrestcupp on 2012-02-03
> **Gremlinzzz said:**
> Had a kernel in a deb package once but when i opened it nothing was there !
:popcorn:

I thought about installing the kernel once, but didn't think I would ever use it.

Nice use of popcorn while we are talking about the kernel. :)

---

### Post by QIII on 2012-02-03
Instead, only try to realize the truth: there is no kernel.

---

