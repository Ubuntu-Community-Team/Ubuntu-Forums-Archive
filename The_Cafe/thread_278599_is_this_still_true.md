---
title: "is this still true?"
date: 2006-10-16
forum: The Cafe
---

### Post by TheRingmaster on 2006-10-16
> Myth 10: "Wine is for Intel x86 only"
Well, it is true that Wine only runs on Intel's x86 processors. Unfortunately it will also require quite a lot of work before it runs on other processor architectures.


when will wine expand?

---

### Post by Kateikyoushi on 2006-10-16
Yes, all AMD processors are also X86 processors the 64 bit versions are called "X86-64".

---

### Post by pelle.k on 2006-10-16
Yes. x86 is a processor architecture. AMD manufactures x86 cpu:s. PPC is another architecture (apple G3 G4 etc.)

---

### Post by TheRingmaster on 2006-10-16
Is that still true then?

---

### Post by .t. on 2006-10-16
It will be true as long as the Win32 API binaries are 32-bit for x86. This won't change ever, and as we see more 64-bit binaries, they will be using Win64. Then, WINE will run on 64-bit x86-64 CPUs. It won't ever run on anything else (unless there is a new Windows CPU architechture to be supported), as binaries are just that, binary. Closed source apps are impossible to port, and so won't run on anything except the architecture they were compiled for. Even if their API can run there. When Windows runs on PowerPC, you'll see Wine running on PowerPC. As in the name, WINE is *not* an emulator.

---

