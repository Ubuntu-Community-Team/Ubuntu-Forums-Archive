---
title: "Please post your glxgears output! Who has the best 3D performance?"
date: 2009-06-19
forum: The Cafe
---

### Post by Hallvor on 2009-06-19
I thought this might be a useful thread for linux users thinking of buying new hardware, and want good 3D performance.

So tell us about: 

1. What hardware you are using.
2. What kind of drivers you are using. Open source or proprietary?
3. The output of glxgears in the terminal.

----------

1. My own specs are listed below; Intel Pentium 4  2,4 ghz, with 1 GB RAM.

My graphics card is an ATI Radeon 9600.

2. I use the Mesa open source drivers.

3. ```
hallvor@debian:~$ glxgears
7168 frames in 5.0 seconds = 1433.526 FPS
7151 frames in 5.0 seconds = 1430.057 FPS
7165 frames in 5.0 seconds = 1432.851 FPS
7152 frames in 5.0 seconds = 1430.363 FPS
7159 frames in 5.0 seconds = 1431.736 FPS
7153 frames in 5.0 seconds = 1430.449 FPS
7161 frames in 5.0 seconds = 1432.126 FPS

```

Most games run OK.

---

### Post by gradinaruvasile on 2009-06-19
3300 with X1600/opensource radeon/dri drivers. Compiz on/off no difference.
8000+(no compiz)/3500 (compiz) with Nvidia 7600GS/128 MB DDR3 / proprietary Nvidia drivers from the site (180.60).

---

### Post by Hallvor on 2009-06-26
Anyone else? :popcorn:

---

### Post by starcraft.man on 2009-06-26
I don't really think glxgears alone is a good measure of a graphics card. For people wanting to know performance, I'd recommend reading review sites like [tomshardware]("http://www.tomshardware.com/us/#redir"), [techreport]("http://techreport.com/") and [anandtech]("http://www.anandtech.com/").

If it makes ya happy, I'll bite.

GTX 260, overclocked.
Latest nvidia driver (185) manually installed.

with compiz
55885 frames in 5.0 seconds = 11176.841 FPS
55883 frames in 5.0 seconds = 11176.498 FPS
55911 frames in 5.0 seconds = 11182.182 FPS

no compiz
108316 frames in 5.0 seconds = 21663.105 FPS
108497 frames in 5.0 seconds = 21699.297 FPS
108229 frames in 5.0 seconds = 21645.705 FPS
108501 frames in 5.0 seconds = 21700.146 FPS

---

### Post by koshatnik on 2009-06-26
4060 frames in 5.0 seconds = 811.961 FPS
3736 frames in 5.0 seconds = 747.177 FPS
4727 frames in 5.0 seconds = 945.385 FPS
26147 frames in 5.0 seconds = 5229.336 FPS
31393 frames in 5.0 seconds = 6278.540 FPS
40451 frames in 5.0 seconds = 8090.092 FPS
43890 frames in 5.0 seconds = 8777.960 FPS
37155 frames in 5.0 seconds = 7428.130 FPS
41874 frames in 5.0 seconds = 8374.639 FPS
45560 frames in 5.0 seconds = 9111.958 FPS
45767 frames in 5.0 seconds = 9153.400 FPS
47336 frames in 5.0 seconds = 9467.189 FPS
38048 frames in 5.0 seconds = 7606.971 FPS

Go me.

---

### Post by ssam on 2009-06-26
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by Rainstride on 2009-06-26
i use a nvidia 8400(gs?) galaxy.

im using the proprietary driver(185.18.14-0ubuntu1). 

With compiz off.
```
13343 frames in 5.0 seconds = 2668.475 FPS
14699 frames in 5.0 seconds = 2939.649 FPS
14154 frames in 5.0 seconds = 2830.734 FPS
14981 frames in 5.0 seconds = 2996.055 FPS
15336 frames in 5.0 seconds = 3067.042 FPS
15033 frames in 5.0 seconds = 3006.593 FPS
15202 frames in 5.0 seconds = 3040.097 FPS
14527 frames in 5.0 seconds = 2905.350 FPS

```

with compiz on.
```
5047 frames in 5.0 seconds = 1009.275 FPS
5151 frames in 5.0 seconds = 1030.178 FPS
4965 frames in 5.0 seconds = 992.997 FPS
5110 frames in 5.0 seconds = 1021.971 FPS
5209 frames in 5.0 seconds = 1041.736 FPS
4410 frames in 5.0 seconds = 881.871 FPS
5064 frames in 5.0 seconds = 1012.708 FPS
5106 frames in 5.0 seconds = 1021.080 FPS

```

not bad for $40 :)

---

