---
title: "Wine 100% X11 CPU on use"
date: 2009-07-13
forum: Wine
---

### Post by painejake on 2009-07-13
Had a search and a google but haven't been able to find a answer to the issue. Whenever i start wine, run a program using wine or even start the wine configuration manager the:

```
/usr/X11R6/bin/X
```

Process jumps too 100% on 1 core. I'm taking a wild stab in the dark saying its a X11/Xorg process the only way i can return the CPU to normals levels is by either killing the process (so it restarts) or a hard restart (logging out and back in might also work)

I'm using Ubuntu 9.04 x86_64 and haven't used wine for a while now. Anyone confirm if this is a bug at all?

If not any suggestions on steps to take? Already tried compiling wine however that didn't work either both stable and latest. Using crossover 7.1 at the moment (as well as wine same thing happens with both) tried cedega trial too and that seemed ok-ish.

Thanks in advance,

Jay

---

