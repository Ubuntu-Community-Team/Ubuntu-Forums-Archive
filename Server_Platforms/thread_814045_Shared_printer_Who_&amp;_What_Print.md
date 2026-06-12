---
title: "Shared printer: Who &amp; What Print?"
date: 2008-05-31
forum: Server Platforms
---

### Post by salvo1 on 2008-05-31
Hi *,
A customer asked me a way to log what users print.

Use case:
X desktop users (Windows) -> Print
Y desktop user (Windows) -> Check

X print a document, his PC asks him an username and a passwrd and send the spool to the printer.

Y wants a web interface with a log:
datetime - user - printed_pdf.

Do i need of a server with cups?? Are there printers with all this system embedded?


My idea is a virtual printer (as the PDFs one):
1. ask username
2. query on SQL db
3. send the spool to the cups server

Is there something in java? I did something like this as fax sender.

A friend of mine told me that I can build this using few bash commands. Is it possible?

---

