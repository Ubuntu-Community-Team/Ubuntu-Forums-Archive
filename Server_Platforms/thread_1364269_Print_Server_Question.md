---
title: "Print Server Question"
date: 2009-12-25
forum: Server Platforms
---

### Post by Ocoolaja on 2009-12-25
I am new to Ubuntu, actually I’m new to Linux generally. The idea was to build simple Ubuntu file and print server, serving a small Windows network.
  Now the question: if I use Ubuntu as genuine print server (instead of simple printer share), does it mean that Windows clients don’t need to have installed printer drivers? I am trying to trick Windows 7 clients to use legacy printer that is not officially supported by this OS.
   
  Thanks, regards

---

### Post by Vegan on 2009-12-25
SAMBA is the solution you want.

sudo apt-get install samba

and then search here for ideas on setting it up.

---

### Post by HermanAB on 2009-12-26
Yes, sorta kinda...

CUPS makes all printers look like postscript printers.  Therefore, you can connect from Windows and use almost any postscript driver to print.  The proper printer driver will work best of course (if the printer has fancy features and multiple trays), but I frequently follow the path of least resistance and us an Apple Laser Writer II driver for Windows, since it is near the top of the list.

You don't have to install Samba.  Just install CUPS and connect to the printer using the machine IP address and printer name URI.

---

### Post by Ocoolaja on 2009-12-26
Thank you, this is the anwer I was hoping for. Of course, Samba and CUPS for file and print server.

---

