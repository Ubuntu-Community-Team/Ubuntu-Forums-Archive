---
title: "ubuntu 14.04 poor performance by bumblebee"
date: 2013-11-25
forum: Ubuntu Development Version
---

### Post by KOSKERS on 2013-11-25
I have installed the bumblebee and nvidia331.20 normally. i can switch between two card normally.
But, when i change to nvidia card in order to play dota2, it is slower than intel card.. WTF.
--Nvidia GTX765M
--Intel HD4600
In 13.10, it run normally. Why????


koskers@koskers-CW35S:~$ glxheads 
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0.0
  Display:     0x2042010
  Window:      0x3e00002
  Context:     0x2050a50
  GL_VERSION:  3.0 Mesa 9.2.2
  GL_VENDOR:   Intel Open Source Technology Center
  GL_RENDERER: Mesa DRI Intel(R) Haswell Mobile 
^C
koskers@koskers-CW35S:~$ primusrun glxheads 
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0.0
  Display:     0x210b6f0
  Window:      0x4200002
  Context:     0x213ac40
  GL_VERSION:  4.4.0 NVIDIA 331.20
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: GeForce GTX 765M/PCIe/SSE2
koskers@koskers-CW35S:~$ primusrun glxgears 
304 frames in 5.0 seconds = 60.754 FPS
300 frames in 5.0 seconds = 59.996 FPS
301 frames in 5.0 seconds = 60.080 FPS
^C
koskers@koskers-CW35S:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
s305 frames in 5.0 seconds = 60.879 FPS
301 frames in 5.0 seconds = 60.040 FPS
^C


plz help me.thx

---

### Post by KOSKERS on 2013-11-25
This is my bumblebee config file.



# Configuration file for Bumblebee. Values should **not** be put between quotes


## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=nvidia
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d


## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false




# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# [https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods](https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods)


## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-331-updates
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-331-updates:/usr/lib32/nvidia-331-updates
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-331-updates/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia


## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

---

### Post by philinux on 2013-11-25
Moved to U+1 forum

---

### Post by soee2 on 2013-12-21
I can confirm this issue. Running Kubuntu 14.04 and performence in steam game sis owfull. All worked fine on 13.10 and the problem showed up after upgrade.

---

### Post by cariboo on 2013-12-21
I'd suggest it's the nvidia driver, as I'm finding the performance of it isn't as good as the previous one. I find I'm getting some tearing on graphics heavy forum pages.

---

### Post by frekja on 2014-01-04
I have a very similar problem with ubuntu 13.10, bumblebee, and nvidia-331 drivers - games run about 10x slower using primusrun and optirun compared to my built-in intel graphics. Nvidia-325 performance was fine.

I can't find any ubuntu-specific advice, but it looks like the problem affects OpenSuse and Arch as well: see [http://forums.opensuse.org/english/get-technical-help-here/hardware/492584-optimus-bumblebee-nvidia-331-20-overmans-repo-very-very-slow-3-12-kernel.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/492584-optimus-bumblebee-nvidia-331-20-overmans-repo-very-very-slow-3-12-kernel.html) and [http://forum.manjaro.org/index.php?topic=8346.0](http://forum.manjaro.org/index.php?topic=8346.0) . These both seem related but I'm not aware of the equivalent packages for ubuntu. I've already tried purging and reinstalling nvidia-331 using the xorg-edgers PPA, but without success.

[UPDATE] ppa-purging bumblebee and xorg-edgers, and manually removing all nvidia drivers, then rebooting and reinstalling fixed this problem for me.

---

### Post by DanyalDenyo on 2014-05-13
I have the same problem. Since I have installed 14.04 the video performance is so bad. I had no problems with the nvidia drivers on ubuntu 13.10.

i5 8GB GeForce 310M
Driver: Nvidia binary driver version 331.38 from nvidia-331

Edit: My computer doesn't have dual GPUs, sorry if this is the wrong place to post

---

### Post by cariboo on 2014-05-13
@DanyalDenyo, I guess you miseed the blue banner at the top of the page, this sub-forum is for the discussion and troubleshooting of Utopic Unicorn, discussions of released versions should take place in the other support sub-forums. Thread closed.

---

