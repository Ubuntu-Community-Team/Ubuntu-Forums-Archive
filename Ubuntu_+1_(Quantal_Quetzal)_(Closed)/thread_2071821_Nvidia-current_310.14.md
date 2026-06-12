---
title: "Nvidia-current_310.14"
date: 2012-10-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-10-16
The new nvidia-current (version 310.14) is available from xorg-edgers PPA now.

---

### Post by funicorn on 2012-10-16
[LIST]
[*]Implemented workarounds for two  Adobe Flash bugs by applying libvdpau commit  ca9e637c61e80145f0625a590c91429db67d0a40 to the version of libvdpau  shipped with the NVIDIA driver.
[*]Fixed an issue which affected the performance of moving windows of VDPAU applications when run in some composite managers.
[*]Added unofficial GLX protocol support (i.e., for GLX indirect rendering) for the GL_ARB_pixel_buffer_object OpenGL extension.
[*]Added  support for HDMI 3D Stereo with Quadro Kepler and later GPUs. See the  documentation for the "Stereo" X configuration option in the README for  details.
[*]Added experimental support for OpenGL threaded  optimizations, available through the __GL_THREADED_OPTIMIZATIONS  environment variable. For more information, please refer to the  "Threaded Optimizations" section in chapter "Specifying OpenGL  Environment Variable Settings" of the README.
[*]Improved performance and responsiveness of windowed OpenGL applications running inside a Unity session.
[*]Added support for OpenGL 4.3.
[*]Added support for the "Backlight" RandR output property for configuring the brightness of some notebook internal panels.
[*][COLOR=Red]Fixed a bug that prevented the Ubuntu Unity launcher panel from unhiding: [https://bugs.launchpad.net/unity/](https://bugs.launchpad.net/unity/)+bug/1057000[/COLOR]
[*]Fixed a bug that caused nvidia-installer to sometimes attempt to write a log file in a nonexistent directory.
[*]Fixed  a bug that caused incorrect input transformation after resizing an  NVIDIA X screen with xserver ABI 12 (xorg-server 1.12) or newer.
[*]Fixed a bug that caused GLX to leak memory when Xinerama is enabled.
[/LIST]

---

### Post by cicoandcico on 2012-10-16
[LIST]
[*]Improved performance and responsiveness of windowed OpenGL applications running inside a Unity session.
[/LIST]
has anyone benchmarked that? games still suck compared to gnome shell, maybe this could help...

---

### Post by pqwoerituytrueiwoq on 2012-10-16
> **funicorn said:**
> Implemented workarounds for two  Adobe Flash bugs by applying libvdpau commit  ca9e637c61e80145f0625a590c91429db67d0a40 to the version of libvdpau  shipped with the NVIDIA driver.
blue people on youtube is [s]fixed[/s] err worked around :)

---

### Post by paul_in_london on 2012-10-16
Not good for me. My GPU isn't supported by the latest nvidia driver. :(

From /var/log/Xorg.0.log.old:

```
...
[    24.481] (II) LoadModule: "nvidia"
[    24.482] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    24.482] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.482]    compiled for 4.0.2, module version = 1.0.0
[    24.482]    Module class: X.Org Video Driver
[    24.520] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    24.520] (EE) NVIDIA:     system's kernel log for additional error messages.
[    24.520] (II) UnloadModule: "nvidia"
[    24.520] (II) Unloading nvidia
[    24.520] (EE) Failed to load module "nvidia" (module-specific error, 0)
...

```

From /var/log/kernel.log:

```
...
Oct 16 22:57:47 localhost kernel: [   12.925173] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 16 22:58:02 localhost kernel: [   27.177056] NVRM: The NVIDIA Quadro FX 1400 GPU installed in this system is
Oct 16 22:58:02 localhost kernel: [   27.177056] NVRM:  supported through the NVIDIA 304.xx Legacy drivers. Please
Oct 16 22:58:02 localhost kernel: [   27.177056] NVRM:  visit http://www.nvidia.com/object/unix.html for more
Oct 16 22:58:02 localhost kernel: [   27.177056] NVRM:  information.  The 310.14 NVIDIA driver will ignore
Oct 16 22:58:02 localhost kernel: [   27.177056] NVRM:  this GPU.  Continuing probe...
Oct 16 22:58:02 localhost kernel: [   27.177099] NVRM: No NVIDIA graphics adapter found!
Oct 16 22:58:02 localhost kernel: [   27.308966] NVRM: The NVIDIA Quadro FX 1400 GPU installed in this system is
Oct 16 22:58:02 localhost kernel: [   27.308966] NVRM:  supported through the NVIDIA 304.xx Legacy drivers. Please
Oct 16 22:58:02 localhost kernel: [   27.308966] NVRM:  visit http://www.nvidia.com/object/unix.html for more
Oct 16 22:58:02 localhost kernel: [   27.308966] NVRM:  information.  The 310.14 NVIDIA driver will ignore
Oct 16 22:58:02 localhost kernel: [   27.308966] NVRM:  this GPU.  Continuing probe...
Oct 16 22:58:02 localhost kernel: [   27.309008] NVRM: No NVIDIA graphics adapter found!
...
```

