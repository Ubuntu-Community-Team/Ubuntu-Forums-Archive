---
title: "NX bit and x86 platform"
date: 2009-04-27
forum: Security
---

### Post by BubuXP on 2009-04-27
The "No eXecute" technology in modern CPUs works for sure with a 64bit OS.
That's because the NX bit is the #63, the last bit of a 64bit memory address.
It will work also in 32bit OSes with PAE enabled (capable of reading 64bit addresses, like the server kernel of 32bit-ubuntu).

The info I cannot find for sure is if a 32bit-ubuntu with a desktop kernel (no server) will take any advantage of this technology.
Does it make any difference having this feature enabled in the bios (for example lower performance)?

Thanks.

---

### Post by BubuXP on 2009-04-28
Even if the "No eXecute" is a security feature, maybe it's better to move this thread in the hardware section of the forum.
If a moderator/admin could move it...

---

