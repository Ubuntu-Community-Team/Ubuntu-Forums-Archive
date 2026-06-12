---
title: "Printer jobs shown as authenticating"
date: 2013-08-23
forum: Server Platforms
---

### Post by AexbYRB on 2013-08-23
Whenever I send a job to the printer it is shown as authebticating, and does not print.
This morning alljobs were shown as completing but not printing.
I am using a Lexmark e232 on ubuntu 12.04 server
I have tried all the usual update stuff but still get these errors.
What can I do?

---

### Post by SeijiSensei on 2013-08-23
Take a look in /var/log/cups on both the client and server and see if there are any clues.

What protocol are you using, IPP?

On the client, try opening a browser and pointing it to [http://localhost:631/](http://localhost:631/).  You'll see the CUPS administration page. You might get some answers there as well.  You can also point a browser at the server's port 631 and see what it reports.

---

### Post by AexbYRB on 2013-08-23
Looking at var/log/cups/error_log file reveals a lot of these errors
failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-International-Lexmark-E232' already exists

---

### Post by SeijiSensei on 2013-08-23
Searching for that error string produced [a number of links](http://www.google.com/#fp=893dcfaea44611aa&q=failed+to+createdevice+org.freedesktop.colormanager.alreadyexists).  Maybe one of them will help.  There are a lot of people reporting issues with printers on 12.04, but there are also postings that suggest many problems have been solved in later releases.  Have you updated your 12.04 installation lately?

---

### Post by AexbYRB on 2013-08-23
Extremely strange. When I looked for that error string I found one forum thread in Italian. I will look through those links.

---

### Post by AexbYRB on 2013-08-23
No joy.

---

