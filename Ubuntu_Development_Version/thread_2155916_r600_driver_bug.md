---
title: "r600 driver bug"
date: 2013-06-19
forum: Ubuntu Development Version
---

### Post by justynt on 2013-06-19
Just posting another bug i found, not necessarily to fix it as more to report it. 

Anyway it seems to be with Radeon cards, cant load the libgl driver r600.

here is the terminal output.

```
 libGL error: failed to load driver: r600libGL error: Try again with LIBGL_DEBUG=verbose for more details.

```

---

### Post by dino99 on 2013-06-20
Where is the report ? Complaining here will never catch the devs attention.

Have you added  "LIBGL_DEBUG=verbose"  on the boot line (that line with "quiet splash" into /etc/default/grub) and what did you got ?

---

### Post by justynt on 2013-06-20
Alright so I am trying to launch braid the game. i have tried ```
 ./braid LIBGL_DEBUG=verbose
``` and i get the same error telling me to add the libgl debug line.

---

