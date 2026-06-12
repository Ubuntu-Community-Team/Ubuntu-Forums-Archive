---
title: "fgl_fglxgears - better than glxgears"
date: 2007-11-02
forum: The Cafe
---

### Post by igknighted on 2007-11-02
I don't know if this comes with Ubuntu, but we have it on our Gentoo boxes at school.  Instead of using glxgears to test 3d rendering, try using 'fgl_fglxgears' instead.  Its a 3d cube that spins and has the traditional spinning gears on each face... very cool.  Probably closer to a true benchmark as well, but not quite as good as using a game like ut2004.

EDIT: I get this: ```
1019 frames in 5.0 seconds = 203.800 FPS
963 frames in 5.0 sec]onds = 192.600 FPS
1070 frames in 5.0 seconds = 214.000 FPS
1093 frames in 5.0 seconds = 218.600 FPS
```

On this computer:```
fitzgid@pluto:~>cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping        : 1
cpu MHz         : 3391.935
cache size      : 1024 KB
...
processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping        : 1
cpu MHz         : 3391.935
cache size      : 1024 KB
...

fitzgid@pluto:~>free
             total       used       free     shared    buffers     cached
Mem:       1032464     975668      56796          0      66812     659348
-/+ buffers/cache:     249508     782956
Swap:       996020        180     995840

fitzgid@pluto:~>lspci
...
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

```

---

### Post by bonzodog on 2007-11-02
Yeah, this is an ATI flgrx driver add on, so it's not on any boxes with nvidia.

---

### Post by igknighted on 2007-11-02
> **bonzodog said:**
> Yeah, this is an ATI flgrx driver add on, so it's not on any boxes with nvidia.

Thats a shame.  It's way cooler than glxgears.  Maybe I'll take a screen cap of it next time I'm in the lab for all you non-ati folk.

---

### Post by FuturePilot on 2007-11-02
> **igknighted said:**
> Thats a shame.  It's way cooler than glxgears.  Maybe I'll take a screen cap of it next time I'm in the lab for all you non-ati folk.

Yes, please. ;)

---

