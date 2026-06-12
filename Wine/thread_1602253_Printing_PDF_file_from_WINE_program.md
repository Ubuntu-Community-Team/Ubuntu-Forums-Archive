---
title: "Printing PDF file from WINE program"
date: 2010-10-21
forum: Wine
---

### Post by growdigital on 2010-10-21
I'm trying to print a PDF file from a WINE program (MYOB). 

The physical printer is found absolutely fine. But there are no options to print to a file, like you can from a linux program. 

Any idea how to get around this? Short of printing out the hard copy and sending it by snail mail!!?

tia, Jake

---

### Post by kostkon on 2010-10-21
I have such an option, I think because I have *cups-pdf* installed. Thus, try installing it. Afterwards, you may need to add it as a printer in your printer prefs.

The PDF files are saved in an folder named 'PDF' in your home folder.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=173049&stc=1&d=1287675765[/IMG]

---

### Post by growdigital on 2010-10-25
> **kostkon said:**
> I have such an option, I think because I have *cups-pdf* installed. Thus, try installing it.

Thanks kostkon, that worked a treat! Installed it via software centre, didn't need setting up, just needed to restart my Wine app. :)

---

### Post by Rob__oo00T on 2011-09-08
> **growdigital said:**
> Thanks kostkon, that worked a treat! Installed it via software centre, didn't need setting up, just needed to restart my Wine app. :)
growdigital, 
how can your PDF are genereted from Wine apps? Are they indexed (means are you able to look inside them and search strings) 
I discover that from Wine apps PDF are different generated that Unix native application.

let me know
Rob

---

### Post by disabledaccount on 2011-09-08
Why using PDF software inside WINE when there are many good linux native programs (exluding evince), like FoxitReader and AdobeReader ( :) )

---

### Post by Rob__oo00T on 2011-09-09
> **tomazzi said:**
> Why using PDF software inside WINE when there are many good linux native programs (exluding evince), like FoxitReader and AdobeReader ( :) )

I use standar PDF reader provided with Ubuntu 11.04, my problem is print inside a WINE environment using PDF output queue.
This generate PDF file not "searchable", not indexed.

---

### Post by Rob__oo00T on 2011-09-17
> **Rob__oo00T said:**
> I use standar PDF reader provided with Ubuntu 11.04, my problem is print inside a WINE environment using PDF output queue.
This generate PDF file not "searchable", not indexed.


I see this from others forum..
Long-known bug: [http://bugs.winehq.org/show_bug.cgi?id=6416](http://bugs.winehq.org/show_bug.cgi?id=6416)

:(:(

---

