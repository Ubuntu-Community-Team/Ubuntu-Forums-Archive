---
title: "32 bit or 64 bit Ubuntu on 2 GB RAM with E300 AMD processor?"
date: 2014-06-17
forum: Ubuntu, Linux and OS Chat
---

### Post by abhishekkjain on 2014-06-17
I am currently running Ubuntu 12.04 64 bit on this device and the top command in terminal gives this output when file transfer is in process with 10 tabs of chrome. I know too much swap is given by mistake...


```
top - 01:12:40 up  2:01,  2 users,  load average: 2.58, 3.63, 3.04Tasks: 197 total,   2 running, 195 sleeping,   0 stopped,   0 zombie
Cpu(s): 30.3%us, 31.4%sy,  0.0%ni, 32.4%id,  5.4%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:   1638220k total,  1564316k used,    73904k free,   458544k buffers
Swap: 17338364k total,   668192k used, 16670172k free,   222024k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                              
 4197 root      20   0 19004 3064  756 R   57  0.2   8:48.07 mount.ntfs                                                                           
 2736 abhishek  20   0 1369m  65m  15m S   51  4.1  27:55.24 nautilus                                                                             
 5325 root      20   0 16444 1712  760 S    8  0.1   3:37.17 mount.ntfs                                                                           
 1049 root      20   0  177m  17m 4752 S    5  1.1   6:49.63 Xorg                                                                                 
 4237 root      20   0 18920 2068  752 S    3  0.1   9:10.48 mount.ntfs                                                                           
 6389 abhishek  20   0 1042m  85m  25m S    3  5.3   0:47.74 chrome                                                                               
 2716 abhishek  20   0 1253m  51m  21m S    3  3.2   5:53.53 compiz                                                                               
   30 root      20   0     0    0    0 S    1  0.0   1:44.24 kswapd0                                                                              
 6885 abhishek  20   0  522m  18m  11m S    1  1.2   0:05.50 gnome-terminal                                                                       
   10 root      20   0     0    0    0 S    1  0.0   0:29.40 rcu_sched                                                                            
 6276 abhishek  20   0  833m  59m  30m S    1  3.7   7:30.58 chrome                                                                               
 6490 abhishek  20   0  965m  63m  24m S    1  4.0   0:59.13 chrome                                                                               
 5292 root      20   0     0    0    0 S    0  0.0   0:38.87 usb-storage                                                                          
 6654 abhishek  20   0  960m  56m  21m S    0  3.6   0:24.23 chrome                                                                               
 6756 abhishek  20   0  923m  13m 9620 S    0  0.8   0:06.78 chrome                                                                               
 6986 root      20   0     0    0    0 S    0  0.0   0:00.31 kworker/1:2                                                                          
    3 root      20   0     0    0    0 S    0  0.0   0:26.89 ksoftirqd/0                                                                          
   13 root      20   0     0    0    0 S    0  0.0   0:15.42 ksoftirqd/1                                                                          
   28 root      20   0     0    0    0 S    0  0.0   0:26.32 kworker/0:1                                                                          
 1116 root      20   0  177m  900  840 S    0  0.1   0:00.69 php5-fpm                                                                             
 2697 abhishek  20   0  685m  13m  11m S    0  0.8   0:07.56 gnome-settings-                                                                      
 6734 abhishek  20   0  953m  60m  23m S    0  3.8   0:14.58 chrome                                                                               
 6982 abhishek  20   0 17444 1496 1076 R    0  0.1   0:00.81 top                                                                                  
    1 root      20   0 24572 1776 1168 S    0  0.1   0:01.95 init                                                                                 
    2 root      20   0     0    0    0 S    0  0.0   0:00.38 kthreadd                                                                             
    5 root       0 -20     0    0    0 S    0  0.0   0:00.00 kworker/0:0H                                                                         
    7 root       0 -20     0    0    0 S    0  0.0   0:00.00 kworker/u:0H                                                                         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.04 migration/0                                                                          
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 rcu_bh                                                                               
   11 root      RT   0     0    0    0 S    0  0.0   0:00.16 watchdog/0                                                                           
   12 root      RT   0     0    0    0 S    0  0.0   0:00.18 watchdog/1                                                                           
   14 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/1                                                                          
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 kworker/1:0H                                                                         
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset       
```

