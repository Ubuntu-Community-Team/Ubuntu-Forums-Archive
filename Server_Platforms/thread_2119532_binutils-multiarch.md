---
title: "binutils-multiarch"
date: 2013-02-24
forum: Server Platforms
---

### Post by asdf32 on 2013-02-24
Hi,
I've installed binutils-multiarch under Ubuntu Server 12.04 and found that it doesn't seem to provide that many other architectures.  I'm trying to build Xen-efi and so need i386pep, but the default list after installing it is just:

```
Supported emulations: elf_x86_64 elf32_x86_64 elf_i386 i386linux elf_l1om elf_k1om

```

I downloaded the source package in order to try and add that support, adding in the x86_64-pep flag to configure, but the same thing happened.  It appears that there is another version of ld created during the package build, in builddir-multi/ld/.libs/ld-new, which is genuinely multiarch:
```

Supported emulations: elf_x86_64 elf32_x86_64 elf_i386 i386linux elf_l1om elf_k1om elf64_ia64 elf64alpha alpha armelf_linux armelf armelfb armelfb_linux armelf_linux_eabi armelfb_linux_eabi hppalinux elf32btsmip elf32ltsmip elf32btsmipn32 elf64btsmip elf32ltsmipn32 elf64ltsmip elf32ppclinux elf32ppc elf32ppcsim elf64ppc elf_s390 elf64_s390 elf32_sparc sparclinux elf64_sparc sun4 elf_i386_fbsd i386bsd elf_x86_64_fbsd elf_l1om_fbsd elf_k1om_fbsd i386pep i386pe m32relf_linux m68kelf m68klinux shlelf32_linux shelf32_linux shlelf_linux shelf_linux elf32_spu

```

If I manually copy this version into place I'm able to build xen.efi (yet to try booting from it though!)  

Am I missing something?  Is there some flag you need to specify when installing binutils-multiarch to get the version with more support?

---

