---
title: "Need i686 Linux ISO"
date: 2018-07-31
forum: Virtualisation
---

### Post by kkgaming1234 on 2018-07-31
I have tried the Ubuntu amd64.iso and the i386.iso but i can't find a 32-bit iso that works with virtualbox, (I am trying to emulate Ubuntu 14.04.5 and 16.04, I don't mind)
When I run the amd64.iso it says it can only run on x86 and x64 processors and only found an i686
and when I run the i368.iso it says pae

I use a Pentium(R) Dual-Core CPU E5300 @ 2.60GHz, (2 Cores) processor
(In case you need that)

if anyone could tell me a solution, or link me an i686 iso that would be great!

---

### Post by Tadaen_Sylvermane on 2018-07-31
You can choose 32 or 64bit in virtualbox. Limitation is that for 64 bit you need to be running 64bit host.

---

### Post by ajgreeny on 2018-07-31
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

What do you mean by this sentence in your post?
> and when I run the i368.iso it says pae
Does it say that you need a pae CPU?

---

### Post by MoebusNet on 2018-07-31
In Virtualbox, you need to enable PAE (Settings>System>Processor>Extended Features: Enable PAE/NX - check the box) for 32-bit to be able to boot. On actual hardware, you will need the 'forcepae -- forcepae' boot option if you are running a PENTIUM-M that does not advertise its PAE  capability due to Intel's firmware bug.

---