### Post by days_of_ruin on 2009-06-26
It really is not a good benchmark, but here is mine:
```
40860 frames in 5.0 seconds = 8171.921 FPS
51127 frames in 5.0 seconds = 10225.228 FPS
51742 frames in 5.0 seconds = 10348.299 FPS
49957 frames in 5.0 seconds = 9991.242 FPS
51630 frames in 5.0 seconds = 10325.866 FPS
50088 frames in 5.0 seconds = 10017.409 FPS
48898 frames in 5.0 seconds = 9779.536 FPS
```

---

### Post by Martje_001 on 2009-06-26
Mine is just way too fast for glxgears I think
```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```
;)

---

### Post by moster on 2009-06-26
CPU: E5200 OC from 2500Mhz to 3400Mhz, cooler standard
GPU: Geforce 9400 GT (GS) I could not find any cheaper from 9XXX series :)
Ubuntu Jaunty x86, driver Nvidia from repos, version 180

Slower is with compiz, faster is without.

```
moster@moster-desktop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/6817 the monitor refresh rate.
25075 frames in 5.0 seconds = 5014.996 FPS
25183 frames in 5.0 seconds = 5036.544 FPS
25215 frames in 5.0 seconds = 5042.555 FPS
^C
moster@moster-desktop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/7117 the monitor refresh rate.
32342 frames in 5.0 seconds = 6468.343 FPS
32457 frames in 5.0 seconds = 6491.259 FPS
32485 frames in 5.0 seconds = 6496.927 FPS
32462 frames in 5.0 seconds = 6492.231 FPS
^C
moster@moster-desktop:~$ 

```

---

### Post by MaxIBoy on 2009-06-26
Glxgears is not a benchmark, nor is it intended to be one. Framerate is tied to your monitor's refresh rate. Nonetheless, this is what I got:
```
~$glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/412368 the monitor refresh rate.
32992 frames in 5.0 seconds
33178 frames in 5.0 seconds
34411 frames in 5.0 seconds
34195 frames in 5.0 seconds
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 45 requests (45 known processed) with 0 events remaining.
~$

```MSI R4850 (Radeon HD 4850 with aftermarket cooler out of the box.)
Phenom X4 9550
4 sticks G.Skill DDR2-1066 RAM (1 gig per stick)
32-bit Ubuntu Karmic (Kernel 2.6.28-13)
AMD drivers version 8.620.

---

### Post by fatality_uk on 2009-06-26
Don't know if the other GLXGEARS thread is dead?


> Running synchronized to the vertical refresh.  The framerate should be
approximately 1/6521 the monitor refresh rate.
90010 frames in 5.0 seconds = 19001.931 FPS
82014 frames in 5.0 seconds = 21402.719 FPS
89824 frames in 5.0 seconds = 19964.699 FPS
89235 frames in 5.0 seconds = 17845.754 FPS
83775 frames in 5.0 seconds = 17754.853 FPS
78079 frames in 5.0 seconds = 19615.728 FPS

---

### Post by Dark Aspect on 2009-06-26
Seems like mine should be higher, but I guess its not a good benchmark.

NVIDA 185.18.14 driver
Geforce 9800 GT

```

Running synchronized to the vertical refresh.  The framerate should be
approximately 1/1340064 the monitor refresh rate.
12455 frames in 5.0 seconds = 2490.914 FPS
12522 frames in 5.0 seconds = 2504.371 FPS
11504 frames in 5.0 seconds = 2300.650 FPS
11703 frames in 5.0 seconds = 2340.532 FPS
11949 frames in 5.0 seconds = 2389.664 FPS
11584 frames in 5.0 seconds = 2316.792 FPS
11631 frames in 5.0 seconds = 2325.914 FPS
11908 frames in 5.0 seconds = 2381.463 FPS
11825 frames in 5.0 seconds = 2364.838 FPS
11808 frames in 5.0 seconds = 2361.479 FPS
```

---

### Post by moster on 2009-06-26
This glxgears is more dependable on CPU then GPU. Myabe we should run some game demo or something and post FPS. Something like OpenArena.

edit:
DarkAspect, you have super VGA card and ultra low CPU. That is not Ok. That CPU was middle range in year 2005. You will not have full benefit of you VGA.

---

### Post by MaxIBoy on 2009-06-26
Well, we could try the unigine tropics demo. I get 55.7 FPS on that.

---

### Post by Dark Aspect on 2009-06-26
> **moster said:**
> This glxgears is more dependable on CPU then GPU. Myabe we should run some game demo or something and post FPS. Something like OpenArena.

edit:
DarkAspect, you have super VGA card and ultra low CPU. That is not Ok. That CPU was middle range in year 2005. You will not have full benefit of you VGA.

I get 41 FPS in Nexuiz maxed out with "#timedemo demos/demo1", but thats with firefox and Ozzy Osbourne playing in the background.

Yes I know about the low CPU trust me, everything I play in windows is normally maxed out with graphics settings. However, any CPU dependent setting like effects detail is usually very very low. Its a happy meduim really since I only dropped $60 for the card and since my cpu is overclock its bareable.

---

