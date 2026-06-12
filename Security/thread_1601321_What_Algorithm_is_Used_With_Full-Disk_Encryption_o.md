---
title: "What Algorithm is Used With Full-Disk Encryption on Ubuntu?"
date: 2010-10-20
forum: Security
---

### Post by 0RaulDuke0 on 2010-10-20
For some reason I can't find any documentation re: the algorithm(s) used by Ubuntu to encrypt the filesystem... Anyone know what it is?? AES?

---

### Post by HermanAB on 2010-10-20
Aes256, cbc, essiv, sha256.

---

### Post by rookcifer on 2010-10-21
AES-cbc-essiv is the default, but you can choose whatever you want to use (whatever the kernel allows).  I know you can use Serpent and Twofish for sure (and others as well iirc).  Newer kernels also support XTS mode which is preferred over cbc (XTS is a new standard).

---

