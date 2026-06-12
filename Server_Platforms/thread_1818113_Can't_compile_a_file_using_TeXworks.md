---
title: "Can't compile a file using TeXworks"
date: 2011-08-04
forum: Server Platforms
---

### Post by Sambambi on 2011-08-04
Hi, I wonder if anyone could help me please.

I am using TeXworks on Windows to write and compile LaTeX. I have been sent a large file which I didn't write but need to compile. When I tried I got the following error message:

! LaTeX Error: You have run the document with pdflatex, but PSTricks                requires latex->dvips->ps2pdf or alternatively the use
                of the package `auto-pst-pdf'. Then you can run
                  `pdflatex -shell-escape <file>' (TeX Live) 
                or
                  `pdflatex -enable-write18 <file>' (MikTeX).


Does this mean I have to compile from the command line in Linux using: 



latex Filename.tex dvips Filename.dvi ps2pdf Filename.pdf  %% ?



This would be a pain, I have Linux, but I can't see the files I have in Windows and I am not sure how to access them.


Is there a way round this using TeXworks?


Many thanks for any help :)

---

### Post by rudelgurke on 2011-08-04
Syntax problem might it be:

latex your_file.tex && dvi2pdf your_file.dvi

Should be it.

---

