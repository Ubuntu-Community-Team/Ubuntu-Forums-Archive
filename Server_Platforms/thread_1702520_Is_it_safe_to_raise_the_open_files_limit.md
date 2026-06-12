---
title: "Is it safe to raise the open files limit?"
date: 2011-03-07
forum: Server Platforms
---

### Post by aharown07 on 2011-03-07
Running an nginx webserver on Ubuntu 10.04 lts
In the process of trying to optimize the mysql, various tuning scripts keep telling me to raise the table cache. But they also say the table cache should stay below 1/3 of the open files limit. I can raise that in mysql, but I guess you're not supposed to raise it above the OS's open files max.

So I'd like to raise it (found what appear to be solid instructions here: [http://tech-torch.blogspot.com/2009/07/linux-ubuntu-tomcat-too-many-open-files.html](http://tech-torch.blogspot.com/2009/07/linux-ubuntu-tomcat-too-many-open-files.html)

But... 
**Post by Kees here says it's not safe to raise it**
[http://old.nabble.com/The-default-file-descriptor-limit-(ulimit--n-1024)-is-too-low-td29758128.html](http://old.nabble.com/The-default-file-descriptor-limit-(ulimit--n-1024)-is-too-low-td29758128.html)
... at least, not safe under certain conditions. But I'm not clear on what the conditions are.

So... **is it safe or not?** If I knew how to just raise it for mysql, I'd do that.
But as you can probably see, I'm pretty new to all this. Don't want to wreck my server.

(my current limit is the default 1024... wd like to go to 2048)

---

### Post by Vegan on 2011-03-07
most programs open and close files so it should be be at issue

---

### Post by aharown07 on 2011-03-07
Thks

Did some more digging, too and this helped
[http://serverfault.com/questions/93234/setting-ulimit-and-ubuntu-8-04](http://serverfault.com/questions/93234/setting-ulimit-and-ubuntu-8-04)

When I do a cat /proc/MYSQLDPID/limits it shows a max open files value of exactly what I set it to in my my.cnf file. So apparently, that gets it what it needs?

But things I'm reading have suggested there is some kind of OS limit on how high I can raise the mysql max open files param also. Not sure how to make sure I avoid that exceeding that. I have about 500 tables.

---

### Post by tgalati4 on 2011-03-07
What's the output of free?

As long as you have enough RAM and swap, you should be OK.  Once your cache gets into swap, things will slow down--a lot.

Learn the ways of The Force:

man vmstat

Reading through the "related posts" from your last link brings up this tidbit:

[http://serverfault.com/questions/233614/mysql-open-files-limit](http://serverfault.com/questions/233614/mysql-open-files-limit)

---

### Post by aharown07 on 2011-03-08
Thanks. 
Should be good there.
Per HTOP...

Mem: 1005M
Used: 545M
Buffers: 39M
Cache: 366M

My swap is set at 256M of which HTOP shows 6M in use.

Maybe I'm way off on this, but I'm thinking I've got memory use balanced reasonably well if we're putting most of it to good use in caching and swapping is minimal.

I guess if I double the table cache at this point I'm going to see a bit more swapping once in a while... is that a bad trade off? I have no idea how much swapping is too much (if it was sitting at 200MB I'd be a bit concerned)

---

### Post by aharown07 on 2011-03-14
Did some more reading about how swap works.
Apparently, data sitting idle in RAM goes to swap eventually in a kind of preemptive way. So swap used will show a gradual increase even though there is plenty of unused RAM.

For the time being, I've switched to a smaller VPS (Linode makes this very easy) with 768 RAM rather than 1024.

At the moment, HTOP stats are

Mem: 751M used: 437M buffers:14M cache:282M
Swap: 3M out of 255M.

I've upped my open files limit to 2700 and set table_open_cache to 900.
(One tuning script says it looks good. Another is recommending even higher table_open_cache)


vmstat, for those who prefer...

```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0   3676  67988  10648 244944    0    0     2     5   12   50  1  0 99  0
```

---

