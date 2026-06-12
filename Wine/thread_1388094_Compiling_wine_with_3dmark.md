---
title: "Compiling wine with 3dmark"
date: 2010-01-22
forum: Wine
---

### Post by logiq on 2010-01-22
Hey,

I'm trying to compile Wine with 3dmark as explained here: [http://www.fsckin.com/2008/02/21/how-to-run-call-of-duty-4-cod4-modern-combat-in-linux/](http://www.fsckin.com/2008/02/21/how-to-run-call-of-duty-4-cod4-modern-combat-in-linux/)

I receive this error:

```

reetype.c:166: error: ‘FT_MulFix’ undeclared here (not in a function)
freetype.c:166: warning: type defaults to ‘int’ in declaration of ‘pFT_MulFix’
freetype.c: In function ‘WineEngGetOutlineTextMetrics’:
freetype.c:4425: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4426: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4428: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4436: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4436: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4440: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4444: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4520: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4521: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4522: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4523: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4524: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4525: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4526: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4527: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4528: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4533: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4534: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4535: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4536: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4537: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4538: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4539: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4540: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4541: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4542: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4547: error: called object ‘pFT_MulFix’ is not a function
freetype.c:4548: error: called object ‘pFT_MulFix’ is not a function
make[2]: *** [freetype.o] Error 1
make[2]: Leaving directory `/home/thomas/wine/wine-0.9.56/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/thomas/wine/wine-0.9.56/dlls'
make: *** [dlls] Error 2

```

So I googled around a found another patch to fix this. It looks like this:

```

diff --git a/dlls/gdi32/freetype.c b/dlls/gdi32/freetype.c 
index cb351db..74e70ea 100644 
--- a/dlls/gdi32/freetype.c 
+++ b/dlls/gdi32/freetype.c 
@@ -163,7 +163,11 @@ MAKE_FUNCPTR(FT_Get_Sfnt_Table); 
 MAKE_FUNCPTR(FT_Init_FreeType); 
 MAKE_FUNCPTR(FT_Load_Glyph); 
 MAKE_FUNCPTR(FT_Matrix_Multiply); 
+#ifdef FT_MULFIX_INLINED 
+#define pFT_MulFix FT_MULFIX_INLINED 
+#else 
 MAKE_FUNCPTR(FT_MulFix); 
+#endif 
 MAKE_FUNCPTR(FT_New_Face); 
 MAKE_FUNCPTR(FT_New_Memory_Face); 
 MAKE_FUNCPTR(FT_Outline_Get_Bitmap); 
@@ -2434,7 +2438,9 @@ static BOOL init_freetype(void) 
     LOAD_FUNCPTR(FT_Init_FreeType) 
     LOAD_FUNCPTR(FT_Load_Glyph) 
     LOAD_FUNCPTR(FT_Matrix_Multiply) 
+#ifndef FT_MULFIX_INLINED 
     LOAD_FUNCPTR(FT_MulFix) 
+#endif 
     LOAD_FUNCPTR(FT_New_Face) 
     LOAD_FUNCPTR(FT_New_Memory_Face) 
     LOAD_FUNCPTR(FT_Outline_Get_Bitmap)

```

I try to patch it with this command line: "patch -p1 < patch.diff", but all I get is this:

```

patching file dlls/gdi32/freetype.c
Hunk #1 FAILED at 163.
Hunk #2 FAILED at 2438.
2 out of 2 hunks FAILED -- saving rejects to file dlls/gdi32/freetype.c.rej

```

Any ideas?

Thanks in advance.

---

### Post by beastrace91 on 2010-01-22
Have you tried running COD4 under the latest Wine (1.1.36) unpatched? That guide you link to is more than a little old (from 2008 - which is forever and a half ago in Wine years) - it details the for use with Wine 0.9.56 (older than the stable beta)

Regards,
~Jeff

---

