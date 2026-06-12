---
title: "What's eating my RAM?"
date: 2010-09-18
forum: Server Platforms
---

### Post by tr333 on 2010-09-18
I have a "Sun Fire X2200 M2" running KVM with 4 virtual machines.  It has two dual-core opteron CPU with 8GB ram.  It appeared to be running low on RAM so I turned off all the virtual machines and stopped the "libvirt-bin" service.  This didn't appear to help as "top" is still showing extremely high RAM usage, even though the top item in "top" is bash with 0.1% of memory usage.

Can anyone explain why the RAM usage is so high?

```
top - 22:23:16 up  9:21,  1 user,  load average: 0.37, 0.37, 0.40
Tasks: 114 total,   1 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.1%sy,  0.0%ni, 99.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194784k total,  7260856k used,   933928k free,  5301164k buffers
Swap: 19800072k total,        0k used, 19800072k free,  1540656k cached

```

---

### Post by CharlesA on 2010-09-18
Post the output of this command:

```
free -m
```

This is what my top says:

```
top - 06:12:29 up  8:20,  1 user,  load average: 0.39, 0.29, 0.27
Tasks: 105 total,   1 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.0%us,  1.4%sy,  0.1%ni, 87.2%id,  3.2%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   6125192k total,  6063084k used,    62108k free,    **70152k buffers**
Swap: 12699640k total,        0k used, 12699640k free,  **4939140k cached**

```

free -m:

```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       5920         60          0         68       4823
-/+ buffers/cache:       1029       **4952**
Swap:        12401          0      12401

```

The way Linux manages memory is a bit different then the way Windows does. It tends to cache all available RAM and use it only when needed. Hence why it says that I've got about 5GB of memory "cached."

---

### Post by tr333 on 2010-09-18
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          8002       7774        227          0       5191       1522
-/+ buffers/cache:       1060       6941
Swap:        19336          0      19336

```

---

### Post by CharlesA on 2010-09-18
The memory is being used for disk buffering.

Give this a shot:

```
sudo sync
sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

[Source.]("http://linuxtidbits.wordpress.com/2008/02/20/purge-memory/")

---

### Post by LightningCrash on 2010-09-19
> **CharlesA said:**
> Post the output of this command:

```
free -m
```



edit: NVM, you already noticed that it was in `top`'s output

---

### Post by tr333 on 2010-09-19
> **CharlesA said:**
> The memory is being used for disk buffering.

Give this a shot:

```
sudo sync
sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

[Source.]("http://linuxtidbits.wordpress.com/2008/02/20/purge-memory/")

Thanks.  That appears to have improved the situation.

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          8002       1486       6516          0          0         11
-/+ buffers/cache:       1474       6528
Swap:        19336          0      19336

```

---

### Post by BkkBonanza on 2010-09-19
It hasn't really changed how much memory is available because "cache buffers" are always available to programs as they request memory. Linux uses them for disk cache when not allocated by programs as an efficiency method. It doesn't leave memory empty when not in use, it puts it to use doing disk caching.

All you've done when you sync disk is wipe out the benefit of caching but not gained anything at all for program memory use.

Better tools like htop (much nicer version of top) will show you the "actual" memory you're using by taking total and subtracting the cache buffers. It colour codes the memory use. If you install that you'll be much happier than with top,

sudo apt-get install htop

I like the tree view (F5) as it shows a tree of what processes own others.

In my opinion the people who wrote "free" should have added a line that calculates how much memory non-caching processes are using and what's left. The way they show memory use has always resulted in confusion from users who don't yet understand how linux manages memory and expect "free" to mean what's really free/available.

---

### Post by The Cog on 2010-09-20
The line you should be looking at is the **-/+ buffers/cache** line - that's the one that counts the memory used for disk caching as unused:
```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       5920         60          0         68       4823
[COLOR="Red"]**-/+ buffers/cache:       1029       4952**[/COLOR]
Swap:        12401          0      12401
```

---

### Post by tr333 on 2010-09-20
> **BkkBonanza said:**
> It hasn't really changed how much memory is available because "cache buffers" are always available to programs as they request memory. Linux uses them for disk cache when not allocated by programs as an efficiency method. It doesn't leave memory empty when not in use, it puts it to use doing disk caching.

All you've done when you sync disk is wipe out the benefit of caching but not gained anything at all for program memory use.

Better tools like htop (much nicer version of top) will show you the "actual" memory you're using by taking total and subtracting the cache buffers. It colour codes the memory use. If you install that you'll be much happier than with top,

sudo apt-get install htop

I like the tree view (F5) as it shows a tree of what processes own others.

In my opinion the people who wrote "free" should have added a line that calculates how much memory non-caching processes are using and what's left. The way they show memory use has always resulted in confusion from users who don't yet understand how linux manages memory and expect "free" to mean what's really free/available.

Thanks for the suggestion.  htop is so much easier to use/understand than normal top.

---

