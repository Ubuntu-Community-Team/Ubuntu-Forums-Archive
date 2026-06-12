---
title: "Warcraft 3: TFT Freezing after 15 mins of play"
date: 2009-01-25
forum: Wine
---

### Post by Xil3 on 2009-01-25
Has anyone had this issue before? Is there some bug with the nvidia 180 drivers that would cause this?

---

### Post by hotweiss on 2009-01-25
Do you have more than 4 GB of memory? If so that is the cause... I had the same problem, I just had to remove two sticks of RAM... It's a wine bug.

---

### Post by Xil3 on 2009-01-25
> **hotweiss said:**
> Do you have more than 4 GB of memory? If so that is the cause... I had the same problem, I just had to remove two sticks of RAM... It's a wine bug.

I have 8 GB - hahaha...

Don't think I'm gonna remove 3 sticks of RAM though. Is there any other way around this?

---

### Post by hotweiss on 2009-01-25
> **Xil3 said:**
> I have 8 GB - hahaha...

Don't think I'm gonna remove 3 sticks of RAM though. Is there any other way around this?

Well the solution is to have no more than 4 GB of RAM because wine keeps on storing textures without taking the 32 bit limit into account. And once it reaches that limit, wine crashes. You can try these tricks here:

[http://forum.winehq.org/viewtopic.php?t=3307&postdays=0&postorder=asc&start=25&sid=b533f4defbabc8bc49a99dcdd24cc6b1](http://forum.winehq.org/viewtopic.php?t=3307&postdays=0&postorder=asc&start=25&sid=b533f4defbabc8bc49a99dcdd24cc6b1)

---

