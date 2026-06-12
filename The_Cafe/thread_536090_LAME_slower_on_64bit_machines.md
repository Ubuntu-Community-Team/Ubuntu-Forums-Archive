---
title: "LAME slower on 64bit machines?"
date: 2007-08-27
forum: The Cafe
---

### Post by PatrickMay16 on 2007-08-27
Hey guys, I have a computer with an AMD64 processor, but I run the 32 bit version of ubuntu for convienience. Though today, I got the 64bit feisty CD, and went and tested a few programs to see if they would be quicker.
I got some interesting results.

Oggenc, encoding a particular file on my 32bit install, takes around 21 seconds. Now, in the 64bit liveCD, oggenc encoded the same file in 14 seconds; an incredible performance increase. 

But Lame, encoding this file on my 32bit install took 21 seconds, while on the 64bit liveCD it took 23 seconds... a performance decrease. 

Does anyone know why this is?

---

### Post by Andrewie on 2007-08-27
are they both on a live-cd?

---

### Post by xzero1 on 2007-08-27
FWIW: You are running in 64-bit mode. Running 32 bit applications in 64-bit mode is probably less efficient due to the encoding of 32 bit instructions in the 64 bit mode.
In other works 64 bit mode is optimized more for 64 bit work. The faster encoding may be due to it being a 64-bit application.

---

### Post by PatrickMay16 on 2007-08-27
> **Andrewie said:**
> are they both on a live-cd?

Nah, only the 64bit system was a liveCD. The 32bit system is the one I have installed on the hard disk.

---

### Post by stmiller on 2007-08-27
This is true, lame is faster on 32bit machines, even when comparing to a compiled 64bit binary.

LAME is optimized for certain 32bit goodies which do not have 64bit counterparts (nasm, in particular). So compiling LAME under 64bit while makes a 64bit binary, does not take advantage of any 64bit goodness.

LAME 4 is a rewrite for 64bit and smp and is in the works by one of the LAME devs.

---