Had to downgrade and pin to previous version:

```
paul@quantal-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.51.really.304.43-0ubuntu1
  Candidate: 310.14-0ubuntu1~xedgers~quantal2
  Version table:
     310.14-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
 *** 304.51.really.304.43-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
paul@quantal-64:~$
```

EDIT: Found out that pinning via synaptic wasn't enough. So I ran:

```
paul@quantal-64:~$ sudo -s
root@quantal-64:~# echo nvidia-current hold | dpkg --set-selections
```

---

### Post by effenberg0x0 on 2012-10-16
I couldn't see a difference in performance (glxgears, gtkperf, HD video playback, Flash, XBMC) from 304.51 to 310.14 using up-to-date QQ with and without the 3 relevant OpenGL settings I mentioned [here]("http://ubuntuforums.org/showthread.php?t=2064664").

Also, I still get art-deco corruption on lightdm, flash video/banner pieces/artifacts in the Dash and random parts of the screen on long sessions (like 8+ hours), flashing windows titlebars (really random) and some other old bugs we know and love.

My tests were on GTS450, GT9500, GT9800. I just bought a GTX550TI and will be testing as soon as I receive it in a couple days. 

The driver is OK for these cards on PP-latest though - no change, no visible bugs.

Regards,
Effenberg

---

### Post by Rukiri on 2012-10-16
since kernel 3.7 is just so new, nvidia drivers will not install or compile from source because 304.51 is not compat nor is 310.14  once 310.14 goes stable is should work in 3.7.

I usually wait until RC4 to actually start using the latest kernel, my drivers never work with rc1.

---

### Post by VinDSL on 2012-10-17
> **paul_in_london said:**
> Not good for me. My GPU isn't supported by the latest nvidia driver. :(
Interesting! nVidia 310.14 didn't work for me either.

The thing is, my GeForce 7600 GT is supposedly supported...

