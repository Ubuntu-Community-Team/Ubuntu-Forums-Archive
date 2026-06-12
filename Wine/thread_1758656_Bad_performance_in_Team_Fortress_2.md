---
title: "Bad performance in Team Fortress 2"
date: 2011-05-14
forum: Wine
---

### Post by Teraspes on 2011-05-14
Hi!

I have been searching for some kind of solution for hours now. I have managed to get Team Fortress 2 to launch, but it runs pretty slowly.

If I run **glxinfo | grep direct** in the terminal, I get:
```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```However, if I run **sudo glxinfo | grep direct**, it outputs this:
```
direct rendering: Yes
```I'm not sure if that is relevant, but it seems a bit odd.

I have Ubuntu 10.10 64-bit. My graphics card is a AMD Radeon 6870 and the driver is the 64-bit driver from their website (CCC 11.5).

What may be the problem with my setup? Just ask if I need to provide any more information.

---

