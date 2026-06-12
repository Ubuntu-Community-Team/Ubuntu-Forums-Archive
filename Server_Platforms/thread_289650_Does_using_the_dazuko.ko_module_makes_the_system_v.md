---
title: "Does using the dazuko.ko module makes the system vulnerable?"
date: 2006-10-31
forum: Server Platforms
---

### Post by qscgz on 2006-10-31
Hi there,

[6.06.1 LTS]

does it really make the system vulnerable (to root kits) using the dazuko.ko module located at:

**/lib/modules/2.6.15-26-386/kernel/fs/dazuko/dazuko.ko**

...like mentioned by kevin_kofler on October 24th, 2006 12:12 am (UTC)
*Syscall Write Protection*
[http://kernelslacker.livejournal.com/57802.html](http://kernelslacker.livejournal.com/57802.html)

"...Dazuko does set the page back to read-only once it's done patching the syscall table. (Or is that ineffective for some reason?) Also, the main Dazuko developer does agree that syscall hacking _is a bad idea long-term_ and is already working on a stacked file system (dazukofs) as a cleaner solution..." 

Thanks for comments:)

---

