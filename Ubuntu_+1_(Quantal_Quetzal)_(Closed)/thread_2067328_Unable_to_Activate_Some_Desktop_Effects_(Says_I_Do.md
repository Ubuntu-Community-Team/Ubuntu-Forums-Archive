---
title: "Unable to Activate Some Desktop Effects (Says I Don't Have OpenGL?)"
date: 2012-10-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jlacroix on 2012-10-06
I installed Kubuntu Quantal 64-bit fresh a few days ago, and I just today activated the binary nvidia driver. Before, I was missing animation effects for the desktop cube and blur (among others) but I didn't really pay any attention. But now I figured by installing the binary driver I would have these effects. Instead, I get this when I enable desktop effects in System Settings:

```
Blur effect requires OpenGL
Cover Switch effect requires OpenGL
Desktop Cube Animiation effect requires OpenGL
Startup Feedback effect requires OpenGL
```

How does one get away with NOT having OpenGL in a Linux distribution? Is that even possible? I can't say I've ever been "missing" OpenGL the entire time I've been using Linux.

Is this a bug?

---

### Post by Gavin77 on 2012-10-06
Just an idea, make sure that in "System Settings > Desktop effects > advanced > Compositing type" is set to OpenGL.

---

### Post by jlacroix on 2012-10-06
> **Gavin77 said:**
> Just an idea, make sure that in "System Settings > Desktop effects > advanced > Compositing type" is set to OpenGL.
That did it. It was set to Raster by default. I never had to change this setting before, but thank you!

---

