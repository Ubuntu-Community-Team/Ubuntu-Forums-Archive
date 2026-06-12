---
title: "find out reason for a kernel panic!"
date: 2008-05-02
forum: Server Platforms
---

### Post by Brazen on 2008-05-02
I had a server lock up and the screen said "kernel panic" on it (along with some other stuff).  It's a production server so I didn't waste any time and just quick power cycled it and it came back up just fine.  Is there any way to find out the reason for the kernel panic?  Some logs I could look at or something?

---

### Post by lemming465 on 2008-05-02
Unfortunately, kernel panics tend to suppress message logging, So when you rebooted and lost the console contents you probably erased a lot of the useful evidence.

The first place to look is */var/log/messages*.  Also /var/log/kern.log.

---

### Post by Brazen on 2008-05-07
> **lemming465 said:**
> Unfortunately, kernel panics tend to suppress message logging, So when you rebooted and lost the console contents you probably erased a lot of the useful evidence.

The first place to look is */var/log/messages*.  Also /var/log/kern.log.

I couldn't really find anything useful in those, but thanks anyway.

---

