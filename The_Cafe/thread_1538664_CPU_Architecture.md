---
title: "CPU Architecture"
date: 2010-07-25
forum: The Cafe
---

### Post by redfox1160 on 2010-07-25
Hello,

I was looking at Arch Linux and went to the downloads page. I wanted to put it on a 32-bit computer, but I am not sure of the architecture of the CPU. I thought it was i386, but I don't know. On the [Arch Linux website]("http://www.archlinux.org/download/") there is only i686, x86-64, and Dual Architecture. I am not sure which one I would choose (or if I could even choose one). Can anyone explain to me how i686, i386, x86, and x64 are different; and which one I would use? Thanks.

---

### Post by Barrucadu on 2010-07-25
Any 32-bit processor newer than a Pentium Pro is i686, i386 is a really ancient (1985) 32-bit architecture. Infact, IIRC, gcc can't even compile i386-compatible binaries any more, as it uses i486 instructions - though I could be completely wrong on that.

x86_64 (or amd64) is, as I'm sure you guessed, the architecture used by most 64-bit systems. It's backwards compatible with 32-bit, so you can run 32-bit stuff on a 64-bit system. There are, however, other 64-bit architectures which Linux can be run on such as ia64, but they aren't commonly used (for the desktop market, at least).

The dual architecture image can be run on both 32- and 64-bit systems. I've never used it, but I assume it detects the architecture of your CPU and installs the appropriate Arch variant for you.

---

### Post by blueturtl on 2010-07-25
The x86 endings refer to the lineage of Intel processors.

The earlier generation CPUs are as follows:

8088
8086
80286
80386 (i386 stands for this chip, as it's the first 32-bit Intel CPU)
80486
80586 (also known as Pentium)
80686 (Pentium PRO / Pentium II)

Anyway, all CPUs starting with the 80386 are 32-bit so what i386 means really is that you must have at least a 386 to run. i686 means Pentium Pro and newer systems.

x64 means Intel's Itanium architecture which is very rare in home systems.
AMD64 means 64-bit desktop CPUs starting with the Athlon64 or Intel Core-series CPUs.

---

