---
title: "Understanding the number of processes the user currently has running"
date: 2013-11-19
forum: Server Platforms
---

### Post by rax_m on 2013-11-19
Caveat: This is on a Redhat Linux system;)


Using the command 
```

> ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 62771
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 1024
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

I am able to see what the resource limitations of a user is. What I want to be able to view and monitor is how many processes the user currently has running out of a total of "max user processes".

I know that just counting the number of processes output by "ps" or "top" does not reflect the true number of processes. 

Does anyone know how I can view that value?

Thanks and regards
Rax

---

### Post by SeijiSensei on 2013-11-19
> **rax_m said:**
> I know that just counting the number of processes output by "ps" or "top" does not reflect the true number of processes.

Why not?  Got any references I can read?  What processes are missing from "ps aux | grep username"?

---

### Post by rax_m on 2013-11-22
Hi 

thanks for the reply. 

I don't have documentation around this, but if I perform the ps command I get the following:
```
 
[jbosssvc@xxxxx-jboss01 ~]$ ps aux | grep jbossuser | wc -l
11

```

And yet my JBoss server is not able to create new threads, when the max user processes = 1024.

However, if I increase the ulimit for max user processes then I am able create more threads.

So to me, the ps command is not reflecting the processes as determined by ulimit. 

Hope that clarifies it. 

Thanks
Rax

---

### Post by rax_m on 2013-11-22
So after a bit more research and tweaking my google search a bit I've found the answer I was looking for. :guitar:
[http://www.scottalanmiller.com/linux/2013/03/09/user-process-limits-preventing-fork-bombs/](http://www.scottalanmiller.com/linux/2013/03/09/user-process-limits-preventing-fork-bombs/)

What I was trying to understand was how to count not only the processes but also the LWP (kind of like threads) that a user had open. 

You can do it on RHEL using the command
```

ps h -Tu user | wc -l

```

Hope it helps someone else.

---

