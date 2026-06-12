---
title: "core 2 duo/i486 - odd?"
date: 2007-08-04
forum: The Cafe
---

### Post by Ultra Magnus on 2007-08-04
I didn't really know where to post this but its a bit odd...

I'm a bit bored so I've been having a go a doing a Linux from Scratch in Vmware... It was all going fine except when I type in..

gcc -dumpmachine

it says "i486-pc-linux-gnu"

I thought, thats odd, I thought I had a core 2 duo processor and i486 is pretty old isn't it?

I tried the same command on Ubuntu and it gave me a similar "i486-linux-gnu".

What exactly does this mean?

---

### Post by Turboaaa2001 on 2007-08-04
In my opinion it is not referencing the CPU. instead the architeture.

A 32 bit OS with either a 32 or 64bit CPU is sometomes called either x86 or 486. If everything is 64bit then its 64.

So to recap what I can figure out in short noticve (at work)

You can havce either a

486 / x86 platform

or 64 platform

---

### Post by ameyer on 2007-08-05
I believe Ubuntu's packages on the x86 platform are compiled to only use the 486 instruction set for compatibility reasons.

---

