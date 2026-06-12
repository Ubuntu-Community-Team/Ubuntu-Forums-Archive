---
title: "[SOLVED] How many different users can linux support?"
date: 2008-11-27
forum: Server Platforms
---

### Post by amac777 on 2008-11-27
Using google search, I see some references to 16-bit UIDs which would mean a total of 65536 unique users (and same for groups). But I also see other pages saying work is being done on 32-bit UIDs, which would allow over 4 million...

Anyone know what the latest kernel supports?

---

### Post by beniwtv on 2008-11-28
The 2.6 kernel can already do over 4 _B_illion users. This was a limitation of the past 2.4 kernels (which you shouldn't really run on a modern server).

[http://linuxgazette.net/issue98/pranevich.html](http://linuxgazette.net/issue98/pranevich.html)

Cheers,

---

### Post by amac777 on 2008-11-28
Ok, great that it's up to 4 billion already. When I was trying to find the answer myself, I also saw some (old) emails that linux couldn't be used in a particular university because they had over 80,000 current users (and, because they were using NFS, they never reused user IDs for security purposes so they needed even more than 80k user IDs). But looks like that problem is all solved now. 

Thanks for the link to the article as well. Very interesting.

---

