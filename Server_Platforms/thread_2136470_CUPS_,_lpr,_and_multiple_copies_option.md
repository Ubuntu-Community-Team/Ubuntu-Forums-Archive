---
title: "CUPS , lpr, and multiple copies option"
date: 2013-04-17
forum: Server Platforms
---

### Post by 2WheelPenguin on 2013-04-17
Sorry if this has been asked & answered, extensive searching everywhere including this forum failed to turn up any answers.
When using lpr from the command line, you are supposed to be able to specify multiple copies of a print job, e.g.

```
lpr -P printer_name -#3 filename.txt
```

should print 3 copies of filename.txt

But it doesn't, you can put any number there, you'll always only get one printout of your file.

lp has a similar flag, e.g.

```
lp -d printer_name -n3 filename.txt
```

which also doesn't work.

Beginning to suspect this is a long standing persistent bug in CUPS.

Any ideas?

TIA

ETA:  Apparently this is only a problem when printing to a shared Windows printer.  Anyone know of a way to fix?  (Besides not using a printer attached to Windows, haha)

---

