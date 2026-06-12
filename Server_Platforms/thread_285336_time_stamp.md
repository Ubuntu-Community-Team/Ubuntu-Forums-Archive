---
title: "time stamp"
date: 2006-10-26
forum: Server Platforms
---

### Post by dirkdekker on 2006-10-26
Hi , I updates Breeze 5.01 server to Dapper 6.0.6.1 LTS
It is a simple server installation, no graphics; only terminal.
I installed program pound (a nice proxy server of Robert Segall).
The results of the $sudo make install action was wrong. It say's >make clock skew detected
Time stamp 2006-18-23 09:24:32 is: 277930051.

What to do now? is the time program confused?
Also I miss my prompt and when I run this:
$ cat /usr/share/terminfo/a/ansi the problem is over till a I start an executable.

Dirk

---

### Post by foxylad on 2006-10-26
I think this issue is caused by one of the source files of the make having a timestamp in the future. The "Time stamp 2006-18-23..." is very suspicious - there is no 18th month in any calandar I know about!

I'd look at the files and see if any have bad dates - you should be able to use the touch utility to correct them. But in any case report this back to the package maintainer so they can fix the issue.

---

### Post by dirkdekker on 2006-10-27
Hi, foxylad, thanks for good info.
the files itself dont have a wired timestamp.
$ls- hal Pound-2.1.5 
...24k 2006-10-23 09:23 z2_2_6_1.py

Is it also possible that te compiler is corrupted.
I have made an upgrade from breeze to dapper !!

---

