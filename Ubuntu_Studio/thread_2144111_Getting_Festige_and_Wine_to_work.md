---
title: "Getting Festige and Wine to work"
date: 2013-05-11
forum: Ubuntu Studio
---

### Post by Sylos on 2013-05-11
Hello all. I've never managed to get a working set up for using VSTs on any of my Linux audio installs and I thought I would now make a proper attempt at it. As predicted - I hit problems.

So..... Im using Tango Studio Karmasutra as the base with the following:

Wine 1.2.3 (with the RT patch I think)
Wineasio 0.9.0
FST  1.11
Festige 0.9.3

I downloaded a few VSTs and put them in the folder for Festige. When I hit "launch" for any of them - nothing happens. So I launched festige from the terminal and get the following output when trying to launch a VST:

```
WINE realtime scheduling hack enabled, realtime base priority has been set to 15
wineserver running SCHED_FIFO at priority 10
yo... lets see...
can't connect to JACK

```

So it would appear that something in my underlying configuration is wrong?

Any help gratefully received.

Cheers

---

### Post by jejeman on 2013-05-11
Start JACK first.

---

### Post by Sylos on 2013-05-12
> **jejeman said:**
> Start JACK first.

Wish it was that simple. JACK is already running but still no connection.

Cheers

---

### Post by CrocoDuck on 2013-05-25
Hi. Dunno how help you. I'm just wondering if wineasio has been properly configured. Have a look: [http://ubuntuforums.org/showthread.php?t=2029348](http://ubuntuforums.org/showthread.php?t=2029348) . Using this procedure I've been able to run NI's Bandstand and GuitarRig under ubuntu 10.04. The version of wineasio that worked with me was the 7.5 .

---

