---
title: "Memory leak on 8.08 LTS server"
date: 2008-07-02
forum: Server Platforms
---

### Post by paj26 on 2008-07-02
I'm running 8.08 LTS, apache2 with php5, rails, and mysql. I have to restart about every 24 hrs as the memory slowly gets eaten up. Watching top, it jumped about 100mb in less than an hour. How can I diagnose/trace this? I'm running apache 2.2.8

---

### Post by robgolding63 on 2008-07-02
Is the swap being used at all? If not, this is just the way Linux handles the memory. I just tried quickly to find an article for you but haven't had any success.

Basically, you can expect to see 98-99% memory usage on a Linux server, without alarm. If the swap starts being used then you know you have a problem. Thinking about it, this behavior makes perfect sense - the RAM is the fastest storage available to the system, so why not use it as much as possible? If another application requires some RAM, the O/S will release it as needed.

Hope this helps!

Rob

---

### Post by paj26 on 2008-07-02
Not sure about swap space, I'll let you know tomorrow. I thought with a server running just those processes that once they were started, that the memory usage should be relatively constant, but I'm not an expert on it. Thanks for the info

---

### Post by windependence on 2008-07-02
[http://thelinuxnewbie.blogspot.com/2006/08/linux-uses-too-much-memory-very-basic.html](http://thelinuxnewbie.blogspot.com/2006/08/linux-uses-too-much-memory-very-basic.html)

[http://www.novell.com/coolsolutions/qna/2327.html](http://www.novell.com/coolsolutions/qna/2327.html)

[http://softwaretracker.blogspot.com/2007/08/understand-why-linux-uses-up-all-memory.html](http://softwaretracker.blogspot.com/2007/08/understand-why-linux-uses-up-all-memory.html)

HTH,

-Tim

---

### Post by paj26 on 2008-07-11
Here's what top looks like right now...

top - 07:43:07 up 1 day, 10:33,  2 users,  load average: 0.02, 0.03, 0.00
Tasks: 114 total,   2 running, 112 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.3%us,  0.3%sy,  0.0%ni, 96.7%id,  0.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3631392k total,  3463588k used,   167804k free,    93872k buffers
Swap:   995988k total,    38656k used,   957332k free,  1826596k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                              
21398 david     20   0 49204  35m 2400 S  1.3  1.0   1:48.46 ruby1.8                                                                                               
 7959 david     20   0 48020  34m 2396 S  0.7  1.0   0:41.26 ruby1.8                                                                                               
 9648 www-data  20   0 23056 8036 4220 S  0.7  0.2   0:00.28 apache2                                                                                               
 9687 www-data  20   0 23632 7932 4036 S  0.7  0.2   0:00.12 apache2                                                                                               
 9735 www-data  20   0 23632 8124 4060 S  0.7  0.2   0:00.12 apache2                                                                                               
 9745 www-data  20   0 23088 7708 3936 S  0.7  0.2   0:00.04 apache2                                                                                               
    1 root      20   0  2980 1864  544 S  0.0  0.1   0:01.02 init                                                                                                  
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                              
    3 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                                                           
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.02 watchdog/0       ....

---

### Post by hyper_ch on 2008-07-11
(1) use [noparse]```

```[/noparse] brackets... makes it easier to read
(2) what does ```
free -m
``` return?

---

### Post by paj26 on 2008-07-11
```
$ free -m
                 total       used       free     shared    buffers     cached
Mem:       3546       3373        172          0        132       1682
-/+ buffers/cache:       1559       1986

```

If I have free memory, why would it go into swap, unless it puts idle processes into swap?

---

### Post by hyper_ch on 2008-07-11
as you can see 1.6 gb ram is cache....

unused ram is wasted ram.

---

