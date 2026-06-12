---
title: "Can Keepass 2 with Mono and Work with Keepass 1 Databases?"
date: 2009-03-27
forum: Security
---

### Post by user2037 on 2009-03-27
Keepass 2.07 beta (portable) works on Ubuntu. However, the stock beta doesn't work with Keepass1 databases because it lacks "KeePassLibC". And my hand-held device only works with Keepass 1 databases.

Does anyone know if it is possible to get KeePassLibC working on Ubuntu? Would Wine help?

Keepassx is nice, but it lacks integration with browsers and the auto-type feature is more limited.

---

### Post by tyangc on 2009-06-09
Hi, 

I have also downloaded the keePass Beta 2.0.7, I can compile and run it in VS2008 on Windows, but I can not import a kdb 1.0 file since the keePasslibc is not included , have you figured out how to do this on ubuntu yet?

Or  there is a separate place I can download keePasslibc project source?

Thank you in advance,

Thomas

---

### Post by tyangc on 2009-06-12
Just figure this out myself:

Put the KeePassLibC32.dll (you can compile the source code of keePass1.16 and get the latest version ) in C:\Windows\System32

But I don't know how to achieve this on a mono platform;)

---

### Post by directhex on 2009-06-12
Is the C library portable? It may take some work to make it compile using gcc on Linux

---

