---
title: "Gimp tools no longer work"
date: 2014-09-17
forum: Ubuntu Studio
---

### Post by i-am4barack-obama on 2014-09-17
Help gimp has stopped working.

My gimp program tools (selection tools other than the menu select all, paint bucket, pencil, paint brush, eraser, spraybrush etc.) stopped working.

I have Ubuntu Studio 12_04 LTS and all the progams are completely up to date.
gimp version 2.6.12-1ubuntu1.3 upgraded 7/22/2014

---

### Post by ibjsb4 on 2014-09-18
Have you tried reinstalling it?

---

### Post by i-am4barack-obama on 2014-09-18
Yes I already tried reinstalling gimp to no avail.

---

### Post by steeldriver on 2014-09-18
Have you tried starting with a clean gimp profile? e.g. backing up the current profile dir and restarting

```

mv ~/.gimp-2.6 ~/.gimp-2.6.bak

```

---

### Post by i-am4barack-obama on 2014-09-18
I deleted the old profile .gimp-2.6 and restarted gimp and it worked!

Your solution would have been a better option especially had I added on brushes etc and it would  have allowed debugging.  Unfortunately I already had: 
   rm -R  ~/.gimp-2.6/  
Thank you.
Cheers

---

