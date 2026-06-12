---
title: "conky crashes unity/compiz"
date: 2012-09-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by RikoW on 2012-09-13
Dear all,

whenever I start conky, it causes unity/compiz (which one?) to restart. Anyone observing something similar?

I suspect it's connected to same of the graphics glitches already reported. My machine has a on-board Intel HD4000 grahic card for the i7 cpu. The video chip set is not recognized properly.

Cheers,

              Riko

---

### Post by stinkeye on 2012-09-16
Had a similar issue and I think it may be due to some compiz plugin.
I'm using a GeForce 9400 GT
NVIDIA Driver Version:304.43

I set compiz back to defaults with ...
```
dconf reset -f /org/compiz/
```

and then reloaded compiz...
```
compiz --replace & disown
```

I'm re-enabling the plugins I use one at a time and running for a while
before enabling another.

So far I have enabled **Desktop Cube**, **Rotate Cube** and **Wobbly Windows**
with no conky problems.


[COLOR="Red"]**_EDIT:_**[/COLOR] It appears to be caused by the animations plugin
when you choose a custom animation for open or close.
When using a custom animation for open or close, adding...
```
& !(class=Conky)
```
to the window match box solves the compiz crashing problem for me.

---

