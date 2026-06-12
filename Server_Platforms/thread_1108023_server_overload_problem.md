---
title: "server overload problem"
date: 2009-03-27
forum: Server Platforms
---

### Post by islanddancer on 2009-03-27
Hi,

I have got another pretty old ubuntu dapper server running apache, postfix,
mailman, etc and there is a ruby script there for generating a download
statistics page for the website. 

the hardware is old, it has a 1G
mem, 2G swap, 1x2.4G P4 cpu etc.

now the load averge for the server is always above 4, somtimes about 6 and the ruby script is a major culprit for the overload. It is a cron job that runs several hours a day. I know the ultimate solution is to modify the ruby script to make it less resource hungry. But since I know nothing about ruby and I need a short term solution soon to get the load down.

I thought of renicing the cron job script to lower priority when the job started. But I don't know if there are other better ways to do this.

Thank you very much for any pointers.

Zhang

---

### Post by tubezninja on 2009-03-27
To help answer this question, we need to know what resource(s) the ruby script is taking up.  You could be low on RAM, or the CPU could be overloaded.  It might even be both.

ON the server itself, what is the output of 'free'?  This shuld tell us how much RAM is being used.

You can also find out CPU utilization by running the 'top' command.  The CPU usage should be up top, and you'll also see a list of the processes using the most resources.

---

### Post by islanddancer on 2009-03-27
> **scaredpoet said:**
> To help answer this question, we need to know what resource(s) the ruby script is taking up.  You could be low on RAM, or the CPU could be overloaded.  It might even be both.

ON the server itself, what is the output of 'free'?  This shuld tell us how much RAM is being used.

You can also find out CPU utilization by running the 'top' command.  The CPU usage should be up top, and you'll also see a list of the processes using the most resources.

             total       used       free     shared    buffers     cached
Mem:          1134       1117         16          0         12        584
-/+ buffers/cache:        520        614
Swap:         1961         76       1884

and the script is taking 40-50% percent of the cpu cycles...

---

