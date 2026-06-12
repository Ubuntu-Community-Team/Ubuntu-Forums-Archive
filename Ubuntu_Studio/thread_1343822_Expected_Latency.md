---
title: "Expected Latency?"
date: 2009-12-02
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2009-12-02
What kind of latency should I expect from ubuntu with RT kernel and RME HDSP MADI card?

Specs:

AMD X2 4800+ 2.4GHz
2GB Ram

---

### Post by VertexPusher on 2009-12-02
> **pepsifx357 said:**
> What kind of latency should I expect from ubuntu with RT kernel and RME HDSP MADI card?
The same as from any other soundcard if there is an ALSA driver available for it. ALSA does not distinguish between professional and consumer hardware. Even a cheap onboard audio interface can be run at 4ms latency if the system is configured properly.

---

### Post by kayosiii on 2009-12-02
My understanding is that <5ms latency should be possible, everything being configured well. It might be worth asking over at ardour.org or linux audio users mailing list to get a more definate answer.

---

