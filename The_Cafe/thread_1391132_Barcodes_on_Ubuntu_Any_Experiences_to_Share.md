---
title: "Barcodes on Ubuntu? Any Experiences to Share?"
date: 2010-01-26
forum: The Cafe
---

### Post by Macchi on 2010-01-26
Hi!

At work we are making some experiments around Barcodes in the Linux-space. 

I am already using Scribus and Inkscape for the creation of tiffs used  in the design and packaging, Kbarcode for simple (static) labels, and will soon look at some PHP barcode extensions for Joomla and Virtuemart.  

Any other hints on Open Source solutions for barcode applications?











(PS: Seriously, despite the fact that I raise this question in the 'Café', I am not talking about a 'Bar'. This is simply about those black and white stripes visible on any package or corner in our daily lives...)

---

### Post by juancarlospaco on 2010-01-26
There are TTF font for BarCodes, 
and a Java App for read them using a WebCam at Sourceforge.net
i installed these on a local shop.
:)

---

### Post by juancarlospaco on 2010-01-26
*[SIZE="1"]internet dejavu[/SIZE]*

---

### Post by Elfy on 2010-01-26
moved to general help

---

### Post by t4thfavor on 2010-01-26
There are options in OpenOffice for barcoding as well.

---

### Post by Macchi on 2010-01-27
> **t4thfavor said:**
> There are options in OpenOffice for barcoding as well.

Yes, I could find the Barcode extension to OpenOffice are at [http://extensions.services.openoffice.org/project/barcode](http://extensions.services.openoffice.org/project/barcode). Read some short notes on my first experiences: 

Just install the Barcode extension and it will l create an extra item in OpenOffice Draw -> Insert -> Barcode. It covers ten different variants of code, including the important EAN-13 that harmonizes with the global tagging standard GS1 . These GS1 codes allow integration of barcodes with RFID codes, Tracking numbers etc.

The generated graphic representation of the barcode can be easily copied and into the pasteboard and pasted into Write and Calc documents.  It will be interesting to see if it can be integrated nicely as a macro within Base, Write and Calc.  

This extension provides the basic functionality for many small and medium organizations to start using barcodes without having to spend days digging in the jungle of alternatives that can be found on the market today.

Before putting such codes into production environments I will have to verify the correctness of the checksums and graphic codes for this OpenOffice extension across different platforms.

---

### Post by Lars Noodén on 2010-01-27
> **Macchi said:**
> Yes, I could find the Barcode extension to OpenOffice are at [http://extensions.services.openoffice.org/project/barcode](http://extensions.services.openoffice.org/project/barcode). Read some short notes on my first experiences: ...


Thanks.  That was something I've been looking for ages, though it would be even better if it worked in Writer as well as Draw.  If you find any FOSS [TTF barcodefonts](http://www.openoffice.org/servlets/ReadMsg?list=discuss&msgNo=63120), those would be great, too.  

[http://qa.openoffice.org/issues/show_bug.cgi?id=68841](http://qa.openoffice.org/issues/show_bug.cgi?id=68841)
[http://qa.openoffice.org/issues/show_bug.cgi?id=5948](http://qa.openoffice.org/issues/show_bug.cgi?id=5948)

---

### Post by Macchi on 2010-01-27
> **Lars Noodén said:**
> Thanks.  That was something I've been looking for ages, though it would be even better if it worked in Writer as well as Draw.  If you find any FOSS [TTF barcodefonts](http://www.openoffice.org/servlets/ReadMsg?list=discuss&msgNo=63120), those would be great, too.  


Hej Lars,

There are some open source ttf barcodefonts at [http://sourceforge.net/projects/openbarcodes/](http://sourceforge.net/projects/openbarcodes/).

These TTF fonts appear to be correct and are directly usable in Write and Calc. Hopefully they also work correctly in Base. 
Only using the font is very raw and limited. It is not practical for use by less experienced people since there is a risk of generating wrong codes, because format and checksums have to be created manually (or manually copied from a reference source).
Apparently only the uppercase letters A,B,C etc give the correct representation for numbers as I have noticed in the EAN-13. 

A parcial solution for barcodes in OpenOffice is to get the existing barcode extension to work as MACROS for Writer, Calc and Base.

Please tell us if you find something new.

---

