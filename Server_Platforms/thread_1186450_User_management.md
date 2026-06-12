---
title: "User management"
date: 2009-06-13
forum: Server Platforms
---

### Post by sport9155 on 2009-06-13
I can't seem to get a search phrased correctly for this as I'm sure its been asked.
 
my remote telnet session was dropped so when I sign back in I'm now there twice.  Now with out rebooting, how would I clean up the first session?
 
Thanks

---

### Post by satyap on 2009-06-13
Either don't worry about it, or (carefully) kill it.

ps axf

That'll get you a process tree. You should easily be able to see which is the stale session. Start killing the processes hanging on to it.

---

