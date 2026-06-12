---
title: "Make Kernel DPKG's on CentOS Host?"
date: 2011-12-26
forum: Server Platforms
---

### Post by WinstonChurchill on 2011-12-26
Here's the deal: I use upstream kernels for several computers (running Ubuntu). I want to compile these on a 24-core Xenon server I have access to. Problem is, the server is running CentOS, and I don't have root access (so KVM is out of the question). I could compile the kernel, then copy it back down and run make-kpkg, but a compiled kernel tree with git data is like 5GB, so that ends up taking longer. So, basically I want to somehow make the kernel packages on the CentOS server.

Any ideas?

---

