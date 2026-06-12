---
title: "Trouble with load averages"
date: 2009-04-19
forum: Server Platforms
---

### Post by Wonslung on 2009-04-19
hello, I've been trying to help a friend of mine with a problem he's been having and i've reached the end of my abilities so i'm turning to the forums for help.
The issue:
  Web/ftp server is experience extreme load for no explainable reason. He's running a seedbox because his country throttles p2p to the point of uselessness.  He's got 30 users and the hardware SHOULD be more than adequate.  (Intel E8400 core2duo w/2GB ram 100Mbit/sec internet 500 GB sata hard drive)

Originally he was getting ungodly loads of up to 40 but averaging 30ish
this was with apache2 php 5.26 mysql 5.0.67 on debian 5

i switched to ubuntu 8.10 server with inginx 0.6.36 php 5.28 (patched for php-fpm) mysql 5.0.67

i've been able to get the loads down to 12-14 but this is still unacceptable....i'm stuck and completely confused...nothing i try works.

the memory isn't being used...it's never over 50%

any help would be appreciate

---

### Post by Sef on 2009-04-19
Moved to server platforms.

---

### Post by Wonslung on 2009-04-19
> **Sef said:**
> Moved to server platforms.

ooo sorry man, i didn't mean to post in the wrong forum =()

---

### Post by Thirtysixway on 2009-04-19
I'm guessing each seed is creating a thread/process.  Is your server running slow?  use top to see what processes are using the most cpu.

---

### Post by Wonslung on 2009-04-20
> **Thirtysixway said:**
> I'm guessing each seed is creating a thread/process.  Is your server running slow?  use top to see what processes are using the most cpu.

yes, i did that but the info doesn't really tell me what's going wrong...nothing is using a ton of cpu nothing is using a ton of memory...the processor seems to be WAITING more than anything else

let me post a cap of it
```
Tasks: 145 total,   3 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  1.3%sy,  0.0%ni,  0.0%id, 96.2%wa,  0.4%hi,  0.9%si,  0.0%st
Mem:   2062388k total,  2011668k used,    50720k free,    18716k buffers
Swap:  2931852k total,     5388k used,  2926464k free,  1538868k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                    
 1106 www-data  20   0 26772 8064 2564 S    1  0.4   0:39.82 python                                                                                                     
 3204 www-data  20   0 40816  21m 2564 S    1  1.1   1:20.68 python                                                                                                     
 6066 www-data  20   0 31864 9844 2344 S    1  0.5   2:09.87 transmissioncli                                                                                            
 6678 www-data  20   0 29780 7668 2348 S    1  0.4   0:58.88 transmissioncli                                                                                            
12566 www-data  20   0 32816  10m 2348 S    1  0.5   2:38.63 transmissioncli                                                                                            
14123 www-data  20   0 28284 6400 2352 S    1  0.3   3:46.00 transmissioncli                                                                                            
14191 www-data  20   0 32340 9428 2340 D    1  0.5   0:47.74 transmissioncli                                                                                            
18479 wonslung  20   0  2416 1164  876 R    1  0.1   0:00.15 top                                                                                                        
20386 www-data  20   0 86152  65m 2556 D    1  3.3   7:29.06 python                                                                                                     
26630 www-data  20   0 32948  13m 2564 S    1  0.7   1:10.77 python                                                                                                     
30533 www-data  20   0 43944  24m 2560 D    1  1.2   4:16.62 python                                                                                                     
31126 www-data  20   0 48176  20m 2564 R    1  1.0   1:50.29 python                                                                                                     
    1 root      20   0  3056 1896  576 S    0  0.1   0:01.54 init                                                                                                       
    2 root      15  -5     0    0    0 S    0  0.0   0:00.09 kthreadd                                                                                                   
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0                                                                                                
    4 root      15  -5     0    0    0 S    0  0.0   0:52.02 ksoftirqd/0                                                                                                
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                 
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1                                                                                                
    7 root      15  -5     0    0    0 S    0  0.0   0:06.95 ksoftirqd/1                                                                                                
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                 
    9 root      15  -5     0    0    0 S    0  0.0   0:02.28 events/0                                                                                                   
   10 root      15  -5     0    0    0 S    0  0.0   0:00.43 events/1                                                                                                   
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                    
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                              
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                              
   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                  
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                  
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                     
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                               
  131 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                                                                                     
  135 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                    
  181 root      15  -5     0    0    0 S    0  0.0   1:36.27 kswapd0  
```

the thing that's strange is this:
before we opened it up to the 30 users it worked fine even with as many as 50 torrents running...i tested it...load never went over 1.0 

as soon as we add the user accounts and they all start logging in it goes nuts....which leads me to believe it's related directly to the web server..i've done everything i know to do....i've switched to the lightest weight web server i can find...i just don't have the experience to diagnose and fix this issue....i hate that fact but i can't avoid it

---

### Post by Wonslung on 2009-04-22
so noone has any ideas?
even some programs or methods to help locate the cause of this load would be helpful....most of the time the cpu is as like.....3-5% and the memory is only 40-50%.

i notice in top that the system is spending an awful amount of time "waiting"

is there anyways to figure out what's causing this?

---

