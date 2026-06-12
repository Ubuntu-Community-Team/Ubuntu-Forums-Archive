---
title: "i686 vs server kernel on Xeon: perfomance dropped down"
date: 2006-11-20
forum: Server Platforms
---

### Post by GSMD on 2006-11-20
Hi.
There is one strange thing about Ubuntu 6.06.1 kernels. I've tried 3 of them testing performance with
[Husdon]("https://hudson.dev.java.net"), actually measuring the time it takes to build a project.
The results are kind of astonishing (Xeon 2,4Ghz *2, 3Gb RAM).[LIST=1]
[*]**i386 **- 47 seconds
[*]**i686 **- 46 seconds
[*]**server **- **56** seconds[/LIST]How could this happen that a server kernel is less productive? BTW, 4 CPUs have been detected both by i686 & server kernels which also remains a quest to me.
Any ideas, fellas? ;)

---

