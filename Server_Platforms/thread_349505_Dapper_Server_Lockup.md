---
title: "Dapper Server Lockup"
date: 2007-01-30
forum: Server Platforms
---

### Post by Linuturk on 2007-01-30
I'm running Ubuntu 6.06 LTS as a server.

I have Cacti (a SNMP monitoring service) installed, with a MySQL backend and a LAMP webserver.

Every night around midnight, the server locks up hard. No webserver, no ssh, now local control (running X with fluxbox) 

The machine is completely unresponsive, and I have to poweroff the server and restart.

I'm hoping this is just a misconfiguration on my part. 

What logs do you need to help me?

---

### Post by MJN on 2007-01-30
/var/log/syslog and /var/log/messages are good starting points.

The 'at midnight' bit sounds promising to be honest - if it's that regular (and predictable) then it shouldn't be too difficult to work out what happens then and why it crashes.

Unfortunately, by their very nature, hard lockups are all-too-often not documented by the logs.

But let's have a look and take it from there...

Mathew

---

### Post by Linuturk on 2007-01-31
The logs your requested are attached to this post.

I've also attached a monthly summary of some common stats for this server.

It didn't lock up last night, so maybe that will help things along.

---

### Post by MJN on 2007-01-31
I had a quick scan of your logs but haven't seen much in the way a boot at just-gone midnight? Can you give me a specific time/date when it froze and your rebooted? (saves me reading a weeks worth of logs!)

I would ordinarily suspect a hardware problem, but given you say it happens at midnight every time this can be all but entirely ruled out.

Mathew

---

### Post by Linuturk on 2007-02-01
It doesn't seem to be exactly midnight. More like around that time.

Here are some dates of the lockups (times are approximations from my Cacti graphs):

1/25/07 - Right after midnight (12:30 AM)
1/29/07 - Looks to be midnight
1/8/07 - Either 1:00 AM or 3:00 AM (The graph appears to have nominal load between 1 & 3)

if I find more, I'll let you know.

---

### Post by Linuturk on 2007-02-05
Any luck with those logs?

---

### Post by Linuturk on 2007-02-08
I have some more information that will help you diagnose this problem.

I've noticed that my RAM is being completely used. Here is the output of free

```
             total       used       free     shared    buffers     cached
Mem:        515936     492804      23132          0     101864     260076
-/+ buffers/cache:     130864     385072
Swap:      2048248          0    2048248
```

I also noticed that the process "php" is using up a ton of the CPU. Up to 99%

Here is the output of top:

```
top - 09:02:41 up 1 day, 23:51,  1 user,  load average: 1.98, 1.96, 1.89
Tasks:  70 total,   3 running,  65 sleeping,   0 stopped,   2 zombie
Cpu(s): 18.3% us, 81.7% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    515936k total,   493176k used,    22760k free,   101916k buffers
Swap:  2048248k total,        0k used,  2048248k free,   260100k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
14292 www-data  25   0 17132 8096 3780 R 73.8  1.6  93:13.04 php
26287 www-data  16   0     0    0    0 Z  3.0  0.0   0:00.09 snmpget <defunct>
25909 www-data  25   0 19088 9.9m 3908 R  0.3  2.0   0:00.58 php
25912 www-data  25   0 17132 8120 3780 S  0.3  1.6   0:00.84 php
    1 root      16   0  1564  528  464 S  0.0  0.1   0:01.44 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0
   64 root      15   0     0    0    0 S  0.0  0.0   0:00.13 pdflush
   65 root      15   0     0    0    0 S  0.0  0.0   0:00.05 pdflush
   67 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
   66 root      15   0     0    0    0 S  0.0  0.0   0:00.08 kswapd0
  655 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod
 1782 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
```

**The load spiked at 7:10 AM this morning (2/8/2007)**

---

### Post by MJN on 2007-02-08
There's nothing necessarilly out-of-the-ordinary there believe it or not...
 
The 'full RAM' syndrome is merely a consequence of how Linux manages its memory - just because it all appears to be in use doesn't necessarilly mean there's no room for anything else. The reasons are many and varied but some of the easier to understand ones are that the memory can be overwritten without necessarilly having to swap out to disk, and much of it could be sat there waiting to be used/implemented by commonly-used functions that may otherwise be sat idle. Hence, you might think you need more RAM you could quite possible double it and still see that it appears 'full' after a period of time.
 
