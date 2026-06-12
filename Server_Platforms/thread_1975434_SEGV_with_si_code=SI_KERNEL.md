---
title: "SEGV with si_code=SI_KERNEL"
date: 2012-05-07
forum: Server Platforms
---

### Post by coleenp on 2012-05-07
The Hotspot JVM has started crashing with a SEGV in code that seems reasonable with the si_code=SI_KERNEL, addr=0.  We think it's a bug in ubuntu, but we seem to be triggering it somehow.   Google searches have been fruitless.    Can someone give us some clues why ubuntu is blasting us with these signals?   This is fairly easy to reproduce.

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x00000000

Registers:
EAX=0x8e2d4b28, EBX=0xa7ede248, ECX=0xa7ede248, EDX=0xa7eebdb0
ESP=0xb77cca20, EBP=0xb77ccd4c, ESI=0xa7eebdb0, EDI=0xa7e4f418
EIP=0xb1a0cdbf, EFLAGS=0x00010206, CR2=0x00000004


The registers all point to legitimate memory addresses (don't know about EFLAGS and CR2).

We have these versions of ubuntu:
2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 i686 GNU/Linux

thanks,
Coleen

---

