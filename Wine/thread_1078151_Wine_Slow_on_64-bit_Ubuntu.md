---
title: "Wine Slow on 64-bit Ubuntu?"
date: 2009-02-23
forum: Wine
---

### Post by Kareeser on 2009-02-23
Hey everybody,

Has anyone noticed Wine starting up programs a lot slower on a 64-bit Ubuntu compared to 32-bit?

When I had 32-bit Ubuntu installed on my system, WINE programs would start up immediately, but with 64-bit, I have to wait at least 10 seconds for something to occur. No error messages seem to occur, it just takes awhile to start up.

Everything is normal afterwards...

Anyone have any ideas?

---

### Post by YokoZar on 2009-02-23
Hmm, interesting observation.  I haven't tested it directly myself, but I do have a theory:

On 32 bit you already have most of the libraries Wine needs already loaded.  On 64 bit the system has to load separate, 32 bit versions of those libraries (since Wine runs in 32 bit mode) - this means a slightly longer load time as they're pulled off of the disk and placed into memory.


One quick note though: on the first load up, Wine will always take a longer time because it has to set up the ~/.wine directory

---

### Post by Kareeser on 2009-02-23
Hm. Seems like a pretty crippling setback for 64-bit computing :(

Thanks for your help, YokoZar, I'll ask again on the WINE forum :)

---

### Post by BoneSmash on 2009-02-23
I experience the same slow startups, it's not THAT big of a deal, but it definitely makes my fast computer seem slow....

---

### Post by Kareeser on 2009-02-23
Thanks for the corroboration, BoneSmash. I'll let you know if I find anything.

---

