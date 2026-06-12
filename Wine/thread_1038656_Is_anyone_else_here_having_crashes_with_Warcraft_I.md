---
title: "Is anyone else here having crashes with Warcraft III on the Ubuntu AMD 64 platform?"
date: 2009-01-13
forum: Wine
---

### Post by hotweiss on 2009-01-13
Is anyone else here having crashes with Warcraft III on the Ubuntu AMD 64 platform? Warcraft III played perfectly on the 32 bit platform...

---

### Post by hotweiss on 2009-01-14
I finally figured it out. The crashes are due to a wine bug. Wine is written in 32 bit code so it is limited to 4 GB of memory. When you have more than 4 GB of memory, the wine bug doesn't put a stop to all the textures it tries to load into memory. So when you go one bit past the 4 GB mark, wine crashes. To fix this bug I simply removed 2 GB from my 6 GB configuration.

---

### Post by Technoviking on 2009-01-14
This maybe a better fix, without removing memory from your computer.

[http://forum.winehq.org/viewtopic.php?t=3307&sid=3fb8fbc4429ff3c0b5f0aafc17e7736a](http://forum.winehq.org/viewtopic.php?t=3307&sid=3fb8fbc4429ff3c0b5f0aafc17e7736a)

Mike

---

### Post by hotweiss on 2009-01-15
> **Technoviking said:**
> This maybe a better fix, without removing memory from your computer.

[http://forum.winehq.org/viewtopic.php?t=3307&sid=3fb8fbc4429ff3c0b5f0aafc17e7736a](http://forum.winehq.org/viewtopic.php?t=3307&sid=3fb8fbc4429ff3c0b5f0aafc17e7736a)

Mike

Ubuntu AMD64 is working perfectly, and I don't need 6 GB; I just had extra sticks lying around. I don't want to fix something that isn't broken...

---

