---
title: "Edgy?"
date: 2006-12-21
forum: The Cafe
---

### Post by Beamerboy on 2006-12-21
My edgy server is showing 2GB RAM usage in top (even though ps aux is not showing any apps using even 0.1% of RAM).  I am confused because the server is only running apache and mysql and apache isonly visible on the vpn and mysql is showing no unauthorised access, so I haven't been rooted.

Does top cache RAM usage stats or something?  Is there anyway to get a true idea of how much ram is actually being used?

[Edit] Never mind Inever noticed the cache, which is at 1.8GB.  I am curious as to what the heck is being cached though, the system is basically idle at the moment and has been since it was booted 34 days ago...

---

### Post by jpkotta on 2006-12-22
If you have free RAM, and you access the HD, the kernel will cache the files you accessed in RAM. This RAM behaves as if it were free; if more RAM is needed, it is immediately overwritten, and it is never written to swap.  If you reaccess the same file though, the cache is used instead.

---

### Post by kripkenstein on 2006-12-22
> **Beamerboy said:**
> Never mind Inever noticed the cache, which is at 1.8GB.  I am curious as to what the heck is being cached though, the system is basically idle at the moment and has been since it was booted 34 days ago...

34 days is a long time, if the system did anything - check for updates, even - then that would get cached (why not cache it, if you have the RAM)? So this is normal.

---

### Post by po0f on 2006-12-22
Beamerboy,

[Link](http://gentoo-wiki.com/FAQ_Linux_Memory_Management).

---

### Post by mcduck on 2006-12-22
if the RAM is not used, then you wasted your money when you bought it ;)

anyway, try 'free -m' and look at the '+/- buffers and cache'-line to see the real memory usage.

---

### Post by Beamerboy on 2006-12-22
Thanks folks

---

