---
title: "When will Nvidia support 64-bit BSD?"
date: 2009-12-26
forum: The Cafe
---

### Post by Dark Aspect on 2009-12-26
Hello,

Does anyone know if Nvidia will every support a 64-bit BSD based kernel? Its seems unfair, their web site offers 64-bit Linux, Windows and Solaris drivers. This leaves FreeBSD and PC-BSD users out in the cold IMO, especially if they have more than 4 GB of RAM.

---

### Post by Bachstelze on 2009-12-26
They do since version 195.22 of the drivers (works on FBSD 8 only).

---

### Post by Dark Aspect on 2009-12-26
> **Bachstelze said:**
> They do since version 195.22 of the drivers (works on FBSD 8 only).

Great, um so do I just select x86 or can you give me a link to the 64-bit drivers? Or can get that via BSD's pkg_add repositories?

Nvidia's web site only shows x86.

---

### Post by Bachstelze on 2009-12-26
[ftp://download.nvidia.com/XFree86/FreeBSD-x86_64/195.22/](ftp://download.nvidia.com/XFree86/FreeBSD-x86_64/195.22/)

The 195.22 drivers are beta, I guess that's why they aren't on the main site. The README is also not accurate, it's basically a copypasta of the x86 one...

---

