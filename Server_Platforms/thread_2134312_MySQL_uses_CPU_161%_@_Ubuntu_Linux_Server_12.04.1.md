---
title: "MySQL uses CPU 161% @ Ubuntu Linux Server 12.04.1"
date: 2013-04-10
forum: Server Platforms
---

### Post by kevinx on 2013-04-10
when i check the running-processes I notice:

```
CPU load averages:     8.76 (1 mins) , 10.82 (5 mins) , 11.32 (15 mins)
CPU type:     Intel(R) Xeon(TM) CPU 3.00GHz , 2 cores

ID        Owner        CPU        Command   
943     mysql     161 %     /usr/sbin/mysqld
```

When I check the memory use: 

```
Real memory: 3.45 GB total / 2.70 GB free   Swap space: 4 GB total / 4 GB free

ID        Owner        Size        Command   
943     mysql     383568 kB     /usr/sbin/mysqld
```

For some reason the MySQL-program uses a lot of CPU. It uses about 161% of CPU.
Is there a way that i can modify MySQL to reduce the CPU-use? 

Kevinx

---

### Post by Doug S on 2013-04-10
Hi and welcome to Ubuntu forums.

Your computer is horrendously overloaded, and your mysql load doesn't explain all of it. You should run "top" and watch it for awhile to try to help figure out why. Here is a snapshot of "top" from one of my 12.04.2 servers:```
top - 20:48:50 up 1 day,  7:01,  4 users,  [COLOR=#ff0000]load average: 0.00, 0.01, 0.05[/COLOR]
Tasks: 134 total,   1 running, 133 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16004120k total, 10868356k used,  5135764k free,  1414964k buffers
Swap:  8294396k total,    95100k used,  8199296k free,  8291260k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4784 doug      20   0 17340 1312  944 R    0  0.0   0:00.15 top
    1 root      20   0 24468 2088 1256 S    0  0.0   0:01.42 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.69 ksoftirqd/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0
    7 root      RT   0     0    0    0 S    0  0.0   0:00.23 watchdog/0
    8 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1
   10 root      20   0     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1
   12 root      RT   0     0    0    0 S    0  0.0   0:00.21 watchdog/1
   13 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/2
   15 root      20   0     0    0    0 S    0  0.0   0:00.18 ksoftirqd/2
   16 root      RT   0     0    0    0 S    0  0.0   0:00.22 watchdog/2
   17 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/3
   18 root      20   0     0    0    0 S    0  0.0   0:02.32 kworker/3:0
   19 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/3
   20 root      RT   0     0    0    0 S    0  0.0   0:00.22 watchdog/3
``````
doug@s15:~/sguide-1304/doug_conflict/serverguide/C$ [COLOR=#ff0000]ps aux | grep -i mysq[/COLOR]
mysql     1705  0.0  0.0 549948  5168 ?        Ssl  Apr09   0:13 /usr/sbin/mysqld
```

---

### Post by kevinx on 2013-04-11
Hi! 

Thanks for your reply.

I folllow your suggestion and did run a top:


[FONT=courier new]Tasks: 220 total,   1 running, 219 sleeping,   0 stopped,   0 zombie            
Cpu(s): 83.2%us, 16.7%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st  
Mem:   3615536k total,  2063004k used,  1552532k free,   264016k buffers        
Swap:  4194300k total,        0k used,  4194300k free,   957776k cached         
                                                                                
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6179 mysql     20   0  383m 235m 7044 S  190  6.7   1314:53 mysqld             
27655 root      20   0 20968 7244 3044 S    3  0.2   0:39.82 python             
30487 www-data  20   0 48760  10m 4168 S    1  0.3   0:00.13 apache2            
 1061 root      20   0 18776  13m 1852 S    1  0.4   0:10.91 miniserv.pl        
27976 mars      20   0  2856 1292  944 R    1  0.0   0:08.45 top                
    1 root      20   0  3512 1888 1252 S    0  0.1   0:01.45 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.31 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.07 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.18 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:01.63 kworker/1:0        
   10 root      20   0     0    0    0 S    0  0.0   0:00.32 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.16 watchdog/1         
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   15 root      20   0     0    0    0 S    0  0.0   0:00.05 kdevtmpfs          
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns  [/FONT]  


It seems Mysql is the only program that uses a lot op CPU.

---

### Post by Doug S on 2013-04-11
Well, you cropped out the load average line, so we don't see that important information. In your original post, the load average and the mysql load did not agree, so I was curious where the rest of the load was from.
What is your server and its mysql database doing?

---

### Post by kevinx on 2013-04-22
The problem is solved, now. A mistake in a PHP-script caused the problem. The MySQL-server does give now between the 11% and 50%. 

Kevinx

---

