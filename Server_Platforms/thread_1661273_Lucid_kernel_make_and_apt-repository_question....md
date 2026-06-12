---
title: "Lucid kernel make and apt-repository question..."
date: 2011-01-06
forum: Server Platforms
---

### Post by VMGuy on 2011-01-06
Hi,

I've made my own kernel for Lucid, based on the Maverick backported kernel and I was wondering if there's a better solution for my problem.

I used some patches that modified the kernel header and source files.
When building the kernel (using the Ubuntu build system) I'm getting two header packages:
- linux-headers-2.6.35-22
- linux-headers-2.6.35-22-<my_flavour>

The problem is now that the generic part was build with exactly the same name and version than the original kernel, but as I've patched the header files the content is different.

When I upload these kernel packages to my apt-repository aptitude thinks my package and the original package are the same and installes the generic part from the Ubuntu repository.

My current solution is apt-pinning (giving my repository a higher priority), but I'm not very happy with that.

Does anyone know another solution?
Actually I'd like to move the patched header files to the flavour specific part of the header files, but how?

Any help is appreciated.

Thanks,
VMGuy

---

