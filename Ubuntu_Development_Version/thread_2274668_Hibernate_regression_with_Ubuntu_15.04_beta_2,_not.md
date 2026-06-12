---
title: "Hibernate regression with Ubuntu 15.04 beta 2, not kernel problem?"
date: 2015-04-21
forum: Ubuntu Development Version
---

### Post by dankegel on 2015-04-21
I use a Thinkserver TS140 as a desktop ( [http://kegel.com/new-computer-2015.html](http://kegel.com/new-computer-2015.html) ).
Great machine, but doesn't support suspend (it's a server, why bother with desktop features?)
Thus if I want to avoid burning power all day after other family members walk away from the machine,
I have to enable hibernate-on-idle.  This seems to work with 14.04.1, even with the mainline 4.0 kernel,
but it doesn't seem to work with Ubuntu 15.04 beta 2.  It hibernates, but when it's time
to resume, I don't think it even notices that it should resume, and does a normal boot.
I filed [https://bugs.launchpad.net/bugs/1443762](https://bugs.launchpad.net/bugs/1443762) but it needs triage still.

Anyone else having hibernate regressions with Vivid?

---

