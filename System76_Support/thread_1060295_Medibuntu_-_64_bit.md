---
title: "Medibuntu - 64 bit"
date: 2009-02-04
forum: System76 Support
---

### Post by jbelmonte on 2009-02-04
I am trying to determine which Medibuntu packages I need to install to be able to access Real Media (.rm) files. I have a Wild Dog with an Intel Quad Core 9550 processor, running 64-bit Intrepid.

The options seem to be....

*    For i386, the package is called w32codecs:
      sudo apt-get install w32codecs

*    For amd64, the package is called w64codecs:
      sudo apt-get install w64codecs

I'm sure I sound like a noob, but I am confused. My system is running 64-bit Intrepid, so I was expecting to install the 64 bit version of the codecs. But the 64-bit Medibuntu package is labeled amd64. That sounds like it is for PCs with AMD processors whereas I have an Intel processor. Are the w64codecs for PCs with AMD processors only? If the w64codecs are AMD specific, are there 64-bit codecs for Intel processors running 64-bit Intrepid? Should I use the 32 bit codecs and force?

TIA for any advice.

edit: I found [http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats) and that answers my question.

---

### Post by thomasaaron on 2009-02-04
OK. 

Yeah, the AMD64 is a legacy name. It works with Intel 64-bit too.

---

