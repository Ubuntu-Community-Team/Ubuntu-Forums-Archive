---
title: "Trusty Tahr lower memory footprint"
date: 2013-10-31
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2013-10-31
Has anybody noticed?

On two installs (one with trusty repositories and one with devel repositories) I am seeing memory usage of less than 50% with a 1GB RAM machine with no apps open. 13.04 had just over 50% and 12.04 just under 70%. In fact when the system is first loaded memory usage is as low as 22%.

Regards.

---

### Post by ventrical on 2013-10-31
Only 26% with 18 tabs open on FF.  It's just awesome whats being done here with trusty.  I wish it would just stay like this :)

---

### Post by rrnbtter on 2013-10-31
Greetings,
My system is reporting 850Meg used from 3.8Gig total which is 24%. I have never observed my 2.8Gig swap being used.  I have three  FF windows open but the number of TSR's will have an impact on the total also.

---

### Post by jerrylamos on 2013-11-01
Just wait.  The kitchen sink hasn't been thrown at it.  As releases roll by trend is up, unless you compare unity to lubuntu to xubuntu to kubuntu.....

---

### Post by grahammechanical on 2013-11-01
After starting this thread I saw my memory usage creep up and up. The culprit was hud-service but today's update seemed to have fixed it. Flavours built on Ubuntu must also benefit from these improvements. A lot of work has been done on Ubuntu mobile to lower memory usage and that work has filtered into Ubuntu desktop. The devs are also looking at upstart to get it switching services in and out as they are needed and not leave them running using memory and CPU cycles. Anyway, I am using System Load Indicator to keep an eye on memory.

---

### Post by rrnbtter on 2013-11-01
Greetings,
I've noticed that lsb-core isn't inatalled which I find odd. Anyone here know if it's absence is on purpose and if not do you suppose there would be negative consequences to installing it. I think it is used to check for linux compatibility and that makes me wonder why it is not in the up-stream. Mir or Unity 8 perhaps?

---

### Post by PJs Ronin on 2013-11-02
I have a Trusty partition that is a clone of a Saucy partition.   After logon with a conky and firefox, Saucy mem is 880M/15.6G while Trusty is 719M/15.6G.

---

### Post by cariboo on 2013-11-02
I see these threads every release, and my memory usage never seems to change:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2001       1914         87          0         56        804
-/+ buffers/cache:       1053        948
Swap:         1999          0       1999
```

I currently have chromium with 8 tabs open, thunderbird, synaptic, a terminal  and qbittorrent running.

---

### Post by grahammechanical on 2013-11-02
This is my free -m

> free -m
             total       used       free     shared    buffers     cached
Mem:           993        822        171          0         17        295
-/+ buffers/cache:        509        484
Swap:         4083          1       4082

At the same time System Load Indicator says

Mem; 516Mb Cache: 310MB

And System Monitor says

Memory 493.2 MiB (49.69%) of 993.7 MiB

Some methods of calculating memory usage include cache memory as used memory. Which is what free -m is doing according to my calculations. 

Used - (Buffers + Cache) = similar amounts as shown by System Monitor and System Load Indicator. The only thing using RAM memory is the OS so it will claim as much memory as is available either as used memory or cache memory. Perfectly acceptable.

Regards.

---

### Post by rrnbtter on 2013-11-02
Greetings,
Interesting! after current updates I'm down to 445Meg of 3.8 Gig and no Swap used. 

[ATTACH=CONFIG]247500[/ATTACH][ATTACH=CONFIG]247501[/ATTACH]

---

