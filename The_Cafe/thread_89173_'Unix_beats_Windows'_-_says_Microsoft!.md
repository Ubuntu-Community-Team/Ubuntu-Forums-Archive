---
title: "'Unix beats Windows' - says Microsoft!"
date: 2005-11-11
forum: The Cafe
---

### Post by BWF89 on 2005-11-11
[QUOTE=http://linux.slashdot.org/linux/05/11/11/1825244.shtml?tid=109&tid=106] Mortimer.CA writes "In a weblog entry, Paul Murphy mentions a Microsoft report (40 page PDF) that in many instances FreeBSD 5.3 and Linux perform better than Windows XP SP2. The report is about MS' Singularity kernel (which does perform better than the OSS kernels by many of the metrics they use), and some future directions in OS design (as well as examination of the way things have been done in the past)." From the post: "What's noteworthy about it is that Microsoft compared Singularity to FreeBSD and Linux as well as Windows/XP - and almost every result shows Windows losing to the two Unix variants. For example, they show the number of CPU cycles needed to "create and start a process" as 1,032,000 for FreeBSD, 719,000 for Linux, and 5,376,000 for Windows/XP."[/QUOTE]
[http://blogs.zdnet.com/Murphy/index.php?p=459](http://blogs.zdnet.com/Murphy/index.php?p=459)

---

### Post by endersshadow on 2005-11-12
> For example, they show the number of CPU cycles needed to "create and start a process" as 1,032,000 for FreeBSD, 719,000 for Linux, and 5,376,000 for Windows/XP

That sentence made my laugh out loud.  Thank you for that :-D

---

### Post by Sirin on 2005-11-12
Funny about how the Mac OS X is the most popular variation of UNIX, yet it is listed nowhere on the page...

---

### Post by GeneralZod on 2005-11-12
The "CPU cycles to start a process" is actually a pretty unfair measurement; UNIX-type systems rely very heavily on processes and less on threads, so are far more heavily optimised for the former than the latter.  In Windows, it's the other way round; threads are more important than processes, and so Windows creates threads faster than UNIX-type systems.  It's really comparing apples to oranges - a lightweight object in Windows is a thread, whereas in UNIX-type systems it's a process.

---

### Post by newbie2 on 2005-11-12
"Given their record in the security area, I don't know why anybody would buy from them," the former White House cybersecurity and counterterrorism adviser said yesterday, when asked for his thoughts on Microsoft's forthcoming line of security software.
[http://seattlepi.nwsource.com/business/212437_rsaclarke17.html](http://seattlepi.nwsource.com/business/212437_rsaclarke17.html)
:p

---

### Post by Brunellus on 2005-11-12
they're trying to massage the PR machinery in preparation for their Singularity OS.

---

