---
title: "undefined reference to ..... errors"
date: 2009-04-26
forum: Ubuntu Dev Link Forum
---

### Post by mohamedlabidi on 2009-04-26
Hi,
I'm new developper with c++ under Linux with Eclipse,
my program use FreeImagePlus library to read images.
Although  I write include "FreeImagePlus" , I still have many errors  :


  
g++ -o exe lets_ocr.cpp  
/tmp/ccS3vADI.o: In function `main':
lets_ocr.cpp: (.text+0x484): undefined reference to `fipImage::fipImage(FREE_IMAGE_TYPE, unsigned short, unsigned short, unsigned short)'
lets_ocr.cpp: (.text+0x4a4): undefined reference to `fipImage::load(char const*, int)'
lets_ocr.cpp: (.text+0x4f8 ) : undefined reference to `fipImage::getBitsPerPixel() const'
lets_ocr.cpp: (.text+0x545): undefined reference to `fipImage::getHeight() const'
lets_ocr.cpp: (.text+0x55c): undefined reference to `fipImage::getWidth() const'
lets_ocr.cpp: (.text+0x5df): undefined reference to `fipImage::getScanWidth() const'
lets_ocr.cpp: (.text+0x62c): undefined reference to `fipImage::getScanWidth() const'
lets_ocr.cpp: (.text+0x643): undefined reference to `fipImage::getHeight() const'
lets_ocr.cpp: (.text+0x65a): undefined reference to `fipImage::accessPixels() const'
lets_ocr.cpp: (.text+0x9d9): undefined reference to `fipImage::getBitsPerPixel() const'
lets_ocr.cpp: (.text+0xa5d): undefined reference to `fipImage::getBitsPerPixel() const'
lets_ocr.cpp: (.text+0xcf9): undefined reference to `fipImage::~fipImage()'
lets_ocr.cpp: (.text+0xd15): undefined reference to `fipImage::~fipImage()'

:confused:
Can some one help me please.
thank you in advance.

---

### Post by Namtabmai on 2009-04-26
Those look like linking errors, you need to tell the compiler to link your program to the FreeImage library with something like;

```
-lfreeimage
```

---

### Post by mohamedlabidi on 2009-04-27
Hi,
Thank you for reply, this problem is solved, but I find other errors:

[COLOR=Blue]FreeImagePlus.h:72: warning: data definition has no type or storage class
FreeImagePlus.h:72: error: expected ‘,’ or ‘;’ before ‘fipObject’
FreeImagePlus.h:81: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fipMemoryIO’
FreeImagePlus.h:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fipMultiPage’
FreeImagePlus.h:83: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fipTag’
FreeImagePlus.h:85: warning: data definition has no type or storage class
FreeImagePlus.h:85: error: expected ‘,’ or ‘;’ before ‘fipImage’
FreeImagePlus.h:340: warning: data definition has no type or storage class
FreeImagePlus.h:340: error: expected ‘,’ or ‘;’ before ‘fipMemoryIO’
FreeImagePlus.h:374: warning: data definition has no type or storage class
FreeImagePlus.h:374: error: expected ‘,’ or ‘;’ before ‘fipMultiPage’
FreeImagePlus.h:412: warning: data definition has no type or storage class
FreeImagePlus.h:412: error: expected ‘,’ or ‘;’ before ‘fipTag’
FreeImagePlus.h:453: warning: data definition has no type or storage class
FreeImagePlus.h:453: error: expected ‘,’ or ‘;’ before ‘fipMetadataFind’[/COLOR]

I copy here this lines : 
[COLOR=Black]
[/COLOR][COLOR=Blue][COLOR=Black]72 :  [/COLOR][COLOR=Black]class FIP_API fipObject
81     class fipMemoryIO;
82     class fipMultiPage;
83     class fipTag;
85     [/COLOR][COLOR=Black]class FIP_API fipImage : public fipObject
340   class FIP_API fipMemoryIO : public fipObject
374  class FIP_API fipMultiPage : public fipObject 
412  class FIP_API fipTag : public fipObject
453  class FIP_API fipMetadataFind : public fipObject


what do you think?
Thank you again
[/COLOR][/COLOR]

---

### Post by zizou_fsegs on 2009-04-29
Hi,
I try to understand those error
I add the library "FreeImage.h" to the folder "c++" 

g++ -o lets_ocr lets_ocr.cpp -l FreeImage.h

but I still have error :

/usr/bin/ld: cannot find -l-xc++-header
collect2: ld returned 1 exit status

what do you think?
thanks

---

