---
title: "Crawler getting access to files in Apache tree"
date: 2009-02-10
forum: Security
---

### Post by howlsmoving on 2009-02-10
I was looking through the apache log and found a crawler accessing files that aren't linked to any of the pages on the site.  How is it bypassing the index.html and finding these pages and files?  Any ideas for how to fix this?

---

### Post by The Tronyx on 2009-02-10
It could be something that is looking for known directory/file names which can be done by W3AF, Nikto, DirBuster and others.  I would recommend utilizing .htaccess to protect these directories and/or folders as well as disabling directory indexing if you haven't done so already.

---

### Post by howlsmoving on 2009-02-11
Thanks for the reply. I have explicitly turned off indexing now (made the option -Indexing in the conf file), but I'm not sure that was the problem (I tried to trick the server into giving me an index, but this didn't work).  Only another crawl will tell.  Also I'm pretty sure it wasn't guessing random file names, the names were relatively obscure and I didn't get a lot of errors.  Any other ideas?  Could it be an exploit?

---

### Post by oraldlight on 2009-02-25
> **howlsmoving said:**
> Thanks for the reply. I have explicitly turned off indexing now (made the option -Indexing in the conf file), but I'm not sure that was the problem (I tried to trick the server into giving me an index, but this didn't work).  Only another crawl will tell.  Also I'm pretty sure it wasn't guessing random file names, the names were relatively obscure and I didn't get a lot of errors.  Any other ideas?  Could it be an exploit?

If you don't mind my noob question: How did you accomplish this?

I'm scratching my head as to what/wherre/why my Gallery2 machine is apparaently trying to reach an IP on every port, constantly.

---

