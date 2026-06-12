---
title: "What is the font used in the Ubuntu Server Brochure?"
date: 2009-03-17
forum: The Cafe
---

### Post by jakesee on 2009-03-17
Greetings everyone,

I'm a new guy just moved in here. To Linux, Ubuntu, this forum and more. Installed Ubuntu a few days ago on Intel Core 2 Duo P8600 and Intel Pentium dual-core T3400, but didn't seem to work on Intel Pentium M at all. I've given up.

Anyway, I was reading all the docs and happen to come across the neatly done up Ubuntu Server Brochure ([http://www.ubuntu.com/files/server/UbuntuServerBrochure804LTS.pdf](http://www.ubuntu.com/files/server/UbuntuServerBrochure804LTS.pdf)).

Can anyone tell me what is the font used for the general text content? I've manged to find some Ubuntu-title font, but that's not the one for the text.

Thanks in advance!


Regards
Jake

---

### Post by yabbadabbadont on 2009-03-17
```
/home/daffy/temp $ strings UbuntuServerBrochure804LTS.pdf | grep -i font
2 0 obj<</ColorSpace<</Cs8 49 0 R/Cs6 52 0 R>>/Font<</F1 47 0 R/F2 48 0 R>>/XObject<</Im10 5 0 R/Im9 4 0 R/Im11 6 0 R>>/ProcSet[/PDF/Text/ImageC]/ExtGState<</GS1 56 0 R/GS2 57 0 R>>>>
8 0 obj<</ColorSpace<</Cs8 49 0 R/Cs6 52 0 R>>/Font<</F1 47 0 R/F2 48 0 R/F3 33 0 R>>/ProcSet[/PDF/Text]/ExtGState<</GS1 56 0 R/GS2 57 0 R>>>>
11 0 obj<</ColorSpace<</Cs8 49 0 R/Cs6 52 0 R>>/Font<</TT2 36 0 R/F1 47 0 R/F2 48 0 R/F3 33 0 R/TT3 35 0 R>>/XObject<</Im12 15 0 R>>/ProcSet[/PDF/Text/ImageC]/ExtGState<</GS1 56 0 R/GS2 57 0 R>>/Shading<</Sh1 17 0 R/Sh2 19 0 R>>>>
13 0 obj<</Type/FontDescriptor/FontBBox[-222 -210 1000 913]/FontName/ArialMT/Flags 32/StemV 88/CapHeight 720/XHeight 600/Ascent 905/Descent -211/ItalicAngle 0>>
14 0 obj<</Type/FontDescriptor/FontBBox[-222 -210 1000 913]/FontName/ArialMT/Flags 32/StemV 88/CapHeight 720/XHeight 600/Ascent 905/Descent -211/ItalicAngle 0>>
21 0 obj<</ColorSpace<</Cs8 49 0 R/Cs6 52 0 R>>/Font<</F1 47 0 R/F2 48 0 R>>/XObject<</Im13 23 0 R>>/ProcSet[/PDF/Text/ImageC]/ExtGState<</GS1 56 0 R/GS2 57 0 R>>>>
25 0 obj<</ColorSpace<</Cs8 49 0 R/Cs6 52 0 R>>/Font<</F1 47 0 R/F2 48 0 R>>/XObject<</Im14 27 0 R>>/ProcSet[/PDF/Text/ImageC]/ExtGState<</GS1 56 0 R/GS3 28 0 R/GS4 29 0 R>>>>
32 0 obj<</Type/FontDescriptor/FontFile3 31 0 R/FontBBox[-157 -250 1126 952]/FontName/FKNILP+MyriadPro-Regular/Flags 4/StemV 88/StemH 67/CapHeight 712/XHeight 472/Ascent 712/Descent -232/ItalicAngle 0/CharSet(/space/B/I/N/D/S/H/C/P/A/M/F/U/Z/e/r/o/n/f/v/c/t/O/three/four/l/y/h/p/a/W/b/Q/L/s/T/i/d/J/K/g/six/period/zero/eight/one/five/seven/nine/two/w/k)>>
33 0 obj<</Type/Font/Encoding 34 0 R/BaseFont/FKNILP+MyriadPro-Regular/FirstChar 32/LastChar 121/Subtype/Type1/ToUnicode 30 0 R/FontDescriptor 32 0 R/Widths[212 500 500 500 500 500 500 500 500 500 500 500 500 500 207 500 513 513 513 513 513 513 513 513 513 513 500 500 500 500 500 500 500 612 542 580 666 500 487 500 652 239 370 542 472 804 658 689 532 689 500 493 497 647 500 846 500 500 553 500 500 500 500 500 500 482 569 448 564 501 292 559 555 234 500 469 236 500 555 549 569 500 327 396 331 500 481 736 500 471]>>
35 0 obj<</Type/Font/Encoding/MacRomanEncoding/BaseFont/ArialMT/FirstChar 222/LastChar 222/Subtype/TrueType/FontDescriptor 14 0 R/Widths[500]>>
36 0 obj<</Type/Font/Encoding/WinAnsiEncoding/BaseFont/ArialMT/FirstChar 32/LastChar 118/Subtype/TrueType/FontDescriptor 13 0 R/Widths[278 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 778 0 0 0 0 0 0 0 0 0 0 722 0 0 0 0 0 0 0 0 0 0 0 0 0 0 556 556 500 556 556 278 556 0 222 0 500 222 833 556 556 556 0 333 500 278 556 500]>>
46 0 obj<</ColorSpace<</Cs8 49 0 R/Cs9 50 0 R/Cs10 51 0 R/Cs6 52 0 R>>/Font<</F1 47 0 R/F2 48 0 R>>/XObject<</Im1 72 0 R/Im2 73 0 R/Im3 74 0 R/Im4 75 0 R/Im5 76 0 R/Im6 77 0 R/Im7 78 0 R/Im8 79 0 R>>/ProcSet[/PDF/Text/ImageC/ImageI]/ExtGState<</GS1 56 0 R/GS2 57 0 R>>>>
47 0 obj<</Type/Font/Encoding 53 0 R/BaseFont/FKMNIK+ArialRoundedMT-Bold/FirstChar 30/LastChar 150/Subtype/Type1/FontDescriptor 54 0 R/Widths[594 0 297 0 0 0 0 0 0 0 354 354 0 583 0 333 313 281 594 594 594 594 594 594 594 594 594 594 313 0 0 0 0 0 0 719 719 740 740 667 604 0 760 313 0 740 604 833 760 792 667 0 719 667 625 760 688 938 604 0 0 0 0 0 0 0 0 594 625 594 625 594 333 625 604 271 0 573 271 885 604 604 625 0 438 542 354 604 542 813 521 542 521 0 0 0 0 354 0 354 0 0 0 0 0 0 0 0 0 0 0 354 0 354 354 313 313 0 0 354 500]>>
48 0 obj<</Type/Font/Encoding 53 0 R/BaseFont/FKMNIL+ArialRoundedMT-Light/FirstChar 30/LastChar 169/Subtype/Type1/FontDescriptor 55 0 R/Widths[500 0 276 0 0 0 0 0 667 0 333 333 0 656 281 333 281 0 552 552 552 552 552 552 552 0 552 552 281 0 0 0 0 0 0 667 667 719 719 615 552 781 719 281 500 667 552 833 719 781 615 781 667 615 552 719 615 885 615 0 0 0 0 0 0 0 0 552 615 552 615 552 281 615 552 219 219 500 219 833 552 552 615 615 333 500 281 552 500 719 500 500 500 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 219 219 0 0 0 500 0 0 0 0 0 0 0 0 0 276 0 0 0 0 0 0 0 0 802]>>
54 0 obj<</Type/FontDescriptor/FontFile3 68 0 R/FontBBox[-174 -211 1185 944]/FontName/FKMNIK+ArialRoundedMT-Bold/Flags 262176/StemV 133/StemH 99/CapHeight 714/XHeight 472/Ascent 712/Descent -232/ItalicAngle 0/CharSet(/space/A/r/o/c/k/s/l/i/d/p/t/u/n/y/f/b/e/bullet/U/S/v/E/eight/period/zero/four/L/T/P/a/w/h/F/m/two/g/one/endash/D/x/C/M/O/X/W/fi/hyphen/parenleft/parenright/three/N/I/slash/K/plus/H/V/five/nine/seven/six/B/quoteleft/quoteright/R/z/colon)>>
55 0 obj<</Type/FontDescriptor/FontFile3 66 0 R/FontBBox[-191 -213 1208 929]/FontName/FKMNIL+ArialRoundedMT-Light/Flags 32/StemV 61/StemH 50/CapHeight 712/XHeight 472/Ascent 712/Descent -232/ItalicAngle 0/CharSet(/space/U/b/u/n/t/S/e/r/v/E/d/i/o/s/c/h/a/g/m/k/f/y/l/w/comma/p/period/W/x/L/j/colon/T/hyphen/q/quoteright/A/P/C/K/O/fi/z/H/I/D/M/Q/J/R/F/X/ampersand/G/parenleft/parenright/N/B/nine/V/six/one/eight/two/five/quoteleft/endash/three/four/zero/plus/copyright)>>

```
If you look closely, I think that you will see some font names in there.  :D

---

### Post by jakesee on 2009-03-17
K, I learnt something new today. I didn't know one could break the PDF apart and read the insides like you did....

Thanks!

EDIT: If there was a "thank you" button like in some other forums, I would have clicked it for you.

---

### Post by yabbadabbadont on 2009-03-17
Any day in which a person learns something, is a good day.  :D

You're welcome.

The PDF format is sort of like a type of Postscript.  At least that is what I have read.  There are editors that can be used to open, examine, and change them.  I've never used one, but I know they exist.  Further, I believe that the actual fonts themselves (in some form or other) are embedded within the PDF.  I don't know if it would be possible to extract them in any usable form though.

---

