---
title: "Photo of document --&gt; PDF"
date: 2010-09-12
forum: The Cafe
---

### Post by hambone79 on 2010-09-12
I have a handy app on my phone called DocScanner that lets me take a photo of a document (such as a receipt, business card, etc.) and convert it to a PDF file. The best part is that it will detect the edges of the document I'm scanning, then crop and adjust the skew. The result is a very nice and usable PDF but it has one drawback...it can't handle engineering drawings because the resolution of my camera isn't high enough.

I know that I can use GIMP and the crop/skew tools to do the same thing with a photo taken with my high res digital camera, but I wanted to see if there is something out there that could help me automate the process like DocScanner does. 

Any ideas?

---

### Post by hambone79 on 2010-09-12
Looks like I have one candidate:

[http://scantailor.sourceforge.net/?q=en](http://scantailor.sourceforge.net/?q=en)

---

### Post by v1ad on 2010-09-13
except now how to compile it ..

---

### Post by HermanAB on 2010-09-13
./configure
make
sudo make install

doesn't work?

---

### Post by v1ad on 2010-09-13
nope, we got the source code done in c++, with no make, or configure file.

---

### Post by doorknob60 on 2010-09-13
It uses cmake, that's why there's no configure script or makefile. [http://sourceforge.net/apps/mediawiki/scantailor/index.php?title=Building_from_source_code_on_Linux_and_Mac_OS_X](http://sourceforge.net/apps/mediawiki/scantailor/index.php?title=Building_from_source_code_on_Linux_and_Mac_OS_X)

---

### Post by v1ad on 2010-09-13
ah that explains it tx. ill see how it goes.

---

### Post by v1ad on 2010-09-13
such a pain, i installed more required libraries that the whole program has files itself.

required libraries.
and u need to install cmake
libboost1.40-dev
libtiff4-dev
libqt4-dev

then run scantailor in console to start, or add it manually in the menu...

---

