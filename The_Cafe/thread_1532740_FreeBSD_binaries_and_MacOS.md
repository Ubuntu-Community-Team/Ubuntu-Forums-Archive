---
title: "FreeBSD binaries and MacOS"
date: 2010-07-16
forum: The Cafe
---

### Post by jerenept on 2010-07-16
Just curious... do FreeBSD binaries run on Mac OS?

Mac OS is based on FreeBSD, according to their website.

---

### Post by ubunterooster on 2010-07-16
I think they would as many UNIX and Linux programs run on MAC OSX with no problem. The _only_ difference* is the GUI




[size=1]*That I know of[/size]

---

### Post by -grubby on 2010-07-16
That doesn't mean it's binary compatible. You can try, but a better bet is [MacPorts](http://www.macports.org/).

---

### Post by Bachstelze on 2010-07-17
> **jerenept said:**
> Just curious... do FreeBSD binaries run on Mac OS?

No.  Only the userspace of OS X is based on FreeBSD, the kernel is not.

---

### Post by schauerlich on 2010-07-17
OS X is POSIX compliant, so a lot of portably-written FreeBSD (and Linux) code will *compile* on OS X. However, they are binary incompatible - OS X uses the [Mach-O](http://en.wikipedia.org/wiki/Mach-o) binary format, and FreeBSD/Linux use [ELF](http://en.wikipedia.org/wiki/Executable_and_Linkable_Format)

---

