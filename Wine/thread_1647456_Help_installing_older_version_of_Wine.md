---
title: "Help installing older version of Wine"
date: 2010-12-17
forum: Wine
---

### Post by vtcat on 2010-12-17
I have a program (TimeMatters 4.0) which did run in an older version of wine a year or two ago when I tested it under (I think) Ubuntu 8.04 with a pre-1.0 wine.  It will not run under 10.10 with wine 1.2.  I know that the AppDB says TM4.0 garbage, but that TM7.0 ran under Feisty with wine 0.9.41.

I'm trying to install wine 0.9.41 under 10.10, but have never compiled from source and am getting errors, specifically:
freetype.c:163: error: ‘FT_MulFix’ undeclared here (not in a function)
freetype.c:163: warning: type defaults to ‘int’ in declaration of ‘pFT_MulFix’
freetype.c: In function ‘WineEngGetOutlineTextMetrics’:
freetype.c:4001: error: called object ‘pFT_MulFix’ is not a function


followed by
make[2]: *** [freetype.o] Error 1
make[2]: Leaving directory `/home/mike2/Downloads/wine-0.9.41/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/mike2/Downloads/wine-0.9.41/dlls'
make: *** [dlls] Error 2

I can post the full output from the terminal of the make/install process if there might be more information in there.  In the alternative, is there anywhere to find the compiled binaries for pre-1.0 versions of wine?

Thanks in advance for any help.

---

### Post by marl30 on 2010-12-17
Use PlayonLinux. It's better for working with multiple/older versions of Wine.

---

