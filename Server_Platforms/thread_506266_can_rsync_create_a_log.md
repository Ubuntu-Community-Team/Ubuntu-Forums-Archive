---
title: "can rsync create a log?"
date: 2007-07-21
forum: Server Platforms
---

### Post by cazz on 2007-07-21
Can rsync create a log so I can see how what file and folder have backup and how did it go.

---

### Post by koenn on 2007-07-21
you can run it verbose with -v and send output to a file with  > file

---

### Post by cazz on 2007-07-22
Hmm you mean

```
rsync -v......................................... > file.txt
```

---

### Post by koenn on 2007-07-22
yep

or if you run it repeatedly : 
rsync -v [other options] src dest   >>  rsynclog.txt

the  >> will keep your old log and append to it, in stead of overwrite it.

---

