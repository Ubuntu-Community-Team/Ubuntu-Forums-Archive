---
title: "File size discrepancy"
date: 2009-02-20
forum: Server Platforms
---

### Post by uvdevnull on 2009-02-20
I have a few sparse image files, but they're identified as having different size based on which command is used:

```

[devvm1: /home/xen/domains/devmail1.eadev]$ du -ah
1.4G    ./disk.img
40K     ./swap.img

```
```

[devvm1: /home/xen/domains/devmail1.eadev]$ ls -lRh
total 1.4G
-rw-r--r-- 1 root root  40G 2009-02-20 10:32 disk.img
-rw-r--r-- 1 root root 1.0G 2009-02-18 11:14 swap.img

```
Why the discrepancy of 'du' showing actual size and 'ls' showing the maximum possible size of the sparse image file?  Even 'ls' itself seems confused, reporting a total of 1.4G (which is correct) but the individual file sizes at their maximum capacity.

---

### Post by kidders on 2009-02-22
Hi there,

You're mixing two definitions of "size". (There are quite a few!) One possible definition is the number of bytes that can be read before reaching the end of a file (displayed by **ls**). Alternatively, you could say the answer is the number of blocks occupied by a file, multiplied by the block size (displayed by **du**).

Put another way, one describes size in terms of the distance between the beginning and the end of a file; the other in terms of the amount of space that cannot now be used by other files. Neither is a particularly good definition of the size of a sparse file.

I hope that helps.

---

### Post by uvdevnull on 2009-02-24
It does, thanks.  Very clear and concise explanation.

---

