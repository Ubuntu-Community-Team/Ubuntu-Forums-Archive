---
title: "Ubuntu 14.04LTS web server randomly freezes every 1 or 2 days"
date: 2016-01-02
forum: Server Platforms
---

### Post by rob134 on 2016-01-02
So already for 1 or 2 weeks now the server freezes on random times without any apparent reason. I went through apache's, mysql and php logs to see if I could find anything of suspicion but did not find anything.
I can ping the server without problem. Connecting SSL,FTP or making any other connection attempt fails. I can only reboot the server (which takes 5 or 10minutes for it to stop and restart) from the hosts' website control panel. Also from that control panel it monitors the CPU load - this always shows 100% from the time it freezes and staying at a 100%.
How can I troubleshoot this?

Thanks!

---

### Post by tripp98 on 2016-01-03
ssh to the server and run top.  what service is using 100%?

---

### Post by MAFoElffen on 2016-01-03
> **tripp98 said:**
> ssh to the server and run top.  what service is using 100%?
While in top, hit <Shift><f>, then press the Letter corresponding to %MEM, then <Enter>

Yoou could also 
```

ps -eo pmem,pcpu,vsize,pid,cmd | sort -k 1 -nr | head -10

```
Which will show the top 10 process sorted by memory use...

2 things to check for that relate to intermittent Apache freezes, modules loaded (memory use) and cron jobs that ran previous to the freeze. Turn off any unused modules. 

If you are using any Python v2.3 web apps, then you might be using the daemon mode of mod_wsgi and have it configured. If so, there is an issue with that module, where you might have to check for threading problems that might require you to periodically forcibly restarting some processes. The issue ticket on this problem says it will run for a couple days, then freeze... One of the work arounds is to force a specific WSGI application to be run within the very first Python sub interpreter created when Python is initialised, the WSGIApplicationGroup directive should be used and the group set to '%{GLOBAL}'.```

WSGIApplicationGroup %{GLOBAL}

```
One last thing to check for in your logs, is that your max limits are not being "maxed." A few options that will cause a freeze when reached are MaxClients, and ThreadsPerChild. But if you do reach one of those limits, your log is going to have an error message similar to this:
```

server reached MaxClients setting, consider raising the MaxClients setting

```
One thing that might help other here, help you, when they see your output ... is to post your Apache config/settings files, which would be httpd.conf, and any includes that branch off from that file.

---

### Post by SeijiSensei on 2016-01-04
How much memory does this machine have?  How much traffic is it handling?

If you're running your own scripts that use PHP to access the MySQL database, have you created all the necessary database indexes to match the queries you make? In particular, if you're using WHERE clauses with multiple fields, do you have a corresponding index that uses all those fields as well?

```
SELECT * from sometable WHERE field1='x' AND field2='y' AND field3='z';
```

will only work efficiently if you have created an index on all three fields.  In PostgreSQL, which I use, I create the index like this:

```
CREATE INDEX some_index_name ON sometable (field1,field2,field3);
```

I'm sure MySQL has a similar command.

---

### Post by rob134 on 2016-01-07
> **tripp98 said:**
> ssh to the server and run top.  what service is using 100%?

When the server freezes ssh is unreachable. It froze again last night and had to give it a reboot. I'll try using the web-based terminal(not sure what the official term is) next time to see if I can input any commands.
Basically when it freezes I have no access to ssh, ftp, although pinging still works. I'll have to wait for it to freeze again so I can try running top.

I just turned on email notification for new messages, hence the late reply. 

Thanks!

---

### Post by MAFoElffen on 2016-01-08
So... When it freezes >> Then it is too late. If you can ping, but not shh, then you could not do any commands like top or ps to diagnose at the time (right?)

One of the hardest things to deal with is to try to re-create an intermittent problem. Next is to try to diagnose an intermittent problem. With this, when it locks up, it is unreachable to diagnose. When you reboot, that condition that caused the lockup is gone. 

The only idea that come to mind is to create a script that intermittently checks your stats and appends it to a log file. Yes, a bit more memory and disk, but may be a way to do unattended monitoring. It could be done over ssh remotely, but that would keep that port open while that monitoring is going on. When you can re-create the condition, we do traces and back-traces to see what is going on ... but since this condition takes 2-3 days for it to happen, a trace might be too much info to try to capture. But a log fed at intervals ... might work.

---

### Post by Habitual on 2016-01-08
> **MAFoElffen said:**
> The only idea that come to mind is to create a  script that intermittently checks your stats and appends it to a log  file.
Or they could usr sar from the sysstat package?

---

### Post by rob134 on 2016-01-14
> **MAFoElffen said:**
> but since this condition takes 2-3 days for it to happen, a trace might be too much info to try to capture. But a log fed at intervals ... might work.
> **Habitual said:**
> Or they could usr sar from the sysstat package?
Thanks. I have sysstat updating log file every 2min now.

It doesn't really show CPU usage per process like top does. So I've created a script that creates top 10 CPU+Memory usage per process every 60min and saves it in a log file. That should give me more insight.

When it froze up yesterday I managed to login the terminal, which is unresponsive, and showed the following messages (see screenshot)[ATTACH=CONFIG]266759[/ATTACH] - not sure what it means.

---

### Post by rob134 on 2016-01-14
According to this [article]("http://www.blackmoreops.com/2014/09/22/linux-kernel-panic-issue-fix-hung_task_timeout_secs-blocked-120-seconds-problem/")
I've set:
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10

To avoid the 120sec timeout. Let's pray to see if that will help!

---

### Post by rob134 on 2016-01-18
> **rob134 said:**
> According to this [article]("http://www.blackmoreops.com/2014/09/22/linux-kernel-panic-issue-fix-hung_task_timeout_secs-blocked-120-seconds-problem/")
I've set:
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10

To avoid the 120sec timeout. Let's pray to see if that will help!

No luck. It actually crashes every day now instead of every 2-4 days. 
I have also set 
```
kernel.hung_task_panic = 1
kernel.hung_task_timeout_secs = 300
kernel.panic = 10

```
in sysctl.conf which should restart the server when there's a kernel panic. But instead it's turning the server off and not turning it on when this happens. 
How come it doesn't restart?
[ATTACH=CONFIG]266826[/ATTACH]

---

### Post by SeijiSensei on 2016-01-19
This sounds more like a memory problem.  Have you run memtest?  You'll have to contend with taking the server offline for a day or two.

I long ago abandoned using my own hardware in favor of virtual servers at [Linode]("http://www.linode.com/").

---

### Post by MAFoElffen on 2016-01-21
+1

Memory <-- that is what I was wondering. 

A couple years ago, one of my IBM XServers would go for a couple days and then freeze with an NMI error. It drove me batty trying to trace that problem. I even swapped disks to run Ubuntu Server 1404LTS 32bit, Win Server 2012R2, Rhel...

A memory test found that a RAM chip in the very last bank... when memory paging got high enough, it would make it to that part of that chip. And it was fairly new ECC Registered memory. I felt like a fool. Been there.

---

