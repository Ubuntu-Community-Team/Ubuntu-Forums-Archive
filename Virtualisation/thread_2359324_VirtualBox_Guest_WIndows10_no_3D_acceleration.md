---
title: "VirtualBox Guest WIndows10 no 3D acceleration"
date: 2017-04-22
forum: Virtualisation
---

### Post by Jonners59 on 2017-04-22
I am running Windows 10 as a guest on a xfce 4.12 using Oracle VirtualBox version Version 5.1.20 r114628 (Qt5.7.1) and latest Guest Additions.  I have an nVidia GoForce GTX950 video card with latest driver.  I have the setting in Display -> Screen for 3D Acceleration and 2D Video Acceleration ticked.

I am trying to run Sketchup 2017, but it will not run without 3D Acceleration enabled, but it says it is either not enabled or the card does not have the capability to run it.  I have seen in earlier versions that there was a bug in the Guest Additions, but can not find anything in the latest to suggest that there is still a problem.  Anyone help please????

---

### Post by efflandt on 2017-04-23
I have never run Windows in virtualbox, but if I try to check "2D Video  Acceleration" for a Linux guest, virtualbox says "Invalid settings  detected". So maybe the problem was the result of checking 2D. But 3D for virtualbox 5.1.20 r114628 definitely works (at  least for Linux client). Following assumes that "Sync to VBlank" is NOT  checked in host. And are you sure you installed updated Guest Additions  from within the Win10 guest? Following examples are glxgears in default  window to full screen in 1600x900 vbox window on 1080p screen, then back to default glxgears window.

Without 3D glxgears was noticeably jerky window or fullscreen. Everything was smooth in 3D.

64-bit 14.04 guest in 64-bit 16.10 host no acceleration:```
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4

OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 11.2.0
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

2392 frames in 5.0 seconds = 478.201 FPS
2288 frames in 5.0 seconds = 457.579 FPS
2303 frames in 5.0 seconds = 460.407 FPS
2325 frames in 5.0 seconds = 464.950 FPS
2129 frames in 5.0 seconds = 424.982 FPS
286 frames in 5.0 seconds = 56.876 FPS   ]
282 frames in 5.0 seconds = 56.312 FPS   ] fullscreen
270 frames in 5.0 seconds = 53.917 FPS   ]
333 frames in 5.0 seconds = 66.586 FPS   ]
2386 frames in 5.0 seconds = 477.135 FPS
2406 frames in 5.0 seconds = 481.053 FPS
2598  frames in 5.0 seconds = 519.429 FPS
```64-bit 14.04 guest in 64-bit  16.10 host 3D acceleration:```
direct rendering: Yes
server glx vendor string: Chromium
server glx version string: 1.3 Chromium
client glx vendor string: Chromium
client glx version string: 1.3 Chromium

OpenGL vendor string: Humper
OpenGL renderer string: Chromium
OpenGL version string: 2.1 Chromium 1.9
OpenGL shading language version string: 4.50 NVIDIA

4607 frames in 5.0 seconds = 921.214 FPS
4864 frames in 5.0 seconds = 972.600 FPS
4914 frames in 5.0 seconds = 982.727 FPS
4900 frames in 5.0 seconds = 979.830 FPS
5152 frames in 5.0 seconds = 1030.251 FPS ]
6654 frames in 5.0 seconds = 1330.624 FPS ] fullscreen
6645 frames in 5.0 seconds = 1328.789 FPS ]
5004 frames in 5.0 seconds = 1000.645 FPS ]
4875 frames in 5.0 seconds = 974.976 FPS
4887 frames in 5.0 seconds = 977.229 FPS
4906 frames in 5.0 seconds = 981.075 FPS
4854  frames in 5.0 seconds = 970.591 FPS
```64-bit Debian8 3D guest  averaged ~1500 FPS throughout and you could not even tell when glxgears  was full screen in the 1600x900 window.

---

### Post by Jonners59 on 2017-04-24
Run into bigger issues.  Seems Dropbox is playing up on all our PCs and Laptops and I followed the instructions now VirtualBox and even SYnaptic won't run....  Frustration.  I thought all these dodgy system upgrades were a thing of the past.

---

