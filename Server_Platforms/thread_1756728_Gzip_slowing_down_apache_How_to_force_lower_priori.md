---
title: "Gzip slowing down apache? How to force lower priority?"
date: 2011-05-12
forum: Server Platforms
---

### Post by diafygi on 2011-05-12
Howdy all,

I'm trying to dump a mysql database on a small web server without killing performance. I tried using the nice command to give the mysqldump and gzip a low priority, but gzip is still taking up 100% CPU. Pages on the web server are loading incredibly slow.

Here's my command:
```
nice -n 19 mysqldump -u USER -pPASSWORD DATABASE | nice -n 19 gzip -9 > OUTFILE.sql.gz
```

How do I get gzip to run without taking up 100% CPU?

I've attached a screenshot of top about 8 seconds into the dump.

---

### Post by a2j on 2011-05-12
is it multi-core cpu?

gzip should take over only one core. or is it only bzip does that?

---

### Post by dtfinch on 2011-05-12
You could also try "ionice -c3" which will lower the I/O priority, which is independent from cpu priority.

And you could lower the cpu usage dramatically by specifying -1 instead of -9 for the gzip compression level. You could also try bzip2, which at its lowest compression level is probably better and faster than gzip's highest.

---

