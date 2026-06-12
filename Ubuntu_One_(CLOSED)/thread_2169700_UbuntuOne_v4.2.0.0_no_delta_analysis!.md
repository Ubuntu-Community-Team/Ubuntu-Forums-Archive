---
title: "UbuntuOne v4.2.0.0: no delta analysis?!"
date: 2013-08-23
forum: Ubuntu One (CLOSED)
---

### Post by tony14 on 2013-08-23
(winXP-SP3 here)

Seems UbuntuOne v4.2.0.0 does not analyze what part of a file has changed. It simply re-sends the whole file again. 

(I have put a TrueCrypt file container, 128MB in the web storage from one machine, synched a folder on another machine. My container appeared there. I've mounted it, changed its' content - approximately few kilobytes, and dismounted my container. The HEX difference does not exceed several blocks, i.e. is much, much less than the whole container size. But UbuntuOne decided to upload the whole 128MB file to the web storage) 

Is it by design?

---

### Post by Irihapeti on 2013-08-23
As far as I know, every version of Ubuntu One uploads the entire file when it's changed.

---

