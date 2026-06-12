---
title: "Server Usable Memory"
date: 2012-07-27
forum: Server Platforms
---

### Post by Kleenux on 2012-07-27
There is a lot of posts about the Free memory on Ubuntu.
Mainly the commands [FONT="Courier New"]free[/FONT] or [FONT="Courier New"]cat /proc/meminfo[/FONT]
E.g.
```
MemTotal:         960176 kB
MemFree:           55292 kB
Buffers:           91188 kB
Cached:           526496 kB
SwapCached:         5912 kB
Active:           410628 kB
Inactive:         423128 kB
```

However, I cannot find a definitive answer as what is the actual usable memory. Ubuntu reserves some of the memory for the Buffers and Caches. And may release some if a greedy process asks for it.

So, what is the "reasonable" usable amount of memory? 

Is "Cached" or "Inactive" a fair indication of what could be used if required (minus a %) ?

---

### Post by BkkBonanza on 2012-07-27
If you go by what free -m says, eg.
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2003       1862        140          0         45       1264
-/+ buffers/cache:        553       1449
Swap:            0          0          0

```
I've typically treated it as 1449 free here. 553 used. This is about what htop shows as "green" as well. I think you can read it as, 

1862 is in use but cache is using 1264 and buffer 45 and those could be released when really needed leaving 553 really, really in use. Of course, releasing buffers may cause some problems and having no cache is bound to slow down a lot of stuff too. So I don't think you'd be wise to force that depth of purge.

edit: 
If you look at /proc/meminfo I think it is the two (anon) lines that are critical. I could be wrong but I read it as those pages of memory cannot be reloaded from a _known_ source. They seem to add up to about the right value too.

---

### Post by DJ_Max on 2012-07-27
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Kleenux on 2012-07-28
Thanks for the explanation, and for the link.

I'm not a newbie, and find (found) pretty confusing the output of the 'free' command. The most compelling proof it is confusing, is that someone (your link) had to register a domain and make a page to explain why 'Linux does not ate my ram', and by the way the site person didn't do the math correctly: the result is 41% and not 42% (he didn't add the remaining not used even in caches amount of 13MB ;)
(ok maybe a rounding error)

So to summarize: while the system (and us) prefer to have more disk buffers, from```
$ free -m
             total       used       free   ...
Mem:             T          u          F   ...
-/+ buffers/cache:         bu         BF
```usable memory =  F + BF

Used memory is   100 * [ ( T - F - BF ) / T ]  % 

The casual 'free' command takes the "liberty" (without the -o option) to have a kind of explanatory line related to the buffers usage. It should also display a line with the actual usable memory. Not everybody knows how a disk caching works.

That would make the 'free' command more interesting.

---

### Post by BkkBonanza on 2012-07-28
No, I'm pretty sure your BF figure already includes the F amount.
Used % = bu/T*100 
Available % = BF/T*100

The "-/+ buffers/cache:" line label is trying to make it clear that this figure is with add/subtract buffers and cache. Add for free, subtract for used. That's why -/+ not +/-. Devs are so particular.

bu + BF = T (except for rounding when using -m)

---

### Post by Kleenux on 2012-07-28
According to free.c, you are right```
            unsigned KLONG buffers_plus_cached = kb_main_buffers + kb_main_cached;
            printf(
                "-/+ buffers/cache: %10Lu %10Lu\n",
                S(kb_main_used - buffers_plus_cached),
                S(kb_main_free + buffers_plus_cached)
            );
```'free' actually sums the main free memory and the (cache+buffers).

So, usable memory = BF :cool:

Another reason for 'free' to be more explicit...

---

