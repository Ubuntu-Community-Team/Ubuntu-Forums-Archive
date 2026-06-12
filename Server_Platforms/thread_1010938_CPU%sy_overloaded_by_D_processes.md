---
title: "CPU%sy overloaded by D processes"
date: 2008-12-14
forum: Server Platforms
---

### Post by Penteado on 2008-12-14
Hi there, 

   i have a server that is having a strange behavior while managing game processes... 

   The %sy is going wild over 60% when a bunch of CS(Counter Strike Game-servers) processes kicks in D state ... As you can see in the result of the top command, there are many processes that has the D state. When i kill one or two the server goes normal. 
 I also noticed that some processes has the same value on the SHR(shared memory?) column, if they share memory is it possible they go into a deadlock?

  How do i script something that kills automatically D state processes? is it possible ?


[SIZE="1"]```
top - 14:41:10 up 14:20,  3 users,  load average: 16.87, 16.71, 16.45
Tasks: 323 total,  20 running, 303 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.9%us, 68.5%sy,  0.2%ni, 14.5%id,  0.0%wa,  0.0%hi,  0.9%si,  0.0%st
Mem:   8178352k total,  8100056k used,    78296k free,   223936k buffers
Swap:  2031608k total,        4k used,  2031604k free,  3946560k cached

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
25390 gameserv  18   0  130m 109m 8568 S   90  1.4   6:59.23 hlds_i686          
23892 gameserv  16   0  166m  73m  13m R   40  0.9  12:57.65 srcds_i686         
24059 gameserv  16   0  168m  74m  13m D   39  0.9   8:41.79 srcds_i686         
17316 gameserv  18   0  205m 100m  15m R   37  1.3 134:51.17 srcds_i686         
17012 gameserv  18   0  205m 111m  13m D   37  1.4 140:25.41 srcds_i686         
17053 gameserv  18   0  187m  93m  13m D   37  1.2 140:32.78 srcds_i686         
17557 gameserv  18   0  186m  93m  12m R   37  1.2 138:31.43 srcds_i686         
18337 gameserv  18   0  163m  69m  13m R   37  0.9 128:23.82 srcds_i686         
16974 gameserv  18   0  163m  69m  13m S   36  0.9 138:16.88 srcds_i686         
16629 gameserv  18   0  164m  71m  13m R   36  0.9 139:00.25 srcds_i686         
17589 gameserv  18   0  164m  70m  13m D   36  0.9 135:31.43 srcds_i686         
18266 gameserv  17   0  163m  69m  13m R   36  0.9 128:41.68 srcds_i686         
16659 gameserv  18   0  202m  98m  15m R   35  1.2 139:16.25 srcds_i686         
17491 gameserv  18   0  157m  65m  12m R   35  0.8 135:17.11 srcds_i686         
18181 gameserv  18   0  163m  69m  13m D   35  0.9 128:31.84 srcds_i686         
15353 gameserv  18   0  157m  65m  12m R   34  0.8 151:30.41 srcds_i686         
 4203 gameserv  16   0 95700  80m 7480 R   12  1.0   4:24.22 hlds_i686         




```[/SIZE]

Thank You in advanced

---

### Post by Penteado on 2008-12-16
bump

---

