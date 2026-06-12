---
title: "stack execution protection and randomization"
date: 2009-02-09
forum: Security
---

### Post by numanahsan on 2009-02-09
Hi all, 

As part of a course assignment i need to write an exploit code to cause a buffer overflow and execute code that is present on stack.

I have turned off the stack randomiztion by the following command:
sysctl -w kernel.randomize_va_space=0
However, i am unable to find a way to turn off the stack execution protection. I am not sure whether there is some stack exec protection in ubuntu or not... so my first question is whether there is something like red hat's exec-shield in ubuntu 8.10 and if there is, how can we turn it off.

I have been trying to cause a buffer overflow and execute instruction from stack, but whenever i try to do so, it gives me a seg fault.

i ve got ubuntu 8.10 64 bit, HOWEVER, the program im debugging is compiled on an i386 machine with stack protection turned off.

Regards,
Numan

---

### Post by numanahsan on 2009-02-09
I have found the solution on another forum.
in order to make the stack of a program executable, you have to set the executable stack flag in the elf binaries. execstack can be used to do this. check out the following link:
[http://pwet.fr/man/linux/administration_systeme/execstack](http://pwet.fr/man/linux/administration_systeme/execstack)

---

### Post by bodhi.zazen on 2009-02-09
Thread closed. We do not support this kind of activity, either posting home work questions (these questions were given to you to solve ;) ) not cracking.

As you can see there are other sites that you may find helpful in those regards.

---

