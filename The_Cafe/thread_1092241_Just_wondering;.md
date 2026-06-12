---
title: "Just wondering;"
date: 2009-03-10
forum: The Cafe
---

### Post by _sAm_ on 2009-03-10
Just wondering;

Lets say you install a program, but never run/use it. This program has programing errors that could be used by hackers/viruses and so on. Will this program be a security-problem if I never run/start/use it?

---

### Post by k2t0f12d on 2009-03-10
Some programs are executed by the system at boot time, others are executable by other programs, and some more are (or come with) libraries that are linked into other programs at runtime.  So the short answer to that is yes, within reason, but it isn't something you should be sweating bullets over unless you *know* why you should be worried.

Removing unused programs is good housekeeping 1) if you are *sure* you and any of the programs you do use never use it, and/or 2) you have a disk space budget.

---

### Post by issih on 2009-03-10
No program, no matter how badly written, or indeed no matter how maliciously written, can do anything to your system in any way unless it is run at least once.

If you run it, or the system runs it automatically, it can do some damage, although the amount it can do is limited assuming you don't run it as root.

As for exposing you to other security risks, there are only two possible ways I can see that happening.

1) A program maliciously or stupidly alters your firewall configuration, which will then leave you more exposed until you correct the change regardless of if the program is running at that moment in time, it must be run at east once though to effect the change.

2) A badly coded program (e.g. buffer overflow in some way) that accesses the internet exposes you to attacks that attempt to run malicious code via the exploit. That kind of vulnerability is only relevant if you are attacked whilst that specific program is running, once again the damage that can be done is limited as long as you aren't running that program as root.

Not a simple answer, sorry about that

Hope that helps

---

