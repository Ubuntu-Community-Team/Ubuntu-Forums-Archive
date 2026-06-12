---
title: "Interesting security bonus of Ubuntu."
date: 2011-05-08
forum: Security
---

### Post by d3v1150m471c on 2011-05-08
I was reading the Ubuntu Wikipedia page when I came across this:
> 
Ubuntu, unlike Debian, compiles their packages using [gcc]("http://en.wikipedia.org/wiki/GNU_Compiler_Collection") features such as [PIE]("http://en.wikipedia.org/wiki/Position-independent_code") and [Buffer overflow protection]("http://en.wikipedia.org/wiki/Buffer_overflow_protection") to [harden]("http://en.wikipedia.org/wiki/Hardening_%28computing%29") their software.[[29]]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#cite_note-28") These extra features greatly increase security at the performance expense of 1% in [32 bit]("http://en.wikipedia.org/wiki/X86") and 0.01% in [64 bit]("http://en.wikipedia.org/wiki/X86-64").[[30]]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#cite_note-29")That's really cool :), I wonder how one goes about this so now I'm gonna look into it further. Just thought someone might find that interesting.

---

### Post by rookcifer on 2011-05-08
> **d3v1150m471c said:**
> I was reading the Ubuntu Wikipedia page when I came across this:
That's really cool :), I wonder how one goes about this so now I'm gonna look into it further. Just thought someone might find that interesting.

You don't have to do anything.  Most packages are compiled like this already.  You can read more about all of these features [here.]("https://wiki.ubuntu.com/Security/Features")  And, yes, I agree that it is an often overlooked security hardening feature of Ubuntu (and some other Linux distros).

---

