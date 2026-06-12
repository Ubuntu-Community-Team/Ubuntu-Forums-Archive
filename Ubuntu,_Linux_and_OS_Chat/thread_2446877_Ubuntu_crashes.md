---
title: "Ubuntu crashes"
date: 2020-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by MaximB on 2020-07-08
Hi,
This is not a support thread, just want to know if anyone else have this issue.

Sometimes when I'm working with Firefox for a few days, some buggy website (Facebook, Youtube...) cases great use of CPU, and the whole system (not just the browser) becomes unresponsive.
This happens a LOT, specially after I bought a new 4K TV monitor (it happened before too, but less).
I have Nvidia GTX 760 videocard with latest proprietary drivers. 
16 GB of RAM
Intel(R) Core(TM) i5-4670K CPU @ 3.40GHz Quad core CPU.
Ubuntu 20.04
Yes, it's not the latest and greatest, but it shouldn't crash so often.

Does anyone else have similar issues? that some applications cases the OS to be unresponsive and forces you to reboot the system?

---

### Post by kc1di on 2020-07-08
I had that happen a few years ago and it was traced back to the Nvidia graphics card.  I solved it by installing the correct Nvidia driver for the card. 
Good Luck in finding an answer.

---

### Post by yetimon_64 on 2020-07-08
Yes I've noticed that a bit lately especially with some videos on sites like facebook (not all of the videos I view, probably only about 1 or 2 in every 10). I haven't had it that bad that the whole system needs rebooting just dropping out the browser tab or window will usually stop the CPU running at high levels here. Occasionally I've reverted to using "xkill", activated from a mouse gesture, to drop the whole browser if it greys out and the CPU really fires up too much for my comfort.

My specs are a bit similar to yours; 16GB ram, Intel Core i7-5500U CPU (hyperthreaded dual core, ie. 4 virtual cores), Hybrid Graphics:  Card-1: Intel HD Graphics 5500. Card-2: NVIDIA GM107M [GeForce GTX 850M]. I usually run my whole desktop on NVidia rather than the Intel setting. My video driver package is the proprietary NVidia 435 drivers. **Edit:** Ubuntu Mate 18.04 used here.

In my case it is only a minor nuisance from time to time and has never locked up the whole OS thankfully. Usually it is firefox and videos that causes it here, not aware of any other apps doing it.

Regards, yeti.

---

### Post by sdsurfer on 2020-07-09
Same here, consistent recurring problems I traced back to Nvidia drivers (Software & Updates -> Additional drivers.) I have three machines with Nvidia hardware.

Infrequent stuff . . . .I love FireFox but usually it's the culprit. I have to use other browsers to test apps, but it's still my preference.

---

### Post by zebra2 on 2020-07-10
Somewhat the same here.  
All intel system Intel® Celeron(R) CPU N3350 @ 1.10GHz × 2 , Mesa Intel® HD Graphics 500 (APL 2).

Ubuntu 20.10 Gnome 3.36.3 Wayland. 

Minor stalls when running video files with Videos or VLC.  Stalled video becomes active with rapid moving of mouse. When mouse becomes active video continues. 
I don't get excited about glitches in dev versions.

Edit: I don't call what I am getting a system crash. More like a library problem.

---

### Post by CatKiller on 2020-07-11
I know you said you weren't particularly looking for support, but > **MaximB said:**
> Sometimes when I'm working with Firefox for a few days, some buggy website (Facebook, Youtube...) cases great use of CPU, and the whole system (not just the browser) becomes unresponsive.
This sounds like an out of memory situation rather than a high load situation. Linux generally remains responsive under load but really struggles when it's out of memory. It's probably worth monitoring memory usage over time and then restarting Firefox when it gets too high. Memory leaking as a class of fault is not uncommon, particularly when running arbitrary code from miscellaneous third parties.

Other potential culprits are stalled I/O and (lack of) hardware accelerated video decoding.

---

