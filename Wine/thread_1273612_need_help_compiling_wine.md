---
title: "need help compiling wine"
date: 2009-09-23
forum: Wine
---

### Post by kurosagi on 2009-09-23
just so everyone knows i am still new to ubuntu and wine.  last night i started compiling wine with a couple of game patches.  i got the patches in fine.  when i tried to *./configure *i kept geting errors. i sorted all them out [mainly messed around till *./configure* finished with no error].  so i ran *./configure* and then *make depend*; it went just fine.  then i ran *make* and every time it gave me this at the end:

```
freetype.c:166: error: ‘FT_MulFix’ undeclared here (not in a function)
freetype.c:166: warning: type defaults to ‘int’ in declaration of ‘pFT_MulFix’
freetype.c: In function ‘WineEngGetOutlineTextMetrics’:
freetype.c:5009: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5010: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5012: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5020: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5020: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5024: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5028: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5109: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5110: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5111: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5112: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5113: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5114: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5115: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5116: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5117: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5122: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5123: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5124: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5125: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5126: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5127: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5128: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5129: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5130: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5131: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5136: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5137: error: called object ‘pFT_MulFix’ is not a function
make[2]: *** [freetype.o] Error 1
make[2]: Leaving directory `/home/patrick/wine-1.0.1/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/patrick/wine-1.0.1/dlls'
make: *** [dlls] Error 2

```i need help sorting thiss problem out please

---

### Post by kurosagi on 2009-09-24
after taking time away i found my answer by putting the error message in google. 
i just needed a patch and i started working just fine.  
for those that need it i found it here: [http://www.nabble.com/-PATCH--Adjust-FT_MulFix-function-to-Freetype-cvs-head.-td19287233.html](http://www.nabble.com/-PATCH--Adjust-FT_MulFix-function-to-Freetype-cvs-head.-td19287233.html)

here is a the patch:
```
diff --git **a**/dlls/gdi32/freetype.c b/dlls/gdi32/freetype.c 
**index** cb351db..74e70ea 100644 
--- **a**/dlls/gdi32/freetype.c 
+++ b/dlls/gdi32/freetype.c 
@@ -163,7 +163,11 @@ MAKE_FUNCPTR(FT_Get_Sfnt_Table); 
 MAKE_FUNCPTR(FT_Init_FreeType); 
 MAKE_FUNCPTR(FT_Load_Glyph); 
 MAKE_FUNCPTR(FT_Matrix_Multiply); 
+#ifdef **FT_MULFIX_INLINED** 
+#define pFT_MulFix **FT_MULFIX_INLINED** 
+#else 
 MAKE_FUNCPTR(**FT_MulFix**); 
+#endif 
 MAKE_FUNCPTR(FT_New_Face); 
 MAKE_FUNCPTR(FT_New_Memory_Face); 
 MAKE_FUNCPTR(FT_Outline_Get_Bitmap); 
@@ -2434,7 +2438,9 @@ static BOOL **init_freetype**(void) 
     LOAD_FUNCPTR(FT_Init_FreeType) 
     LOAD_FUNCPTR(FT_Load_Glyph) 
     LOAD_FUNCPTR(FT_Matrix_Multiply) 
+#ifndef **FT_MULFIX_INLINED** 
     LOAD_FUNCPTR(**FT_MulFix**) 
+#endif 
     LOAD_FUNCPTR(FT_New_Face) 
     LOAD_FUNCPTR(FT_New_Memory_Face) 
     LOAD_FUNCPTR(FT_Outline_Get_Bitmap) 
```

---

### Post by Kinst on 2009-10-03
Hey can you help me? I don't know how to apply a patch. I tried adding lines by hand but it still gave me an error:

```
freetype.c:166: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FT_MulFix_i386’
freetype.c:171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘static’
freetype.c: In function ‘AddFontToList’:
freetype.c:1176: warning: implicit declaration of function ‘pFT_New_Face’
freetype.c: In function ‘init_freetype’:
freetype.c:2302: error: ‘ifndef’ undeclared (first use in this function)
freetype.c:2302: error: (Each undeclared identifier is reported only once
freetype.c:2302: error: for each function it appears in.)
freetype.c:2302: error: expected ‘;’ before ‘FT_MulFix_i386’
freetype.c: In function ‘WineEngGetOutlineTextMetrics’:
freetype.c:4849: warning: implicit declaration of function ‘pFT_MulFix’
make[2]: *** [freetype.o] Error 1
make[2]: Leaving directory `/home/mshaw/Desktop/wine-0.9.58/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/mshaw/Desktop/wine-0.9.58/dlls'
make: *** [dlls] Error 2

```

---

