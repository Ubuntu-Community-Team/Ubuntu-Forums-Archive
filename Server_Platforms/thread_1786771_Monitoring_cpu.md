---
title: "Monitoring cpu"
date: 2011-06-20
forum: Server Platforms
---

### Post by lt-mini on 2011-06-20
Hi all,

I'm monitoring all kind of things like ( Mem, network, cpu, IOPS,..)

But still not found a command where i can see the CPU usage but in MHZ ( or Hz).

Using top or looking into /proc/cpuinfo doesn't give me the info i want.

Anyone now if this is possible? 

Info using ubuntu server 10.04. 

Greets

---

### Post by TechSupportx86 on 2011-06-20
I don't think you can see usage in Mhz

---

### Post by Paul Weaver on 2011-06-21
A modern CPU can do a variety of things in parallel (both on a per-core basis, but also in the same core), so measuring "how many mhz" is used is wonky to say the least. 

You could get the current mhz/core from /proc/cpuinfo, cut to get total CPU usage you'll need to use /proc/stat. Measure over a given second and compute the changes in values per core. That gives you a %age/core used, which you can multiply by the speed/core to get total mhz in use.

e.g.
cpu0 -- 45% used, 1.2ghz core
cpu1 -- 99% used, 1.2ghz core
Total is .99*1.2 + .45*1.2 == 1.72ghz


cpu0 -- 15% used, 2.4ghz core
cpu1 -- 32% used, 2.4ghz core
cpu2 -- 12% used, 2.4ghz core
cpu3 --  1% used, 2.4ghz core
Total is .15*2.4 + .32*2.4 + .12*2.4 + .01*2.4 == 1.4ghz


My laptop, cpu 1, is currently at 1.19ghz
cpu user  nice sys   idle
cpu0 52660 85 19049 3332302 791 0 127 0 0 0
cpu0 52665 85 19053 3332396 791 0 127 0 0 0

So thats 5/0/4/94

So on cpu0, User is taking 5/103 * 1.19ghz use, 4/103 system. Total use "104Mhz"

Repeat for cpu1,cpu2,cpu3

---

### Post by lt-mini on 2011-06-22
Hey Paul,

Thanks for this information. Only the last part is not so clear for me.


I was always wondering what the /proc/stat gives me. I knew the first four numbers what they mean (user, system,..) but never which unit they have.

example:
cpu0 52660

Do this means, 52660 action that cpu took from the start of the server?

In your calculations, you measured the system and user ( measured in 1 second), but what do you mean with deviding it with 103? %age/core? what does it really mean?



@Tech

Yes could be, not found anything till now. Only know that esxi server can measure cpu usage in Mhz, so was looking how i can get the same in ubuntu or any other linux server.


Kind Regards,

---

### Post by Paul Weaver on 2011-06-24
man proc has information on /proc/stat

They're measured in "ticks", which is usually 1/100th of a second. 103 was the number of ticks that had passed between my two samples, if it spend 45 ticks in 103 ticks in "user" time, then that's just under 45% CPU use in user time.

---

