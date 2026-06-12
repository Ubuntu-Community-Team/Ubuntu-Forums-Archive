---
title: "is tar (bzip2) multithreaded"
date: 2006-02-07
forum: Server Platforms
---

### Post by kakashi on 2006-02-07
i am wondering if tar is multithreaded. i just got a dual core ipteron. 
when compressing with bzip only one core is used but on gzip both cores are bieng used ?? 

also anyone know any other compression tools that are multithreaded (so its fast) and have a higher or equal compression ratio than bzip

---

### Post by Glut on 2006-02-08
AFAIK tar itself is not multithreaded. My understanding of tar is that it's limited by the speed of i/o. This is not necessarily the case with compression,  which generally relies on cpu speed. I'd be very surprised if there are multithreaded algorithms, as you'd have to read from two different inputs at the same time which can slow i/o considerably, probably forming another bottleneck.

Having just done a quick experiment, ps reports a single thread in use regardless of compression used.

---

### Post by kakashi on 2006-02-17
for the record 7 zip is multithreaded.

---

### Post by syadnom on 2008-03-12
tar is rarely CPU bound unless it is running on fuse or some other CPU intensive filesystem.  Typically I/O bandwidth is the bottleneck.

bzip2 is not multi-threaded
7z IS multithreaded and can produce smaller output that bzip2

7z is a great compression utility.

---

