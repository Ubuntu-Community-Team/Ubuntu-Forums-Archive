---
title: "Limit memory available to processes to avoid system death"
date: 2009-02-24
forum: Ubuntu Brainstorm
---

### Post by michaeljt on 2009-02-24
Not sure if this really belongs here, but here goes...

My system has 2GB RAM and 1GB swap, which is the default amount created by Ubuntu.  This should be a sensible configuration, but it has a big disadvantage: a runaway process can bring the system to a halt (I have left it for an hour in such a situation to see if it recovered, but no luck) by allocating memory until the system starts thrashing.  With 1GB of swap, this can go on for a long time.  If processes are not allowed to allocate more memory than 80% of physical RAM (I tested this quickly using ulimit -v) then the system becomes much more stable.  (Note that sysctl -w vm.overcommit_memory=2 does nothing to help here.)  However, setting such a ulimit by default is not an option, as it prevents some software, such as Wine, from working as it should (Wine needs to control the first 3.6GB of its address space to properly emulate Windows behaviour).  Does anyone familiar with this stuff have cleverer solutions to deal with this, that could be applied by default?

---

### Post by smartboyathome on 2009-02-24
You should report this when it happens, as it is usually a memory leak in some program. I don't think the solution is to limit memory, but to limit processes. When I run htop, I usually see big apps have more than one process in the table.

---

### Post by michaeljt on 2009-02-24
I did report the most reliable way I found to reproduce this (gnash on a particular webpage).  At least the part of gnash which was "running away" was a single process, which went on expanding until the system started thrashing to death.  You are right though, that that is just one way that this can occur (several large processes running in parallel can also trigger it).  Perhaps the better way is just to propose more appropriate values for the amount of swap on the system.

---

### Post by smartboyathome on 2009-02-24
Or, perhaps, help fix the projects? I haven't had any run away processes, and gnash is alpha software, so I would suggest getting involved with gnash instead of limiting the many because of the few.

---

### Post by michaeljt on 2009-02-24
Perhaps you have misunderstood me somewhat - I am talking about the robustness of the underlying system here.  Perhaps you use your system in different ways to me, but this "swap to death" is something that does happen to me on quite a regular basis, under different circumstances.  On the whole, it is something that I would expect a solid system to prevent, even if individual processes do misbehave (Windows 3.0 was also reliable if all processes behaved...).  Just as a modern Linux system (and presumably most others) protect you against fork bombs, even if a good application will never trigger a fork bomb.

---

### Post by smartboyathome on 2009-02-24
> **michaeljt said:**
> Perhaps you have misunderstood me somewhat - I am talking about the robustness of the underlying system here.  Perhaps you use your system in different ways to me, but this "swap to death" is something that does happen to me on quite a regular basis, under different circumstances.  On the whole, it is something that I would expect a solid system to prevent, even if individual processes do misbehave (Windows 3.0 was also reliable if all processes behaved...). 

You can always set swappiness to a lesser value. Swap isn't the problem, though, gnash is. So doing something like this won't prevent it.

> **michaeljt said:**
> Just as a modern Linux system (and presumably most others) protect you against fork bombs, even if a good application will never trigger a fork bomb.

Last time I tried it, neither Ubuntu, Arch Linux, nor Puppy Linux prevented fork bombs (yes, I tried on all 3). They all don't limit processes by default.

---

### Post by movieman on 2009-02-24
> **michaeljt said:**
> On the whole, it is something that I would expect a solid system to prevent, even if individual processes do misbehave (Windows 3.0 was also reliable if all processes behaved...).

What exactly do you expect an operating system to do when it runs out of memory?

Note that you can set a memory size limit when starting a process if you don't want it to use too much; if you don't specify a limit, is the operating system supposed to guess that you really meant that you wanted a limit?

Seriously, this is a very difficult problem and there's no good 'one size fits all' solution to it; when you run out of resources you run out of resources.

---

### Post by michaeljt on 2009-02-25
> **movieman said:**
> What exactly do you expect an operating system to do when it runs out of memory?

Note that you can set a memory size limit when starting a process if you don't want it to use too much; if you don't specify a limit, is the operating system supposed to guess that you really meant that you wanted a limit?

Seriously, this is a very difficult problem and there's no good 'one size fits all' solution to it; when you run out of resources you run out of resources.

Basically, what I am looking for is better ways of spotting the problem before it becomes critical and taking whatever steps are needed to avoid it.  As I wrote in my initial post, at least setting a general memory limit using ulimit -v causes Wine and probably other software not to work.  Since at least in the case of Wine this is a false positive (I will look at its code when I have time to see if this can be fixed there) I am looking for ways to refine this process.

---

### Post by lithorus on 2009-02-25
Look into memlockd. From the apt description :
> When a system starts paging excessively it may be impossible for the sysadmin to login for the purpose of killing the runaway processes (sometimes the login program times out due to thrashing).  Memlockd allows important system files (such as /bin/login, /bin/getty, and the admin shell) to be locked in memory so that there will be no delay in accessing executable pages.  In my tests this can decrease the time required for the administrator to login on a thrashing system by a factor of more than 3.

---

### Post by movieman on 2009-02-25
> **michaeljt said:**
> Basically, what I am looking for is better ways of spotting the problem before it becomes critical and taking whatever steps are needed to avoid it.

And what do you expect it to do? Do you want the operating system to start randomly killing processes _before_ it runs out of memory? You could adopt the Windows 'I'm going to expand your swap file to 100GB' approach, but that still doesn't help for long with a rogue process allocating all the memory it can... in fact, the results could be worse if your important system processes get swapped out to make space for the rogue process.

---

