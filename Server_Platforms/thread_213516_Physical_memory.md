---
title: "Physical memory"
date: 2006-07-11
forum: Server Platforms
---

### Post by Compact on 2006-07-11
I've got a Ubuntu server as a web server using apache. Pysical memory is always 94 % used, is it logic? How can I solve it if it is a problem?

---

### Post by Kurt` on 2006-07-11
It's just the way Linux works.

In addition to currently running programs being loaded into memory, Linux also likes to cache lots of stuff in ram.

High ram usage isn't a problem, as all the cached stuff is unloaded as soon as a program needs that space (it's instant).

Check the attachment. It's a screenshot of [PHPSysInfo](http://phpsysinfo.sf.net) running on my server.

To find out how much ram I am really using, I would subtract the "buffers" and "cached" from the total being "used".

---

### Post by Compact on 2006-07-12
[LEFT]Ok, thank you for you answer, so it is normal: [http://www.alcalleop.net/phpsysinfo](http://www.alcalleop.net/phpsysinfo) ? I also have phpsysinfo.
I think the server is down now...[/LEFT]

---

### Post by zzHanks on 2008-02-04
> **Kurt` said:**
> To find out how much ram I am really using, I would subtract the "buffers" and "cached" from the total being "used".
I don't understand why you have to do that to get the real thing 

Could someone explain please?

** Edit:**
I think I get it, just had to think a little bit.

---

