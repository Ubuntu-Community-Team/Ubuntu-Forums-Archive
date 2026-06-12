---
title: "Chrooting into an older Ubuntu version?"
date: 2011-01-11
forum: The Cafe
---

### Post by nerdopolis on 2011-01-11
Hi.

I can't put this into the support fourm as it involves an unsupported version (4.10)

When I try to chroot into Ubuntu 4.10 (as a test case) I get a segmentation fault when I run some apps in it. Such apps like bash and ls.

sh works, and bash does not, and whats weird is if that I try to run Ubuntu 4.10's bash directly it actually WORKS (I would think I would get a library error...) Whats also wierd is that when I chroot with sh, and run ls, ls seems to list the folder, and then prints out "Segmentation fault", and sh also exits.

strace works. The last lines 3 that strace says for running ls is (the line above these is it printing the folder list)
```
munmap(0xb788300, 4096)    = 0
exit_group(0)       = ?
Segmentation fault
```
I was getting another weird error before, which I stopped by passing vdso=0 to the kernel.

Anyone have any experience with chroot not working for older versions? I even tried rbinding /dev /sys and /proc. Is there a kernel option I am missing, or should I be using a different Kernel?

I know 4.10 is an extreme test case...

---

### Post by nerdopolis on 2011-01-13
I guess no one had this experience happen before?

---

### Post by 3Miro on 2011-01-13
Correct me if I am wrong, but didn't 4.10 come with kernel 2.4. Kernel 2.4 and kernel 2.6 are very different animals, it is natural to expect that system tools like bash will not work.

---

### Post by nerdopolis on 2011-01-13
I think its Kernel 2.6.8...

I thought the User mode compatibility was stable as far as the Kernel is concerned... I could be wrong.

---

### Post by nerdopolis on 2011-01-14
sorry for the bump, but does anybody have any ideas?

EDIT: should this be moved to the support forum, even this involves a non-supported version?

---

