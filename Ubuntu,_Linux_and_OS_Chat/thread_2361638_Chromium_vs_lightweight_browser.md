---
title: "Chromium vs lightweight browser"
date: 2017-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by ubu112 on 2017-05-18
Please,I just tried Chromium but I didn't see the lightweight browsers,like Midori,Xombrero etc.

Can someone tell me which are differences and which is the best?

Thank you

---

### Post by vasa1 on 2017-05-18
See [https://en.wikipedia.org/wiki/Comparison_of_lightweight_web_browsers](https://en.wikipedia.org/wiki/Comparison_of_lightweight_web_browsers) for starters.

---

### Post by ubu112 on 2018-02-04
I have Acer Aspire AOA150/ZG5 with just 1 Gb of RAM.

Now, I have Firefox (default) and Chromium browsers.I tried with free -m and Firefox consumes a little more memory.

I was thinking of replacing one of the two,watching Wikipedia,QupZilla has the latest stable release,but I don't know how it works.

Is it worth replacing one of the two,if yes which one,with QupZilla? or use only one to save resources? or leave everything as it is?

Thank you

---

### Post by ubu112 on 2018-02-04
I'll make an other thread in right section,sorry

---

### Post by mastablasta on 2018-02-05
the use of a lighter desktop will leave you more ram available for browser. if you use LXDE for example you should have about 850 MB ram available for browser, which should be more than enough, unless you need to work with plenty of tabs. if you do think about upgrading ram or replacing the notebook with a newer one. you could get a used business class laptop with warranty relatively cheap and they usually are linux compatible + will have plenty of RAM and descent CPU. not to mention the matt screen rather than the idiotic glossy screen.

---

### Post by poorguy on 2018-02-05
I use ***"Netsurf Web Browser" ***for web surfing for information only and it works well although some websites appear to be rearranged sometimes as java script is disabled.

---

### Post by ubu112 on 2018-02-05
@mastablasta,@poorguy thank you for your answers.

I have Lubuntu 16.04 LTS and I have available 850 Mb,I tried with 2 tabs open and I still have about 700 Mb (Firefox),600 Mb (Chromium).

With these 2 browsers I'm sure that are well maintained,what about lightweights ????

Maybe,I'm wrong but I think that the best choice is leave all as it is.

Thank you

---

### Post by mastablasta on 2018-02-06
you use up a lot of RAM on Firefox. do you have any extra plugin installed?

i need to check ho much the latest version takes on Linux, but on Win7 Firefox takes between 300 and 500MB with flash and no script installed (this is form my memory). the old ESR Firefox on winXP takes about 200-300 MB with plenty plugins added and a few tabs open. in any case 700 MB is a bit too much.

at work i have Chrome on win 10 (it a basic install nothing was added) and with 3 tabs open it takes less than 200 MB (at least that is what is reported).

one thing to be mindful with linux is the way it uses RAM. if it has it available it will use it. you should not worry about RAM usage unless you are hitting /swap often. in other words even if firefox is showing 700 Mb it might only be using a part of it. it just didn't release the ram yet because there was no need to do so.

you can monitor ram usage with top or htop command. then check if swap is being used.

to test the theory open chromium and firefox at the same time. if they really do use that much ram, then  you shouldn't be bale to open them without some heavy /swap usage.

---

### Post by ubu112 on 2018-02-06
@mastablasta,thank you for your advice.

I want to follow your suggestion,but please,I'm not expert like you.I mean to monitor RAM usage with "top", have I just to write in the terminal "top"?

I open Firefox+Chromium and I can see how much RAM is used.

As I wrote above,Firefox+Chromium with 2 tabs open will take about 400 MB.

Let me try with "top" and I'll tell you the results.

Thank you

---

### Post by ubu112 on 2018-02-06
```
top - 23:32:12 up 22 min,  1 user,  load average: 0,35, 0,57, 0,50
Tasks: 140 total,   1 running, 139 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0,7 us,  1,2 sy,  0,0 ni, 97,3 id,  0,7 wa,  0,0 hi,  0,2 si,  0,0 st
KiB Mem :  1009684 total,    32156 free,   340388 used,   637140 buff/cache
KiB Swap:  1034748 total,  1034416 free,      332 used.   577752 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                  
 3600 user      20   0    8100   3460   3016 R   1,3  0,3   0:00.66 top                                                      
 3598 root      20   0       0      0      0 S   1,0  0,0   0:00.44 kworker/u4:1                                             
  714 root      20   0  100244  15268  13040 S   0,3  1,5   0:04.58 NetworkManager                                           
  762 root      20   0   71976  26388  20364 S   0,3  2,6   0:33.61 Xorg                                                     
top - 23:41:36 up 32 min,  1 user,  load average: 0,18, 0,30, 0,39
Tasks: 138 total,   1 running, 137 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1,4 us,  1,5 sy,  0,0 ni, 97,1 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  1009684 total,    34860 free,   335768 used,   639056 buff/cache
KiB Swap:  1034748 total,  1034416 free,      332 used.   581332 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                  
  762 root      20   0   72668  27704  21680 S   2,3  2,7   0:53.00 Xorg                                                     
 3580 user      20   0   89352  23288  19932 S   1,3  2,3   0:20.56 lxterminal                                               
 3600 user      20   0    8100   3460   3016 R   1,0  0,3   0:05.01 top                                                      
 3658 root      20   0       0      0      0 S   0,7  0,0   0:01.40 kworker/u4:2                                             
  761 root      20   0    4436    196      0 S   0,3  0,0   0:00.22 irqbalance                                               
 1080 user      20   0   72432  17180  14212 S   0,3  1,7   0:02.93 openbox                                                  
 3391 user      20   0  920288 189204 105360 S   0,3 18,7   0:33.95 firefox                                                  
    1 root      20   0   25100   5156   3860 S   0,0  0,5   0:04.81 systemd                                                  
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd                                                 
    4 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                                             
    6 root      20   0       0      0      0 S   0,0  0,0   0:00.10 ksoftirqd/0                                              
    7 root      20   0       0      0      0 S   0,0  0,0   0:01.61 rcu_sched                                                
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh                                                   
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 migration/0                                              
   10 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 lru-add-drain             
```

[B]Firefox+Chromium with 4 tabs open.

Unfortunately,I don't understand all these numbers.

Thank you
[/B]

---

### Post by mastablasta on 2018-02-07
just the top numbers.
Thats 340 MB used: [I]340388 used
[/I]Also for example:
firefox takes up 18.7 % of all your memory
this is the %MEM column

htop will have a small graph on top.

---

### Post by vasa1 on 2018-02-07
And```
KiB Swap:  1034748 total,  1034416 free,      **332 used**.
```

---

### Post by ubu112 on 2018-02-07
@mastablasta,@vasa1 thank you for your answers.

I'd say,I can be satisfied,I mean with just 1 Gb of RAM,I can hold Firefox+Chromium with no problems and don't think at lightweight browsers.Do you agree with me?

But,I thought that if I have free memory available,swap won't be touched.This isn't true.

Thank you

---

### Post by monkeybrain20122 on 2018-02-08
> **ubu112 said:**
> 
But,I thought that if I have free memory available,swap won't be touched.This isn't true.




This is not true. The threshold of dropping to swap is determined by swappiness. The default is 60. This is probably about right for your case. [https://askubuntu.com/questions/103915/how-do-i-configure-swappiness](https://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

---

### Post by vasa1 on 2018-02-08
> **monkeybrain20122 said:**
> This is not true. The threshold of dropping to swap is determined by swappiness. The default is 60. This is probably about right for your case. [https://askubuntu.com/questions/103915/how-do-i-configure-swappiness](https://askubuntu.com/questions/103915/how-do-i-configure-swappiness)OP, it's worth reading the comments there as well :)

---

### Post by ubu112 on 2018-02-08
@monkeybrain20122,@vasa1 thank you I learnt something more.

I probably don't have swappiness set at 60%. Why ? Have I to worry about it ?

Please,I'd like to have your opinions about:

> [COLOR=#000000]I'd say,I can be satisfied,I mean with just 1 Gb of RAM,I can hold Firefox+Chromium with no problems and don't think at lightweight browsers.Do you agree with me?[/COLOR]


Thank you

---

