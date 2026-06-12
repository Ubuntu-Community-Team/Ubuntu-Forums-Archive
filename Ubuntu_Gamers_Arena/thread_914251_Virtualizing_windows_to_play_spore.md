---
title: "Virtualizing windows to play spore"
date: 2008-09-08
forum: Ubuntu Gamers Arena
---

### Post by JebusWankel on 2008-09-08
I want Spore so badly. I don't expect Wine to support it well very soon, so I'd like to virtualize windows to get it running. I have a new laptop with Core 2 Duo processor that supports VT, Intel X3100 graphics, and a gig of ram. Should I use Xen, VMware, Virtualbox, or Qemu. Qemu doesn't seem to want to take full advantage of my processor, so I doubt I'll end up with that. I'd like to do as little compiling as possible. What should I do?

---

### Post by itsbradman on 2008-09-08
I don't think direct x works with any virtual platform, so gaming via vm isn't much of an option. Believe that virtualbox can translate direct x into open gl, but I'm not sure how well that works.

---

### Post by belgarth on 2008-09-08
I was able to get spore to run in wine once I cracked the exe (Currently the authentication seems to be failing, there's a wine bug for it). Unfortunately the graphics seem to be really messed up. I don't know how to explain it exactly, but the best I can come up with is when something moves there is a trail of old copies of it that aren't getting removed properly.

I've never used wine before, so maybe the problem is something simple. Still looking into it.

---

### Post by JebusWankel on 2008-09-08
Wow it looks like the Wine folks really got into gear. I remember the creature creator being rated as garbage not too long ago but I guess the demand really got things going.

---