I am thinking to upgrade to 14.04 so was just thinking to ask experts what is better? 32 bit or 64 bit? I know RAM is min for 64 bit and process is very weak AMD E-300 ([http://www.cpubenchmark.net/cpu.php?cpu=AMD+E-300+APU&id=248](http://www.cpubenchmark.net/cpu.php?cpu=AMD+E-300+APU&id=248)),

So what will be good burdening my RAM with 64 bit or burdeining my CPU with 32 bit?

Daily work to be done:
I need to do some simple developmemnt work in python and mysql so I will need apache too.
I will need chrome or firefox.
Sublime Text
Some directories in nautilus.

Currently I hardlyget grey screen but it becomes laggy when I switch to opened tab afterlong time.

---

### Post by help_me2 on 2014-06-17
Get more ram, or stick with 32 bit. 2bg ram is too low for 64 bit. I have 3 tabs open, and my email client open, and I'm using 1.7gb of ram. 4gb of ram is probably the least amount you want.

---

### Post by grahammechanical on 2014-06-17
Excuse me but I have been running Ubuntu 64 bit on a machine with 1 GB RAM for years without any problems. In fact right now I am running Utopic Unicorn 64 bit (14.10 development branch). The amount of RAM is not a consideration in deciding whether to run 32 bit or 64 bit.

If the CPU is 32 bit we must run 32 bit Ubuntu whatever the amount of RAM we have. If the CPU is 64 bit then we can run either 64 bit Ubuntu or 32 bit Ubuntu because the CPU architecture is backwards compatible with the 32 bit CPU instruction set.

In the past some recommended 32 bit because most applications had been coded for the 32 bit CPU architecture but that no longer holds especially as Ubuntu has multiarch libraries and has had them for a couple of years.

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

I have found Ubuntu 14.04 to be using 15 - 20% less RAM than 12.04 did and it is much quicker at freeing up memory once an application has been closed than 12.04 ever was. The Ubuntu developers have done a lot of work over the last year on a version of Ubuntu for phones and tablets. These devices require an OS to make efficient use of system resources to provide a good user experience and to prolong battery power. The lessons learned are being applied to Ubuntu on the desktop. so, we should see Ubuntu being even more efficient in future.

Right now I am using Chromium and that is a memory hog if ever there was one. But with one tab open only 575 MB of memory is being used. It rises to 737 MB with 4 tabs open.

If the CPU architecture is 64 bit then use a 64 bit OS and get the benefit of the 64 bit instruction set. One day in the not too distant future 32 bit Ubuntu will be discontinued because there will be few machines with 32 bit CPUs. And those that are still being used will not have graphic adapters capable of supporting modern Linux distributions.

The minimum system requirements for Windows 8 is 1GB RAM for Windows 8 32 bit and 2GB RAM for Windows 8 64bit. Please do not confuse Ubuntu with any Microsoft product.

Oh, by the way, greyed out application windows are not due to memory being used up. The greying out of an application window is Ubuntu way of saying that the application is busy.

Install system-load-indicator (indicator-multiload) and watch what is happening to the CPU, RAM and other stuff second by second.

Regards.

---

### Post by LastDino on 2014-06-17
Just a thought, but if you are really worried about RAM consumption, go little lighter and install Xubuntu. x64 bit would only consume more RAM when running x32 applications and the amount is negligible. 

Though, 2GB is quite sufficient, RAM in locale market there atm is fairly cheap. I wouldn't hesitate to get one more stick. And if you do that, you can quite easily get performance boost by reducing swappiness value.

Also, there is difference in actual RAM usage and what is shown in system monitors, as they also include cache which is dynamically allocated to programs.

tl;dr version would be to install best architecture possible and then worry about other things. In this case, it would be x64.

---

### Post by mastablasta on 2014-06-18
64 bit. you will use a bit more ram. but it's negligable. and if possible try to upgrade the ram. i think i will do it this summer. E-300 should support up to 8Gb ram if the motherboard supports it.

the GPU Will take up to 512MB ram and the system close to 500 MB i believe. so you will have arround 1 GB left.

i can even run some servers in virtualbox quite normally (though the 450 APU is a little bit stronger than yours).

---

