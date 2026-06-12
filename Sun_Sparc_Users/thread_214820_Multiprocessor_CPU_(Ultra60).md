---
title: "Multiprocessor CPU (Ultra60)"
date: 2006-07-13
forum: Sun Sparc Users
---

### Post by recupero on 2006-07-13
Hi!
My Ultra60 biprocessor runs in single-processor mode with Ubuntu.
I tried compiling the kernel with SMP enabled,#CPU=2.
Is this the correct way to handle 2 processors?

---

### Post by netztier on 2006-07-13
> **recupero said:**
> 
Is this the correct way to handle 2 processors?

This is of course the correct way to go if you like to push your piano to your chair, as we say. ;-) Of course it gets the job done, but there's less complicated ways.

Simply [installing the SMP Kernel]("http://www.ubuntuforums.org/showthread.php?p=982848#post982848") might also have worked. Please read the linked thread, you'll see how to tell if you have SMP enabled or not. The information I gave in that thread referred to the Ubuntu 6.06-beta days when "Ubuntu 6.06 LTS for SPARC" was not yet available.

However - If I am not mistaken - the server-kernels the way they come with the [Ubuntu-server install CDs ]("http://releases.ubuntu.com/6.06/")(such as the **SPARC server install CD**) already have SMP support built-in.

kind regards

Marc

---

### Post by Sproggit on 2006-12-03
Tru # CPU = 4 (or 3, actually)
For some odd reason your second CPU is identified as no. 2 (and the first as no. 0.

The Sproggg

---

