---
title: "Adobe Reader can't open PDF created through cups-pdf and Open Office."
date: 2007-05-06
forum: The Cafe
---

### Post by kagashe on 2007-05-06
Hi,

I was using cups-pdf and Open Office (even gedit) to create PDF documents. My wife writes in Devanagri script and I use to create PDF and send to her brothers in USA (who may not have those fonts).

Since April 16, I use my daugther's desktop on which I recently installed Feitsy. Today I converted some interesting web pages into PDF and tried to open them in Adobe Reader (latest version available on Feisty). The documents failed to open, although, they are opening on other Linux PDF viewers. I created a document in Open Office and I could not open it in Adobe Reader.

Adobe Reader is my favorite PDF viewer. It is also a necessity since the people who read my documents use it. Moreover my monthly credit card statement arrives in password protected PDF which opens only in Adobe Reader.

As far as I recollect till Dapper (probably Edgy also) I could open such documents (created through cups-pdf) in Adobe Reader and I was surprised this time.

[doPDF]("http://www.dopdf.com/") is similar program (freeware) to add a virtual printer in Windows. I converted same web pages to PDF using it in Windows XP and it opened in Adobe Reader (version Acrobat 5.0).

Is it a problem with the latest Adobe Reader or the latest cups-pdf and Generic driver?

kagashe

Problem solved:
I was using Print to file option in cups-pdf printer and I was getting postscript (.ps) file and not PDF (.pdf) file. In fact Print to file does not have an option to save in .pdf format. When I did not check the box "Print to file" I could make a PDF which went into "PDF" folder in my home directory.

---

### Post by Oki on 2007-05-06
Glad to hear it worked out:) 

You say you like Adobe Reader, but have you tried kpdf? Its faster to open and showing pdf then Adobe, love how you can easily zoom in, change paper and so on. Just as Foxit reader are better then Adobe on the wintendo platfrom. And have you tried to open your pdf from the bank in Koffice? When I tried Kwriter it didnt bother to take any notice of the protection - so perhaps that is an option for you. 

Have a nice day

---

### Post by stchman on 2007-05-21
> **kagashe said:**
> Hi,

I was using cups-pdf and Open Office (even gedit) to create PDF documents. My wife writes in Devanagri script and I use to create PDF and send to her brothers in USA (who may not have those fonts).

Since April 16, I use my daugther's desktop on which I recently installed Feitsy. Today I converted some interesting web pages into PDF and tried to open them in Adobe Reader (latest version available on Feisty). The documents failed to open, although, they are opening on other Linux PDF viewers. I created a document in Open Office and I could not open it in Adobe Reader.

Adobe Reader is my favorite PDF viewer. It is also a necessity since the people who read my documents use it. Moreover my monthly credit card statement arrives in password protected PDF which opens only in Adobe Reader.

As far as I recollect till Dapper (probably Edgy also) I could open such documents (created through cups-pdf) in Adobe Reader and I was surprised this time.

[doPDF]("http://www.dopdf.com/") is similar program (freeware) to add a virtual printer in Windows. I converted same web pages to PDF using it in Windows XP and it opened in Adobe Reader (version Acrobat 5.0).

Is it a problem with the latest Adobe Reader or the latest cups-pdf and Generic driver?

kagashe

Problem solved:
I was using Print to file option in cups-pdf printer and I was getting postscript (.ps) file and not PDF (.pdf) file. In fact Print to file does not have an option to save in .pdf format. When I did not check the box "Print to file" I could make a PDF which went into "PDF" folder in my home directory.

I am not really getting what you are saying in this article.

Openoffice.org has a PDF creation built in.  You just hitthe Export to PDF box and then select a filename.

cups-pdf is to be used when the application does not have pdf creation ability.  To use cups-pdf you need to create a printer.  Use the generic printer and select postscript color.  Now that you have a printer you can hit the print button on the application and then select the name of the PDF.  Cups-pdf saves the PDF file in your /home/<your_home>/PDF folder.

Adobe Acrobat has zero to do with pdf creation usung cups-pdf.

---

