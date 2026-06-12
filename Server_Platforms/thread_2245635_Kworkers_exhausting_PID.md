---
title: "Kworkers exhausting PID"
date: 2014-09-25
forum: Server Platforms
---

### Post by exillmat on 2014-09-25
Hello everyone
I really hope you can help me, since I have encountered a strange problem with my server that forces me to reboot it around every 12 hours uptime. It is an Ubuntu Server 14.04.1 LTS running Kernel 3.13.0-36 x68_64 and normally I could run for weeks and even months before I need to reboot it. I know fairly enough about Linux and have a good grasp on what is going on my server. But this problem have made my head spin, and I have tried to goggle myself to the answer but with no luck.
When I first discovered this problem I, thought it was a hardware problem in the RAM, but I have tested it twice with the built in Memtest tool from the Grub boot menu and I found no problem with the RAM.
A few days ago (I think it was Saturday or Sunday) my server suddenly stopped responding. I went to the physical console to see what was going on and the screen wont wake. I had to hard reset it to get it back up again, 12 after that crash the same thing happened, It set the monitor on the physical console to never turn off I hope that it would bring me close to my answer and it helped. Now I could see that the kernel was outputting a really long error. I started to look further for the answer, and one time I used the screen command I noticed the PID on that command was 20000+. That seemed odd to me, so I started to focus on the PID in the top command and now I think I have found the problem.
On the screen shots I took on my phone you can see that one or several of my kworkers are exhausting my PID’s resulting in my server hitting 40000 PID’s and stopping from making new processes and that is what I think is resulting in the crash. When I google kworker and PID I get a lot of results with kworkers using up all their CPU power, but that is not the issue with my system and I can’t find anything about kworkers using up all the PID on a system. I can find one or two subjects on PID exhaustion but with no solution to fix it.
I have also tried to enable all kinds of logs on the server to help me find the exact problem, so if you need a specific log entry, let me know.

---

### Post by exillmat on 2014-09-25
Just found out that Java was the cause of the problem.
I have just purged Java from my system and are now waiting with top in my screen to see if the kworkers returns.

---

### Post by exillmat on 2014-09-26
Problem still exists.

---

### Post by Doug S on 2014-09-26
Hi and welcome to Ubuntu forums.

I am having trouble to be sure I understand your predicament correctly.

> **exillmat said:**
> ... one time I used the screen command I noticed the PID on that command was 20000+. That seemed odd to me, so I started to focus on the PID in the top command and now I think I have found the problem.
On the screen shots I took on my phone you can see that one or several of my kworkers are exhausting my PID&#8217;s resulting in my server hitting 40000 PID&#8217;s and stopping from making new processes and that is what I think is resulting in the crash. When I google kworker and PID I get a lot of results with kworkers using up all their CPU power, but that is not the issue with my system and I can&#8217;t find anything about kworkers using up all the PID on a system. I can find one or two subjects on PID exhaustion but with no solution to fix it.Having a PID of 20000+ is normal.
Also your screen shots show that there are not a lot of tasks total. I would have expected a huge number of tasks if you were somehow exhausting the availble PID numbering. Example (sort of):```
top - 14:09:48 up 22:29,  2 users,  load average: 6.80, 1.58, 0.56
[COLOR=#ff0000]Tasks: 8722 total,  43 running, 8679 sleeping[/COLOR],   0 stopped,   0 zombie
%Cpu(s): 75.6 us, 14.7 sy,  0.0 ni,  9.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16002500 total,  4325640 used, 11676860 free,   598104 buffers
KiB Swap:  8294396 total,        0 used,  8294396 free.  1720992 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
15578 doug      20   0   32772   9348   1152 R   4.5  0.1   0:00.68 top
 7154 doug      20   0    4200    360    280 S   0.5  0.0   0:00.03 consume
 7176 doug      20   0    4200    360    280 S   0.5  0.0   0:00.03 consume
 7291 doug      20   0    4200    360    280 S   0.5  0.0   0:00.03 consume
 7308 doug      20   0    4200    360    280 S   0.5  0.0   0:00.03 consume
 7316 doug      20   0    4200    360    280 S   0.5  0.0   0:00.02 consume
 7345 doug      20   0    4200    356    280 S   0.5  0.0   0:00.04 consume
 ...
 8263 doug      20   0    4200    360    280 S   0.5  0.0   0:00.03 consume
 ...
```Note also that once the maximum PID number has been used, the system will roll over and start again reusing available PIDs. Example:```
consume: 20 20 0.2  PID: [COLOR=#ff0000]32762[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284952393  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]32763[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284952978  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]32764[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284953647  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]32765[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284954312  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]32766[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284954982  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]32767[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284955584  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]300[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284956169  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]301[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284956755  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]302[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284957336  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]303[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284958022  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]304[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284958686  Total sleep: 0
consume: 20 20 0.2  PID: [COLOR=#ff0000]305[/COLOR] - fixed load method:  Elapsed: 0  Now: 1411766284959349  Total sleep: 0
```Just for completeness, this is how my "top" normally appears:```
top - 14:20:37 up 22:40,  2 users,  load average: 0.01, 0.87, 1.14
[COLOR=#ff0000]Tasks: 162 total,   1 running, 161 sleeping,[/COLOR]   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16002500 total,  2848272 used, 13154228 free,   598372 buffers
KiB Swap:  8294396 total,        0 used,  8294396 free.  1720996 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
  919 doug      20   0   24956   1712   1156 R   0.3  0.0   0:00.01 top
    1 root      20   0   33916   3284   1488 S   0.0  0.0   0:04.90 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.23 ksoftirqd/0
    4 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    ...
```Can you gain any further insight from the log files in /var/log?

Note: The "consume" program in my examples is just a tool I use, and not relevant to the conversation. I used it to create a lot of tasks and to use up a lot of PIDs.

---

