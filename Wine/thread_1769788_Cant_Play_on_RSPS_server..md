---
title: "Cant Play on RSPS server."
date: 2011-05-28
forum: Wine
---

### Post by mophead123 on 2011-05-28
When ever i click on the Run.bat in using wine nothing happens.
@echo off
Title Client
START java -Xmx512m Gui 30 0 lowmem members 32
exit
Thats what the code is for my Run.bat
sorry if this is a stupid question. I am quite new to Ubuntu can someone help me get the client running so i can play. p.s i have java and JDK installed.

---

### Post by lightstream on 2011-05-29
That batch file is merely running the Java program itself. Try running it natively by typing this in a terminal:
```
cd /path/to/where/Run.bat/is
java -Xmx512m Gui 30 0 lowmem members 32
```

---

