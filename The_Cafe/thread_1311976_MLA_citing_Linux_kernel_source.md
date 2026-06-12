---
title: "MLA citing Linux kernel source"
date: 2009-11-02
forum: The Cafe
---

### Post by kevstar31 on 2009-11-02
I am working on a research paper and i want to use a quote from help text in the Linux configuration options.
> If this option is disabled, you allow userspace (root) access to all of memory, including kernel and userspace memory. Accidental access to this is obviously disastrous, but specific access can be used by people debugging the kernel. Note that with PAT support enabled, even in this case there are restrictions on /dev/mem use due to the cache aliasing requirements.

If this option is switched on, the /dev/mem file only allows userspace access to PCI space and the BIOS code and data regions. This is sufficient for dosemu and X and all common users of /dev/mem.

If in doubt, say Y.
[http://cateee.net/lkddb/web-lkddb/STRICT_DEVMEM.html](http://cateee.net/lkddb/web-lkddb/STRICT_DEVMEM.html)

Would this work?:
> Torvalds, Linus et.al. "CONFIG_STRICT_DEVMEM:Filter Access to /dev/mem." Linux Kernel. 2:6:27(9 Oct 2008). Linux Kernel Driver Database.

---

