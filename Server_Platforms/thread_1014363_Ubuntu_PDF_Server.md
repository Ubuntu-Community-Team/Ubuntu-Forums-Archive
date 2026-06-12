---
title: "Ubuntu PDF Server"
date: 2008-12-17
forum: Server Platforms
---

### Post by NeoGreen on 2008-12-17
Hello all, 
I want to build a server, in which I can use to create PDF files sort of like adobe Distiller Server.  I need to a windows hosted machines to be able to connect to it and create pdf's.  Is this possible, if so can you guide me in the right direction?  Any advice is gladly appreciated.

Thanks :KS

---

### Post by twright on 2008-12-17
why don't you just use a cronjob to automatically convert any files in a directory then use ftp to put any files in that directory

---

### Post by binbash on 2008-12-17
cups server + cups-pdf might do the trick

---

### Post by NeoGreen on 2008-12-17
Thanks for the advice guys.  I'll give it a shot.

---

### Post by NeoGreen on 2008-12-23
I have built the server and installed the cups and cups-pdf I have also installed Samba so the Windows machines can see it.  How do I connect the windwos machines to the ubuntu server so  they can start using the pdf creator?  Please advise.

---

### Post by HermanAB on 2008-12-23
Here is the simple solution:
[http://sourceforge.net/projects/pdfcreator/](http://sourceforge.net/projects/pdfcreator/)

Just install that on each Windows PC.

Cheers,

Herman

---

