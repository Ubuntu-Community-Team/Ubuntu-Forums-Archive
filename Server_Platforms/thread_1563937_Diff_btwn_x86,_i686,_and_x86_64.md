---
title: "Diff btwn x86, i686, and x86_64"
date: 2010-08-29
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-29
Hi friends!. I need help on the following things:

1) Differences between x86, i686, and x86_64
2) How to check if the processor is of 32 bit or 64 bit on Ubuntu
3) How to check if operating system(ubuntu) is of 32 bit or 64 bit



Thanks all!

---

### Post by TwoEars on 2010-08-29
I'll simplify things, to make this easier -
i686 is an enhanced version of x86. 
x86 is a 32 bit instruction set, x86_64 is a 64 bit instruction set. Generally, the major difference is the amount of RAM that's addressable - under 32 bit, the limit is about 3.4GBs, under 64 bit, it's much higher. You can extend the 32 bit limit via PAE(which is actually 36 bits)


To check if a processor is 64 bit(most, if not all, modern ones are), you need to run ```
grep lm /proc/cpuinfo
```, if it returns something, then you can use 64 bit software.

```
uname -a
``` will tell you if it's 32 bit or 64 bit, on the bit on the end.

---

### Post by anchise on 2010-08-29
Two Ears already said it all, but if you want to read a bit into this topic, try the wikipedia article on ISA (instruction set architecures). [http://en.wikipedia.org/wiki/Instruction_set](http://en.wikipedia.org/wiki/Instruction_set)

---

### Post by Thyagaraj on 2010-08-30
Thank you! 
TwoEars simplified the confusion but the one. To check if my processor is of 32 bit or 64 bit, I used "grep lm /proc/cpuinfo" as you posted. It didn't show any output.
Thanks anchise

---

### Post by TwoEars on 2010-08-30
> **Thyagaraj said:**
> Thank you! 
TwoEars simplified the confusion but the one. To check if my processor is of 32 bit or 64 bit, I used "grep lm /proc/cpuinfo" as you posted. It didn't show any output.
Thanks anchise

In that case, it can't use 64 bit.
You might want to post the output of ```
cat /proc/cpuinfo
``` just in case, though :)

---

### Post by anchise on 2010-08-30
lm in the cpuinfo flags stands for "long mode", which means 64-bit. If you don't have this flag your system is not 64-bit. As grep lm /proc/cpuinfo filters the output of cpuinfo and searches for "lm", this command will yield no result on 32-bit systems as yours.

EDIT: Sorry, I haven't seen that two ears already had answered your question.

---

### Post by Thyagaraj on 2010-09-03
Thanks a lot. It really helped me.

---

