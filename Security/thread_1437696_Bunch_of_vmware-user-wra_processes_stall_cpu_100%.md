---
title: "Bunch of vmware-user-wra processes stall cpu 100%"
date: 2010-03-24
forum: Security
---

### Post by totalz on 2010-03-24
this is scary, bunch of vmware-user-wra processes stall cpu 100%!!

What's going on?  Server has just been restarted!

Before I restarted, the root started all this [B]vmware-user-wra!!
[/B]I was configuring vncserver!

After restart, it's started by user roo300 which I have used to login via SecureShell!

```

top - 20:20:29 up 4 min, 85 users,  load average: 76.57, 35.14, 13.60
Tasks: 629 total,  90 running, 539 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5%us, 98.5%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3873304k total,   369500k used,  3503804k free,    50492k buffers
Swap:  1309256k total,        0k used,  1309256k free,    47516k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                           
 4492 roo300    20   0  1872  528  444 R    5  0.0   0:10.78 vmware-user-wra                   
 4508 roo300    20   0  1872  524  444 R    5  0.0   0:10.74 vmware-user-wra                   
 4554 roo300    20   0  1872  524  444 R    5  0.0   0:10.00 vmware-user-wra                   
 5047 roo300    20   0  1872  524  444 R    5  0.0   0:04.32 vmware-user-wra                   
 5207 roo300    20   0  1872  528  444 R    5  0.0   0:02.51 vmware-user-wra                   
 5345 roo300    20   0  1872  528  444 R    5  0.0   0:01.02 vmware-user-wra                   
 4444 roo300    20   0  1872  524  444 R    5  0.0   0:11.37 vmware-user-wra                   
 4451 roo300    20   0  1872  524  444 R    5  0.0   0:11.24 vmware-user-wra                   
 4481 roo300    20   0  1872  528  444 R    5  0.0   0:10.72 vmware-user-wra                   
 4495 roo300    20   0  1872  524  444 R    5  0.0   0:10.75 vmware-user-wra                   
 4518 roo300    20   0  1872  528  444 R    5  0.0   0:10.29 vmware-user-wra                   
 4532 roo300    20   0  1872  524  444 R    5  0.0   0:10.17 vmware-user-wra                   
 4535 roo300    20   0  1872  524  444 R    5  0.0   0:10.21 vmware-user-wra                   
 4541 roo300    20   0  1872  524  444 R    5  0.0   0:10.20 vmware-user-wra                   
 4570 roo300    20   0  1872  524  444 R    5  0.0   0:09.90 vmware-user-wra                   
 4574 roo300    20   0  1872  528  444 R    5  0.0   0:09.95 vmware-user-wra                   
 4836 roo300    20   0  1872  528  444 R    5  0.0   0:06.99 vmware-user-wra                   
 4408 roo300    20   0  1872  528  444 R    5  0.0   0:12.58 vmware-user-wra                   
 4421 roo300    20   0  1872  524  444 R    5  0.0   0:12.73 vmware-user-wra                   
 4425 roo300    20   0  1872  528  444 R    5  0.0   0:12.03 vmware-user-wra                   
 4432 roo300    20   0  1872  524  444 R    5  0.0   0:11.74 vmware-user-wra                   
 4436 roo300    20   0  1872  524  444 R    5  0.0   0:11.70 vmware-user-wra                   
 4458 roo300    20   0  1872  528  444 R    5  0.0   0:11.10 vmware-user-wra                   
 4462 roo300    20   0  1872  528  444 R    5  0.0   0:11.11 vmware-user-wra                   
 4467 roo300    20   0  1872  524  444 R    5  0.0   0:11.17 vmware-user-wra                   
 4472 roo300    20   0  1872  524  444 R    5  0.0   0:10.97 vmware-user-wra                   
 4478 roo300    20   0  1872  524  444 R    5  0.0   0:10.94 vmware-user-wra                   
 4484 roo300    20   0  1872  524  444 R    5  0.0   0:10.61 vmware-user-wra                   
 4517 roo300    20   0  1872  528  444 R    5  0.0   0:10.43 vmware-user-wra                   
 4519 roo300    20   0  1872  524  444 R    5  0.0   0:10.23 vmware-user-wra                   
 4520 roo300    20   0  1872  528  444 R    5  0.0   0:10.39 vmware-user-wra                   
 4521 roo300    20   0  1872  528  444 R    5  0.0   0:10.19 vmware-user-wra                   
 4526 roo300    20   0  1872  524  444 R    5  0.0   0:10.09 vmware-user-wra                   
 4529 roo300    20   0  1872  524  444 R    5  0.0   0:10.24 vmware-user-wra                   
 4531 roo300    20   0  1872  528  444 R    5  0.0   0:10.19 vmware-user-wra                   
 4545 roo300    20   0  1872  528  444 R    5  0.0   0:09.98 vmware-user-wra                   
 4550 roo300    20   0  1872  524  444 R    5  0.0   0:09.99 vmware-user-wra                   
 4559 roo300    20   0  1872  528  444 R    5  0.0   0:09.94 vmware-user-wra                   
 4561 roo300    20   0  1872  524  444 R    5  0.0   0:09.87 vmware-user-wra                   
 4562 roo300    20   0  1872  528  444 R    5  0.0   0:09.96 vmware-user-wra                   
 4569 roo300    20   0  1872  524  444 R    5  0.0   0:09.89 vmware-user-wra                   
 4575 roo300    20   0  1872  528  444 R    5  0.0   0:09.86 vmware-user-wra                   
 4576 roo300    20   0  1872  528  444 R    5  0.0   0:09.74 vmware-user-wra 

```

---

### Post by CharlesA on 2010-03-24
I sure hope you secured VNC.

Looks like you got hit with a forkbomb or something similar (or something just cracked yer box).

---

### Post by totalz on 2010-03-24
Actually whenever I start vncserver, sth sill forks up this vmware-user-wra non-stop!

---

