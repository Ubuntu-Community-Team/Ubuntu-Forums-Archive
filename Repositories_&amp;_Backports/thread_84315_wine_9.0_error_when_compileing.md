---
title: "wine 9.0 error when compileing"
date: 2005-10-30
forum: Repositories &amp; Backports
---

### Post by brykn on 2005-10-30
Hello,
I was installing wine 9.0 and ran into a problem.

gcc -c -I. -I. -I../../include -I../../include -I/usr/X11R6/include -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith -g -O2 -o bitblt.o bitblt.c
bitblt.c:27:27: X11/Intrinsic.h: No such file or directory
bitblt.c: In function `BITBLT_InternalStretchBlt':
bitblt.c:1334: error: `pixel' undeclared (first use in this function)
bitblt.c:1334: error: (Each undeclared identifier is reported only once
bitblt.c:1334: error: for each function it appears in.)
bitblt.c:1334: error: syntax error before "xor_pix"
bitblt.c:1337: error: `xor_pix' undeclared (first use in this function)
make[2]: *** [bitblt.o] Error 1
make[2]: Leaving directory `/home/kyle/wine-0.9/dlls/x11drv'
make[1]: *** [x11drv] Error 2
make[1]: Leaving directory `/home/kyle/wine-0.9/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

Can anyone help me?
thank you for your time.

---

### Post by traherom on 2005-10-31
Is it from CVS, or is it the regular download?

---

### Post by No6 on 2005-10-31
Is there a particular reason for compiling? The deb for breezy is available here : [http://wine.sourceforge.net/apt/breezy/wine_0.9.0-winehq-1_i386.deb]("http://wine.sourceforge.net/apt/breezy/wine_0.9.0-winehq-1_i386.deb")

Oh, It looks like you haven't got the xorg dev files installed.

---

