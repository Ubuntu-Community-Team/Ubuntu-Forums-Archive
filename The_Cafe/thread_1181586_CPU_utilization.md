---
title: "CPU utilization"
date: 2009-06-08
forum: The Cafe
---

### Post by ProgramErgoSum on 2009-06-08
Hi,
I was converting a .wmv file (approx 290 MB) to .ogg file and I can see the CPU utilization topping 90%. This is on a dual CPU laptop. What I find curious is, for every crest of a given CPU, there is an opposite and almost equal trough of other CPU in a given time duration. Is this pairing of crests and troughs a design feature - (not that I object to this) ? If yes, then is this a result of Ubuntu doing its job ? Is such 'pairing of high and low' regardless of OS ?

Yes, there were brief periods when the CPUs showed similar peaks or lows.

---

### Post by Moustacha on 2009-06-08
I've always guessed it's because the data gets loaded into the other core's L2 cache while the first core is busy processing the data in its L2 cache. No idea if this is true though.

---

### Post by keplerspeed on 2009-06-08
I have seen exactly the same cpu usage pattern on intel core2 duo.

---

### Post by 3rdalbum on 2009-06-08
The transoding software is single-threaded, so the code can only use one core at a time.

I've sometimes been told that the core utilisation will swap on purpose as a kind of "load-levelling" mechanism, but I'm not sure if this is really correct as the swapping seems to be kinda arbitrary, and it's not an instant switch. Moustacha's explanation seems more logical to me.

---

### Post by ProgramErgoSum on 2009-06-08
And, that behavior is controlled by the OS or application software or... ?

---

### Post by LowSky on 2009-06-08
its controlled by the CPU own interal system. Its to share the load effectively. this way the CPU can complete other tasks while still doing the original task. On older machines with only one core, if you were doing something simular and say opened a web browser, the machine would conintiue to do the first job, and as soon as memory was freed up it would open the browser and go back to its task. on some machines doing this could actually ruin the encoding process or cause a slight hiccup on the recording. With multiple cores that happening is less likely.

---

### Post by Delever on 2009-06-08
And I thought that's Linux CPU scheduler working... ;)

---

### Post by H2SO_four on 2009-06-08
I see the same behaviour with my quad.  A single threaded process will "jump" from one core to another every so often.  (sometimes though, the program will use one core exclusively until a task has been completed)

---

### Post by CrazyArcher on 2009-06-08
A single-threaded application working on a multi-core CPU won't necessarily take 100% of a single core, let alone distribute the load among all the cores equally. The process will take resources equivalent to 100% of a single core, but that's all about it. There's a chance that a process will be set with core affinity and try to execute all the instructions over the same core, but the chance is slim (very slim).

---

### Post by ssam on 2009-06-08
its probably good to move the process around for thermal reasons. some times its good to keep a process one core, if it has cached data that only that core can access, but lots of dual cores used a shared cache.

---

### Post by ProgramErgoSum on 2009-06-09
Thank you, people, for the answers !

---

### Post by Kingsley on 2009-06-15
Can anybody explain why both cores on my Intel processor are being used at about the same percentage? I'm ripping a VCD into .avi format using 64-bit VLC.

See screenshot.

---

### Post by Moustacha on 2009-06-15
More than likely it's using two threads

---

