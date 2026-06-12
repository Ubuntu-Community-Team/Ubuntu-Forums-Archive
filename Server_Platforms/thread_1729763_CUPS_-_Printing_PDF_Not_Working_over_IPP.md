---
title: "CUPS - Printing PDF Not Working over IPP"
date: 2011-04-15
forum: Server Platforms
---

### Post by kurzweil4 on 2011-04-15
I have installed CUPS 1.4 on Ubuntu server 64 bit. When I print a PDF locally from the machine, the filters work correctly, and the PDF prints as expected. But, when I print a PDF to the same printer using IPP from another machine, the PDF gets sent directly to the printer in a raw text format, printing the actual PostScript-like commands in the PDF.

Here are the commands I am using:

Local:

lp -d PRINTER_NAME file.pdf

Remote:

lp -d ipp://host:631/printers/PRINTER_NAME file.pdf

Is there something special that must be setup when you want to enable filtering when printing through IPP? Any other ideas on what might be wrong?

Thanks,
Kurz

---

