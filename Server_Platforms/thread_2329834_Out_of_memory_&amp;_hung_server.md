---
title: "Out of memory &amp; hung server"
date: 2016-07-05
forum: Server Platforms
---

### Post by mbt1974 on 2016-07-05
Hello, new ubuntu user here, with a system performance/crash problem.

I'm running Ubuntu 16.04 LTS. The primary application is a data scraping application that runs using Ptyhon, but I don't know much more (I inherited this system)

About once a day, the system hangs, and I need to force power a reboot. Looking at syslog prior to the crash, I see lots of this:
```

kernel: [337097.144809] Out of memory: Kill process 18723 (python3) score 1 or sacrifice child
chrome[23517]: segfault at 968 ip 00007f1770b0f643 sp 00007ffedb9d6180 error 4 in libX11.so.6.3.0[7f1770ae7000+135000]

```

So it definitely appears related to the chrome data scrapping app.

I was also able to grab a top prior to the system going south, and this is what it looks like:


```

top - 09:11:06 up 3 days, 21:42, 1 user, load average: 3.56, 2.82, 2.74
Tasks: 1224 total, 2 running, 1146 sleeping, 0 stopped, 76 zombie
%Cpu(s): 0.4 us, 22.7 sy, 0.0 ni, 34.3 id, 42.2 wa, 0.0 hi, 0.4 si, 0.0 st
KiB Mem : 6110848 total, 95140 free, 5752904 used, 262804 buff/cache
KiB Swap: 4190204 total, 0 free, 4190204 used. 35072 avail Mem


PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
44 root 20 0 0 0 0 R 56.4 0.0 931:58.24 kswapd0
19059 root 20 0 493820 10148 0 D 8.5 0.2 0:06.72 chrome
19115 root 20 0 295124 8136 1872 D 7.5 0.1 0:04.52 exe
19335 root 20 0 29440 6860 2272 D 5.9 0.1 0:01.84 lsb_release
19050 root 20 0 101504 1816 0 S 5.6 0.0 0:04.68 chromedriver
1020 root 20 0 186736 2496 2012 S 3.6 0.0 31:26.55 vmtoolsd
19336 root 20 0 42916 3072 1236 R 1.3 0.1 0:00.53 top
7 root 20 0 0 0 0 S 0.3 0.0 2:04.52 rcu_sched
13 root 20 0 0 0 0 S 0.3 0.0 0:37.36 ksoftirqd/1
18 root 20 0 0 0 0 S 0.3 0.0 0:04.04 ksoftirqd/2
1058 root 20 0 275768 1380 1264 S 0.3 0.0 5:04.02 accounts-daemon
1511 root 20 0 544600 12368 0 S 0.3 0.2 6:07.94 BrowserBlocking
8721 root 20 0 544600 11668 0 S 0.3 0.2 4:51.54 BrowserBlocking
9667 root 20 0 544580 11684 0 S 0.3 0.2 7:21.08 BrowserBlocking
17002 root 20 0 544652 12620 0 S 0.3 0.2 7:11.47 BrowserBlocking
17007 root 20 0 544620 32 0 S 0.3 0.0 10:47.17 BrowserBlocking
17538 root 20 0 544600 9648 0 S 0.3 0.2 7:10.04 BrowserBlocking
17692 root 20 0 544672 9240 0 S 0.3 0.2 6:33.28 BrowserBlocking
20142 tcollins 20 0 95496 868 600 S 0.3 0.0 0:07.23 sshd
24064 root 20 0 544600 12608 0 S 0.3 0.2 6:22.87 BrowserBlocking
24404 root 20 0 544632 580 0 S 0.3 0.0 7:47.06 BrowserBlocking
25683 root 20 0 544620 32 0 S 0.3 0.0 10:37.95 BrowserBlocking
26795 root 20 0 544600 12632 0 S 0.3 0.2 5:08.05 BrowserBlocking
28073 root 20 0 544600 5288 0 S 0.3 0.1 5:03.94 BrowserBlocking
30258 root 20 0 544620 656 44 S 0.3 0.0 8:19.33 BrowserBlocking
32106 root 20 0 544620 7500 0 S 0.3 0.1 6:12.29 BrowserBlocking
1 root 20 0 38308 1748 520 S 0.0 0.0 7:54.03 systemd
2 root 20 0 0 0 0 S 0.0 0.0 0:12.14 kthreadd
3 root 20 0 0 0 0 S 0.0 0.0 0:26.54 ksoftirqd/0
5 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kworker/0:0H
8 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcu_bh
9 root rt 0 0 0 0 S 0.0 0.0 0:00.62 migration/0
10 root rt 0 0 0 0 S 0.0 0.0 0:01.11 watchdog/0
11 root rt 0 0 0 0 S 0.0 0.0 0:01.21 watchdog/1
12 root rt 0 0 0 0 S 0.0 0.0 0:00.60 migration/1
15 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kworker/1:0H
16 root rt 0 0 0 0 S 0.0 0.0 0:01.26 watchdog/2
17 root rt 0 0 0 0 S 0.0 0.0 0:00.57 migration/2
20 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kworker/2:0H
21 root rt 0 0 0 0 S 0.0 0.0 0:01.08 watchdog/3
22 root rt 0 0 0 0 S 0.0 0.0 0:00.56 migration/3
23 root 20 0 0 0 0 S 0.0 0.0 1:19.05 ksoftirqd/3
25 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kworker/3:0H
26 root 20 0 0 0 0 S 0.0 0.0 0:00.00 kdevtmpfs
27 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 netns
28 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 perf
29 root 20 0 0 0 0 S 0.0 0.0 0:02.12 khungtaskd
30 root 0 -20 0 0 0 S 0.0 0.0 0:00.02 writeback
31 root 25 5 0 0 0 S 0.0 0.0 0:00.00 ksmd
32 root 39 19 0 0 0 S 0.0 0.0 0:07.51 khugepaged
33 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 crypto
34 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kintegrityd

```

