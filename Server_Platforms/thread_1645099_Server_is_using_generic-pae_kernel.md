---
title: "Server is using generic-pae kernel"
date: 2010-12-14
forum: Server Platforms
---

### Post by tuaris on 2010-12-14
For some reason, my Ubuntu server is using the generic-pae kernel.  How do I change it to use the server optimized version?

---

### Post by CharlesA on 2010-12-14
Install the 64-bit version.

IIRC the 32-bit version uses the generic kernel, tho it shouldn't make much difference.

EDIT: You could try installing the server kernel, but I don't know how well that'll work.

---

### Post by dtfinch on 2010-12-14
I think the 32 bit server kernel was just renamed to generic-pae, and the linux-image-server package now points to it. PAE is needed to support more than 4gb ram on 32 bit.

---

