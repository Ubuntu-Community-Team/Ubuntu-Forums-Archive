---
title: "Server Slows and MySQL Stops"
date: 2011-11-06
forum: Server Platforms
---

### Post by MickSulley on 2011-11-06
I have a problem with my LAMP server running Ubuntu 10.10 server.  It is a home system used for file storage and controlling my heating system.  It has been running happily for a couple of years but I had felt it had slowed down a bit over the last few weeks and yesterday MySQL stopped.  I rebooted and it ran for about an hour, then MySQL stopped again.  Top showed high load and zero available swap space.

I suspected AVG as the cause as I was seeing multiple avg* processes running, so I tried to remove it, but in 'top' I still sometimes see many avgscand processes running.  How do I remove them?

I am very inexperienced in diagnosing server problems, I have looked at various log files but don't really know what I am looking at.  In kern.log.1 I have found 
> 
Nov  5 23:29:38 solar kernel: [ 7094.253392] Out of memory: kill process 16758 (avgscand) score 4134 or a child
Nov  5 23:29:38 solar kernel: [ 7094.256393] Killed process 16758 (avgscand) vsz:264612kB, anon-rss:158264kB, file-rss:0kB
which doesn't look good.

Is there a way to test the hardware?  Could it be a memory failure?  What else can I do to diagnose the problem?

Thanks
Mick

---

### Post by ian dobson on 2011-11-06
Hi,

Just run top and see what process it eating all your memory.

to kill all processes with a specific name, just use:-

kill -9 processname

Regards
Ian Dobson

---

### Post by MickSulley on 2011-11-06
It all looks OK now.  Looking back through the kern.log files it seems that 'Out of memory' messages have been quite frequent.  I am guessing that this should not happen unless something has gone wrong, is there any way I can look back through the logs to see what it was?

When this happens how does it decide what to kill?  

Thanks 
Mick

---

### Post by ian dobson on 2011-11-06
Hi,

The oom (out of memory) killer looks at all processes looking at the amount of memory a process is actually using, process owner, memory used by child processes and several other factors to see what process to kill.

What hardware is your server running on? If possible try adding more memory, that would be the easiest solution.

Regards
Ian Dobson

---

### Post by MickSulley on 2011-11-06
The hardware is pretty low spec and yes I agree that more memory should fix it, but I am really interested to find out what caused it.  It runs some python code that controls my heating system, holds a load of files and that is about it, so it isn't doing much.  

As I said earlier I suspect AVG caused it, I have removed it now (I think/hope!) so I will try to recreate the situation as it was when it broke and see what happens.

Thanks for your help
Mick

---

### Post by ian dobson on 2011-11-06
Hi,

Try typing

locate avgscand

from the terminal prompt, just to see if the avg scanner deamon is really deinstalled.

free will show how much memory your system is using,  ps -aux how much memory each process is using.

Regards
Ian Dobson

---

