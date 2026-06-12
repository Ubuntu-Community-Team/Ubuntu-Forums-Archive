---
title: "Do i need to set audio priorities in limits.conf for JACK if I have 4GB RAM?"
date: 2009-02-22
forum: Ubuntu Studio
---

### Post by msu3 on 2009-02-22
I recently installed 8.04 Ubuntu Studio amd64, and playing music in Audacious set to JACK through my Firebox works fine out of the box. 

Can I safely select "No memory lock" with 4 GB RAM? If I want to get into recording with Ardour, should I set the priorities? Should I allocate half?

---

### Post by raboofje on 2009-09-25
> **msu3 said:**
> Can I safely select "No memory lock" with 4 GB RAM?

I'm not sure, but I'd guess this option prevents audacious from memlocking some bits of the memory it uses.

Memlocking certain important blocks of memory prevents them from being swapped out. While this might be unlikely to happen with 4GB of RAM available, it shouldn't hurt.

> If I want to get into recording with Ardour, should I set the priorities?

Yes.

> Should I allocate half?

You could probably do with less, but it can't hurt much: (unless people are being sloppy) memory won't be allocated unless needed afaik.

---