Any suggestion where to go from here? A daily reboot seems to help but of course that's not ideal.

Thanks all!
Matt

---

### Post by TheFu on 2016-07-05
Please edit the first post and use "code tags" so the data lines up. Too hard to read otherwise.

If you are seeing out of memory issues, the fix is easy.  Add more RAM. Looks like all the RAM and all the swap are being used already, so perhaps chomping up the workload into smaller bites or redesigning the python to use less RAM would be required too.

I'd begin by installing and running server performance monitoring tools to look for when and where the issues are located. With a few days of that data, you might be able to trace the root cause. In the meantime, rebooting 2x a day would seem prudent, but only you know if that is possible.  Predictable downtime is always better than unpredictable downtime in my book.

Crashing is unacceptable. Only poorly written code can cause a system crash - it really shouldn't be possible. Does that program run as root?  I'd fix that first.

---

### Post by mbt1974 on 2016-07-05
Thanks for the tip, I edited the post.

I can certainly add more RAM and swap. But your insight about the app seems appropriate.  I'll try to track down the original developer.

Can you point me to an article or suggestion on the server performance monitoring tools? I googled it and find lots of different open source options.   I wasn't sure if you were referencing something specific to ubuntu server? 

-Matt

---

### Post by TheFu on 2016-07-05
Ah ... much nicer.  Don't use chrome here and don't know what "BrowserBlocking" is ... but that appears to be the issue. Can you tune the app to have few of those processes?  

**Performance Monitoring**
There is nothing special about Ubuntu vs any other Linuxen.  Whatever tool you would use on any other distro will work here.
If you have multiple systems, I'd use the same performance and alarming on Ubuntu as used on the others.  Nagios is popular for alarming. Zabbix, etc... 

I use **munin** currently for performance and system utilization capture, but **monit**, **sysusage**, **cacti** and 20 others are just as good. Admin's choice.  As you add more systems, I find it best to have a single box generate the graphs, not each box individually. Plus generating the graphs on-demand will save lots of wasted CPU.  The important thing is to have all the data BEFORE you need it.

Think I found a how-to on linux.com or howtoforge or some reputable website like that to setup munin. Took about 5 min to setup both the client and the server total.

---

### Post by ajgreeny on 2016-07-05
*Thread moved to **Server Platforms**.* which is more appropriate for the problem.

---

### Post by lukeiamyourfather on 2016-07-06
If you know what the application is doing and how it's doing it then you can probably tweak the behavior to be more memory efficient. If you don't want to mess with it then install more memory. Looks like it has 6GB which isn't much for "data scraping" or whatever the machine is up to. A 64GB kit of DDR4 memory is between $250 and $350 these days.

---

### Post by MAFoElffen on 2016-07-06
I have a sort of curiosity kind of question to the OP.

-You said you inherited this server (it is now yours and under your control).
- You said it ran an application that you didn't know much about or what it did. But that it was written in Python. Coding in many languages, it is possible to act in a recursive manner, in which it calls a the same function, from within itself, until it evaluates true. It adds t the stack, in memory ... and if it does not evaluate to true,it will run out of memory or reach a stack overflow... This is just one example, codewise.

But that is not my questions.My questions, based on what you did say above:
Now that it is your's, has it's job changed? If it has changed, is that program necessary to it's new role?

Like I said, I'm curious.

---

