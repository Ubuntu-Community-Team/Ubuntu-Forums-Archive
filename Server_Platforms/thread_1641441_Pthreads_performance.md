---
title: "Pthreads performance"
date: 2010-12-09
forum: Server Platforms
---

### Post by colinhercus on 2010-12-09
Hi,

I have a multi-threaded job on Ubuntu 10.4 Server that has 9 threads, one master distributing work to 8 other threads and I'm running this on an 8-core server. The master thread basically just does IO, almost no computation.

When I run this and view in top the process seems to get stuck at 700% CPU utilisation, never reaching 800%. when I display threads in top, two theads are stuck at 50% and 6 are at 100%.

top - 15:44:19 up  6:36,  1 user,  load average: 12.57, 11.38, 7.42
Tasks: 328 total,  13 running, 315 sleeping,   0 stopped,   0 zombie
Cpu(s): 87.5%us,  0.1%sy,  0.0%ni, 12.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  49499748k total,  3254432k used, 46245316k free,    65180k buffers
Swap: 19535000k total,        0k used, 19535000k free,  1290520k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
16528 colin     20   0 2016m 1.9g 1.1g R 99.9  4.0  13:03.27 novoalign 
16526 colin     20   0 2016m 1.9g 1.1g R 99.7  4.0  13:04.84 novoalign
16529 colin     20   0 2016m 1.9g 1.1g R 99.7  4.0  13:05.59 novoalign 
16530 colin     20   0 2016m 1.9g 1.1g R 99.7  4.0   9:44.57 novoalign
16532 colin     20   0 2016m 1.9g 1.1g R 99.7  4.0  13:05.49 novoalign
16533 colin     20   0 2016m 1.9g 1.1g R 99.7  4.0  11:16.16 novoalign
16527 colin     20   0 2016m 1.9g 1.1g R **49.7**  4.0  10:44.29 novoalign 
16531 colin     20   0 2016m 1.9g 1.1g R **49.7**  4.0   9:11.88 novoalign        

It looks like Ubuntu is keeping one CPU reserved for other jobs but there is nothing else running on the system so why can't   we use all the cores?

Is there some config parameter I can change to get all cores working?

Thanks, Colin

---

