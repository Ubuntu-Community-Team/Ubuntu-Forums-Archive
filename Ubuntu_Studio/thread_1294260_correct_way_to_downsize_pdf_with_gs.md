---
title: "correct way to downsize pdf with gs"
date: 2009-10-18
forum: Ubuntu Studio
---

### Post by washakie on 2009-10-18
Hello,

I am trying to downsize (in terms of filesize) an A0 poster in pdf format. Currently the filesize is 30mb. I have tried the following:

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

It works in reducing my size to 5mb, however, the entire background content of the file becomes black rather than white.

I have also tried:

ps2pdf -dPDFSETTINGS=/screen output.ps output.pdf

This seems to only select a small portion (perhaps an A4 area) of the file, rather than the entire file.

Suggestions?

---

