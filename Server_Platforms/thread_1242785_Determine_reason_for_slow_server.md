---
title: "Determine reason for slow server"
date: 2009-08-17
forum: Server Platforms
---

### Post by KayakJim on 2009-08-17
My web server running Ubuntu 8.04 Hardy 64-bit is suddenly running extremely slow.

Running "top", displays "load average: 45.87, 53.10, 58.16" with a lot (~15) of apache2 processes.

Running ps aux | grep 'apache2' just returns a lot of "/usr/sbin/apache2 -k start"

Is it possible to determine exactly what is slowing my server down and what all those "/usr/sbin/apache2 -k start" processes are actually running?

---

### Post by jocampo on 2009-08-17
Can you please copy/paste or post your TOP result? ...

---

### Post by KayakJim on 2009-08-17
I restarted the apache process and that seems to have corrected the issue. 

I would still like to know how to determine exactly what was running that was slowing my server down.

@jocampo, output from top (please note this was after restarting apache):
```
top - 13:47:46 up 19 days, 10 min,  1 user,  load average: 0.56, 0.55, 0.59
Tasks: 127 total,   1 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.8%us,  1.0%sy,  0.0%ni, 95.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   7872040k total,  7523224k used,   348816k free,     9560k buffers
Swap:        0k total,        0k used,        0k free,  6148520k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                     
18388 www-data  15   0  381m  24m  14m S    5  0.3   0:00.15 apache2                      
18389 www-data  15   0  380m  21m  13m S    1  0.3   0:00.04 apache2                      
 1508 mysql     15   0  999m 428m 7272 S    1  5.6  82:38.26 mysqld                       
18362 www-data  16   0  381m  23m  14m S    1  0.3   0:00.21 apache2                      
18364 www-data  15   0  383m  27m  16m S    1  0.4   0:01.53 apache2                      
18320 www-data  15   0  384m  33m  21m S    0  0.4   0:02.96 apache2                      
    1 root      15   0  4068  892  592 S    0  0.0   0:00.68 init                         
    2 root      RT   0     0    0    0 S    0  0.0   0:00.12 migration/0                  
    3 root      34  19     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0                  
    4 root      RT   0     0    0    0 S    0  0.0   0:00.04 watchdog/0                   
    5 root      10  -5     0    0    0 S    0  0.0   0:00.56 events/0                     
    6 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                      
    7 root      12  -5     0    0    0 S    0  0.0   0:00.00 kthread                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 xenwatch                     
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 xenbus                       
   17 root      RT  -5     0    0    0 S    0  0.0   0:00.04 migration/1                  
   18 root      34  19     0    0    0 S    0  0.0   0:00.30 ksoftirqd/1                  
   19 root      RT  -5     0    0    0 S    0  0.0   0:00.02 watchdog/1                   
   20 root      10  -5     0    0    0 S    0  0.0   0:00.35 events/1                     
   50 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                    
   51 root      10  -5     0    0    0 S    0  0.0   0:00.03 kblockd/1                    
   52 root      20  -5     0    0    0 S    0  0.0   0:00.00 cqueue/0                     
   53 root      10  -5     0    0    0 S    0  0.0   0:00.00 cqueue/1                     
```

---

### Post by jocampo on 2009-08-17
:( ... sad my friend, why you restarted the server? basic rule, servers should not be restarted, avoid press that button as a plague. Now is going to be more difficult to troubleshoot.

Yeah, that TOP screenshoot looks ok, no problems there... please post again if you got problems, but don't reboot ;-) ...at least, get as much info as you can before press the button

---

### Post by KayakJim on 2009-08-17
> **jocampo said:**
> :( ... sad my friend, why you restarted the server? basic rule, servers should not be restarted, avoid press that button as a plague. Now is going to be more difficult to troubleshoot.
I only restarted the apache process not the entire server. ;)

Is there any command that you can think of that would tell me what the "/usr/sbin/apache2 -k start" was for (e.g. a particular script, file, etc.)?

---

