---
title: "How to Purge Printer Jobs?"
date: 2009-01-17
forum: Security
---

### Post by edisav on 2009-01-17
I notices that the documents that I print remain active in the queue for a long time. I'd like to delete, but even better, shred those files.

How can I get rid of them? 

Thanks!

---

### Post by HermanAB on 2009-01-17
[http://localhost:631](http://localhost:631)

Login as root.

Cheers,

Herman

---

### Post by lensman3 on 2009-01-17
Easiest, I think, is from the command line as root do:

lpq   (this will list the printer queue.  The print files will have a number associated).

then

lprm <number>      (line printer ReMove). 


Should remove the hung jobs.

---

