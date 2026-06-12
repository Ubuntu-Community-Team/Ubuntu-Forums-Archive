---
title: "Buffer Overflow Protection."
date: 2007-06-08
forum: Server Platforms
---

### Post by Glich on 2007-06-08
Hi, I was wandering, is buffer overflow an issue in Ubuntu? If so, what buffer overflow protection methods does Ubuntu implement out of the box?

I have heard of a method which encrypts all the instructions inside a program in memory before it begins to execute. Then the instructions are decrypted before execution. The encryption is routine is random and changes at each reboot. This would prevent shell code from executing and therefore buffer overflow attacks from happening.

Have you heard of a similar method?

Thanks.

---

### Post by Mr. C. on 2007-06-08
Every program that uses memory has the potential for a buffer overflow.  It is the nature of programming to request / specify a chunk of memory to be used for internal operations.  If the programmer is not careful and does not bounds check or limit access to that chunk, you have a buffer overflow situation which might be exploitable.

MrC

---

