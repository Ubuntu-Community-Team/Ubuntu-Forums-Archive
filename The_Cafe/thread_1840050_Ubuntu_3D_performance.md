---
title: "Ubuntu 3D performance"
date: 2011-09-06
forum: The Cafe
---

### Post by 3Miro on 2011-09-06
This thread was inspired by:

[http://ubuntuforums.org/showthread.php?t=1839558](http://ubuntuforums.org/showthread.php?t=1839558)

which was closed for some unknown reason (Sef talked about outdated versions, but the tests were done on 10.04 LTS).

At any rate, I have several Linux distributions installed on my machine:

Athlon Phenom II x6 1090T 3.4Ghz
8GB DDR3 RAM
Nvidia Asus GTX260 896MB RAM

I tested Unique Heaven 2.5 benchmark on 1024x768 64-bit extreme (everything is 64-bit).

Here are the tests:

```

Ubuntu 11.04 Unity:        48.1/1210
Ubuntu Classic (Compiz):   48.1/1212
Ubuntu Classic No Effects: 49.5/1247
```

```

Arch Gnome 3 Gnome-shell: 48.0/1208
Arch Gnome 3 Metacity:    52.8/1329
Arch XFCE:                52.8/1330
```

```

Gentoo Gnome 2.32 Compiz:   46.4/1168
Gentoo Gnome 2.32 Metacity: 52.7/1328
Gentoo XFCE:                52.4/1319
```

```

Fedora 15 KDE with composition: 43.1/1086
Fedora 15 KDE w/o composition:  52.3/1317
```

```

Debian Gnome 2.32 Compiz:   40.3/1016
Debian Gnome 2.32 Metacity: 50.4/1269

```

Notes: 
- all distros were updated and rebooted right before the test.
- Metacity and XFWM4 have composition disabled.
- Gnome 3 + Metacity = Gnome 3 fallback mode
- Gentoo uses ~amd64 (aka unstable/beta) for the kernel, Nvidia driver and Compiz.
- there was nothing other than bare DE running during the tests.

Conclusions: 
- the main competition between Unity, Compiz and Gnome-shell seems to be a statistical tie. 
- Ubuntu's Metacity does seem to perform worse than others, but Unity is fine (they probably have stopped working on Metacity).
- when it comes to no-effects, Metacity, XFCE and Kwin perform in a statistical tie.
- Kwin with effects may have a specific issue with some effects or something. Graphics was noticeably laggy, however, I have not see anything like this in the past. Maybe I only need to disable a specific effect (I used defaults) or there is some Fedora specific bug.

**Main Conclusion:**
When it comes to 3D graphics, Ubuntu is no better or worse than the others and in the end it really doesn't matter which distro you use.

I will try Debian, but not now, I don't feel like installing another distro tonight.

PS: 48.1/1210 means Frames Per Second: 48.1 and Total Score: 1210.

PSS Added Debian.

---

### Post by sffvba[e0rt on 2011-09-06
I am not surprised...


404

---

### Post by _d_ on 2011-09-06
> **3Miro said:**
> ...

Game, Set, Match.

---

### Post by Shining Arcanine on 2011-09-07
Phoronix has new benchmarks showing PC-BSD outpeforming Ubuntu at running the Linux Unigine Heaven binary:

[http://www.phoronix.com/scan.php?page=article&item=linux_games_bsd&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_games_bsd&num=1)

It is not a huge margin, but it is somewhat embarrassing when your OS is slower at running native software than another OS's emulation layer.

---

### Post by LowSky on 2011-09-07
Here are my results. Anyone have a Ubuntu system with similar hardware to test my results.

```
FPS: 57.4
Scores:	1445
Min FPS: 25.3
Max FPS: 60.6

Hardware
Binary:	Linux 64bit GCC 4.4.5 Release Mar 1 2011
Operating system: Linux 3.0-ARCH x86_64
CPU model: AMD Phenom(tm) II X4 B50 Processor
CPU flags: 3499MHz MMX+ 3DNow!+ SSE SSE2 SSE3 SSE4A HTT
GPU model: GeForce GTX 460 PCI Express 280.13 1024Mb
```

---

