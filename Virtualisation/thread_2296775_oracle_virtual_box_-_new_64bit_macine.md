---
title: "oracle virtual box - new 64bit macine"
date: 2015-09-28
forum: Virtualisation
---

### Post by hezy2 on 2015-09-28
Hello,
message: "This kernel requires an x86-64 cpu, but only detected an i686 cpu. Unable to boot - please use kernel appropriate for your cpu.", when trying to install a 64bit Linux disribution (openfiler) on virtual box 5. Host OS is ubuntu 15.04. Thanks,
Hezy.

---

### Post by QIII on 2015-09-28
Hello!

What is the installed CPU?

---

### Post by hezy2 on 2015-09-28
Intel® Pentium(R) CPU P6200 @ 2.13GHz × 2

---

### Post by QIII on 2015-09-28
According to ARK, that does use the 64 bit instruction set.

Is VT-x enabled in your BIOS?

Edit -- never mind.   ARK says VT-x is not supported with that CPU.

You should still be able to run a 32 bit VM if you disable VT-x in your VM setup.  VB normally detects if VT-x is available, but check to be sure.

---

