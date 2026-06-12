---
title: "How does dynamic memory allocation work for intergrated video?"
date: 2005-09-09
forum: The Cafe
---

### Post by godzero on 2005-09-09
I Have a shared memory video controller, which can allocate up to 64MB. At boot time, it allocates 2 MB.

Once I'm fully booted up, lets say I launch tux racer. There should be more texture than can fit in 2 MB, so it needs to allocate more memory.

How does this happen? Does the gpu request memory from the driver, or is it handled by the mmu? Does the kernal think the driver or Xorg allocated more memory, or does it think the world is shrinking?

---

### Post by joker on 2005-09-09
Its been a long time since I had an integrated video solution so this may no longer be accurate, but I had to set how much memory I wanted to be allocated for video in the system bios, and that amount was subtracted from the amount of memory the OS could use as conventional memory.  There was not a dynamic reallocation of memory when it was needed by the video card or the OS.

---

### Post by godzero on 2005-09-10
I remember those from back in the day... jump into bios, set the amount of ram to use...

The more modern ones (like mine) do use dynamic allocation, in fact there's no way to override it.

---

### Post by WildTangent on 2005-09-10
my Radeon Xpress 200 (X300 based) can only be set to take 16, 32, 64 or 128 MB, no dynamic allocation. i have mine set for 128, but i have a GB of memory so its not much of a loss

-Wild

---

### Post by TravisNewman on 2005-09-10
At least Wild got it ;)

The OP is talking about Dynamic Memory Allocation. Basically, its like CPU frequency scaling on laptops. It doesn't use it unless it needs it, then it takes it automatically. Quite interesting, but I have no clue how it works.

---

### Post by floppy on 2005-09-10
For a good explanation of how it works, try this Intel document:
[ftp://download.intel.com/support/graphics/intel845g/dvmt.pdf](ftp://download.intel.com/support/graphics/intel845g/dvmt.pdf)

---

### Post by godzero on 2005-09-12
That was exactly what I wanted, thanks *floppy*

---

### Post by Circus-Killer on 2008-08-25
> **godzero said:**
> I Have a shared memory video controller, which can allocate up to 64MB. At boot time, it allocates 2 MB.

Once I'm fully booted up, lets say I launch tux racer. There should be more texture than can fit in 2 MB, so it needs to allocate more memory.

How does this happen? Does the gpu request memory from the driver, or is it handled by the mmu? Does the kernal think the driver or Xorg allocated more memory, or does it think the world is shrinking?

are you asking simply out of interest, or are you like me who seems to think that it doesnt work in ubuntu?
cos everything works fine until i try play graphic intensive games like doom3.
i've got a sneaking suspicion that the dynamic video memory thingy dont work so well in ubuntu. im pretty sure my video memory is sticking to the lowest 8mb without trying to access more.

---

### Post by -grubby on 2008-08-25
> **Circus-Killer said:**
> are you asking simply out of interest, or are you like me who seems to think that it doesnt work in ubuntu?
cos everything works fine until i try play graphic intensive games like doom3.
i've got a sneaking suspicion that the dynamic video memory thingy dont work so well in ubuntu. im pretty sure my video memory is sticking to the lowest 8mb without trying to access more.

This post is 3 years old..

---

### Post by Circus-Killer on 2008-08-25
whoops, talk about waking the dead :P

---

### Post by Sinkingships7 on 2008-08-25
> **Circus-Killer said:**
> whoops, talk about waking the dead :P

Well, while we're awake, might as well make the most of it before it's closed. What graphics card do you have?

---

### Post by Sef on 2008-08-25
Closed.  Necromancing.

---

