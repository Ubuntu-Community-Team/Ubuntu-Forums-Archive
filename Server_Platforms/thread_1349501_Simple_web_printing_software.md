---
title: "Simple web printing software?"
date: 2009-12-08
forum: Server Platforms
---

### Post by halfthelaw on 2009-12-08
Sorry if this is the wrong place to put this...
I'm looking for software that I can set up in Apache to let users upload PDFs remotely and have the printer automatically print the file. I've googled, but only seem to find commercial printers. Any ideas where I might find such software?

Cheers,
law/2

---

### Post by Vegan on 2009-12-08
You will need to write the software to accept an upload and then deal with it. You could use ftp for example, but then the problem of printing it will require some code as well.

You could use a bash script and rub it as a cron job. Just add a symbolic link to the program.

---

### Post by halfthelaw on 2009-12-08
Yes, I know I can do something of that sorts. I'm asking if there's already code released to do this so I can save myself the effort :)

---

