---
title: "kernel build cpu utilization"
date: 2024-01-10
forum: Ubuntu Development Version
---

### Post by carbonbased80 on 2024-01-10
Not sure if this is the right sub-forum, but there doesn't appear to be one specific to kernel builds.

I'm building kernels from jammy and lunar currently, on a 48 core system, and I'm finding, when building a kernel from, for example; git://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/lunar, that the build, by default, is done in parallel, but the CPU utilization is considerably lower than if I were to `make -j48` on a stock Linux build from kernel.org.

I definitely realize that the Ubuntu kernel build is building more; it's compiling the apps, and generating debians for various things, but I was surprised to see many of the cores being only 10-30% utilized.

I'm wondering if there are ways to increase the number of parallel tasks for the build, or other techniques to better utilize the CPU cores at hand?

Thanks,
Jeff

---

### Post by TheFu on 2024-01-10
If you aren't CPU bound, then check for other limits, like being RAM or I/O bound.
Until the core libraries are built, there are dependencies that have to be solved/built before anything else can be built too.

---

