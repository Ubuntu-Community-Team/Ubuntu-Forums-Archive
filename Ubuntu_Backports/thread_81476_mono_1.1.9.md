---
title: "mono 1.1.9"
date: 2005-10-24
forum: Ubuntu Backports
---

### Post by asv on 2005-10-24
Does anyone know if a package exists for mono 1.1.9? Is the only way to currently install it on ubuntu via source?

---

### Post by Farina on 2005-10-24
[QUOTE=asv]Does anyone know if a package exists for mono 1.1.9? Is the only way to currently install it on ubuntu via source?[/QUOTE]

Assuming you are not running the AMD64 release (something that bit me last time on hoary) you can get binaries for the newer monos by adding following repository to your sources.list:

> deb [http://debian.meebey.net/](http://debian.meebey.net/) ./

I have the latest release from this repo.  --version is as follows:
```
mono --version
Mono JIT compiler version 1.1.9.2, (C) 2002-2005 Novell, Inc and Contributors. www.mono-project.com
        TLS:           normal
        GC:            Included Boehm (with typed GC)
        SIGSEGV      : normal
        Globalization: normal

```

---

### Post by bytter on 2005-10-29
You can also get it from the dapper repositories (AMD64 too).

---

### Post by Kyral on 2005-10-29
Its not really suggested to upgrade to Dapper. I made Mono packages in a Breezy PBuilder if anyone wants them (i386 only)

---

