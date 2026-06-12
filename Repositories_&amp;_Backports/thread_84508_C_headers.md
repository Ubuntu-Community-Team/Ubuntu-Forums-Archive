---
title: "C headers"
date: 2005-10-31
forum: Repositories &amp; Backports
---

### Post by dimovich on 2005-10-31
I tried compiling some C code, but found that I have no C standard header files... What package should I download to install those headers ?

thanks

---

### Post by dimovich on 2005-11-04
No one ? Please...

---

### Post by RayH on 2005-11-04
Kind of complicated for a beginner, but your looking for linux headers.  Type uname -r at the terminal.  That will tell you your kernel version.  Then open Synaptic, search for linux headers and grab the ones that match your kernel version (the regular one and likely the one with the 386 extension).  You may need more (gcc, gcc++, etc).  If the program you're trying to compile is a popular one, then try searching for that application or the specific error that you are having.

---

### Post by niko_ on 2005-11-04
hi dimovich, just type this:

> sudo apt-get install build-essential

---

