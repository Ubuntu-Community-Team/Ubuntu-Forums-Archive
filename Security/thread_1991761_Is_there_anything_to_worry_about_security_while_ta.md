---
title: "Is there anything to worry about security while taking system backup?"
date: 2012-05-30
forum: Security
---

### Post by newhere_m on 2012-05-30
Suppose someone is taking a complete system backup with well-known tools (e.g., "redo" backup & recovery/clonezilla etc). In case unfortunately the system crashes and one recovers the system with additional installed programs, saved files etc using redo, is there anything to worry about security? I am not asking because I have faced any strange behavior but only theoretically, should one look for something that tells that security had not been compromised in the process of backing up data and recovering? After all we are not getting the software from ubuntu repository; so should one not be careful?

Are there better backup solutions compared to not-so-sound solutions from security point of view?

---

### Post by Hungry Man on 2012-05-30
I guess like... "theoretically" if you're backing up the entire system including the OS malware might be able to embed itself somewhere dangerous and then you'd restore and get screwed.

I don't think this is likely because permissions would probably still be held so it would need root to do this.

I can't think of anything else except that rogue backup software could, of course, rewrite your system however it likes.

---

