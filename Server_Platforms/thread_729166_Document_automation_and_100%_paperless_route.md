---
title: "Document automation and 100% paperless route"
date: 2008-03-19
forum: Server Platforms
---

### Post by netlogic on 2008-03-19
Paper is such a waste as many companies are utilizing the dual monitors setup. Not to mention, it is a security concern since users are keep on forgetting to shred the documents. You have to hire more administrative assistances to manage the papers. Also, I want to reduce users saving way too many important documents in their mail folders. Paper is bad for the environment, security issue, and increase the operating business expenses. How are you guys going paperless? I want to do following things.

1.Each departments manage their own wiki for the intranet
1.Example: accounting department has read and write access to their page and others have read only
2.What are good options for this? Can you recommend me some applications?
2. Keeping all documents in PDF format. No more MsOffice formats. This makes it harder to deploy OpenOffice in the future. If the changes in the documents are no longer required, I want to lock the documents to PDF. 
1.What are good command line applications that automates Office docs to pdf? I want to setup a cron job handle this. I want users just drop their Word, Powerpoint, and Excel documents in the network share, automates the copy, and convert them to pdf. Letting your standard Windows users to convert things aren't option. Some of them barely find their mouse cursor on the screen.
3.Searchable Intranet servers. I need a web application server that can index pdf, MS office and OpenOffice docs, and other various non-html formats. The security is also a concern. They need to able to logon to the search engine with their credentials to view documents their departments can view. I don't want HR to view certain documents in Accounting, etc.

Thanks again.

---

### Post by HermanAB on 2008-03-19
Some Ideas:
OpenOffice can export to PDF.
Another way is to install a PDF 'Printer'.
The SANE system for scanners can make a scanner network acessible.
HylaFax does the same for fax machines.

Cheers,

Herman

---

### Post by netlogic on 2008-03-19
Thanks Herman!
You are like a Gobuntu robot. You are full of knowledge and answering most answers.

> OpenOffice can export to PDF.
Another way is to install a PDF 'Printer'.
The SANE system for scanners can make a scanner network acessible.
HylaFax does the same for fax machines.

I know about this, but do you know anyway it can be exported through commandline so it can be done in a batch mode? The hard lesson I learned in the past is delegating too much to users always slow down the project.  Also, do you know a good php modules or other solutions for indexing pdf, docs, and other non-html documents? What would a good wiki tool that allows certain groups have permission to write? Anything that can work with PAM?

Thanks.

---

### Post by MommiesBoy on 2008-05-08
This is where i am but my desire is for the pdf's to be **searchable**.
I would to do this in Linux but i've searched and the only answer that keeps on popping up is Adobe Acrobat.
Is there any way this can be done in linux?
Yes I know of tesseract but the desire is for **searchable** pdf's.
I have no problems using Microsoft Document Imaging to handle the ocr as it even embeds the text in the tiff..somehow. How do i convert this tiff, with the embeded text, into a **searchable** pdf?

Thanks

---

