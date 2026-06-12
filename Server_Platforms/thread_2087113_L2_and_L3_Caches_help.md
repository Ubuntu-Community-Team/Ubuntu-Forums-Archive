---
title: "L2 and L3 Caches help"
date: 2012-11-22
forum: Server Platforms
---

### Post by kpholmes on 2012-11-22
Im looking at some of the AMD 4200 and 6200 server CPUs, and theres so many decisions! the part that im so unsure of is the level of caches, for example on the 4284 series there 3 different versions. (1) ie. the OS4284WLU8KGUWOF has 1MB of L2 cache; and the OS4284WLU8KGUS has 8MB?? both are Opteron 4284 CPUs. While reading online I ran across an article saying that having larger cache results in more seeking time, Im so confused with the whole situation. Is it better to have a large L2 cache? Or is it better to have a CPU that has a smaller faster L2 cache and then a large L3 cache?



thanks in advance!



(1) AMD 4284 CPUs - [http://shop.amd.com/us/All/Compare/Products?SearchFacets=category%3AProcessor%3Bmodelnum%3A4284&id=OS4284WLU8KGUWOF&id=OS4284WLU8KGUS&id=OS4284WLU8KGU](http://shop.amd.com/us/All/Compare/Products?SearchFacets=category%3AProcessor%3Bmodelnum%3A4284&id=OS4284WLU8KGUWOF&id=OS4284WLU8KGUS&id=OS4284WLU8KGU)

---

### Post by Vegan on 2012-11-22
In general the more L1 the better, same for L2 and L3

L1 is fastest, L2 next up, L3 is closer to main memory in performance.

---

### Post by ibjsb4 on 2012-11-22
Four or five years ago I took a look at Xeon L2 and L3 performance results.  What I found was only small performance gain and in some cases a minor performance loss with L3.  I concluded its better to have a large L2 and no L3.

---

### Post by kpholmes on 2012-11-22
thanks for the replies everybody! this really helps! i couldn't find L1 cache info on AMD's site, same with newegg:(


any recommendations on websites that list hardware info? i check out tomshardware and manufacturer sites..

thanks again!

---

