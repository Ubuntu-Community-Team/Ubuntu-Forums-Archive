---
title: "Stack execution protection?"
date: 2009-11-27
forum: Security
---

### Post by 0xeb on 2009-11-27
Hello

I am new to Linux and Ubuntu and have some questions regarding stack 
execution protection.

I was working with Ubuntu 7, and have something like this in my program:

say, EIP=080484B5
and ESP=BF82F4F0
@eip: jmp esp

Under GDB I get an exception and the exception address is @ esp

Now in Ubuntu 9, x86:

@eip: jmp esp

Under GDB I get an exception and the exception address is @ eip !

Can someone tell me where I can read more about this mechanism? what program 
enforces this protection and why Ubuntu 7 reports the exception @ esp and 
Ubuntu 9 @ eip.

Please advise.

--
Elias

---

### Post by __p1n__ on 2009-11-27
Start here [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/) and go through the changelogs.

---

