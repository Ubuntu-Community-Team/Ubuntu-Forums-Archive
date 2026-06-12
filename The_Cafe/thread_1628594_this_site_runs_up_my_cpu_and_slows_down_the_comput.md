---
title: "this site runs up my cpu and slows down the computer"
date: 2010-11-22
forum: The Cafe
---

### Post by sdowney717 on 2010-11-22
[http://www.centurycouncil.org/content/girl-talk-atlanta-dream-host-sleepover-middle-school-girls](http://www.centurycouncil.org/content/girl-talk-atlanta-dream-host-sleepover-middle-school-girls)

It looks like a plain jane site
Does it affect your PC?
notice xorg is way up there

---

### Post by czr114 on 2010-11-22
The culprit is that badly-behaved Javascript scroll at the left. I've seen a lot of trouble from those across multiple browsers.

Hopefully those will be less of a problem in FF4's optimized JS engine.

---

### Post by simpleblue on 2010-11-22
I'm running Chrome on F14 and while the numbers do seem higher then usual, they are not as high as yours when I go to that site:

```
top - 22:52:31 up 23:08,  2 users,  load average: 0.91, 0.99, 0.96
Tasks: 189 total,   2 running, 186 sleeping,   0 stopped,   1 zombie
Cpu(s):  6.6%us,  2.9%sy,  0.0%ni, 90.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3610672k total,  1676148k used,  1934524k free,   133472k buffers
Swap:  5701628k total,        0k used,  5701628k free,   853736k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4561 user      20   0  267m 104m  22m R  8.5  3.0   3:42.30 chrome             
 1808 root      20   0 54096  23m  15m S  4.2  0.7  33:40.67 Xorg               
 2626 user      20   0  580m  85m  32m S  2.2  2.4  25:07.52 chrome             
 5575 user      20   0  205m  32m  20m S  2.2  0.9   9:14.96 chrome             
 7947 user      20   0  107m  11m 8064 S  1.1  0.3   0:04.61 metacity           
 2116 user      20   0  169m 5440 4284 S  0.7  0.2   3:07.29 pulseaudio         
 5555 user      20   0  216m  81m  16m S  0.5  2.3   3:34.86 chrome             
  148 root      15  -5     0    0    0 S  0.1  0.0   0:08.62 kslowd000          
  940 root      20   0     0    0    0 S  0.1  0.0   0:31.55 phy0               
 1477 root      20
```

---

### Post by NightwishFan on 2010-11-23
Here is mine, yes I see this issue as well.

```
Tasks: 164 total,   2 running, 162 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.1%us, 17.6%sy,  0.0%ni, 55.1%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   3057724k total,  2994256k used,    63468k free,    27624k buffers
Swap:  4096532k total,    27864k used,  4068668k free,  2426880k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1064 root      20   0  181m  32m  16m R   60  1.1  27:05.06 Xorg               
14985 virgil    20   0  650m 139m  30m S   28  4.7   2:57.82 firefox-bin        
15190 virgil    20   0 77680  19m  13m S    1  0.6   0:16.57 npviewer.bin       
 2617 virgil    20   0  205m  11m 8760 S    0  0.4   0:13.75 metacity           
 2658 virgil    20   0  256m  12m 8504 S    0  0.4   0:20.56 wnck-applet        
15320 virgil    20   0  210m  14m  10m S    0  0.5   0:00.25 gnome-terminal     
15339 virgil    20   0 19224 1432 1048 R    0  0.0   0:00.05 top                
    1 root      20   0 23696 1760 1192 S    0  0.1   0:00.54 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:01.14 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    6 root      20   0     0    0    0 S    0  0.0   0:02.46 ksoftirqd/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.87 events/0           
    8 root      20   0     0    0    0 S    0  0.0   0:00.74 events/1           
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper
```

---

### Post by madjr on 2010-11-23
> **sdowney717 said:**
> [http://www.centurycouncil.org/content/girl-talk-atlanta-dream-host-sleepover-middle-school-girls](http://www.centurycouncil.org/content/girl-talk-atlanta-dream-host-sleepover-middle-school-girls)

It looks like a plain jane site
Does it affect your PC?
notice xorg is way up there

you should install noscript or something like that.

that site owner / webmaster should get an email

how many cores your cpu has? i presume is one because is very high

oh and how you get nautilus to use 200+ mb!

---

### Post by Spice Weasel on 2010-11-23
How did you get your memory usage that high?

---

### Post by sdowney717 on 2010-11-23
> how many cores your cpu has? i presume is one because is very high
it is a dual core e6550 cpu

---

### Post by sdowney717 on 2010-11-23
tried chrome and it is fine.
So just firefox does this.

---

### Post by sdowney717 on 2010-11-23
> How did you get your memory usage that high?
I have some tabs open?

WHAT is that tabs from other computers???
If I click on it wow, just awful.
Sometimes I have seen a lot of weird tabs open up or even empties.
I think I counted at least 50 once.
I really wonder sometimes.

---

