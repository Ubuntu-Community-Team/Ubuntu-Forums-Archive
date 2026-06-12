---
title: "mir performance with glxgears and other info"
date: 2014-04-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-04-25
Just testing unity-system-co performance.

with-mir

```

ventrical@ventrical-desktop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
2753 frames in 5.0 seconds = 550.537 FPS
2745 frames in 5.0 seconds = 548.931 FPS
2727 frames in 5.0 seconds = 545.074 FPS
2715 frames in 5.0 seconds = 542.526 FPS
2732 frames in 5.0 seconds = 546.348 FPS
2706 frames in 5.0 seconds = 540.632 FPS
2750 frames in 5.0 seconds = 549.898 FPS
2731 frames in 5.0 seconds = 545.880 FPS
2729 frames in 5.0 seconds = 545.703 FPS
2669 frames in 5.0 seconds = 533.750 FPS
2651 frames in 5.0 seconds = 529.565 FPS

```

with-xorg

```

ventrical@ventrical-desktop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
259 frames in 5.0 seconds = 51.742 FPS
246 frames in 5.0 seconds = 49.108 FPS
250 frames in 5.0 seconds = 49.717 FPS
261 frames in 5.0 seconds = 52.103 FPS
248 frames in 5.0 seconds = 49.179 FPS
247 frames in 5.0 seconds = 48.981 FPS
250 frames in 5.0 seconds = 49.908 FPS
249 frames in 5.0 seconds = 49.375 FPS
246 frames in 5.0 seconds = 49.108 FPS
246 frames in 5.0 seconds = 49.106 FPS
248 frames in 5.0 seconds = 49.504 FPS

```

```

ventrical@ventrical-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
ventrical@ventrical-desktop:~$ 

```

```


ventrical@ventrical-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
ventrical@ventrical-desktop:~$ 

```

---

### Post by grahammechanical on 2014-04-25
@ventrical, if you do not mind me saying so, there is something very wrong with the results for with-mir. This is what I get with xserver.

> graham@Sdb8-Roll-Dev:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
270 frames in 5.0 seconds = 53.764 FPS
265 frames in 5.0 seconds = 52.990 FPS
248 frames in 5.0 seconds = 49.566 FPS
250 frames in 5.0 seconds = 49.991 FPS
248 frames in 5.0 seconds = 49.412 FPS
249 frames in 5.0 seconds = 49.524 FPS
249 frames in 5.0 seconds = 49.609 FPS
249 frames in 5.0 seconds = 49.608 FPS
248 frames in 5.0 seconds = 49.599 FPS
249 frames in 5.0 seconds = 49.758 FPS
251 frames in 5.0 seconds = 50.198 FPS
252 frames in 5.0 seconds = 50.330 FPS


I am not running xmir so I cannot compare but it sure cannot speed things up by more than 10 times. My guess is that mesa-utils is not compatible with mir. I found this the other day. It is old but somewhere there might be something that points to a better method of testing performance.

