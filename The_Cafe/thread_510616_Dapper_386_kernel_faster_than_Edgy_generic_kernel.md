---
title: "Dapper 386 kernel faster than Edgy generic kernel?"
date: 2007-07-26
forum: The Cafe
---

### Post by PatrickMay16 on 2007-07-26
Hey guys, I'm running an Athlon64 3800+ with Edgy which I just upgraded from dapper.
I did a test before upgrading, where I was using the latest 386 kernel for dapper. I encoded a particular file using oggenc with these options: "-q 5".  The result was, the file encoded in 21.6 seconds.
Then after upgrading to edgy I installed the 'generic' kernel, because I'm soon going to be replacing the current processor with a dual core one and need an SMP kernel. 
The result is, this kernel (2.6.17-12-generic) encoded the same file at 22.6 seconds, a whole second slower than before.

Why is this?

---

### Post by thisllub on 2007-07-26
Do it a dozen times.

---

### Post by reacocard on 2007-07-26
> **PatrickMay16 said:**
> Hey guys, I'm running an Athlon64 3800+ with Edgy which I just upgraded from dapper.
I did a test before upgrading, where I was using the latest 386 kernel for dapper. I encoded a particular file using oggenc with these options: "-q 5".  The result was, the file encoded in 21.6 seconds.
Then after upgrading to edgy I installed the 'generic' kernel, because I'm soon going to be replacing the current processor with a dual core one and need an SMP kernel. 
The result is, this kernel (2.6.17-12-generic) encoded the same file at 22.6 seconds, a whole second slower than before.

Why is this?

SMP kernels are always a little slower on non-SMP hardware.

---

### Post by PatrickMay16 on 2007-07-26
> **thisllub said:**
> Do it a dozen times.

Yeah, I did that both times around. The result was always 21.6 for the first, and 22.6 for the second.

> 
SMP kernels are always a little slower on non-SMP hardware.

Ah, I get you. Thanks.

---

