---
title: "problem with barnyard2 (IDS)"
date: 2012-08-30
forum: Security
---

### Post by Leo Matheus on 2012-08-30
im havving a problem with barnyard2.
when i run it, he show me a massege like:
WARNING: Unable to open waldo file '/var/log/snort/barnyard2.waldo' (No such file or directory)

i have restarted him bu still, he dont create the file .waldo.

when i use touch barnyar2.waldo he give me another error, and dont write in the file.

I had created a rule to detect icmp on snort, to see if he write, but no deal.

any idea what could be?
im using barnyard2-1.7
snort-2.9.2.3
ubuntu 12.04

---

### Post by Leo Matheus on 2012-09-05
i have made some updates, so here is the new versions:
snort-2.9.3
barnyard2-1.8
ubuntu 12.04 ;)

---

### Post by Leo Matheus on 2012-09-06
Well, i have found the problem.

I have to create an output on snort.conf

output unified2: filename snort.u2, limit 128

then give the comand

chown snort.snort /var/log/snort/barnyard2.waldo 

and run barnyard2 with

barnyard2 -c (path)/barnyard2.conf -d /var/log/snort -f snort.u2 -w /var/log/snort/barnyard2.waldo


:guitar:

---

