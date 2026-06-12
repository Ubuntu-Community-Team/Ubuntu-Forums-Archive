---
title: "Printer selection smaller in server"
date: 2006-02-26
forum: Server Platforms
---

### Post by fizgig on 2006-02-26
In my regular Breezy installation I have a large selection of printers including the one I want: PSC-1600.  In the admin page of the cups webserver I don't see that available.

In the linuxprinting site I see the driver that I need is hpijs.  Can anyone give me a clue as to how to proceed?

---

### Post by fizgig on 2006-02-26
Well, I copied the PPD driver I found from linuxprinting.org into /usr/share/cups/model/hp-ppd/ , restarted cupsys and there it was in the web page!  Worked great.

---

