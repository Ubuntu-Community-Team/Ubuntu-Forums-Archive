---
title: "help on squid"
date: 2009-10-28
forum: Server Platforms
---

### Post by mykelm03 on 2009-10-28
on my squid.conf, for cache_swap_high = 95%, cache_swap_low = 90%...i got a 90gb hdd and 70gb of it allocated for my cache_dir. checking my /var/spool/ (check below jpg attachement)..is it the swap.state the cached sites? kinda confused...and its 73048 (is it 73GB???)...so newbie on linux and squid...

---

### Post by koenn on 2009-10-28
> **mykelm03 said:**
> on my squid.conf, for cache_swap_high = 95%, cache_swap_low = 90%...i got a 90gb hdd and 70gb of it allocated for my cache_dir. checking my /var/spool/ (check below jpg attachement)..is it the swap.state the cached sites? kinda confused...and its 73048 (is it 73GB???)...so newbie on linux and squid...
the cached content is in the numbered subdirectories of /var/spool/ ... 
eg .../00/00 , 00/01 etc.

swap.state is (probably) just an index of what's in the cache.
73048 is the file size of swap.state - i think it's in KB, so that would be ~ 72 MB

---

### Post by Lars Noodén on 2009-10-28
Ubuntu 9.10 has [squid 2.7](http://www.visolve.com/squid/squid27/contents.php).  The configuration file is rather daunting, but it is possible to plod through it. 

The [cache size is in MB](http://www.visolve.com/squid/squid27/logs.php#cache_dir) 

swap_high and swap_low help squid pace the removal of cached material, older stuff gets moved out to make way for new stuff.

[http://www.visolve.com/squid/squid27/cachesize.php#cache_swap_low_cache_swap_high](http://www.visolve.com/squid/squid27/cachesize.php#cache_swap_low_cache_swap_high)

The users' guide should be here:
[http://www.deckle.co.za/squid-users-guide/Squid_Configuration_Basics](http://www.deckle.co.za/squid-users-guide/Squid_Configuration_Basics)
but just at the moment I'm not able to get through to that server.

---

### Post by mykelm03 on 2009-10-28
thanks, but still confused...try to issue this command, 

root@cacheserver:~# du -hs /var/spool/squid/

but not displaying anything...is there any way i could check the disk usage for my cache_dir? i really liked to know whether my squid is purging cache sites when it reaches the high and low water mark...

---

### Post by Lars Noodén on 2009-10-29
> **mykelm03 said:**
> thanks, but still confused...try to issue this command, 

root@cacheserver:~# du -hs /var/spool/squid/

but not displaying anything...is there any way i could check the disk usage for my cache_dir? i really liked to know whether my squid is purging cache sites when it reaches the high and low water mark...

**du** would be the way to check disk usage.  I see on my machine that with a fresh set up of squid, the default setup in karmic uses 17M even before I start to cache.  du should show something.  How about checking other directories to make sure the line is correct. (e.g. one of my keyboards has a tendency to let me type hidden but invalid symbols.  They'll show up if I cut and paste, but not initially.)

If you have the cache directory in its own, separate partition, then you could use df as well.  

The default is /var/spool/squid/ 

[INDENT][FONT="Courier New"]cache_dir ufs /var/spool/squid 100 16 256[/FONT][/INDENT]

See if you've changed that:

[INDENT][FONT="Courier New"]egrep "^cache_dir" /etc/squid/squid.conf \
  || echo "Nope, still using default"[/FONT][/INDENT]

---