The 99% CPU usage is another one not to get too hung up about - unless it was running at 99% all the time on a particular process. Most processes, given a long enough (I'm talking milliseconds) runtime can consume the CPU for 99% of its process time - this only becomes a problem if it persists causing other process to queue.
 
Your 'load' figures (top line) could well suggest your PC has not got quite enough oomph for its current tasks - plenty of discussions on the web what it measures but generally speaking a value of 1 means the CPU has got 'just enough to do' at that moment in time. Higher than 1 means processes are being queued. However, if you've got a dual CPU then 2 is this 'just enough' point etc so take that into account. However, the you'd have to monitor your figures over time as the current snapshot could've been taken following you using various programs on the machine.
 
Mathew

---

### Post by Linuturk on 2007-02-09
That is the exact problem I'm experiencing. After a certain event or point, processes start to que up. There was a point where my load average reached 6.0!!

The server isn't a wimp by any streatch. It has an AMD running at 1.5 ghz and 512 MB of RAM. This should be plenty for a local intranet web server that polls about 60 clients via snmp.

Can you give me further assistance on diagnosing this exponential increase?

---

### Post by MJN on 2007-02-09
It's kind of difficult (for me at least) to suggest what the problem is particularly as the symptoms (hard lockups) are not particularly helpful when it comes to diagnosing the cause.
 
Given they seem to happen at roughly the same time each night you could do worse than sit in front of it watching the output of top and seeing what processes kick in immediately prior to the lockup.
 
Of course, odds are that when you're watching it won't fail but that's to be expected... ;)
 
Mathew

---

### Post by Linuturk on 2007-02-13
I've been monitoring the system for a while, and I have started noticing a trend. The server's load will be reported as really high before the lockup. I believe I posted a graph that shows that trend above. 

It appears to be tied to snmpwalk polling the clients every 5 minutes. As you can imagine, 57 clients take a lot of resources to poll. Any tips on optimizing the default LAMP install on Ubuntu Dapper? Anyone with experience with Cacti that could help?

---

### Post by Linuturk on 2007-02-21
I've been working with the folks at the cacti forums. A suggestion by "TheWitness" gave me what seems to be the answer.

edit your php.ini file 
/etc/php5/apache2/php.ini 

and change the memory limit from 8M to something higher. I went to 128M. The problem hasn't happened again, but I will be sure to post if it does.

---

### Post by Linuturk on 2007-02-26
[http://forums.cacti.net/viewtopic.php?p=92977&sid=c8fc338d2ba51298d5b5358afd497e27#92977](http://forums.cacti.net/viewtopic.php?p=92977&sid=c8fc338d2ba51298d5b5358afd497e27#92977)

^^ Cacti Thread

There is good news and bad news.

The good news is, the server didn't lockup over the weekend.

The bad news is, the load of the machine is back up to 6.0 (and even spiked to 8.0)

I only have some 60 clients on this server, and the hardware specs are good. Is this kind of load normal?

---

### Post by TheWitness on 2007-02-28
Without seeing your Cacti log's, I can be of no help.

TheWitness

---

### Post by Linuturk on 2007-02-28
It seems I had the log files turned off. I have turned them back on, and I will post them after a few polls.

The server is running well, and with a small load, so this should be a good control to compare the logs when the server load skyrockets like it does.

```
View Cacti Log File [74 Items]
02/28/2007 03:47:41 PM - SYSTEM STATS: Time:160.5032 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:42:43 PM - SYSTEM STATS: Time:161.6720 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:37:43 PM - SYSTEM STATS: Time:161.5688 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:32:44 PM - SYSTEM STATS: Time:163.4598 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:27:41 PM - SYSTEM STATS: Time:159.4439 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:22:43 PM - SYSTEM STATS: Time:161.4384 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:17:42 PM - SYSTEM STATS: Time:160.4639 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:12:44 PM - SYSTEM STATS: Time:163.4158 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:07:43 PM - SYSTEM STATS: Time:161.4527 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 03:02:41 PM - SYSTEM STATS: Time:160.6004 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:57:43 PM - SYSTEM STATS: Time:162.4737 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:52:44 PM - SYSTEM STATS: Time:162.4884 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:47:44 PM - SYSTEM STATS: Time:162.4583 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:42:43 PM - SYSTEM STATS: Time:161.4498 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:37:43 PM - SYSTEM STATS: Time:161.4630 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:32:43 PM - SYSTEM STATS: Time:161.4282 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:27:42 PM - SYSTEM STATS: Time:161.4481 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:23:00 PM - SYSTEM STATS: Time:178.5352 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:17:43 PM - SYSTEM STATS: Time:161.4467 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:12:44 PM - SYSTEM STATS: Time:162.5388 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:07:42 PM - SYSTEM STATS: Time:159.4581 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 02:02:57 PM - SYSTEM STATS: Time:175.5144 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:57:39 PM - SYSTEM STATS: Time:158.4458 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:52:41 PM - SYSTEM STATS: Time:159.4567 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:47:41 PM - SYSTEM STATS: Time:159.4305 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:42:42 PM - SYSTEM STATS: Time:160.4698 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:37:41 PM - SYSTEM STATS: Time:159.4550 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:32:57 PM - SYSTEM STATS: Time:175.5218 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:27:42 PM - SYSTEM STATS: Time:161.4557 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:22:42 PM - SYSTEM STATS: Time:161.4727 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:17:56 PM - SYSTEM STATS: Time:174.5373 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:12:41 PM - SYSTEM STATS: Time:159.4387 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:07:43 PM - SYSTEM STATS: Time:161.4420 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 01:02:43 PM - SYSTEM STATS: Time:161.4543 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:57:58 PM - SYSTEM STATS: Time:176.5007 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:52:44 PM - SYSTEM STATS: Time:163.4559 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:47:47 PM - SYSTEM STATS: Time:165.4568 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:42:43 PM - SYSTEM STATS: Time:161.4372 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:38:02 PM - SYSTEM STATS: Time:180.4999 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:32:45 PM - SYSTEM STATS: Time:163.4517 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:27:45 PM - SYSTEM STATS: Time:163.4487 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:22:45 PM - SYSTEM STATS: Time:164.4572 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:17:44 PM - SYSTEM STATS: Time:162.4428 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:12:45 PM - SYSTEM STATS: Time:163.4519 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:08:02 PM - SYSTEM STATS: Time:180.5771 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 12:02:43 PM - SYSTEM STATS: Time:161.4568 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:57:43 AM - SYSTEM STATS: Time:161.4492 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:52:44 AM - SYSTEM STATS: Time:162.4503 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:47:59 AM - SYSTEM STATS: Time:177.5251 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:42:39 AM - SYSTEM STATS: Time:158.4745 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:37:40 AM - SYSTEM STATS: Time:159.4296 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:32:43 AM - SYSTEM STATS: Time:161.4635 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:27:41 AM - SYSTEM STATS: Time:159.4158 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:22:42 AM - SYSTEM STATS: Time:160.4785 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:17:41 AM - SYSTEM STATS: Time:159.4564 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:12:56 AM - SYSTEM STATS: Time:175.5429 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:07:39 AM - SYSTEM STATS: Time:158.4205 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 11:02:42 AM - SYSTEM STATS: Time:161.4123 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:58:10 AM - SYSTEM STATS: Time:188.5644 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:52:43 AM - SYSTEM STATS: Time:161.4341 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:47:41 AM - SYSTEM STATS: Time:159.4419 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:42:47 AM - SYSTEM STATS: Time:166.4707 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:37:40 AM - SYSTEM STATS: Time:159.4284 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:32:40 AM - SYSTEM STATS: Time:159.4297 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:27:42 AM - SYSTEM STATS: Time:160.4358 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:22:43 AM - SYSTEM STATS: Time:161.4591 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:18:05 AM - RECACHE STATS: RecacheTime:8.6465 HostsRecached:1
02/28/2007 10:17:56 AM - PCOMMAND: Poller[0] Host[59] WARNING: Recache Event Detected for Host
02/28/2007 10:17:56 AM - SYSTEM STATS: Time:174.5141 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:17:28 AM - CMDPHP: Poller[0] ASSERT: '85715114<10189' failed. Recaching host 'faia-189.FAIA.COM', data query #9
02/28/2007 10:17:28 AM - CMDPHP: Poller[0] ASSERT: '85715104<10179' failed. Recaching host 'faia-189.FAIA.COM', data query #8
02/28/2007 10:17:28 AM - CMDPHP: Poller[0] ASSERT: '85715094<10168' failed. Recaching host 'faia-189.FAIA.COM', data query #1
02/28/2007 10:12:42 AM - SYSTEM STATS: Time:160.4360 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
02/28/2007 10:07:52 AM - SYSTEM STATS: Time:170.5500 Method:cmd.php Processes:1 Threads:N/A Hosts:58 HostsPerProcess:58 DataSources:462 RRDsProcessed:203
```

Here is the control. The server maintained normal load during this log.

---

### Post by Linuturk on 2007-03-01
[http://pastebin.ca/377117](http://pastebin.ca/377117)

There are the logs at medium. requested in the other forum, but here for reference.

---

### Post by Linuturk on 2007-03-14
In the end, The Witness recommended I use Cactid instead of the PHP based poller. Unfortunately, the cacti-cacid package in dapper is broken. I've requested a backport, but they haven't got around to it yet.

---

