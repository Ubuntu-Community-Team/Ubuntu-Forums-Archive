---
title: "9 infected files...how to identify?"
date: 2005-11-02
forum: Server Platforms
---

### Post by user_stu on 2005-11-02
ClamAv reports i have 9 infected files.
1. How do I identify them and
2. what do I do with them?

(I ran clamscan -v -r -i /) 

For those that are interested I am also running Firestarter.

Cheers
Stuart

---

### Post by niko_ on 2005-11-02
which files ? does it report with what are they infected?

---

### Post by user_stu on 2005-11-02
[QUOTE=niko_]which files ? does it report with what are they infected?[/QUOTE]

No that's the problem -- all I get is:

----------- SCAN SUMMARY -----------
Known viruses: 40914
Engine version: 0.87
Scanned directories: 12481
Scanned files: 93801
Infected files: 9
Data scanned: 3206.98 MB
Time: 2345.604 sec (39 m 5 s)

---

### Post by niko_ on 2005-11-02
try it with; clamscan --debug --verbose -r -i /

---

### Post by user_stu on 2005-11-02
Woah. That's not what I expected. WHat does this mean lol?

---

