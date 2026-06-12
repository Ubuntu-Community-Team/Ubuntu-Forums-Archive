---
title: "x86/i686 discrepency"
date: 2009-10-18
forum: Server Platforms
---

### Post by Muscovy on 2009-10-18
I tried installing server edition (9.04) on my old computer to reduce the overhead from GUI, but the LiveCD says something like "This kernel only supports x86-x64. You seem to have a i686 processor."
  I will assume that x86-x64 is 32 and 64 bit, so it's eligible. So why can't this computer be installed upon?

---

### Post by cariboo on 2009-10-18
If you don't have a 64-bit CPU you can't install a 64-bit OS. If the installer is telling you that the CPU is an i686, you have to install the 32-bit server version.

---

### Post by Muscovy on 2009-10-18
The disk says it's x86-x64. Doesn't that mean it's both?

---

### Post by undecim on 2009-10-18
No, the x86 just means that the processor takes x86 instructions. The 64 means that those instructions are in 64 bits, but your processor can only use 32 at a time, so you need the i386 (32-bit) version

---

