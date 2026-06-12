---
title: "dead script archive to restore panels?"
date: 2010-09-26
forum: The Cafe
---

### Post by sdowney717 on 2010-09-26
[http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/](http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/)

tried to unpack and got errors.
Does anyone know why?

---

### Post by NightwishFan on 2010-09-26
Run a file command to she what type it really is:
```
file */path/to/archive.tar.gz*
```

---

### Post by sdowney717 on 2010-09-26
scott@scott-desktop:~$ cd Desktop
scott@scott-desktop:~/Desktop$ file PanelRestore.tar.gz
PanelRestore.tar.gz: gzip compressed data, from Unix
scott@scott-desktop:~/Desktop$

---

### Post by FuturePilot on 2010-09-26
Someone fails at archiving. It's gzipped twice.

```
gunzip PanelRestore.tar.gz
mv PanelRestore.tar{,.gz}
```

Then it will work.

---

### Post by cariboo on 2010-09-26
I just double clicked it in the file download bar in chromium, file-roller decompressed it with zero problems.

---

