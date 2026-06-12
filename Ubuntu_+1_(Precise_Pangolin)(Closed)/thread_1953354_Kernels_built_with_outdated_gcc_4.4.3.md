---
title: "Kernels built with outdated gcc 4.4.3"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-04-06
Looking at kern.log, i'm surprised to see that kernels, even the latest, are still built with an outdated gcc release :

Linux version 3.4.0-999-generic-pae (apw@gomeisa) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #201204050406 SMP Thu Apr 5 08:21:51 UTC 2012

should not be built with a more recent version like 4.6 ?

hm, maybe an explanation : ubuntu gcc bugs dont get much attention
[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bugs?field.status%3Alist=NEW&orderby=-date_last_updated&start=0](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bugs?field.status%3Alist=NEW&orderby=-date_last_updated&start=0)

so still using the 4.4 branch with some patches for security.

---

### Post by chrisccoulson on 2012-04-06
The default kernel is built with the default toolchain. The issue is that you are using a non-standard kernel

---

### Post by dino99 on 2012-04-06
Hope we get LLVM/clang soon, for better compilation and less errors

---

### Post by Bobhuber on 2012-04-06
> **dino99 said:**
> Hope we get LLVM/clang soon, for better compilation and less errors
+1 - I've got a new FX processor and can't take advantage of the newest cflags.

---

### Post by dino99 on 2012-04-06
> **Bobhuber said:**
> +1 - I've got a new FX processor and can't take advantage of the newest cflags.

sadly its not ready on linux kernel but arm actually; might need a few more months to see it on x86

---

