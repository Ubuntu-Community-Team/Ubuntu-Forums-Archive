---
title: "PDF to ODF convertor??"
date: 2007-10-28
forum: The Cafe
---

### Post by kevdog on 2007-10-28
Any suggestions how to convert pdf to odf?? I can do pdf2ps, but kind of stuck after that!!

---

### Post by SunnyRabbiera on 2007-10-28
well if its a text based PDF you could just copy the text...

---

### Post by kevdog on 2007-10-28
I tried that -- it didnt exactly work -- all the text was copied but the formatting was destroyed.

Anyone ever used this?? unoconv
[http://dag.wieers.com/home-made/unoconv/](http://dag.wieers.com/home-made/unoconv/)

---

### Post by Martje_001 on 2007-10-28
[http://media-convert.com/](http://media-convert.com/)

?

---

### Post by ssam on 2007-10-28
its not a trivial thing to do. PDF does not contain the structual information that a word processor document does. however there is work on an openoffice pdf import

have a read of
[http://wiki.services.openoffice.org/wiki/Writer/ToDo/PDF_Import](http://wiki.services.openoffice.org/wiki/Writer/ToDo/PDF_Import)

also have a look at kword, i think it has basic pdf import

---

### Post by kevdog on 2007-10-28
Ill take a look at kword, and thanks for the heads-up about formatting information not contained in the pdf.

Has anyone used, or know anything about this project??  It looks interesting although I dont know how to use it.
[http://dag.wieers.com/home-made/unoconv/](http://dag.wieers.com/home-made/unoconv/)

---

### Post by pagingmrherman on 2007-11-28
It works but it's flaky as hell under gutsy.  I use it to convert odt files to MS Word doc files.  It's the only thing in the world that can do it in a shell script.

It uses the the UNO bindings for openoffice and there's a bug in gutsy that causes it to crash.  Practically every day I have to run: 

sudo ldconfig -v /usr/lib/openoffice/program

to get it to work.

Also, if soffice is running in headless mode, you can't run any openoffice programs.  You have to have to do a 

killall soffice

However, as long as you did the ldconfig and have soffice running in headless mode, you can convert documents using

unoconv -f doc myfile.odt

and most of the time it spits out myfile.doc.  Sometimes it does a core dump though and I have to redo the ldconfig and/or restart soffice in headless mode.

---

### Post by kevdog on 2007-11-28
Sounds like an unreliable solution to me.  Thanks for the headsup.

---

### Post by fluteflute on 2007-11-29
If you just want to edit the pdf you can use pfedit

[http://www.getdeb.net/app.php?name=PDF+Editor](http://www.getdeb.net/app.php?name=PDF+Editor)

---

### Post by hanzomon4 on 2007-11-29
ODF? What is that, an oss PDF-like format?

---

### Post by ssam on 2007-11-29
> **hanzomon4 said:**
> ODF? What is that, an oss PDF-like format?

ISO standard for spreadsheets, charts, presentations and word processing documents.

[http://en.wikipedia.org/wiki/OpenDocument](http://en.wikipedia.org/wiki/OpenDocument)

openoffice's default format. used by most opensource word processors, and a few closed source ones.

---

### Post by hanzomon4 on 2007-11-29
Oh!! I see, it's the catchall name for the various extensions and such like *.odt.

---

### Post by ssam on 2007-11-30
this was posted yesterday [http://www.linux.com/feature/122195](http://www.linux.com/feature/122195)

the goal is to write a powerful pdf library and then to build an acrobat type aplication on top of it.

---

### Post by kevdog on 2007-11-30
Thanks for the update -- I hope that project takes off!

---

### Post by bruce89 on 2007-11-30
pdftotext might be of use.

pdftoabw seems to convert PDF to AbiWord's format.

Both are in poppler-utils (installed by default).

---

