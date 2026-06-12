---
title: "Dual and Quad core preformance"
date: 2009-03-23
forum: System76 Support
---

### Post by echo314 on 2009-03-23
What kinda difference will I see between the standard 2.6 GHz dual-core on the Serval Pro and a Core 2 Quad at 2.0 GHz? What areas would likely see a difference? Daily tasks like having Fx open with a few tabs, including streaming vid? What about games, is the step down in GHz negated by the cores, or do apps/Linux even take advantage of the extra cores? 

The quad seems like a low speed for newer games. I have an Athlon 2000 or 3000+, at about 2GHz. I think it odd that even though I got this years ago, I can still get a processor clocked at the same speed. Hence, I am interested in how much the extra cores make up for the lower speed in desktop tasks, and more demanding games.

---

### Post by jjacobs2 on 2009-03-23
Any core 2 duo architecture will be far faster than the old Athlon 64 chips.  You should only compare MHZ between processors with the same architecture, otherwise google for some benchmarks to compare them.  Flash video, especially h264, can be very processor intensive however linux does not currently support multithreaded video decoding so the 2.6 ghz dual core would be faster for now.  In the future when multithreading works the quad will be faster.  Linux itself is multithreaded but many games are not or will not use more than 2 cores so you would get better performance right now from the dual core for that as well.  Another factor is the power requirements for the quad core being significantly higher than the dual core, almost double the P series chips for a similar price.  This will cause greater heat generation and decreased battery life.  In overall benchmarks you could expect the quad core at 2 ghz to be about 50% faster than the dual core if all cores are utilized.

---

### Post by echo314 on 2009-03-23
Ah, so 2 GHz on an older arch. is not really comparable to the same on a newer arch. Makes sense...

Does the same hold true then for speed increase increments? I would not expect a .13 GHz increase to get me much benefit with my current proc, but I see for the Serval I can up the 2.4 to 2.53 for $55. Whats the gain here, if any? After that, a similar jump in speed runs about $100 or so. I'm guessing 2.4/5 is the sweet spot right now, then? Or is it really bottom of the barrel?

I get kinda confused sometimes...not knowing whether the lowest, 2.4GHz procs with the Serval are what I would find in a bargain bin at Frys, or if the 2.4 is still a respectable proc, its just Sys76 sets their standards a little high. I guess that might be a dumb questions, since the laptop itself is one of the more high-end ones offered by 76...

It just seems like getting the lowest offered would not be a good idea.

---

### Post by jdb on 2009-03-23
> **echo314 said:**
> Ah, so 2 GHz on an older arch. is not really comparable to the same on a newer arch. Makes sense...

Does the same hold true then for speed increase increments? I would not expect a .13 GHz increase to get me much benefit with my current proc, but I see for the Serval I can up the 2.4 to 2.53 for $55. Whats the gain here, if any? After that, a similar jump in speed runs about $100 or so. I'm guessing 2.4/5 is the sweet spot right now, then? Or is it really bottom of the barrel?

I get kinda confused sometimes...not knowing whether the lowest, 2.4GHz procs with the Serval are what I would find in a bargain bin at Frys, or if the 2.4 is still a respectable proc, its just Sys76 sets their standards a little high. I guess that might be a dumb questions, since the laptop itself is one of the more high-end ones offered by 76...

It just seems like getting the lowest offered would not be a good idea.

Look at the size of L2 cache also, that makes a big difference.

jdb

---

### Post by echo314 on 2009-03-23
> **jdb said:**
> Look at the size of L2 cache also, that makes a big difference.

jdb

Wait! Don't go! So the 6mb options would be a good choice over the 3mb one?

I just have to ask then, do the 800 vs 1000 FSB speeds affect much? lol, at this rate I'm just going to keep raising my standards until I get the Bonobo :)

---

### Post by thomasaaron on 2009-03-23
Yes, the more cores, the higher the FSB and the larger the cache, the faster you go.

---

### Post by Captain_Falafel on 2009-03-24
> **echo314 said:**
> Wait! Don't go! So the 6mb options would be a good choice over the 3mb one?

I just have to ask then, do the 800 vs 1000 FSB speeds affect much? lol, at this rate I'm just going to keep raising my standards until I get the Bonobo :)

So would there be a significant difference in performance in everyday tasks and average/above average photo editing in GIMP between L2 3MB cache and 6MB cache?

---

### Post by thomasaaron on 2009-03-24
*Probably.*

I guess if they were very heavy graphics would be able to notice the difference more. If you're talking about taking the red-eye out of family photos, maybe not.

---

### Post by Captain_Falafel on 2009-03-24
> **thomasaaron said:**
> *Probably.*

I guess if they were very heavy graphics would be able to notice the difference more. If you're talking about taking the red-eye out of family photos, maybe not.

It's more along the lines of merging 3 to 5 photos together for an HDR effect and using brushes on large amounts of pixelage, and stichting multiple photos in Hugin for panoramas. I know for a fact that I'd get a considerable differece between my current 4-year-old laptop with 1.6 ghz intel pentium m processor and any core 2 duo processor.. but I especially don't want GIMP to lag when using the intel graphics card, which mine lags like no other.. It's like the brush follows the mouse pointer after a few seconds ;) 

how much integrated memory does the intel graphics card use up?

---

### Post by jdb on 2009-03-24
> **Captain_Falafel said:**
> It's more along the lines of merging 3 to 5 photos together for an HDR effect and using brushes on large amounts of pixelage, and stichting multiple photos in Hugin for panoramas. I know for a fact that I'd get a considerable differece between my current 4-year-old laptop with 1.6 ghz intel pentium m processor and any core 2 duo processor.. but I especially don't want GIMP to lag when using the intel graphics card, which mine lags like no other.. It's like the brush follows the mouse pointer after a few seconds ;) 

how much integrated memory does the intel graphics card use up?

Recently read data from memory is stored in L2 cache.
L2 cache access is typically 3 or 4 times faster than memory access.
Program code is full of short loops and subroutines that often run from cache instead of memory.
The bigger the cache the more likely that is to happen.

jdb

---

