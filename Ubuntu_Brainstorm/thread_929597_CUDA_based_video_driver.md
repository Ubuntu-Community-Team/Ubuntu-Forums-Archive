---
title: "CUDA based video driver?"
date: 2008-09-25
forum: Ubuntu Brainstorm
---

### Post by artsci2 on 2008-09-25
Is the NVidia GPU progamming system CUDA an opportunity for the open source community to write video drivers for Linux?

---

### Post by gnomeuser on 2008-09-25
> **artsci2 said:**
> Is the NVidia GPU progamming system CUDA an opportunity for the open source community to write video drivers for Linux?

The short answer is no.

The long also no, since CUDA requires driver support (I refer to the case of chicken v. egg) and the task you describe isn't encompassed in the CUDA space.

[http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

Basically CUDA could be used for things like writing accelerated video codec decoders (and infact one Google Summer of Code project did this for Schrodinger/Dirac) but not for writing a driver to power the video card itself.

---

