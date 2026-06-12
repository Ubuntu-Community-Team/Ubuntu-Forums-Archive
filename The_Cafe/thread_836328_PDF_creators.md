---
title: "PDF creators?"
date: 2008-06-21
forum: The Cafe
---

### Post by Dr Small on 2008-06-21
Besides OpenOffice and Scribus, what can I make PDFs in? I just would like an idea of different things I could try, to convert some things into PDFs.

Dr Small

---

### Post by adityakavoor on 2008-06-21
You could use abiword or even gedit.

Use the print option in gedit to export as pdf

---

### Post by Dr Small on 2008-06-21
I might take a look at Abiword, since from what I recall, it is small and probably doesn't require many libs like gedit.

---

### Post by junior aspirin on 2008-06-21
if you are running hardy, you should be be able to use any program to create a PDF. Just print the document and select the PDF printer option.

---

### Post by Dr Small on 2008-06-21
I'm not running Hardy or Ubunt for that matter. That's why I wanted to see what applications I could use though, that were lightweight. And as far as Abiword, Gedit and OpenOffice go, none are lightweight and require alot of gnome libraries just to even run, which is ridiculous.

Things should be more centered on GTK than a certain DE.

---

### Post by -grubby on 2008-06-21
> **Dr Small said:**
> 
Things should be more centered on GTK than a certain DE.

Yes, ugg... I hate all the KDE Libraries I have to download just to use Kate.

---

### Post by spupy on 2008-06-21
> **Dr Small said:**
> Things should be more centered on GTK than a certain DE.

I'm not using Gnome, yet all gtk programs that can print, can print to a PDF file. I guess it's a feature of the gtk print dialog.

---

### Post by LaRoza on 2008-06-21
> **Dr Small said:**
> I'm not running Hardy or Ubunt for that matter. That's why I wanted to see what applications I could use though, that were lightweight. And as far as Abiword, Gedit and OpenOffice go, none are lightweight and require alot of gnome libraries just to even run, which is ridiculous.

Things should be more centered on GTK than a certain DE.

Well, they are built that way. They are much "lighter" if the system has those libraries already.

What DE do you use?

---

### Post by -grubby on 2008-06-21
> **LaRoza said:**
> 
What DE do you use?

Dr Small uses IceWM

---

### Post by LaRoza on 2008-06-21
> **nathangrubb said:**
> Dr Small uses IceWM

[http://en.wikipedia.org/wiki/List_of_PDF_software](http://en.wikipedia.org/wiki/List_of_PDF_software)

I found pdftk, trying it now.

---

### Post by days_of_ruin on 2008-06-21
Inkscape

---

### Post by Dr Small on 2008-06-21
> **days_of_ruin said:**
> Inkscape
Yes, but I plan to do text, formatting (similar to open office) and then save it as a PDF.

---

### Post by LaRoza on 2008-06-21
> **Dr Small said:**
> Yes, but I plan to do text, formatting (similar to open office) and then save it as a PDF.

Ok, to use an app with a lot of features, you will have to use the libraries for it. I use wmii, a very light window manager, yet I use Opera (which uses two (or more) QT libraries), OpenOffice (lots of libraries) and Thunar and Krita. 

Without a full features editor, you will most likely need to look at smaller utilities.

[http://www.linuxquestions.org/questions/linux-software-2/command-line-text-to-pdf-conversion-290058/](http://www.linuxquestions.org/questions/linux-software-2/command-line-text-to-pdf-conversion-290058/)

---

### Post by Mateo on 2008-06-21
LaTeX is the obvious choice for what you want.  Lightweight, check.  Word processing type features, check.  Convert to PDF, check.

---

### Post by mrgnash on 2008-06-21
LaTeX = the &#945; and the &#969; when it comes to producing PDF documents. Scribus and Inkscape are pretty neat for certain applications as well (brochures and the like).

---

### Post by brunovecchi on 2008-06-22
+1 to LaTeX. You can build tex files directly to pdf using pdflatex. Alternatively, you could get to the pdf by doing:
latex filename.tex && dvips filename.dvi && ps2pdf filename.ps

If you don't want to get dirty with LaTeX jargon, I suggest you try LyX ([http://www.lyx.org/]("http://www.lyx.org/")). It's great.

---

