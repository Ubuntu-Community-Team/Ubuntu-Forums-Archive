---
title: "pdflib"
date: 2006-09-20
forum: Server Platforms
---

### Post by gmarton on 2006-09-20
Hi,
I installed pdflib binary by adding the appropriate libpdf_php.so to /usr/lib/php4/20050606/ and adding extension=libpdf_php.so to php.ini.

Works great on my laptop which has a Desktop install (installed all the LAMP packages so I can develop on it) but wort work on a server install:


> 
PHP Warning:  Unknown(): Unable to load dynamic library '/usr/lib/php4/20050606/libpdf_php.so' - /usr/lib/php4/20050606/libpdf_php.so: ELF file data encoding not big-endian in Unknown on line 0



Has anyone loaded pdflib for php with a server install successfully?

Thanks!

---

### Post by spp on 2006-09-22
It sounds like you or someone compiled the pdflib library on one platform (iX86) and are using it on another platform (PPC,SPARC).  That is where the endian issues usually come into play. 

And my condolences on using PDFLib :)

I have spent many a fortnight tweaking a damn PDF because it did not look right. Look into pc4p as a wrapper library to make your life easier. There is a quick patch to get it working for later versions of PHP/PDFLib.

SP

---

### Post by gmarton on 2006-09-22
Thanks, 
AAAAAAAAAH! I cant believe i did not think about the processor differences just copied the library over from an x86 machine :( .
Yes pdflib is a bit painful but already did a large project using it.

Did not check if the other pdf generators support non-standard fonts, line and charcter spacing plus I use the PDI functionality to alter pdfs.

Thanks for your help!

---

### Post by gmarton on 2006-09-22
Oh no!
There is no PHP pre-compiled DSO available for linux on ppc. The one thats there is complied for osx. Tried that one just to see IF but no luck.
I get a different error:
> /usr/lib/php4/20050606/libpdf_php.so' - /usr/lib/php4/20050606/libpdf_php.so: invalid ELF header in Unknown on line 0


I guess there is no way around this, I would have to compile pdflib/php instead of using the one from the repository. Which is sort of bad because I lose the convenience of apt-get updating the php packages.

I will now investigate if there is a way to complie the PHP DSO because just compiling it creates an object which has to be compiled into php... --with-pdflib. 
I'm trying to avoid compiling php just because of pdflib and on a test server.

---

### Post by gmarton on 2006-09-22
Success!
They had a PHP binary for Linux/PPC of pdflib version 5.
Out of date but the project was initially done with 5 so it will work. 

In the future I will use another library, had enough fun with this one....

Read up some in the docs, my next stop would have to be using PEAR to build a DSO on this linux-PPC.

---

