---
title: "printer serving multiple OSs"
date: 2013-03-08
forum: Server Platforms
---

### Post by wlraider70 on 2013-03-08
I'm experimenting with sharing a basic USB printer to my network. Hp deskjed d2660.

One of my windows machines doesn't like the drive that linux seems to like. Is it possible to have a linux, driver, a MS driver and mac driver for one printer. 
Or is the limitation the poor HP driver?


Edit: I was able to select a different driver in Windows and have that work, but I still wonder about my earlier question.

---

### Post by SeijiSensei on 2013-03-08
Are you using CUPS and Samba?

One option with CUPS is to configure the server to use the native Linux driver and have all the clients use a plain Postscript driver.  There is an Apple PS driver in Windows that I've used for this task.  Otherwise I just install the native drivers for the printer on each client and pass the rendered document to Linux for printing.

---

