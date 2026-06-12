---
title: "memory usage - understanding free command"
date: 2009-07-09
forum: Server Platforms
---

### Post by nix4me on 2009-07-09
I don't quite understand the output of the free command.  I have a dedicated server running in a datacenter and I am unsure if I need more memory or not.  Here is the output of the free command:

# free
             total       used       free     shared    buffers     cached
Mem:        507280     483332      23948          0       4312     181132
-/+ buffers/cache:     297888     209392
Swap:      1015800      38528     977272

Do I truly only have 23K of free memory?  Or is the cached amount available too?  How do I read the output to understand when i need to consider getting more memory?

---

### Post by bab1 on 2009-07-09
Thy using this:```
free -mt
```

This displays the memory in megabytes and with a total.  If you wish you can use g instead of the m and it will read in gigabytes.

Mine displays as```
             total       used       free     shared    buffers     cached
Mem:           344        336          8          0         18         86
-/+ buffers/cache:        231        113
Swap:         1427        103       1323
Total:        1772        440       1332

```

The total line is useful here.  I only have (roughly) 350 Meg if RAM on this host along with 1 GB of swap.  The physical RAM will be used until there is a need to swap data to disk to accommodate more recent activity.  Using most of the RAM is not a cause for concern until there is excessive disk I/O from using swap.

---

### Post by thegeekscope on 2012-09-05
A very nice explanation of Linux free command output can be found here

[http://www.thegeekscope.com/check-linux-memory-usage-using-free-command/](http://www.thegeekscope.com/check-linux-memory-usage-using-free-command/)

Hope this will be helpful.

---

### Post by SeijiSensei on 2012-09-05
Linux will try and use all of the available physical memory.  What is not being used by programs is used to cache disk operations.  If you open additional programs, then the cache figure will decline as that memory is allocated to the new programs.  Your figures suggest you have around 300 MB in use by the OS and programs, and 180 MB being used to cache files.

Then there is swap.  Most of your swap is not in use, which is a good state of affairs.  Some components of the Linux kernel swap themselves out after being run at boot.  They account for that 30MB or so of your swap in use.  The result is idle.

I generally use the **top** command to get a quick overview of the state of a machine.  To see everything you could possibly want to know about memory, run the command "cat /proc/meminfo".

You are nowhere near the situation where the machine is starved for memory.

---

### Post by Cheesemill on 2012-09-05
A good explanation can be found here:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by sisco311 on 2012-09-05
[[img]http://ompldr.org/tYzBtcQ[/img]](http://ompldr.org/vYzBtcQ)

---

