---
title: "CUPS printing very slowly"
date: 2009-09-07
forum: Server Platforms
---

### Post by jjoswig on 2009-09-07
Hello,

here's my setup:
- Ubuntu Jaunty
- Core 2 Duo, 2.8 GHz
- 4 Gig of RAM
- Canon ir C3080i with UFR2 driver

The problem is, that after submitting a job (PDF file, around 1 MB), it lasts almost 30 second until the printer outputs the print job. It also occurs, if I'm submitting more than one printjob simultaneously - there's always a delay between the printjobs.
I read several bug reports on launchpad, saying that ghostscript is taking that much time to render the PDF file, but I observed the output of "top" and saw, that ghostscript is almost running for 7 seconds, which is quite OK I think.
But there are also processes running "c3pldrv" and "pstoufr2cpca" which are part of the UFR2 driver from Canon. I don't know if they are the reason, why CUPS and my printer are that slow.

Does anyone know what the problem is? Or is that just a problem of the UFR2 driver from Canon?

Thanks!

---

