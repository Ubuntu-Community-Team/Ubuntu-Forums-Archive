---
title: "Error Printing with CUPS and new printer"
date: 2009-02-14
forum: Server Platforms
---

### Post by the-hogg on 2009-02-14
I consider myself a moderate linux user...hehe.  I have been running ubuntu server 8.04.1 for a while.  It is a web server, samba server, and cups server.

I have successfully installed and printed through a cups-server before.  All the pc's on my network can print to it, even my Dell laptop (Vista 32-bit) via wireless.  Printer was an Epson Stylus CX 3800.

My printer broke and I just bought an Epson Stylus NX 400.  I cannot print from my Dell laptop anymore (using Vista 32-bit).
[LIST=1]
[*]I got all my other pc's working correctly on the new printer.
[*]I can access the cups web interface from my laptop.
[*]I can print a test page from the cups web page from my laptop.
[*]Vista can "see" and connect to the new printer from my laptop.
[*]But I cannnot print a test page from the printer area from the laptop and I cannot print any document from the laptop.
[/LIST]

I know the terminal fairly well.  But I am stumped.  I am doing something wrong or I don't have a driver correctly installed or something.

Any ideas?  I would appreciate the help.

---

### Post by Thirtysixway on 2009-02-16
It looks like an issue with vista, possibly drivers for the new printer.  Try re adding the printer on your vista machine.  Also try looking online for vista-specific drivers.

This could be one of the driver issues that vista is famous for.

---

### Post by the-hogg on 2009-02-16
Thanks for the feedback ThirtySix.  I have tried to install from scratch a couple of times.  My gut is that it is a driver issue.  

For clarification - I installed drivers on my Vista laptop that were appropriate for the printer...plus I have the installation CD.

However, should I try to install Vista drivers in CUPS or on the server itself?  Seems like I have read about people doing that somehow.

Thanks again for the reply.

---

### Post by Thirtysixway on 2009-02-17
> **the-hogg said:**
> 
However, should I try to install Vista drivers in CUPS or on the server itself?  Seems like I have read about people doing that somehow.


If you can find info on it you can try.  I've never heard of doing that though.

---

