---
title: "Problem printing a scanned text"
date: 2018-09-19
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-09-19
Tested on both Cosmic & bionic  ](*,)

Printer Canon mx475 
- use SimpleScan to scan a black text on a white paper
- save into a file as pdf
- open the pdf: see that both the text and background are scanned
- print that pdf: only get a greyed background printed, so the text appear as negative (not printed)

Well, that is not what is expected. 
Looking at xsane settings, i have made tests with "front, back, both" options, without clear diff.
Also recheked the printing settings (was using the installed default ones)

So the questions are:
- how to only scan a text (without the background) ?
- is that issue a cups/SimpleScan/else problem ?

New test after installing xsane, and selecting 'slice':
- the save file only has text, not background (expected)
- but printing it again set a background  :(

So cups seems to be blamed now.
Note that was previously (some months ago) working as expected.

---

