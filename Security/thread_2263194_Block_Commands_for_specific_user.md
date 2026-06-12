---
title: "Block Commands for specific user"
date: 2015-01-30
forum: Security
---

### Post by chris344 on 2015-01-30
Hey guys I have a problem, 

I want to block a specific command like ln for user tom, how can I do that ? 
Tried using google but, didn't find the answer : >

I'm working on ubuntu server 14.04

Cheers 
Chris

---

### Post by Lars Noodén on 2015-01-30
There's not really a way to black list access but you can white list.  You could make their shell [rbash](http://manpages.ubuntu.com/manpages/trusty/en/man1/rbash.1.html) and then set up custom $PATH for them.  The directory for that custom path can then contain hardlinks to the programs that they are allowed to run.

---

### Post by alexeevdv on 2015-01-30
I think you can do it via SELinux [http://en.wikipedia.org/wiki/SELinux](http://en.wikipedia.org/wiki/SELinux)

---

