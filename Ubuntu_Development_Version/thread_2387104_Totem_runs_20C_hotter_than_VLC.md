---
title: "Totem runs 20C hotter than VLC"
date: 2018-03-14
forum: Ubuntu Development Version
---

### Post by thebman2 on 2018-03-14
In 18.04, running video in Totem I noticed laptop heating up rather quickly (68-70C). Installed VLC and it will play same videos 20-25C cooler. Is this a known issue maybe easily correctable on my end thru configuration? Not sure where to look.

System:    Host: XPS-9360 Kernel: 4.15.0-10-generic x86_64 bits: 64
           Desktop: Gnome 3.27.92
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: laptop System: Dell product: XPS 13 9360 serial: N/A
           Mobo: Dell model: 0TPN17 v: A00 serial: N/A
           UEFI: Dell v: 2.5.1 date: 01/25/2018
Battery    BAT0: charge: 41.8 Wh 72.3% condition: 57.8/60.0 Wh (96%)
CPU:       Quad core Intel Core i7-8550U (-MT-MCP-) speed/max: 1502/4000 MHz
Graphics:  Card: Intel UHD Graphics 620
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1920x1080@59.93hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
           version: 4.5 Mesa 18.0.0-rc4

---

### Post by roots on 2018-03-15
As a starting point, you could check if the excess load is CPU bound and which processes are causing it by using ```
$ top
``` while running totem vs. vlc.

In addition, you could check the GPU load for totem vs. vlc by checking the output of

```
$  sudo intel_gpu_top
```.

You may have to install Intel GPU tools first:

```

$ sudo apt install intel-gpu-tools

```


Btw.: Welcome to Ubuntuforums! ;-)

---

### Post by thebman2 on 2018-03-15
I did a fresh install yesterday and updated, started checking functionality and noticed the heat issue. I did run the commands you listed on gnome/xorg, gnome/wayland, and on unity and the heat difference is only apparent in gnome/xorg. I will post results later today.

---

### Post by thebman2 on 2018-03-15
gnome-xorg-totem   temp 72C

  render busy:  18%:                                    render space: 9/16384

 task  percent busy
                            GAM:  18%:                         vert fetch: 9606696 (12087/sec)

                             CS:  18%:                            prim fetch: 3337874 (4131/sec)

                             VS:   5%:            VS invocations: 6566196 (8160/sec)

                           URBM:   5%:     GS invocations: 0 (0/sec)

                            SVG:   2%:                              GS prims: 0 (0/sec)

                             VF:   2%:                              CL invocations: 3283098 (4080/sec)

                           GAFS:   2%:     CL prims: 3250312 (4080/sec)

                             RS:   0%:                              PS invocations: 85091066300 (106520640/sec)

                            TSG:   0%:                           PS depth pass: 84200872674 (105096210/sec)

                             CL:   0%:                       
                            VFE:   0%:                       
                             SF:   0%:                       
                            SDE:   0%:      
 
 
 gnome-xorg-vlc  temp 51C
 
 render busy:   8%:     render space: 4/16384

                           task  percent busy

                            GAM:   9%:                            vert fetch: 6203825 (165119/sec)

                             CS:   7%:          prim fetch: 2149575 (57341/sec)

                           GAFS:  1%                        VS invocations: 4233612 (114484/sec)

                           URBM: 1%    GS invocations: 0 (0/sec)

                            SVG:   0%:                               GS prims: 0 (0/sec)

                             VS:   0%:                              CL invocations: 2116806 (57242/sec)

                             SF:   0%:                                   CL prims: 2098738 (57046/sec)

                             CL:   0%:                             PS invocations: 65027653500 (818919704/sec)

                             VF:   0%:                             PS depth pass: 64429315386 (804940295/sec)

                            TSG:   0%:                       

                            VFE:   0%:                       
                             RS:   0%:                       
                            SDE:   0%:                       
                           GAFM:   0%:

---

### Post by thebman2 on 2018-03-15
gnome-xorg-vlc
top - 11:10:21 up 55 min,  1 user,  load average: 0.77, 0.82, 0.86
Tasks: 240 total,   1 running, 170 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.7 us,  1.1 sy,  0.0 ni, 96.0 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem :  8048760 total,  5247408 free,  1325652 used,  1475700 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  6189244 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1055 brent     20   0 4224188 392240  89496 S  11.3  4.9   4:49.91 gnome-shell 
 3601 brent     20   0 2513236 115572  73024 S   8.9  1.4   0:01.52 vlc         
  883 brent     20   0  466776 122636  95780 S   5.3  1.5   3:23.51 Xorg        
 1078 brent      9 -11 2213848  12620   9356 S   2.6  0.2   0:27.14 pulseaudio  

gnome-xorg-totem
top - 11:16:36 up  1:01,  1 user,  load average: 1.32, 1.02, 0.92
Tasks: 242 total,   1 running, 169 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.4 us,  1.5 sy,  0.0 ni, 93.8 id,  0.2 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem :  8048760 total,  5163468 free,  1356532 used,  1528760 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  6138352 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1055 brent     20   0 4221880 394776  89244 S  18.5  4.9   5:28.92 gnome-shell 
 3843 brent     20   0 2299560 103284  65208 S  15.5  1.3   0:01.64 totem       
  883 brent     20   0  458680 118752  92148 S  11.2  1.5   3:50.96 Xorg        
 1078 brent      9 -11 2213848  12668   9404 S   1.7  0.2   0:28.27 pulseaudio

---

