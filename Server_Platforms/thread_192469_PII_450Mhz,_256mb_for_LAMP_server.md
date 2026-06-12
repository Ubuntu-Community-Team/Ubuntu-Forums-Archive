---
title: "PII 450Mhz, 256mb for LAMP server???"
date: 2006-06-08
forum: Server Platforms
---

### Post by skafiskafnjak on 2006-06-08
PII 450Mhz 
256Mb
SCSI Ultra2 hard disk

[B]Can this server be used to host forums with around 20 users online at the same time.
3-4 of them download or upload files at the same time. (PDF files 10mb each)[/B]

My interent:

640kbps upload
4mbps download

Installed Ubuntu Dapper, server LAMP installation.

Thanks

---

### Post by paritybit on 2006-06-08
If you disable X and stuff, I would say this machine will run it like a dream. I have a PIII in a very similar configuration and it works great.

---

### Post by TriggerHappyChewie on 2006-06-08
Yes.  Believe it or not, it doesn't take much to run a server.  If your internet has sucky upload, (which it doesn't), you would have a problem.  I would try to disable as many things as you can that you don't need.  (Printing, sound, X, etc.)  Also, I reccomend using lighttpd instead of Apahce.  It's a little more difficult to install, but it's worth it.

---

### Post by Deusiah on 2006-06-09
I have a 275 MHz ARM (about the equivilent of a P120) box with 64Mb of RAM running Debian, Lighty, MySQL and PHP and it runs really well so a 450 Mhz box should have no probs.

---

### Post by arix on 2006-07-12
I'm use an k6-2 350Mhz with 256Mhz for hosting and everything is ok.You must modify apache2.conf directives for maximum performance (tunning).

---

