---
title: "Linux Kernel"
date: 2008-09-20
forum: The Cafe
---

### Post by bigbear2350 on 2008-09-20
What type of kernel is the linux kernel?

---

### Post by OutOfReach on 2008-09-20
AFAIK it's monolithic

---

### Post by dje on 2008-09-20
yes it is a monolithic kernel - [wikipedia article]("http://en.wikipedia.org/wiki/Linux_kernel")

dje

---

### Post by Steveway on 2008-09-20
Go to wikipedia: [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)
EDIT: dje beat me to it.

---

### Post by Lostincyberspace on 2008-09-20
> **bigbear2350 said:**
> What type of kernel is the linux kernel?


The Linux kind.
:lolflag::lolflag::lolflag::lolflag::lolflag:  :lolflag::lolflag::lolflag:

---

### Post by Prospero2006 on 2008-09-20
It's not monolithic.
It's modular.

Windows is monolithic.


That's right isn't it?

---

### Post by FuturePilot on 2008-09-20
> **Prospero2006 said:**
> It's not monolithic.
It's modular.

Windows is monolithic.


That's right isn't it?

No, Linux is a monolithic kernel.
[http://en.wikipedia.org/wiki/Monolithic_kernel]("http://en.wikipedia.org/wiki/Monolithic_kernel")

---

### Post by insane_alien on 2008-09-20
No, the linux kernel is definitely monolithic. all the subprocesses run in the main kernel thread which is the definition of monolithic kernels.

the monolithicness does not depend on how many modules/files parts of the kernel are stored in.

---

### Post by earthpigg on 2008-09-20
> **bigbear2350 said:**
> What type of kernel is the linux kernel?

its like popcorn kernels, but it feeds your soul and not your stomach.

---

### Post by david_lynch on 2008-09-20
> **FuturePilot said:**
> No, Linux is a monolithic kernel.
[http://en.wikipedia.org/wiki/Monolithic_kernel]("http://en.wikipedia.org/wiki/Monolithic_kernel")

No, windoze nt and later are supposedly a "microkernel" design.

Linux is a monolithic, modular kernel.

---

### Post by xArv3nx on 2008-09-20
> **david_lynch said:**
> No, windoze nt and later are supposedly a "microkernel" design.

Linux is a monolithic, modular kernel.
i thought windows and mac os x had a hybrid kernel.

---

### Post by earthpigg on 2008-09-20
> **xArv3nx said:**
> i thought windows and mac os x had a hybrid kernel.

os x = unix = monolithic

right? ;)

---

### Post by mc4100 on 2008-09-20
> **Prospero2006 said:**
> It's not monolithic.
It's modular.

Windows is monolithic.


That's right isn't it?

It is monolithic. Possibly related:
[http://en.wikipedia.org/wiki/Loadable_Kernel_Module](http://en.wikipedia.org/wiki/Loadable_Kernel_Module)

---

### Post by Prospero2006 on 2008-09-20
> **FuturePilot said:**
> No, Linux is a monolithic kernel.
[http://en.wikipedia.org/wiki/Monolithic_kernel]("http://en.wikipedia.org/wiki/Monolithic_kernel")

I'm glad I got that fact straight then.

Thanks,

---

### Post by snova on 2008-09-20
Linux is technically monolithic, since most of the drivers are built in. But it's modular at the same time, since a good many can also be separated.

If the definition of a microkernel is one where drivers are processes, then Linux is monolithic no matter how you look at it. But if by "micro" you mean "split into pieces", then it fits in both categories.

OS X is built on Mach, AFAIK, which is a microkernel.

As far as Windows goes, Microsoft says that it's a "hybrid", but a look at Wikipedia shows that for the most part, it's monolithic. It appears as though it has similar driver loading capabilities as Linux does, though.

---

