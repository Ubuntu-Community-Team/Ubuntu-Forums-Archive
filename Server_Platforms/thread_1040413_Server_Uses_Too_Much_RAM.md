---
title: "Server Uses Too Much RAM"
date: 2009-01-15
forum: Server Platforms
---

### Post by HighCommander540 on 2009-01-15
I have been running a Ubuntu 7.10 LAMP server for about a year now. Up until a few weeks ago it has been using very little RAM, like around 100 MB (I don't have the most popular site).
 
Recently it has been using increasingly more RAM, when I check usually around 300MB. There hasn't been anymore traffic...I first thought it was the BASH scripts I was using, because I just learned how to write them a couple weeks ago and that is around the time of the increase, but I stopped all of them and still the increase.
 
I have noticed that a lot more instances of Apache are running now than I have ever seen before. IDK, why.
 
Also, I do run a TeamSpeak server, but they is not much activity there either.  I do have it set to autostart with a cron job, that uses a BASh script. But the cron job always zombies for some reason and shows up as defunct.
 
Can someone please help me figure out what the problem is?

---

### Post by Cracauer on 2009-01-15
How do you measure how much RAM is used by what?

---

### Post by linux_tech on 2009-01-15
> **Cracauer said:**
> How do you measure how much RAM is used by what?

In terminal type:

```

free -m
top

```

to get a est of memory usage

---

### Post by HighCommander540 on 2009-01-15
> **linux_tech said:**
> In terminal type:

```

free -m
top

```

to get a est of memory usage

Yes, that is exactly how I check the RAM usage.  First, I usually run a "free -m" to see how much is being used and then I use "top" to find out what is using the most.

Usually, top -u www-data. And I find that there are a lot of Apache threads running.

Anyone have any advice?

---

### Post by Cracauer on 2009-01-15
That's not useful to debug performance problems. Unix/Linux will always take up all RAM, in fact it is a problem when it doesn't.

---

### Post by HighCommander540 on 2009-01-15
No, that is wrong...Very wrong. The system will cache all of the RAM, but it knows how much of the actual RAM it is using for processes and not just in its cache. MAC OS X does the same thing and both know how much their processes are actually using.

If your computer tells you that itis "using" all of your RAM all the time, then there is something considerably wrong with **your** computer sir.

So is there anyone that has any actual advice? Because it didn't always use this much RAM.

---

### Post by Cracauer on 2009-01-15
So your claim is that your "server" (I assume that means apache) takes up more RAM now and that interactive processes are slowed down by lack of available memory now?

Can you post, exactly, how much RSS your interactive programs had before and after?

---

### Post by cariboo on 2009-01-15
I would be really helpful if you pasted the outputs of:

```
free -m
```

and 

```
top
```

in your next post. Just ssh into your server and  run the apps and paste the output from your terminal into your post. Remember to use the ```

``` tags.

Jim

---

### Post by HighCommander540 on 2009-01-16
> **Cracauer said:**
> So your claim is that your "server" (I assume that means apache) takes up more RAM now and that interactive processes are slowed down by lack of available memory now?

Can you post, exactly, how much RSS your interactive programs had before and after?

No, they don't run any slower and nothing at all on the system is affected. No speed difference, its just that there is more RAM being used now then ever before for no apparent reason.


free -m:

             total       used       free     shared    buffers     cached
Mem:          3034        408       2626          0        139        163
-/+ buffers/cache:        105       2929
Swap:         3153          0       3153

top:

top - 04:25:19 up 6 days, 23:33,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  59 total,   2 running,  57 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3107836k total,   418040k used,  2689796k free,   142784k buffers
Swap:  3229024k total,        0k used,  3229024k free,   167452k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
20548 zac       20   0  2308 1084  856 R  0.3  0.0   0:00.04 top
    1 root      20   0  2844 1692  548 S  0.0  0.1   0:01.61 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:03.11 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.51 kblockd/0
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  150 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  151 root      20   0     0    0    0 S  0.0  0.0   0:02.05 pdflush
  152 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  194 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1321 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd
 1325 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1353 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1355 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux
 1581 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1583 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 2097 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 scsi_eh_2
 2098 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 scsi_eh_3
 2317 root      15  -5     0    0    0 S  0.0  0.0   0:15.47 kjournald
 2470 root      16  -4  2224  672  380 S  0.0  0.0   0:00.47 udevd
 2909 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
 3756 dhcp      18  -2  2440  772  452 S  0.0  0.0   0:00.01 dhclient3
 4055 root      20   0  1716  516  444 S  0.0  0.0   0:00.00 getty
 4056 root      20   0  1716  516  444 S  0.0  0.0   0:00.00 getty
 4060 root      20   0  1716  512  444 S  0.0  0.0   0:00.00 getty
 4061 root      20   0  1716  512  444 S  0.0  0.0   0:00.00 getty
 4063 root      20   0  1716  508  444 S  0.0  0.0   0:00.00 getty
 4104 syslog    20   0  1936  684  532 S  0.0  0.0   0:07.49 syslogd
 4123 root      20   0  1872  544  448 S  0.0  0.0   0:00.04 dd
 4125 klog      20   0  3152 2016  424 S  0.0  0.1   0:00.11 klogd
 4144 root      20   0  5312 1024  672 S  0.0  0.0   0:02.51 sshd
 4328 root      20   0  3628  956  748 S  0.0  0.0   0:00.67 vsftpd
 4353 daemon    20   0  1984  420  300 S  0.0  0.0   0:00.00 atd
 4364 root      20   0  2104  892  712 S  0.0  0.0   0:00.50 cron
 4424 root      20   0  1716  516  444 S  0.0  0.0   0:00.00 getty
19287 root      20   0 23276 6788 3904 S  0.0  0.2   0:00.85 apache2
19293 www-data  20   0 27068  10m 4192 S  0.0  0.4   0:01.70 apache2
19338 www-data  20   0 28360  12m 4184 S  0.0  0.4   0:01.61 apache2
19360 www-data  39  19 95900 2056 1452 S  0.0  0.1   0:42.60 server_linux
19458 root      20   0  1772  524  440 S  0.0  0.0   0:00.00 mysqld_safe
19497 mysql     20   0  125m  17m 5092 S  0.0  0.6   0:13.13 mysqld
19499 root      20   0  2920  696  596 S  0.0  0.0   0:00.00 logger
19570 www-data  20   0 26596  10m 4200 S  0.0  0.3   0:01.51 apache2
19658 www-data  20   0 26832  10m 4252 S  0.0  0.3   0:00.96 apache2
19659 www-data  20   0 27856  11m 4352 S  0.0  0.4   0:01.10 apache2
19660 www-data  20   0 26788  10m 4100 S  0.0  0.3   0:00.74 apache2
19898 www-data  20   0 26580  10m 3960 S  0.0  0.3   0:00.36 apache2
19899 www-data  20   0 26828  10m 3660 S  0.0  0.3   0:00.59 apache2
20093 www-data  20   0 31440  15m 4308 S  0.0  0.5   0:01.43 apache2

That is what I can get on the screen. The rest of the processes are off the window.

---

### Post by Cracauer on 2009-01-16
You are making up a problem you don't have.

This is all perfectly working.

---

### Post by Thirtysixway on 2009-01-16
Doesn't matter if I have vmware running on my server or not, it says that my free memory is "5".  Linux just keeps a hold of your ram and give it to applications.

---

### Post by HighCommander540 on 2009-01-16
Ok, well I will take your word on it. I just find it odd that it would do this out of no where.  Thanks for your help guys. I apologize for the distress.

---

### Post by ryanfx on 2009-01-16
Don't worry about RAM being taken up.  Unused memory = wasted memory.

People complain about OS's like Vista taking up too much RAM because it preloads commonly used apps in in available memory.  When the application is called the computer simply retrieves it from memory instead of accessing it from the hard drive first.

---

### Post by jamessnell on 2009-09-15
This seems like a problem I've been having, though my server is running out of memory - it eventually dies with the console showing a bunch of out of memory error messages (if I leave it long enough). My website is also quite low traffic.

Here's output from top -u www-data (this server has an uptime of about 5mins when I ran this command):
```
top - 16:42:45 up 8 min,  1 user,  load average: 0.11, 0.12, 0.08
Tasks:  80 total,   1 running,  79 sleeping,   0 stopped,   0 zombie
Cpu0  : 11.0%us,  1.0%sy,  0.0%ni, 87.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.3%st
Cpu1  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    368836k total,   321640k used,    47196k free,     2304k buffers
Swap:  1048568k total,    13892k used,  1034676k free,    39152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                           
 3064 www-data  16   0  201m  34m 4780 S   12  9.6   0:22.68 apache2                                                                                                                                            
 3058 www-data  15   0  204m  37m 4772 S    0 10.4   0:03.11 apache2                                                                                                                                            
 3059 www-data  15   0  292m  63m 8100 S    0 17.6   0:00.89 apache2                                                                                                                                            
 3060 www-data  15   0  179m  10m 3036 S    0  2.9   0:00.02 apache2                                                                                                                                            
 3061 www-data  15   0  209m  42m 4764 S    0 11.8   0:00.36 apache2                                                                                                                                            
 3062 www-data  18   0  178m 8636 1780 S    0  2.3   0:00.00 apache2                                                                                                                                            
 3065 www-data  15   0  204m  37m 4752 S    0 10.4   0:00.41 apache2                                                                                                                                            
 3066 www-data  15   0  179m  10m 3044 S    0  2.8   0:00.00 apache2                                                                                                                                            
 3067 www-data  15   0  178m  10m 3036 S    0  2.8   0:00.00 apache2                                                                                                                                            
 3068 www-data  15   0  210m  42m 4752 S    0 11.9   0:00.30 apache2
```

When I run free -m it eventually will show 0 free memory in swap and like 4mb for ram.

Any suggestions on what to consider next?

---

### Post by Cracauer on 2009-09-15
Looks fine so far. Why don't you post the same top output from right before the crash?

And don't only include www-data. In fact `ps -alxwwww` would be more useful.

---

### Post by jamessnell on 2009-09-15
hmm, I'm less convinced I have a real problem. My swap was set to 512MB before and my box only gets 360MB of ram. I've since increased the swap to 1024MB and I haven't noticed a problem since.. Maybe I just need more than 360+512 for a LAMP setup?

---

### Post by Cracauer on 2009-09-15
> **jamessnell said:**
> hmm, I'm less convinced I have a real problem.  

That is what I was thinking.

 > **jamessnell said:**
>  My swap was set to 512MB before and my box only gets 360MB of ram. I've since increased the swap to 1024MB and I haven't noticed a problem since.. Maybe I just need more than 360+512 for a LAMP setup?

With mysql and php in there? Certainly.

You see we all ran 256-512 MB machines for web applications in 1996 or whereabouts. But all this software is really not prepared to run on that low memory anymore, the kernel in particular.

And even at the time you gave it a GB of swap or so.

---

### Post by jamessnell on 2009-09-15
Yeah, I'm kinda mortified to seem to need that much swap, but whatever..

---

### Post by Akita on 2009-09-15
Do you have a software RAID array? If your memory "problems" happen once a month and you have software RAID, look for an mdadm job in /etc/cron.d. By default there's a once per month job that does a consistency check on RAID arrays, and it does the damn thing in RAM. I watched a system of mine use all of it's swap and try to die once a month for 3 months after upgrading a RAID1 array to a pair of TB drives. The check every month used 100% RAM AND the swap. Got rid of the cron job and the once-per-month problem went away .. go figure. I think that default check was fine in the days of 20GB drives - LOL.

---

### Post by jamessnell on 2009-09-15
Interesting notion, but no, I don't have a software raid setup. I WAS noticing this problem very frequently - as in within a few mins of rebooting the machine.

Since I doubled the swap space earlier today I still haven't seen the box return to that insane sort of use as before. I think all it really was, was something "lame" in Apache and MySQL effectively requiring a certain amount of stuff to be cached and my machine not initially having the total memory to handle it all (I mean memory = ram + swap).

I guess it's all good now. I'll post more if I see a nasty return to how it was.. But given how fast it happened before and that it's been quite a few hours - I think I *may* be out of those particular woods.

Thanks for the support friends,

Cheerio,
  J

---

