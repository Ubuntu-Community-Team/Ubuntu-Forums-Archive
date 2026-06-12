---
title: "cal/gcal/etc - how to print one date per line"
date: 2008-11-16
forum: Server Platforms
---

### Post by davidmaxwaterman on 2008-11-16
Hi,

I've been using cal for a long time, but I now find myself wanting something like a '-1/' option, that would print this :

2008/11/01
2008/11/02
2008/11/03
...
etc.

for the months I specify on the command line.

Cal didn't have such an option, so I downloaded gcal, but I can't make sense of it.

Is there some other obvious way of doing this?

Max.

---

### Post by kerry_s on 2008-11-16
man date

example:
date +%F

---

### Post by davidmaxwaterman on 2008-11-16
> **kerry_s said:**
> man date

example:
date +%F

...but that only seems to do one day. I want :

```
   November 2008    
Mo Tu We Th Fr Sa Su
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
```

but with one line per day/date.

Max.

---

