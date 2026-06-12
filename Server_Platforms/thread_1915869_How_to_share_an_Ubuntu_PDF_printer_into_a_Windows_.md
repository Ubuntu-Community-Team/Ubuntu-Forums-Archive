---
title: "How to share an Ubuntu PDF printer into a Windows network with no folder shares?"
date: 2012-01-27
forum: Server Platforms
---

### Post by sojamm on 2012-01-27
Hi dears,
 
I am in a Windows network infrastructure, where I am migrating services to Ubuntu servers (DHCP, DNS, PDC-?,...).
 
One of the services I want to migrate is the shared PDF printer I have in a Windows server ([http://www.tinypdf.com/](http://www.tinypdf.com/)). When a Windows user select the mentioned shared PDF printer (no local installation required in the user's PC), the "printer driver" asks the user for the path/name for the new PDF file to be created.
 
Several advantages I can see, indeed:
 
- the file is directly stored in the user's environment,
- the user is free to set the path and name of the file,
- the user gets the file open as it is created,
- there is no need for sharing additional folders in the linux server,
- no need for searching you PDF file in a networked drive/folder, mixed with other users PDFs,
- confidential PDF files are not available to any user with "PDF printing" capabilities,
- very easy/simple solution from the user perspective
 
And finally my question, is there any way to deploy sometyhing similar using an Ubuntu server?
 
Many thanks.
 
PS: I had a look, but I am not finding a solution behaving in a similar way

---

### Post by LHammonds on 2012-01-27
I don't know about the server-based PDF services...mainly because I don't see a need for them at my site.  When I roll out PCs, I include a PDF printer as part of the base setup.  This is the utility I install: [PDFCreator](http://sourceforge.net/projects/pdfcreator/)

LHammonds

---

### Post by HermanAB on 2012-01-28
Yup, a networked PDF printer is the wrong way to do it, use pdfcreator.

---

### Post by sojamm on 2012-02-02
HI,

Many thanks for your replies.

I found interesting sharing a PDF printer, because I have many users moving from one PC to another, even with laptops. In the login script, I added the PDF printer, so everytime they login, they have all there resources available, including their usual PDF printer.

It is true that the PDF docs they produce are simple text documents from 1-10 pages, usually (i.e. very low consumption in network and server resources).

Any tips?

Thanks in advance.

---

