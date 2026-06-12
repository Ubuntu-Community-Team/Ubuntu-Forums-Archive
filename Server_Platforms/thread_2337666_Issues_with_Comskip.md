---
title: "Issues with Comskip"
date: 2016-09-20
forum: Server Platforms
---

### Post by AATLEMIDRM on 2016-09-20
Is there an issue installing Comskip on a headless server? It was throwing all sorts of errors for me, identical to those earlier in the thread, until I installed Unity. Now it's still not compiling, but the errors look to me like it's looking for graphical settings that don't exist because I've never actually logged in graphically. (undefined reference to `XDisplayName', for example.)

Is there some convenient way to tell it to ignore anything that's X11 related and just build the cli stuff?

---

### Post by howefield on 2016-09-20
Post moved to its own thread and to the "*Server Platforms*" forum, probably a better fit.

---

### Post by AATLEMIDRM on 2016-09-20
> **howefield said:**
> Post moved to its own thread and to the "*Server Platforms*" forum, probably a better fit.

Probably, but now I have to flesh out the "earlier in this thread" comment. :)

---

### Post by AATLEMIDRM on 2016-09-20
Refers to this thread:

[https://ubuntuforums.org/showthread.php?t=2337011](https://ubuntuforums.org/showthread.php?t=2337011)

---

### Post by AATLEMIDRM on 2016-09-21
It turned out that there was a previously known issue with 14.04 LTS. Upgrading to 16.04 LTS solved this for me.

---

### Post by cariboo on 2016-09-21
Could you let us know what you did to solve the problem, so others can benefit from your experience.

---

