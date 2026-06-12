---
title: "Crash in a C program"
date: 2019-01-12
forum: Ubuntu Application Development
---

### Post by SteMMo on 2019-01-12
Hello all,
I'm developing a C application running on a embedded board - x86 platform - running LUbuntu 13.10.
This application is launched by a PHP script.
After a day the board shows a window that reports an internal error:
[INDENT]ExecutablePath: MyApp
ProblemType: Crash
Architecture: i386
CodeDump: (binary data)
..
SegvAnalysis: Skipped: missing required fiels "Disassembly"
Signal: 11
..[/INDENT]

This should be a Segmentation Error exception and of course I'd like to know where.
I'm not able to find the coredump file: do I need to enable the generation of it?
In the case, is it possible to understand which code raises the exception - possibly off-line ?

thanks,
regards

---

### Post by TheFu on 2019-01-12
13.10 support ended in 2014.  
Support for 14.04 LTS ends in a few months, so either 16.04 or 18.04 are the only remaining options today.
[https://www.ubuntu.com/about/release-cycle](https://www.ubuntu.com/about/release-cycle) has more details.

---

