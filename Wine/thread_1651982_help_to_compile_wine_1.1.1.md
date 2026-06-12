---
title: "help to compile wine 1.1.1"
date: 2010-12-24
forum: Wine
---

### Post by gufide on 2010-12-24
I need to compile wine 1.1.1 but I've go a build error:
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
make[2]: Leaving directory `/home/master/wine-1.1.1/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/master/wine-1.1.1/dlls'
make: *** [dlls] Error 2
```

someone can help me?

---

### Post by marl30 on 2010-12-24
If you need that specific version of Wine to run a particular program, you could actually use PlayonLinux and download and assign the Wine version you need. 

The first thing you do when you run PlayonLinux... go to Tools > Manage Wine Versions. You will see a list with all of the available versions of Wine ever made. Download the version you want. After it has been downloaded, close the Tools menu. Then click on install. Go down to the bottom left and choose this: install a .pol or unsupported application. Then you choose Manual installation from the menu it brings up. Click next. Choose install a program in a new prefix. Give the prefix a name. Press next. Then check to assign Wine version and configure Wine (if you need to pre-set Wine's configuration). Click next. It will then asked you which Wine version you want to use. Select the version you downloaded, which would be 1.1.1. Then everything else from there on is pretty much straightforward. Hope this helps.

---

### Post by gufide on 2010-12-24
thank you but I need to patch it so I need to compile it

---

### Post by gufide on 2010-12-25
bump

---

### Post by gufide on 2010-12-26
no one know how to compile wine 1.1.1?

---