[http://samohtv.wordpress.com/](http://samohtv.wordpress.com/)

glmark2 is in the trusty/utopic software centre.

[https://launchpad.net/glmark2](https://launchpad.net/glmark2)

Regards.

---

### Post by ventrical on 2014-04-25
Thanks for your reply. Actually I was quite surprised. I did notice however that with-xorg the gears are rather chunky but with-xmir it is extremely smooth. I'll look for other tests.

---

### Post by grahammechanical on 2014-04-25
I have just installed OpenGL (ES) 2.0 benchmark. It is run in a terminal with glmark2 and Wow! Is that a unicorn I see before me? Just let it run and run. It will eventually stop and this is what I get with xserver.

> graham@Sdb8-Roll-Dev:~$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     nouveau
    GL_RENDERER:   Gallium 0.4 on NVA5
    GL_VERSION:    3.0 Mesa 10.1.0
=======================================================
[build] use-vbo=false: FPS: 113 FrameTime: 8.850 ms
[build] use-vbo=true: FPS: 115 FrameTime: 8.696 ms
[texture] texture-filter=nearest: FPS: 113 FrameTime: 8.850 ms
[texture] texture-filter=linear: FPS: 118 FrameTime: 8.475 ms
[texture] texture-filter=mipmap: FPS: 114 FrameTime: 8.772 ms
[shading] shading=gouraud: FPS: 112 FrameTime: 8.929 ms
[shading] shading=blinn-phong-inf: FPS: 116 FrameTime: 8.621 ms
[shading] shading=phong: FPS: 114 FrameTime: 8.772 ms
[bump] bump-render=high-poly: FPS: 113 FrameTime: 8.850 ms
[bump] bump-render=normals: FPS: 112 FrameTime: 8.929 ms
[bump] bump-render=height: FPS: 114 FrameTime: 8.772 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 113 FrameTime: 8.850 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 114 FrameTime: 8.772 ms
[pulsar] light=false:quads=5:texture=false: FPS: 111 FrameTime: 9.009 ms
[desktop] blur-radius=5:effect=blur: passes=1:separable=true:windows=4: FPS: 108 FrameTime: 9.259 ms
[desktop] effect=shadow:windows=4: FPS: 97 FrameTime: 10.309 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 34 FrameTime: 29.412 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 35 FrameTime: 28.571 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 35 FrameTime: 28.571 ms
[ideas] speed=duration: FPS: 70 FrameTime: 14.286 ms
[jellyfish] <default>: FPS: 111 FrameTime: 9.009 ms
[terrain] <default>: FPS: 56 FrameTime: 17.857 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 111 FrameTime: 9.009 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 110 FrameTime: 9.091 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 111 FrameTime: 9.009 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 112 FrameTime: 8.929 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 115 FrameTime: 8.696 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 113 FrameTime: 8.850 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 114 FrameTime: 8.772 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 112 FrameTime: 8.929 ms
=======================================================
                                  glmark2 Score: 101 
=======================================================

If only I knew what it meant.

---

### Post by ventrical on 2014-04-25
I installed a program from the Software Center called Blobs. It measures fps. I am still getting 3 to 4 times faster than with xorg.

---

### Post by ventrical on 2014-04-25
I think it is an average score.

With mir.

```

ventrical@ventrical-desktop:~$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     nouveau
    GL_RENDERER:   Gallium 0.4 on NVA8
    GL_VERSION:    3.0 Mesa 10.1.0
=======================================================
[build] use-vbo=false: FPS: 211 FrameTime: 4.739 ms
[build] use-vbo=true: FPS: 236 FrameTime: 4.237 ms
[texture] texture-filter=nearest: FPS: 219 FrameTime: 4.566 ms
[texture] texture-filter=linear: FPS: 216 FrameTime: 4.630 ms
[texture] texture-filter=mipmap: FPS: 225 FrameTime: 4.444 ms
[shading] shading=gouraud: FPS: 211 FrameTime: 4.739 ms
[shading] shading=blinn-phong-inf: FPS: 212 FrameTime: 4.717 ms
[shading] shading=phong: FPS: 203 FrameTime: 4.926 ms
[bump] bump-render=high-poly: FPS: 195 FrameTime: 5.128 ms
[bump] bump-render=normals: FPS: 233 FrameTime: 4.292 ms
[bump] bump-render=height: FPS: 217 FrameTime: 4.608 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 194 FrameTime: 5.155 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 119 FrameTime: 8.403 ms
[pulsar] light=false:quads=5:texture=false: FPS: 203 FrameTime: 4.926 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 210 FrameTime: 4.762 ms
[desktop] effect=shadow:windows=4: FPS: 226 FrameTime: 4.425 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 179 FrameTime: 5.587 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 191 FrameTime: 5.236 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 175 FrameTime: 5.714 ms
[ideas] speed=duration: FPS: 221 FrameTime: 4.525 ms
[jellyfish] <default>: FPS: 139 FrameTime: 7.194 ms
[terrain] <default>: FPS: 27 FrameTime: 37.037 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 253 FrameTime: 3.953 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 192 FrameTime: 5.208 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 253 FrameTime: 3.953 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 256 FrameTime: 3.906 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 199 FrameTime: 5.025 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 237 FrameTime: 4.219 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 260 FrameTime: 3.846 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 213 FrameTime: 4.695 ms
=======================================================
                                  glmark2 Score: 204 
=======================================================
ventrical@ventrical-desktop:~$ 

```

So ..according to this test it can be assumed that with-mir is twice as fast as xorg and I think we are running the same graphics adapter cards (nVidia GeForce 218).

  There is the old mir bug, though, that old bug that makes typing in from the keyboard show a significant delay.

---

### Post by grahammechanical on 2014-04-25
I have just run glmark2 on my 14.04 install that I was using as a fallback OS. I installed ubuntu-desktop-mir and unity-system-compositor and I made sure that it was running on xmir and this is what I got

>  graham@sda2-fallback:~$ glmark2=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     nouveau
    GL_RENDERER:   Gallium 0.4 on NVA5
    GL_VERSION:    3.0 Mesa 10.1.0
=======================================================
[build] use-vbo=false: FPS: 287 FrameTime: 3.484 ms
[build] use-vbo=true: FPS: 324 FrameTime: 3.086 ms
[texture] texture-filter=nearest: FPS: 309 FrameTime: 3.236 ms
[texture] texture-filter=linear: FPS: 310 FrameTime: 3.226 ms
[texture] texture-filter=mipmap: FPS: 319 FrameTime: 3.135 ms
[shading] shading=gouraud: FPS: 304 FrameTime: 3.289 ms
[shading] shading=blinn-phong-inf: FPS: 303 FrameTime: 3.300 ms
[shading] shading=phong: FPS: 301 FrameTime: 3.322 ms
[bump] bump-render=high-poly: FPS: 250 FrameTime: 4.000 ms
[bump] bump-render=normals: FPS: 324 FrameTime: 3.086 ms
[bump] bump-render=height: FPS: 317 FrameTime: 3.155 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 277 FrameTime: 3.610 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 191 FrameTime: 5.236 ms
[pulsar] light=false:quads=5:texture=false: FPS: 283 FrameTime: 3.534 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 299 FrameTime: 3.344 ms
[desktop] effect=shadow:windows=4: FPS: 301 FrameTime: 3.322 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 211 FrameTime: 4.739 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 220 FrameTime: 4.545 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 214 FrameTime: 4.673 ms
[ideas] speed=duration: FPS: 285 FrameTime: 3.509 ms
[jellyfish] <default>: FPS: 196 FrameTime: 5.102 ms
[terrain] <default>: FPS: 48 FrameTime: 20.833 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 312 FrameTime: 3.205 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 296 FrameTime: 3.378 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 311 FrameTime: 3.215 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 312 FrameTime: 3.205 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 306 FrameTime: 3.268 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 312 FrameTime: 3.205 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 311 FrameTime: 3.215 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 289 FrameTime: 3.460 ms
=======================================================
                                  glmark2 Score: 277 
=======================================================

I have xserver glmark2 score = 101 and xmir glmark2 score = 277. Yes, similar Nvidia card. GT220 but the important point is not that we are comparing the results from two different machines but we are comparing two results on the same machine. The difference being the video server, x compared to mir.

Regards.

---

### Post by ventrical on 2014-04-25
I have been doing some research on testing graphics adapters.. etc...and some say that fps rates are not an accurate way to test. To each their own. By your results and the results I have also put up I would say it is safe to assume that these test prove that mir  runs significantly faster than xorg.

Regards..

---

### Post by Mateusz Stachowski on 2014-04-26
First of all glxgears is not a benchmark. Then you have this:

> Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.

The results should be around the refresh of your monitor which in most cases this would be 60 FPS. You get much more FPS under XMir because of this bug:

[[regression] GL(X) apps don't have vsync when running under XMir]("https://bugs.launchpad.net/xmir/+bug/1211186")

---

### Post by ventrical on 2014-04-26
> **Mateusz Stachowski said:**
> First of all glxgears is not a benchmark. Then you have this:



The results should be around the refresh of your monitor which in most cases this would be 60 FPS. You get much more FPS under XMir because of this bug:

[[regression] GL(X) apps don't have vsync when running under XMir]("https://bugs.launchpad.net/xmir/+bug/1211186")

How about the Blob(s) test? <from USC> They both cannot be wrong , can they? or is this mir bug making a run across the board?

regards..

---

### Post by Mateusz Stachowski on 2014-04-26
I think that this bug has also skewed the results you are getting with glmark2 and Globs (it isn't Blobs). 

If I remember correctly I also had much higher scores in glmark2 on XMir than X server but UNIGINE Heaven 3.0 was actually a little bit slower. The same thing showed in Phoronix tests.

Also there was this bug with Nouveau on XMir (kernel bug):

[nouveau: Graphics tearing and abnormally high FPS with nouveau (no vsync)]("https://bugs.launchpad.net/mir/+bug/1195811")

Daniel van Vugt one of the Mir developers marked it as Fix Released but perhaps he was mistaken or the bug is still happening with XMir but not native Mir. The native Mir demos (like egltriangle and eglplasma) that I run on Trusty were constrained on vsync (60 FPS).

---

### Post by fjgaude on 2014-04-26
frank@flash:~$ glmark2
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     Intel Open Source Technology Center
    GL_RENDERER:   Mesa DRI Intel(R) Haswell Desktop 
    GL_VERSION:    3.0 Mesa 10.1.0
=======================================================
[build] use-vbo=false: FPS: 3381 FrameTime: 0.296 ms
[build] use-vbo=true: FPS: 3476 FrameTime: 0.288 ms
[texture] texture-filter=nearest: FPS: 3982 FrameTime: 0.251 ms
[texture] texture-filter=linear: FPS: 3967 FrameTime: 0.252 ms
[texture] texture-filter=mipmap: FPS: 3929 FrameTime: 0.255 ms
[shading] shading=gouraud: FPS: 2986 FrameTime: 0.335 ms
[shading] shading=blinn-phong-inf: FPS: 3083 FrameTime: 0.324 ms
[shading] shading=phong: FPS: 3032 FrameTime: 0.330 ms
[bump] bump-render=high-poly: FPS: 1426 FrameTime: 0.701 ms
[bump] bump-render=normals: FPS: 4114 FrameTime: 0.243 ms
[bump] bump-render=height: FPS: 3981 FrameTime: 0.251 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 1989 FrameTime: 0.503 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 830 FrameTime: 1.205 ms
[pulsar] light=false:quads=5:texture=false: FPS: 2744 FrameTime: 0.364 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 822 FrameTime: 1.217 ms
[desktop] effect=shadow:windows=4: FPS: 1365 FrameTime: 0.733 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 922 FrameTime: 1.085 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 1040 FrameTime: 0.962 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 1020 FrameTime: 0.980 ms
[ideas] speed=duration: FPS: 2270 FrameTime: 0.441 ms
[jellyfish] <default>: FPS: 1468 FrameTime: 0.681 ms
[terrain] <default>: FPS: 196 FrameTime: 5.102 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 3293 FrameTime: 0.304 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 3404 FrameTime: 0.294 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 3291 FrameTime: 0.304 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 3313 FrameTime: 0.302 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 3395 FrameTime: 0.295 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 3304 FrameTime: 0.303 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 3217 FrameTime: 0.311 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 3280 FrameTime: 0.305 ms
=======================================================
                                  glmark2 Score: 2617 
=======================================================

---

### Post by grahammechanical on 2014-04-27
@fjgaude

Is that with Xserver or Xmir?

Regards.

---

### Post by fjgaude on 2014-04-27
Neither, but with xorg! Notice my signature... just Intel built-in graphics under Haswell chip set.

GtkPerf 0.40 - Starting testing: Sun Apr 27 08:41:37 2014

GtkEntry - time:  0.01
GtkComboBox - time:  0.31
GtkComboBoxEntry - time:  0.24
GtkSpinButton - time:  0.03
GtkProgressBar - time:  0.03
GtkToggleButton - time:  0.08
GtkCheckButton - time:  0.03
GtkRadioButton - time:  0.05
GtkTextView - Add text - time:  0.14
GtkTextView - Scroll - time:  0.03
GtkDrawingArea - Lines - time:  0.25
GtkDrawingArea - Circles - time:  0.21
GtkDrawingArea - Text - time:  0.08
GtkDrawingArea - Pixbufs - time:  0.01
 --- 
Total time:  1.50

---

### Post by grahammechanical on 2014-04-27
I have noticed that subsequent runs of glmark2 produce slightly better results but that runs 4 and 5 and onwards show no improvement over run 3. This is what I get

Utopic + Xserver + Compiz + Unity 7 glmark 2 scores run 1 = 100; run 2 = 102; run 3 = 102; run 4 = 101.

Utopic + Xmir + Compiz + Unity 8 glmark2 scores run 1 = 272; run 2 = 293; run 3 = 294; run 4 = 294.

I am now curious as what scores I get with Kubuntu (Xserver + Kwin) and Xubuntu and Wayland/Weston or any other Wayland compositor that is developed. Over the next 18 months we will have opportunities for comparing a few video server/compositor combinations.

Regards.

---

### Post by fjgaude on 2014-04-27
I'll wait until 14.10 is near release before I think of trying xmir in Unity or whatever. My box is fast enough for all the things I do. I'm not a heavy gamer, but a graphic designer. I'm good for the mid-level games with Intel built-in HD4600 graphics.

---

### Post by jerrylamos on 2014-04-28
> **grahammechanical said:**
> @ventrical, if you do not mind me saying so, there is something very wrong with the results for with-mir. This is what I get with xserver.

I am not running xmir so I cannot compare but it sure cannot speed things up by more than 10 times. My guess is that mesa-utils is not compatible with mir. I found this the other day. It is old but somewhere there might be something that points to a better method of testing performance.

[http://samohtv.wordpress.com/](http://samohtv.wordpress.com/)

glmark2 is in the trusty/utopic software centre.

[https://launchpad.net/glmark2](https://launchpad.net/glmark2)

Regards.
I've used gtkperf for screen performance before.

sudo apt-get install gtkperf
gtkperf

I got the same results for tahr and utopic.

How do I run mir on utopic?  A quick google looked like some info for 13.10 maybe last August.

Thanks.

---

### Post by fjgaude on 2014-04-28
@jerryamos: "I got the same results for tahr and utopic."

So do it and even the the last update to 13.10. All the same in gtkperf and with hdparm -tT /dev/sda. Didn't try glmark2 except on 14.10.

---

### Post by jerrylamos on 2014-04-29
> **fjgaude said:**
> @jerryamos: "I got the same results for tahr and utopic."

So do it and even the the last update to 13.10. All the same in gtkperf and with hdparm -tT /dev/sda. Didn't try glmark2 except on 14.10.
I'm not familiar with glmark2. On 14.04 I got:
glmark2
Error: Glmark2 needs OpenGL(ES) version >= 2.0 to run (but version string is: '1.4 Mesa 10.1.0')!

Thanks...

---

### Post by grahammechanical on 2014-04-29
> [COLOR=#000000]How do I run mir on utopic? [/COLOR]
We install ubuntu-desktop-mir and unity-system-compositor . They are in the software centre. We also need to be running on an open source video driver. I also installed OpenGL (ES) 2.0 benchmark from the software centre and I have no problems running it with the command glmark2.

>   OpenGL Information
    GL_VENDOR:     nouveau
    GL_RENDERER:   Gallium 0.4 on NVA5
    GL_VERSION:    3.0 Mesa 10.1.0


To test that Xmir is actually running

```
 grep -i LoadModule /var/log/Xorg.0.log
```

And look to see if the Xmir module is loaded.
Regards.

---

### Post by grahammechanical on 2014-04-29
Now I really am confused. I have been running glmark2 on Utopic both on xserver and xmir and these are some of the scores.

xserver + Unity 7 score = 101
xserver + flashback (compiz) score = 92
xserver + flashback (metacity) score = 547
xmir + unity 8 score = 272
xserver + xubuntu score = 487

It seems that the window compositor plays a big part in what is going on. And at the moment Ubuntu is using Compiz as the compositor. I cannot wait until we have the opportunity to compare full Mir and a Wayland compositor.

---

### Post by jerrylamos on 2014-04-30
Well Mir must be running because the screen is screwed up and browser overlaid on top of terminal window.  Cursor only works over part of the screen.  How do I turn Mir off?

'Way back last fall, Mir couldn't handle two displays.

Mir still can't handle two displays here, the built-in display and the external higher resolution display.

The images get overlaid,

The cursor can't handle the two images.

I couldn't even get an ubuntu-bug going.  I could enter the command, but the end of the line was overlaid by the other screen so I couldn't enter any responses.

Whew.  Got Mir stopped with the 13.10 directions: [https://wiki.ubuntu.com/Mir/Installing#preview](https://wiki.ubuntu.com/Mir/Installing#preview)

---

### Post by ventrical on 2014-04-30
Since you brought up Wayland I am somewhat confused also. Is ayland installed or can we implement it with some command. It has been downloaded and installed , apparently .. or are these just dummy transitionals?

---

### Post by grahammechanical on 2014-04-30
I notice that Weston is not installed. I guess that Weston is the compositor.

At the moment I am collecting data using glmark2-es2 and I am putting what I find in a spreadsheet. It is a bit too much like work as far as I am concerned. I see three factors effecting results. 1) the display server - Xserver or Xmir. 2) the compositor - Compiz or Metacity or wherever. 3) the video driver. I am using Nouveau. I am keeping out of proprietary. It will add confusion.

The most interesting comparison will be between the Xserver/Compiz combination and Mir and whatever Wayland compositor is released. There is Weston. Gnome are working on one. I am not sure if that is Weston or a Gnome specific Wayland compositor. As far as I know KDE people are not yet working on a KDE Wayland compositor. It all makes the coming months interesting from the point of view of the practical tester.

I need to research Wayland. We may need to start a thread specific to testing coming compositors on the development branch. I have not studied this but I think that Metacity is scoring higher than Compiz because its 2D results are boosting the end score. How well does Metacity do with 3D effects? That is the question. As I say, I have not examined that. Not yet.

End users will need a new display server/compositor combination that performs at least as well as the present Xserver combinations and they will prefer better performance. 

Regards.

---

### Post by ventrical on 2014-04-30
> **grahammechanical said:**
> I notice that Weston is not installed. I guess that Weston is the compositor.

At the moment I am collecting data using glmark2-es2 and I am putting what I find in a spreadsheet. It is a bit too much like work as far as I am concerned. I see three factors effecting results. 1) the display server - Xserver or Xmir. 2) the compositor - Compiz or Metacity or wherever. 3) the video driver. I am using Nouveau. I am keeping out of proprietary. It will add confusion.

The most interesting comparison will be between the Xserver/Compiz combination and Mir and whatever Wayland compositor is released. There is Weston. Gnome are working on one. I am not sure if that is Weston or a Gnome specific Wayland compositor. As far as I know KDE people are not yet working on a KDE Wayland compositor. It all makes the coming months interesting from the point of view of the practical tester.

I need to research Wayland. We may need to start a thread specific to testing coming compositors on the development branch.  

Regards.

Agreed. Thanks for your detailed synopsis of these current scenarios  and your suggestions.

Regards..

---

### Post by grahammechanical on 2014-04-30
I have been nosing around. I found this in ArchLinux wiki

> [COLOR=#000000][FONT=sans-serif]Wayland is most probably installed on your system already as it is an indirect dependency of [/FONT][/COLOR][COLOR=#000000][FONT=monospace][gtk2]("https://www.archlinux.org/packages/?name=gtk2")[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] and [/FONT][/COLOR][COLOR=#000000][FONT=monospace][gtk3]("https://www.archlinux.org/packages/?name=gtk3")[/FONT][/COLOR]

I think that explains why we have Wayland Libraries in Ubuntu. I found this as regards the intentions of the Gnome Devs.

> 
[LIST]
[*]GNOME 3.12 (Mar 2014)
[LIST]
[*]Complete port of GNOME to Wayland
[*]Most parts of GNOME will still work under X (some parts may be hard to keep working under both X and Wayland)
[*]All core GNOME applications work with Wayland
[/LIST]
[/LIST]


Ubuntu Gnome as yet does not have Gnome 3.12. We need this PPA

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

From the little reading I have done I do not think that Wayland and its compositors are further advanced than Mir. There is still a lot of work to be done by both camps. And for all the moans about fragmentation when it come to compositors the developers of each desktop environment are having to code their own compositor.

---

### Post by ventrical on 2014-05-21
unity system compositor and mir desktop are now downloaded but you still have to evoke the code to install them.


 After trying on a fairly new install I still get bug soup when trying to run unity8.

```


ventrical@ventrical-MS-7798:~$ unity8
Need to use QMirServerApplication
Need to use QMirServerApplication
unity::action::ActionManager::ActionManager(QObject*):
    Could not determine application identifier. HUD will not work properly.
    Provide your application identifier in $APP_ID environment variable.
file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/Tabs.qml:341: TypeError: Cannot call method 'indexOf' of undefined
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Unable to register launcher name 
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
file:///usr/share/unity8/Shell.qml:615:5: QML Binding: Binding loop detected for property "target"
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:62:20: QML QQuickImage: Failed to get image from provider: image://theme/firefox
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:62:20: QML QQuickImage: Failed to get image from provider: image://theme/firefox
file:///usr/share/unity8/Launcher/LauncherDelegate.qml:62:20: QML QQuickImage: Failed to get image from provider: image://theme/firefox
Could not resolve property : linearGradient9800
Could not resolve property : linearGradient9800
Could not resolve property : linearGradient9800
Could not resolve property : linearGradient9800
Could not resolve property : linearGradient9800
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
file:///usr/share/unity8/Stages/PhoneStage.qml:165:5: QML Connections: Cannot assign to non-existent property "onScreenshotChanged"
file:///usr/share/unity8/Stages/PhoneStage.qml:59:5: QML Connections: Cannot assign to non-existent property "onApplicationRemoved"
file:///usr/share/unity8/Stages/PhoneStage.qml:59:5: QML Connections: Cannot assign to non-existent property "onApplicationAdded"
file:///usr/share/unity8/Stages/PhoneStage.qml:59:5: QML Connections: Cannot assign to non-existent property "onFocusedApplicationIdChanged"
file:///usr/share/unity8/Stages/PhoneStage.qml:59:5: QML Connections: Cannot assign to non-existent property "onFocusRequested"
Need to use QMirServerApplication
Need to use QMirServerApplication
Need to use QMirServerApplication
file:///usr/share/unity8/Stages/PhoneStage.qml:51: TypeError: Property 'get' of object [object Object] is not a function
file:///usr/share/unity8/Shell.qml:251:9: QML Connections: Cannot assign to non-existent property "onApplicationRemoved"
file:///usr/share/unity8/Shell.qml:251:9: QML Connections: Cannot assign to non-existent property "onApplicationAdded"
file:///usr/share/unity8/Shell.qml:251:9: QML Connections: Cannot assign to non-existent property "onFocusedApplicationIdChanged"
file:///usr/share/unity8/Shell.qml:251:9: QML Connections: Cannot assign to non-existent property "onFocusRequested"
file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/Themes/Ambiance/TabBarStyle.qml:62: TypeError: Cannot read property 'selectedIndex' of null
file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/MainView.qml:202:5: QML StyledItem: Binding loop detected for property "style"
file:///usr/share/unity8/Stages/PhoneStage.qml:60:17: Unable to assign null to QObject*
file:///usr/share/unity8/Stages/PhoneStage.qml:117: TypeError: Property 'findApplication' of object [object Object] is not a function
file:///usr/share/unity8/Stages/PhoneStage.qml:116:39: Unable to assign [undefined] to QString
file:///usr/share/unity8/Stages/PhoneStage.qml:166:17: Unable to assign [undefined] to QObject*
file:///usr/share/unity8/Stages/PhoneStage.qml:194: TypeError: Property 'findApplication' of object [object Object] is not a function
file:///usr/share/unity8/Shell.qml:51:52: Unable to assign [undefined] to QString
file:///usr/share/unity8/Shell.qml:252:21: Unable to assign null to QObject*
file:///usr/share/unity8/Shell.qml:415:25: Unable to assign null to QObject*
file:///usr/share/unity8/Shell.qml:424: TypeError: Cannot read property 'length' of undefined
file:///usr/share/unity8/Shell.qml:474: TypeError: Property 'findApplication' of object [object Object] is not a function
file:///usr/share/unity8/Shell.qml:473:43: Unable to assign [undefined] to QString
file:///usr/share/unity8/Shell.qml:475:29: Unable to assign [undefined] to bool
file:///usr/share/unity8/Shell.qml:633:18: Unable to assign [undefined] to bool

** (unity8:3930): WARNING **: Unable to register app: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid application ID
ERROR! Caught unity::scopes::TimeoutException: Request timed out after 300 milliseconds
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/Themes/Ambiance/TabBarStyle.qml:72: TypeError: Cannot read property 'selectedIndex' of null
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
UbuntuKeyboardInfo - socket error: "QLocalSocket::connectToServer: Invalid name" 
Failed to connect to "/run/user/1000/ubuntu-keyboard-info" after 10 failed attempts 
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by ventrical on 2014-05-21
Still have the cursor delay with Mir when editing and repsonding to messages .. etc..

EDIT:

Actually this cursor bug is really a pain (fast pc or no fast pc).. so I'm switching back to xorg dry, unless anyone has a suggested work-a-round?
 

I relented and see that unity8 mir can be run from lightdm - but no mouse pointer.

---

