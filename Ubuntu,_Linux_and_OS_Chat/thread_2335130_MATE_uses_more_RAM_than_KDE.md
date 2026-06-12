---
title: "MATE uses more RAM than KDE?"
date: 2016-08-25
forum: Ubuntu, Linux and OS Chat
---

### Post by cAzJJBx on 2016-08-25
After a fresh boot, KDE is using 476.9 MiB while MATE is taking up 575.5 MiB.  What's up with that? 


[http://i.imgur.com/EveLx3g.png](http://i.imgur.com/EveLx3g.png)
[http://i.imgur.com/UNaYGGq.png](http://i.imgur.com/UNaYGGq.png)

---

### Post by TheFu on 2016-08-26
Being pretty has a price?  Was there a question that someone here can answer? Both seem extremely bloated to me.

BTW, if you post the output from **free -m**, it would be easier for some people to understand and uses much less bandwidth. Plus the GUI wouldn't be sucking up even more RAM so we'd know it was the base system and not the system monitor tool.

---

### Post by grahammechanical on 2016-08-26
Are you comparing installs of Kubuntu and Ubuntu Mate or installs of the KDE and Mate desktop environments?

---

### Post by cAzJJBx on 2016-08-26
> **grahammechanical said:**
> Are you comparing installs of Kubuntu and Ubuntu Mate or installs of the KDE and Mate desktop environments?

Ubuntu MATE 16.04.1 on one computer and Mint 18 KDE beta on another.

---

### Post by QIII on 2016-08-26
Then your results are questionable.

You can conduct a more meaningful experiment by using the same underlying OS on each system so that the difference is limited to the DE.

In fact, a minimal install with KDE added versus a minimal instal with MATE added would be most ideal.

---

### Post by coffeecat on 2016-08-26
@ cAzJJBx, I've reduced your large offsite images in the first post to hyperlinks. Please be considerate of those with limited bandwidth and/or those using mobile devices to view the forum by using the image attachment function to create thumbnails.

Oh, and...

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by cAzJJBx on 2016-08-26
I just switched my MATE install to Lubuntu. Much much better!

---

### Post by user1397 on 2016-08-27
What ever happened to unused ram is wasted ram...

---

### Post by nargaroth_reg on 2016-08-27
IMHO much depends on the startup applications, I've reduced the default resource usage significantly on both desktops by disabling some I don't use (i. e., akonadi, bluetooth service). Currently after boot my Ubuntu Mate 16.04 installation uses approximately 325 mb of RAM.

---

### Post by RichardET on 2016-08-27
On my ~2 month old dell 3655 with ~16GB of RAM, 1 TB HD, which currently uses Ubuntu Mate, with boinc running and a 2GB VM of FreeBSD:

```
Tasks: 234 total,   5 running, 229 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.2 us,  1.4 sy, 97.4 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 15336496 total,  9906936 free,  1377576 used,  4051984 buff/cache
KiB Swap:  7274492 total,  7274492 free,        0 used. 11456048 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 7571 boinc     39  19   51592  50296   3928 R  99.7  0.3 133:51.13 setiathome+ 
 6459 boinc     39  19   55688  54400   3868 R  98.3  0.4 146:50.35 setiathome+ 
 8122 boinc     39  19   51592  50240   3868 R  97.3  0.3  75:20.18 setiathome+ 
 8380 boinc     39  19   51592  50244   3868 R  93.0  0.3  41:22.95 setiathome+ 
10024 rthornt+  20   0 4690568 366268 345264 S   7.6  2.4   2:13.53 vmware-vmx  
 2752 root      20   0  336972  78844  55660 S   1.7  0.5   1:49.93 Xorg        
10204 rthornt+  20   0  781376  31368  25144 S   1.0  0.2   0:00.56 mate-termi+ 
10221 rthornt+  20   0   48968   3852   3160 R   0.7  0.0   0:00.08 top         
 2782 boinc     30  10  285924  15960  11836 S   0.3  0.1   0:28.12 boinc       
 5173 rthornt+  20   0  424860  24072  18292 S   0.3  0.2   0:13.24 marco       
 8143 root      20   0       0      0      0 S   0.3  0.0   0:08.80 kworker/2:0 
 8751 rthornt+  20   0 1355300 296696  74680 S   0.3  1.9   0:20.03 chromium-b+ 
 9996 root      20   0       0      0      0 S   0.3  0.0   0:00.85 kworker/0:0 
10128 rthornt+  20   0 1141684 259644 100100 S   0.3  1.7   0:29.94 firefox     
    1 root      20   0  119712   5936   4052 S   0.0  0.0   0:02.35 systemd     
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kthreadd    
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.10 ksoftirqd/0 
rthornton@Inspiron-3655:~$
```

---

### Post by user1397 on 2016-08-27
I agree with what others have said, I would just disable any startup services you don't use and not worry about the amount of ram the idle desktop environment is taking up, unless of course you happen to have a system with a low amount of ram.  Then you should consider lighter DE's or just opt out of using a DE entirely and just use a window manager like openbox.

---

### Post by SeijiSensei on 2016-08-28
> **user1397 said:**
> What ever happened to unused ram is wasted ram...

Linux leaves very little RAM unused.  What isn't occupied by code and buffers is used to cache disk transactions.  Using "free" gives:

```

             total       used       free     shared    buffers     cached
Mem:       8112044    7434236     677808      45832     308568    4944096

```

Most of my memory is devoted to caching.  Were I to launch more programs, that cached figure would fall as memory is devoted to the new processes.

---

### Post by poorguy on 2016-08-28
I'm using Ubuntu Mate 16.04 and Linux Mint 18 Mate and Linux Mint 18 on my computers seems to use more memory also.
I'm using [ htop and free -m ] instead of system monitor for this reason.

[http://askubuntu.com/questions/787642/system-monitor-doesnt-accurately-show-memory-usage](http://askubuntu.com/questions/787642/system-monitor-doesnt-accurately-show-memory-usage)

---

