---
title: "Format of files to cups for printing to other printer formats"
date: 2017-10-08
forum: Ubuntu Dev Link Forum
---

### Post by mtmigs on 2017-10-08
I have a program that was written decades ago which can format it reports for several different printers. The reports are simply lines of text 6 lines per inch vertical spacing and the horizontal spacing is either 10 cpi or 17 cpi. The program knows the codes for IBM, Epson, and Okidata dot matrix printers and PCL for HP LaserJet printers. For those printers the data is simply output to /dev/lp0 as raw text which cups sends to the printer.

I was looking at a few other printers I might like to use but they all used propriatary printer control languages. For those printers the program needs to send something to cups that allows cups to filter (Filter is the word they use in the vary basic documentation i read about cups.) the program output into something the printer will understand.

I am trying to find what formats cups will accept for filtering to those other printers? I suspect postscript is one of the options but that one would require major rewriting of the program for it to output. Are there any other formats available?

---

### Post by SeijiSensei on 2017-10-09
First, I'd see if those other printers support PCL. My Brother supports various languages like Postscript and PCL.

---

### Post by mtmigs on 2017-10-12
> **SeijiSensei said:**
> First, I'd see if those other printers support PCL. My Brother supports various languages like Postscript and PCL.

I already checked and the printers I would like to use do not support PCL.

---

