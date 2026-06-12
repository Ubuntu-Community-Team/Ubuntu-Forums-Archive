---
title: "Ubuntu server problems"
date: 2009-02-25
forum: Server Platforms
---

### Post by Rekoil on 2009-02-25
Hi,

I recently switched from Debian etch to Ubuntu server 8.10 on my home server because I found the newer packages in it very useful. However I have been having some problems (well, one major annoyance rather) with it that I'm hoping can be sorted through the help of this community, that is, unrar seems to run extremely slow.

Back in Debian (etch x86_64) extracting a 1.2gb split rar archive would take something like 40-50 seconds. However, extracting the same archive in Ubuntu is taking much much longer.

Ubuntu:
real 3m7.611s
user 0m7.580s
sys 0m6.600s

My laptop:
real 0m42.545s
user 0m7.986s
sys 0m5.511s

Now my laptop is a tiny bit faster than the server, clocking in at 2.5ghz Intel C2D (Penryn) whereas the server is running on a 2.2ghz AMD X2 (4200+), but the results with my server running Debian were very similar to those of my laptop.

uname:
```
root@ubuntu-server:~# uname -a
Linux super-server 2.6.27-11-server #1 SMP Thu Jan 29 20:13:12 UTC 2009 x86_64 GNU/Linux
```
```
Rekoil-MBP:~ rekoil$ uname -a
Darwin Rekoil-MBP.local 10.0.0d4 Darwin Kernel Version 10.0.0d4: Mon Jan 26 18:10:46 PST 2009; root:xnu-1378.2~1/RELEASE_I386 i386
```

Inter-disk transfers have also been much slower than before.

If anyone has any insight on the problem I'd love to know.

Regards,
Adrian

---

### Post by Rekoil on 2009-02-26
Interesting... so no one finds this a problem? I've seen similar threads without replies as well. Is it just my hardware? Because a friend with ubuntu server on his home server is reporting no such problem.

---

### Post by volkswagner on 2009-02-26
> **Rekoil said:**
> Interesting... so no one finds this a problem? I've seen similar threads without replies as well. Is it just my hardware? Because a friend with ubuntu server on his home server is reporting no such problem.

You may want to check if it is disk related.

[This thread]("http://ubuntuforums.org/showthread.php?t=941421") may be of interest.

---

### Post by Rekoil on 2009-02-26
It could be, but in that case it would be the way in which Ubuntu handles disk I/O and not the disk itself because as I said, in Debian it was fine and none of the hardware has changed.

I am reinstalling Debian on the server tonight but would still love to help solve this problem if I can be of any assistance. I've been speaking to friends at uni about it today and none of them have had such a problem with Ubuntu server or Ubuntu itself, I'm thinking it could be an isolated incidence with my hardware.

---

