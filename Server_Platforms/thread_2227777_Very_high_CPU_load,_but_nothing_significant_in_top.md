---
title: "Very high CPU load, but nothing significant in top"
date: 2014-06-03
forum: Server Platforms
---

### Post by rob67 on 2014-06-03
I'm running Ubuntu Linux 12.04.1, with VirtualMin 4.08.gpl GPL and 2 CPU cores.


  Pretty much all the time for the last few weeks, it's been running at  well above load average of 5, usually up closer to 10, sometimes  reaching 20.


  Right now, CPU load averages: 9.20 (1 min) 8.20 (5 mins) 7.81 (15 mins) 


  At the same time, VirtualMin returns:


  Virtual Memory: 996 MB total, 15.44 MB used  
Real Memory: 3.80 GB total, 972.43 MB used 
Local disk space: 915.94 GB total, 116.03 GB used 


  Have restarted (shutdown -rf now) the machine a few times and sure enough sooner or later we're back up with high CPU loads.


  Running top (or htop) returns nothing significant at all running at  high CPU - in fact watching it for a few minutes and the highest item  would maybe high 3% CPU.


  Top returns this also:
  Cpu(s):  2.2%us,  1.2%sy,  0.0%ni,  0.0%id, 96.5%wa,  0.0%hi,  0.2%si,  0.0%st


  The %wa concerns me as it's so high - seems to stay up above 80%.


  I understand this is % in wait, but not sure what that means in practical terms.


  Where can I start to debug this and figure out what's causing the high CPU load?


  Thanks in advance

---

### Post by sandyd on 2014-06-04
You have high iowait
Use something like
```

iotop
```
to see what is causing the issue.

---

### Post by thnewguy on 2014-06-04
The high wait percentage suggests your system spends a lot of time waiting for disk (or other IO) reads/writes. As sandyd suggested above, take a look at iotop and see what process is blocking input/output.

---

### Post by rob67 on 2014-06-04
Thanks for the replies.

itop returns:

INT                NAME          RATE             MAX
 42 [MSI-edge      ahci]   107 Ints/s     (max:   416)
 43 [MSI-edge      eth0]    11 Ints/s     (max:    93)

That's it...

Rate fluctuates between 40ish and 160ish for INIT 42, and 3 and 25 for INIT 34

No idea what this means sorry!

Thanks

Currently have a load average of about 11.

---

### Post by rob67 on 2014-06-04
I also ran TOP to ID "D" status processes:

top - 09:06:33 up 6 days, 19:55,  4 users,  load average: 20.79, 17.90, 13.76
Tasks: 232 total,   1 running, 208 sleeping,  23 stopped,   0 zombie
Cpu(s):  4.4%us,  9.3%sy,  1.3%ni, 10.8%id, 73.9%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3983680k total,  1878180k used,  2105500k free,   378640k buffers
Swap:  1019900k total,    21000k used,   998900k free,   594768k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  235 root      20   0     0    0    0 D    0  0.0  43:59.91 flush-8:0
12488 root      20   0  4312  968  668 D    0  0.0   0:02.70 updatedb.mlocat
21169 root      20   0 65208  58m 1948 D    0  1.5   0:15.33 /usr/share/webm
27808 munin     20   0 22268 9892 1640 D    0  0.2   0:00.14 /usr/share/muni
28859 root      20   0  4536 1008  716 D    0  0.0   0:00.13 chown
28904 root      20   0  4472  764  656 D    0  0.0   0:00.03 chown
28905 root      20   0  4472  760  656 D    0  0.0   0:00.03 chown
29099 root      20   0  4472  764  656 D    0  0.0   0:00.01 chown
29103 root      20   0  4472  764  656 D    0  0.0   0:00.00 chown
29107 root      20   0  4472  760  656 D    0  0.0   0:00.03 chown
29110 root      20   0  2848 1196  864 R    0  0.0   0:00.00 top
29162 root      20   0  4472  764  656 D    0  0.0   0:00.00 chown
29165 root      20   0  4472  764  656 D    0  0.0   0:00.00 chown
29166 root      20   0  4472  760  656 D    0  0.0   0:00.00 chown
29168 root      20   0  4472  764  656 D    0  0.0   0:00.00 chown
29172 root      20   0  4472  764  656 D    0  0.0   0:00.00 chown
29173 root      20   0  4472  760  656 D    0  0.0   0:00.00 chown
29175 root      20   0  4472  760  656 D    0  0.0   0:00.00 chown
29176 root      20   0  4472  760  656 D    0  0.0   0:00.00 chown
29178 root      20   0  4472  760  656 D    0  0.0   0:00.00 chown
Total: 20

The first line, flush-8:0 seems a bit dubious, with a TIME+ of 44  hours... Not sure what this is or what to do about it though...

---

### Post by sandyd on 2014-06-09
> **rob67 said:**
> Thanks for the replies.

itop returns:

INT                NAME          RATE             MAX
 42 [MSI-edge      ahci]   107 Ints/s     (max:   416)
 43 [MSI-edge      eth0]    11 Ints/s     (max:    93)

That's it...

Rate fluctuates between 40ish and 160ish for INIT 42, and 3 and 25 for INIT 34

No idea what this means sorry!

Thanks

Currently have a load average of about 11.

The command is 'iotop' not 'itop'

---

