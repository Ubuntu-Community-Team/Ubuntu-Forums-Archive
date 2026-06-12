---
title: "Hacking Ubuntu to Improve Performance"
date: 2007-04-16
forum: The Cafe
---

### Post by newbie2 on 2007-04-16
> This feature includes various hacks to boost Ubuntu's performance, such as viewing running processes, identifying resources, finding process startups, tuning kernel parameters, and speeding up boot time. This is a complete chapter in the ExtremeTech book "Hacking Ubuntu: Serious Hacks Mods And Cusomtizations."
[http://www.extremetech.com/article2/0,1697,2114115,00.asp](http://www.extremetech.com/article2/0,1697,2114115,00.asp)
:cool:

---

### Post by DC@DR on 2007-04-16
Wow, such a valuable link, thanks for sharing it :-)

---

### Post by kostkon on 2007-04-16
Cool, thanks!!

---

### Post by jamesrl on 2007-04-17
Be sure to read the comments section, as there is some questionable advice in the article.  Particularly the comment that Ubuntu can only use 1 Gb of physical memory; my laptop has 2 Gb of memory, and Ubuntu Edgy/Feisty has always been using all of it (I didn't have 2 Gb with Breezy/Dapper) according to system monitors (e.g. "free", or "cat /proc/meminfo").

Checking my current memory usage (running with kubuntu feisty a few web browsers open (both with konqueror, firefox), kontact (kmail, akregator, kalendar, kgpg), konsole, a few system monitors (superkaramba), some music (amarok), beryl for desktop effects, and many daemons running in the background (sshd, php, apache, etc), I see:
```

jamesrl@redsox2007:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2018       1703        315          0        230        754
-/+ buffers/cache:        718       1299
Swap:         2047          0       2047

```
and then turning on windows XP in a virtual machine (Virtual Box) that allocates 512 Mb to it to boost up my memory usage, I get 

```

jamesrl@redsox2007:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2018       1965         53          0         30        629
-/+ buffers/cache:       1305        712
Swap:         2047          0       2047

```
This seems like its properly using all of my 2Gb of memory, even properly utilizing unused memory as "cache" (754 Mb in normal operation when plenty of free memory) and then shrinking that cache when more memory is being used (it moved down to 629 Mb of memory when it ran out of free memory).

I usually have an applet in the monitoring cpu/mem/swap usage, and have never noticed swap being used at all (except for hibernation; and maybe once using like 2 Mb out 2 Gb).

When someone from the ubuntu team challenged him on this in the comments, he tried defending it with some [article]("http://kerneltrap.org/node/2450") from February 2004, saying that the 2.6 kernel (2.6.3 or so in 2/2004), can't handle more than 1 Gb of physical memory.  [I'm not an expert on memory usage; the article could possibly be technically true still, e.g. maybe the kernel can only access 1 Gb and other programs can access more than that; or its due to the difference between high and low memory or something.]

But i am trying to say ubuntu clearly can properly utilize systems with at least 2 Gb of memory (at least in 2007; right now im running feisty's 2.6.20-15).

---

### Post by jamesrl on 2007-04-18
Also don't trust the part about how cron is wasted; by default lots of things are installed in cron.  For example, just look in:
```

/etc/cron.daily/
/etc/cron.weekly/
/etc/cron.monthly/
```
In cron.daily I find scripts that update the locate database, the apt package descriptions, updates the man database, rotates the logs, among other things.  [This way i don't have to wait forever to search for a file with locate, or run sudo updatedb, every day myself.]

In cron.weekly / cron.monthly
there's things like popularity-contest and stuff with logs that should be done occasionally but not necessarily every day.

---

