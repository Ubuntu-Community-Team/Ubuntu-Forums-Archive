---
title: "Virtual Kernel Error"
date: 2009-02-19
forum: Virtualisation
---

### Post by PJFinega on 2009-02-19
I'm trying to set up Virtualbox for my Ubuntu (II), but every version I install I get the error

Error! Your kernel source for kernel 2.6.24-19-generic cannot be found at
/lib/modules/2.6.24-19-generic/build or /lib/modules/2.6.24-19-generic/source.

Except in the package manager it is installed/after I reinstall all applicable packages I still get the error

Help please?

---

### Post by PJFinega on 2009-03-26
Gee thanks Ubuntu forums. I solved it on my own. I didn't update my Grub.lst when I upgraded from Heron to Ibex, so it was loading the wrong kernels. Just pick the correct Ubuntu kernel from the boot menu and it'll work.

---