SOURCE: [http://www.nvidia.com/object/linux-display-ia32-310.14-driver.html](http://www.nvidia.com/object/linux-display-ia32-310.14-driver.html)
> GeForce 600 series:
GTX 690, GTX 680, GTX 670, GTX 660 Ti, GTX 660, GTX 650 Ti, GTX 650, GT 645, GT 640, GT 630, GT 620, GT 610, 605

GeForce 600M series:
GTX 680M, GTX 675MX, GTX 675M, GTX 670MX, GTX 670M, GTX 660M, GT 650M, GT 645M, GT 640M LE, GT 640M, GT 635M, GT 630M, GT 625M, GT 620M, G610M

GeForce 500 series:
GTX 590, GTX 580, GTX 570, GTX 560 Ti, GTX 560 SE, GTX 560, GTX 555, GTX 550 Ti, GT 545, GT 530, GT 520, 510

GeForce 500M series:
GTX 580M, GTX 570M, GTX 560M, GT 555M, GT 550M, GT 540M, GT 525M, GT 520MX, GT 520M

GeForce 400 series:
GTX 480, GTX 470, GTX 465, GTX 460 v2, GTX 460 SE v2, GTX 460 SE, GTX 460, GTS 450, GT 440, GT 430, GT 420, GT 415, 405

GeForce 400M series:
GTX 485M, GTX 480M, GTX 470M, GTX 460M, GT 445M, GT 435M, GT 425M, GT 420M, GT 415M, 410M

GeForce 300 series:
GT 340, GT 330, GT 320, 315, 310

GeForce 300M series:
GTS 360M, GTS 350M, GT 335M, GT 330M, GT 325M, GT 320M, 320M, 315M, 310M, 305M

GeForce 200 series:
GTX 295, GTX 285, GTX 280, GTX 275, GTX 260, GTS 250, GTS 240, GT 240, GT 230, GT 220, G210, 210, 205

GeForce 200M series:
GTX 285M, GTX 280M, GTX 260M, GTS 260M, GTS 250M, GT 240M, GT 230M, GT 220M, G210M

GeForce 100 series:
GT 140, GT 130, GT 120, G 100

GeForce 100M series:
GTS 160M, GTS 150M, GT 130M, GT 120M, G 110M, G 105M, G 103M, G 102M

GeForce 9 series:
9800 GX2, 9800 GTX+, 9800 GTX/GTX+, 9800 GT, 9650 S, 9600 GT, 9600 GSO 512, 9600 GSO, 9600 GS, 9500 GT, 9500 GS, 9400 GT, 9400, 9300 SE, 9300 GS, 9300 GE, 9300 / nForce 730i, 9300, 9200, 9100

GeForce 9M series:
9800M GTX, 9800M GTS, 9800M GT, 9800M GS, 9700M GTS, 9700M GT, 9650M GT, 9650M GS, 9600M GT, 9600M GS, 9500M GS, 9500M G, 9400M G, 9400M, 9300M GS, 9300M G, 9200M GS, 9100M G

GeForce 8 series:
8800 Ultra, 8800 GTX, 8800 GTS 512, 8800 GTS, 8800 GT, 8800 GS, 8600 GTS, 8600 GT, 8600 GS, 8500 GT, 8400 SE, 8400 GS, 8400, 8300 GS, 8300, 8200, 8100 / nForce 720a

GeForce 8M series:
8800M GTX, 8800M GTS, 8700M GT, 8600M GT, 8600M GS, 8400M GT, 8400M GS, 8400M G, 8200M G, 8200M

**[COLOR="DarkRed"]GeForce 7 series:[/COLOR]**
7950 GX2, 7950 GT, 7900 GTX, 7900 GT/GTO, 7900 GS, 7800 SLI, 7800 GTX, 7800 GT, 7800 GS, 7650 GS, 7600 LE, **[COLOR="DarkRed"]7600 GT[/COLOR]**, 7600 GS, 7550 LE, 7500 LE, 7350 LE, 7300 SE / 7200 GS, 7300 LE, 7300 GT, 7300 GS, 7150M /NVIDIA nForce 630M, 7150 / NVIDIA nForce 630i, 7100 GS, 7100 / NVIDIA nForce 630i, 7050 PV / NVIDIA nForce 630a, 7050 / NVIDIA nForce 630i, 7050 / NVIDIA nForce 610i, 7050 / nForce 620i, 7025 / NVIDIA nForce 630a, 7000M /NVIDIA nForce 610M

NVS Series:
NVS 310, NVS 300

Quadro series:
K5000, 7000, 6000, 600, 5000, 410, 4000, 400, 2000D, 2000

Quadro FX series:
FX Go1400, FX 700, FX 5800, FX 580, FX 570, FX 5600, FX 560, FX 5500, FX 550, FX 540, FX 500/FX 600, FX 4800, FX 4700 X2, FX 4600, FX 4500 X2, FX 4500, FX 4000, FX 380 LP, FX 3800, FX 380, FX 370 Low Profile, FX 3700, FX 370, FX 3500, FX 350, FX 3450/4000 SDI, FX 3400/4400, FX 330, FX 3000, FX 2000, FX 1800, FX 1700, FX 1500, FX 1400, FX 1300, FX 1100, FX 1000, CX

Quadro Notebook series:
K5000M, K4000M, K3000M, K2000M, K1000M, 5010M, 5000M, 4000M, 3000M, 2000M, 1000M


---

### Post by VinDSL on 2012-10-17
> **effenberg0x0 said:**
> I still get art-deco corruption on lightdm, flash video/banner pieces/artifacts in the Dash and random parts of the screen on long sessions (like 8+ hours), flashing windows titlebars (really random) and some other old bugs we know and love.
I wasn't getting a panel or dash in Unity with 310.14.  GS was running in fallback mode.  LXDE/Openbox worked fine.

I downgraded to Edger's 304.51, and everything is back to "normal" now...  ;)

---

### Post by Harry33 on 2012-10-17
I found these differencies with my Nvidia GTX285 card and official QQ kernel:

- with 310.14 (beta) during booting process switching from TTY1 is delayd showing login texts before TTY7 comes in.

- with 304.51 (stable) all is well.

---

### Post by cariboo on 2012-10-17
Apparently 304.60 will be released on Friday, with more bug fixes.

---

