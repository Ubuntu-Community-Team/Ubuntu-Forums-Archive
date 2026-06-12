---
title: "[SOLVED] Application to create pdfs?"
date: 2007-07-19
forum: The Cafe
---

### Post by urukrama on 2007-07-19
I'm looking for something that allows me to create pdfs in Ubuntu, specifically to convert multiple files (especially image files like .jpg) into a single pdf file. 

OpenOffice's convert to pdf is handy, as is using cups to print to pdf, but I haven't seen anything yet that allows you to easily convert a bunch of files into a single pdf file.

In Windows, I used Adobe Acrobat Proffessional, but that doesn't work in Linux. Any suggestions?

---

### Post by WinterWeaver on 2007-07-19
give Scribus a go... it's a very good app, quite like Quark (which was used by publishers back in the day, before Adobe InDesign)

---

### Post by urukrama on 2007-07-19
I used to have scribus installed. Does it do that? I want something were you can just select a bunch of files and then let the application create a pdf (ie., not something where you first have to load each individual picture and arrange them a bit, etc.) I never really used Scribus, but I'll reinstall it and check it out. Thanks for the quick reply.

---

### Post by WinterWeaver on 2007-07-19
hmm... no... scribus does not do that afaik.... you have to manually bring every pic into a page.

do a quick search on the forums for this. I've looked for PDF editors before, and there are quite a bunch out there. Some are quite horrible though lmao.

---

### Post by helliewm on 2007-07-19
Try PDF Edit. The latest ver ion is available at [www.getdeb.net](www.getdeb.net).

Helen

---

### Post by urukrama on 2007-07-19
Yeah, there are a lot of pdf edit applications around, but I haven't seen one to easily create pdfs. I searched the forums and google, but had no success.

---

### Post by Incense on 2007-07-19
Just install Cups-PDF and, add the PDF printer, and anything you can print, you can make into a PDF. Works great!

sudo apt-get install cups-pdf

---

### Post by urukrama on 2007-07-19
I know you can use cups to create pdfs, but it isn't really practical if you have to make a single pdf file out of say 150 jpg files.

---

### Post by Dragonbite on 2007-07-19
So are you looking for something like Acrobat where I can pull in multiple files (multiple PDFs, or not) and re-arrange their order, edit text/images of them and save it as a PDF?

---

### Post by urukrama on 2007-07-19
exactly!

---

### Post by Dragonbite on 2007-07-19
Add one more person interested in finding a tool like that .  My work is heavy on PDFs and it's rubbing off on me :)

---

### Post by urukrama on 2007-07-19
I'm really surprised there isn't something like that, or if there is, that it isn't more known.

---

### Post by eddin on 2007-07-19
you can try pdftk, which is found in the repositories. be warn that it is CL-based.

---

### Post by dshuck on 2007-07-20
I know it isn't terribly practical for everyone since not everyone writes CFML code, but Adobe ColdFusion 8 releasing within the next... well... soon.... has this ability.  I have been working with the beta release and it allows very smooth PDF creation and merging of documents.  I may try to write a web-based application to do this down the line after its public release.

---

### Post by Jose Catre-Vandis on 2007-07-20
pdftk is the way to go at the moment, and once you have learned a few of the stock commands, it would be easy to apply them to scripts in order to simplify batch processing.

---

### Post by urukrama on 2008-01-21
I finally found the application I was looking for: **[gscan2pdf]("http://gscan2pdf.sourceforge.net/")**

It is exactly what I wanted. You can scan to pdf or create a single pdf file from multiple pages.

---

### Post by quinnten83 on 2008-01-21
> **urukrama said:**
> I finally found the application I was looking for: **[gscan2pdf]("http://gscan2pdf.sourceforge.net/")**

It is exactly what I wanted. You can scan to pdf or create a single pdf file from multiple pages.

man only took you 6 months...
(so far for the benefits of open source :()
:(:(:(:(

---

### Post by Mateo on 2008-01-21
I used to want to do the same thing to keep things like receipts and bank statements.  But I found that saving as png and archiving via tar files would just as well.  They'll even open in evince or your favorite comic reader.

---

### Post by urukrama on 2008-01-22
> **quinnten83 said:**
> man only took you 6 months...
(so far for the benefits of open source :()
:(:(:(:(

Better late than never. :-)

**Mateo**: I do the same and use Comix to view my archived scanned images. Sometimes I need to email scanned files in a pdf format to someone, though, and gscan2pdf is excellent for that.

---

