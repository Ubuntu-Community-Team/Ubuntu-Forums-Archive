---
title: "Trusty - Problems with the new 3.13.0-1-generic kernel - won't go past login screen"
date: 2014-01-08
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-01-08
Any one else having boot problems with the new 3.13.0-1-generic kernel. This is not a beta or whatever it came through regular updates.
My system will not boot into that kernel. I thought I had lost the install and prepared for a fresh install. Even had burned the DVD-RW to do so.

Then I managed to get rid of the 3.12.0-5-generic and somehow it magically let me boot up with the 3.12.0-7-generic kernel and everything is fine. 
I tried the 3.13.0-1-generic again and same thing. This is with Unity and Flashback (with Compiz). I didn't try any others but figured if it would not log into Unity it was not going to login to anything.

*sigh*

Solved: Moved on - installed the 3.13.0-3-generic kernel and deleted this one.

---

### Post by P-I H on 2014-01-08
I haven't tried the new kernel myself yet, but it might be the problem with the Nvidia driver. Take a look at this thread.
[http://ubuntuforums.org/showthread.php?t=2195166](http://ubuntuforums.org/showthread.php?t=2195166)
I am using 3.13 rc5 with the change proposed by VinDSL.

---

### Post by howefield on 2014-01-08
Was reading this thread whilst updating but no problem on reboot.

"Stock" install with nvidia 331-updates driver.

---

### Post by xc3RnbFO8P on 2014-01-08
No problem here:
> Linux version 3.13.0-1-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu/Linaro 4.8.2-12ubuntu2) ) #16-Ubuntu SMP Tue Jan 7 19:44:06 UTC 2014
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: ION/integrated/SSE2
OpenGL version string:  3.3.0 NVIDIA 331.20


```
rig@rig-Aspire-R3600:~$ cat /var/log/Xorg.0.log | grep -i nvidia
[    39.014] (II) Module glx: vendor="NVIDIA Corporation"
[    39.014] (II) NVIDIA GLX Module  331.20  Wed Oct 30 17:36:48 PDT 2013
[    39.014] (==) Matched nvidia as autoconfigured driver 0
[    39.014] (==) Matched nvidia as autoconfigured driver 2
[    39.015] (II) LoadModule: "nvidia"
[    39.015] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    39.017] (II) Module nvidia: vendor="NVIDIA Corporation"
[    39.229] (II) NVIDIA dlloader X Driver  331.20  Wed Oct 30 17:16:53 PDT 2013
[    39.229] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    39.229] (II) NOUVEAU driver for NVIDIA chipset families :
[    39.240] (II) NVIDIA(0): Creating default Display subsection in Screen section
[    39.240] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    39.240] (==) NVIDIA(0): RGB weight 888
[    39.240] (==) NVIDIA(0): Default visual is TrueColor
[    39.240] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    39.240] (**) NVIDIA(0): Enabling 2D acceleration
[    40.256] (II) NVIDIA(0): Display (LG Electronics W2452 (DFP-0)) does not support NVIDIA
[    40.256] (II) NVIDIA(0):     3D Vision stereo.
[    40.257] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[    40.259] (II) NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
[    40.260] (--) NVIDIA(0): Memory: 524288 kBytes
[    40.260] (--) NVIDIA(0): VideoBIOS: 62.79.6c.00.01
[    40.262] (--) NVIDIA(0): Valid display device(s) on ION at PCI:3:0:0
[    40.262] (--) NVIDIA(0):     CRT-0
[    40.262] (--) NVIDIA(0):     LG Electronics W2452 (DFP-0) (boot, connected)
[    40.262] (--) NVIDIA(0): CRT-0: 300.0 MHz maximum pixel clock
[    40.262] (--) NVIDIA(0): LG Electronics W2452 (DFP-0): Internal Single Link TMDS
[    40.262] (--) NVIDIA(0): LG Electronics W2452 (DFP-0): 165.0 MHz maximum pixel clock
[    40.262] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    40.263] (**) NVIDIA(0):     device LG Electronics W2452 (DFP-0) (Using EDID
[    40.263] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    40.267] (==) NVIDIA(0): 
[    40.267] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    40.267] (==) NVIDIA(0):     will be used as the requested mode.
[    40.267] (==) NVIDIA(0): 
[    40.268] (II) NVIDIA(0): Validated MetaModes:
[    40.268] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[    40.268] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    40.305] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    40.305] (--) NVIDIA(0):     option
[    40.307] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    40.320] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[    40.465] (==) NVIDIA(0): Disabling shared memory pixmaps
[    40.465] (==) NVIDIA(0): Backing store disabled
[    40.465] (==) NVIDIA(0): Silken mouse enabled
[    40.467] (==) NVIDIA(0): DPMS enabled
[    40.469] (II) NVIDIA(0): [DRI2] Setup complete
[    40.469] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    40.785] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event6)
[    40.786] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event5)
[    40.787] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 Phantom (/dev/input/event4)
[    44.265] (II) NVIDIA(GPU-0): Display (LG Electronics W2452 (DFP-0)) does not support NVIDIA
[    44.265] (II) NVIDIA(GPU-0):     3D Vision stereo.
```

---

### Post by ajgreeny on 2014-01-08
I have just updated my trusty system (Xubuntu 64bit running in virtualbox (PUEL with all guest additions extensions etc etc, on an i5-3570K with integrated HD4000 graphics and 8GB ram) and restarted with the new 3.13.0-1 kernel.

It started easily enough but it was impossible to get full screen with the native monitor resolution of 1440x900.  For now I have removed the 3.13 kernel, but anyone have any ideas how to use it and run the resolution I need.

EDIT:
I have only just realised, being a new virtualbox user, that I needed to reinstall the guest-additions for the new kernel.
Having now done that everything is now working great again.

Problem over for me !

---

### Post by Mateusz Stachowski on 2014-01-08
I updated the kernel couple hours ago and it also didn't work for me with Nvidia drivers. Fortunately there is a new release of nvidia-graphics-drivers-331 which has patch for 3.13 kernel.

[https://launchpad.net/ubuntu/trusty/+source/nvidia-graphics-drivers-331/331.20-0ubuntu8](https://launchpad.net/ubuntu/trusty/+source/nvidia-graphics-drivers-331/331.20-0ubuntu8)

---

### Post by Cavsfan on 2014-01-08
Thanks for the replies!!! I tried my best to figure it out on my own. But, I removed the 3.12.0-7 kernel and tried to re-install it and there was no source for it. So, I bit the bullet and downloaded an ISO.
In the process of getting it all put back together. :) The 3.13 kernel did not come on the ISO so I got it on an update rebooted. Then went to install an Nvidia driver and things had definitely changed as far as what is available on this install versus what I had. The install I had was pre-alpha and worked fine until the 3.13 kernel came down the pipe.

I installed nvidia-331-updates and this is what came with it automagically:

[ATTACH=CONFIG]249324[/ATTACH]

It was probably time for this and I was able to back everything up before hand which wasn't a whole lot since this is early developmenal release.

I know the prime and the cuda stuff was not available to me before so maybe this is a plus.
I'll have more to report once I get it all back like it was. 

Thanks again. :)

---

### Post by spupazza on 2014-01-08
> **Cavsfan said:**
> Any one else having boot problems with the new 3.13.0-1-generic kernel. This is not a beta or whatever it came through regular updates.
My system will not boot into that kernel. I thought I had lost the install and prepared for a fresh install. Even had burned the DVD-RW to do so.

Then I managed to get rid of the 3.12.0-5-generic and somehow it magically let me boot up with the 3.12.0-7-generic kernel and everything is fine. 
I tried the 3.13.0-1-generic again and same thing. This is with Unity and Flashback (with Compiz). I didn't try any others but figured if it would not log into Unity it was not going to login to anything.

*sigh*

I got the same issue : installed a command line system with ubuntu server daily image, updated the system (so including the new  kernel) and after that installed xorg,kde-plasma-desktop and nvidia 331.20.
Then rebooted and got the same issue you're facing,

---

### Post by Elfy on 2014-01-08
working fine for me in Xubuntu - though that's with nouveau - not managed to get past the nvidia issue yet, but that's more to do with having time

---

### Post by craig10x on 2014-01-08
Got that kernel update this morning...i have intel on my computer...it boots up fine but i do notice two terminal lines come up before the log in page to the desktop comes up...goes by pretty fast but i did notice one of the lines said " 14.04 trusty tahr"....wasn't getting that when booting up before this update...

---

### Post by cariboo on 2014-01-08
I did the update this morning without any problems, I'm running Unity, with nVidia 331 drivers.

---

### Post by Mateusz Stachowski on 2014-01-09
This should be resolved for everyone using up to date Nvidia drivers because yesterday there was a new release of **nvidia-graphics-drivers-331 **which has support for Linux 3.13.

```
$ apt-cache policy nvidia-331nvidia-331:
  Zainstalowana: 331.20-0ubuntu8
  Kandyduj&#261;ca:   331.20-0ubuntu8
  Tabela wersji:
 *** 331.20-0ubuntu8 0
        500 http://ftp.vectranet.pl/ubuntu/ trusty/restricted amd64 Packages
        100 /var/lib/dpkg/status



```

[https://launchpad.net/ubuntu/trusty/+source/nvidia-graphics-drivers-331/331.20-0ubuntu8](https://launchpad.net/ubuntu/trusty/+source/nvidia-graphics-drivers-331/331.20-0ubuntu8)

> [COLOR=#333333][FONT=Ubuntu Mono]nvidia-graphics-drivers-331 (331.20-0ubuntu8) trusty; urgency=low[/FONT][/COLOR]
  * debian/templates/nvidia-graphics-drivers-uvm.install.in,
    debian/templates/dkms_nvidia_uvm.conf,
    debian/dkms_nvidia_uvm/patches/buildfix_kernel_3.12.patch:
    - Add support for Linux 3.12.
  * debian/templates/dkms_nvidia.conf.in,
    debian/dkms_nvidia/patches/buildfix_kernel_3.13.patch:
    - Add support for Linux 3.13. [COLOR=#333333][FONT=Ubuntu Mono] -- Alberto Milone <[/FONT][/COLOR][alberto.milone@canonical.com]("https://launchpad.net/~albertomilone")[COLOR=#333333][FONT=Ubuntu Mono]>   Wed, 08 Jan 2014 14:58:56 +0100[/FONT][/COLOR]

---

### Post by Shiba on 2014-01-09
Being this solved, I now have a different problem: X doesn't detect my laptop monitor anymore and exits with "no screen found". If someone is facing the same problem, I opened a bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1267437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1267437)

---

### Post by Elfy on 2014-01-09
> **Mateusz Stachowski said:**
> This should be resolved for everyone using up to date Nvidia drivers because yesterday there was a new release of **nvidia-graphics-drivers-331 **which has support for Linux 3.13....

The graphics driver might install properly - however I am still left with an unbootable machine - unless I fiddle with lightdm.conf

```
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
display-setup-script=/sbin/prime-offload
display-stopped-script=/sbin/prime-switch
```

works for Ubuntu I assume - it'll not get much joy with Xubuntu

Obviously editing that file to 
```

[SeatDefaults]
#greeter-session=unity-greeter
#user-session=ubuntu
display-setup-script=/sbin/prime-offload
display-stopped-script=/sbin/prime-switch
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
```

let's me in.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1267442](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1267442)

---

### Post by Cavsfan on 2014-01-09
Working fine here after yesterday's daily ISO. I got a few more updates to the 331.20 driver today:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  [COLOR=#ff0000]nvidia[/COLOR]-331-updates                                    331.20-0ubuntu9                      amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  [COLOR=#ff0000]nvidia[/COLOR]-libopencl1-331-updates                         331.20-0ubuntu9                      amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  [COLOR=#ff0000]nvidia[/COLOR]-opencl-icd-331-updates                         331.20-0ubuntu9                      amd64        NVIDIA OpenCL ICD
ii  [COLOR=#ff0000]nvidia[/COLOR]-prime                                          0.5.2                                amd64        Tools to enable NVIDIA's Prime
ii  [COLOR=#ff0000]nvidia[/COLOR]-settings                                       331.20-0ubuntu6                      amd64        Tool for configuring the NVIDIA graphics driver

```

I do not have nvidia-331nvidia-331 installed. In Synaptic I just ticked nvidia-331-updates and the rest were added as dependencies.

I guess this is the future coming to Ubuntu perhaps. :)

---

### Post by xc3RnbFO8P on 2014-01-09
More is better :)

> rig@rig-Aspire-R3600:~$ dpkg -l | grep nvidia
ii  libkwinactivenvidiahack4                              4:4.10.97-0ubuntu2                                  amd64        library used by nvidia cards for the KDE window manager
rc  libkwinnvidiahack4                                    4:4.10.3-0ubuntu3                                   amd64        library used by nvidia cards for the KDE window manager
rc  nvidia-304                                            304.88-0ubuntu2                                     amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-325                                            325.15-0ubuntu1~xedgers~saucy3                      amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-331                                            331.20-0ubuntu9                                     amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                                         1:0.2.87                                            amd64        transitional package for ubuntu-drivers-common
rc  nvidia-experimental-310                               310.14-0ubuntu1                                     amd64        Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                 331.20-0ubuntu9                                     amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.20-0ubuntu9                                     amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                   331.20-0ubuntu1~xedgers~trusty1                     amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                          0.5.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu6                                     amd64        Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-304                                   304.88-0ubuntu1                                     amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-319                                   331.20-0ubuntu6                                     amd64        Transitional package for nvidia-settings
rc  nvidia-settings-325                                   325.15-0ubuntu1~xedgers~saucy2                      amd64        Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-331                                   331.20-0ubuntu1~xedgers~trusty1                     amd64        Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-experimental-310                      310.14-0ubuntu1                                     amd64        Tool for configuring the NVIDIA graphics driver
rig@rig-Aspire-R3600:~$ 


---

### Post by QDR06VV9 on 2014-01-09
> **Cavsfan said:**
> Working fine here after yesterday's daily ISO. I got a few more updates to the 331.20 driver today:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  [COLOR=#ff0000]nvidia[/COLOR]-331-updates                                    331.20-0ubuntu9                      amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  [COLOR=#ff0000]nvidia[/COLOR]-libopencl1-331-updates                         331.20-0ubuntu9                      amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  [COLOR=#ff0000]nvidia[/COLOR]-opencl-icd-331-updates                         331.20-0ubuntu9                      amd64        NVIDIA OpenCL ICD
ii  [COLOR=#ff0000]nvidia[/COLOR]-prime                                          0.5.2                                amd64        Tools to enable NVIDIA's Prime
ii  [COLOR=#ff0000]nvidia[/COLOR]-settings                                       331.20-0ubuntu6                      amd64        Tool for configuring the NVIDIA graphics driver

```

I do not have nvidia-331nvidia-331 installed. In Synaptic I just ticked nvidia-331-updates and the rest were added as dependencies.

I guess this is the future coming to Ubuntu perhaps. :)

Interesting?? I have used the persistence 331, since the beginning of Trusty but I also seemed to have escaped the problems I have read here.(Lucky I Guess)
```
ii  nvidia-319                                            331.20-0ubuntu9                      amd64        Transitional package for nvidia-319
ii  nvidia-331                                            331.20-0ubuntu9                      amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                 331.20-0ubuntu9                      amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.20-0ubuntu9                      amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                   331.20-0ubuntu1~xedgers~trusty1      amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                          0.5.2                                amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu6                      amd64        Tool for configuring the NVIDIA graphics driver
```

---

### Post by Doug S on 2014-01-09
> **Cavsfan said:**
> Any one else having boot problems with the new 3.13.0-1-generic kernel.For me, it was just the opposite. 2 days ago I wasted a good part of the day trying to make my 14.04 desktop VM work. It had been working fine a few weeks ago, but not with an up to date system of 2 days ago (Not always, but sometimes I was able to ssh to the VM to do updates). I was very much "Grrrr" by the end of the day. First thing yesterday morning updates included the new kernel, and then everything was fine for desktop display, which I do via VNC on the VM.

---

### Post by Cavsfan on 2014-01-09
I didn't see where the xedgers drivers were available until now. :)

Do we go with **xorg-edgers fresh X crack** or the regular **X Updates** ppa?

I already have the 331.20 driver working OK. My middle of the road Geforce 9800 GT 1TB Mem doesn't necessarily *need* the latest driver but it doesn't usually hurt either.

---

### Post by Cavsfan on 2014-01-09
> **Doug S said:**
> For me, it was just the opposite. 2 days ago I wasted a good part of the day trying to make my 14.04 desktop VM work. It had been working fine a few weeks ago, but not with an up to date system of 2 days ago (Not always, but sometimes I was able to ssh to the VM to do updates). I was very much "Grrrr" by the end of the day. First thing yesterday morning updates included the new kernel, and then everything was fine for desktop display, which I do via VNC on the VM.

Glad it fixed your system. I spent several hours trying to make it work but had to give up. It broke most every one else's. :)

---

### Post by cecilpierce on 2014-01-09
I've tried nvidia-current, nouveau and nvidia-331 with 3.13.0-1 and the old 3.12.? 
Did lsmod|grep nvidia and nouveau, no drivers ?
All I get is black screen with an 'X' mouse cursor ???

---

### Post by QDR06VV9 on 2014-01-09
> **cecilpierce said:**
> I've tried nvidia-current, nouveau and nvidia-331 with 3.13.0-1 and the old 3.12.? 
Did lsmod|grep nvidia and nouveau, no drivers ?
All I get is black screen with an 'X' mouse cursor ???

Have you tried "control+alt+F1" 
Then login text mode, Then Startx?
For Me after that a simple reboot worked.

---

### Post by cecilpierce on 2014-01-09
> **runrickus said:**
> Have you tried "control+alt+F1" 
Then login text mode, Then Startx?
For Me after that a simple reboot worked.

I think I did? tried so many things I can't remember, I'll try it again, thanks.

---

### Post by cecilpierce on 2014-01-09
Well at least I can boot now with the 3.12.0-7-generic and nouveau but 3.13.0-1 still freezes.   :(

For some reason nvidia drivers will not install ?

---

### Post by camski.watersport on 2014-01-09
I have the same issue, occurred last night after update, was running 304-dev without an issue (that was the only one i could get 14.04 working on, no screen found issues), have now tried 320 and 331 without success, purged all and tried again with 304-dev and still no go. I have terminal and ssh access but when i try to run x11vnc it shows no screen found.  Since reinstalling 304-dev Xorg.0.log shows the driver now appears to be loading and detecting screen but X11vnc does not load. As i'm trying to get this working remotely i'm unable to see so will check this evening.

---

### Post by QDR06VV9 on 2014-01-10
> **Cavsfan said:**
> I didn't see where the xedgers drivers were available until now. :)

Do we go with **xorg-edgers fresh X crack** or the regular **X Updates** ppa?

I already have the 331.20 driver working OK. My middle of the road Geforce 9800 GT 1TB Mem doesn't necessarily *need* the latest driver but it doesn't usually hurt either.

Sorry Cavsfan I need to check posts a liittle better!
I'm using This
```
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 
```

---

### Post by Cavsfan on 2014-01-10
> **runrickus said:**
> Sorry Cavsfan I need to check posts a liittle better!
I'm using This
```
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 
```

That's OK. I see your using the fresh crack PPA. Nothing like **xorg-edgers fresh X crack** :lol: Maybe I should give that a try. What could go wrong right? :lol:

---

### Post by QDR06VV9 on 2014-01-10
> **Cavsfan said:**
> That's OK. I see your using the fresh crack PPA. Nothing like **xorg-edgers fresh X crack** :lol: Maybe I should give that a try. What could go wrong right? :lol:

It has been pretty smooth and stable unless I test new kernels!;)
(fingers crossed)

---

### Post by Cavsfan on 2014-01-10
> **runrickus said:**
> It has been pretty smooth and stable unless I test new kernels!;)
(fingers crossed)

I guess I should go ahead and add that ppa if nothing else for the nvidia-persistenced package.
There is a bug to get nvidia-persistenced added to the main repository.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1246735](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1246735)

So it must be something I need. I don't know enough about all of this to know if I should add my name to the bug so I won't.

It appears to be worth adding though since it says "Load the NVIDIA kernel driver and create device files". I see no other package that does that.

---

### Post by Cavsfan on 2014-01-10
I just seen this article [SIZE=3]NVIDIA (Optimus) PRIME Update Lands In Ubuntu 14.04[/SIZE] from phoronix.

[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)

---

### Post by Cavsfan on 2014-01-10
> **runrickus said:**
> Interesting?? I have used the persistence 331, since the beginning of Trusty but I also seemed to have escaped the problems I have read here.(Lucky I Guess)
```
ii  nvidia-319                                            331.20-0ubuntu9                      amd64        Transitional package for nvidia-319
ii  nvidia-331                                            331.20-0ubuntu9                      amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                 331.20-0ubuntu9                      amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.20-0ubuntu9                      amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                   331.20-0ubuntu1~xedgers~trusty1      amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                          0.5.2                                amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu6                      amd64        Tool for configuring the NVIDIA graphics driver
```

Ok, I installed the PPA and updated then installed nvidia-persistenced. This is what I have now:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                            331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-331-updates                                    331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                   331.20-0ubuntu1~xedgers~trusty1                amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                          0.5.3                                          amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu6                                amd64        Tool for configuring the NVIDIA graphics driver

```

Should I uninstall nvidia-331, nvidia-libopencl1-331 and nvidia-opencl-icd-331? Or like Ringi says moar is better. :P

Although everything seems to be working pretty well, I just wonder about the duplication.

---

### Post by QDR06VV9 on 2014-01-10
> **Cavsfan said:**
> Ok, I installed the PPA and updated then installed nvidia-persistenced. This is what I have now:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                            331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-331-updates                                    331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                   331.20-0ubuntu1~xedgers~trusty1                amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                          0.5.3                                          amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu6                                amd64        Tool for configuring the NVIDIA graphics driver

```

Should I uninstall nvidia-331, nvidia-libopencl1-331 and nvidia-opencl-icd-331? Or like Ringi says moar is better. :P

Although everything seems to be working pretty well, I just wonder about the duplication.
All I ever do to install current driver for xedger is "apt-get install nvidia-331" Or for the lappy "apt-get install nvidia-current" and it pulls in what you see from my previous output.
If it did not uninstall anything I would think you are fine..

---

### Post by ventrical on 2014-01-10
It works excellently here on Lubuntu.

```

ventrical@ventrical-Asus-Overclock:~$ dpkg -l | grep nvidia
ii  nvidia-304                           304.116-0ubuntu2                     i386         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current                       304.116-0ubuntu2                     i386         Transitional package for nvidia-current
ii  nvidia-libopencl1-304                304.116-0ubuntu2                     i386         NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304                304.116-0ubuntu2                     i386         NVIDIA OpenCL ICD
ii  nvidia-settings                      331.20-0ubuntu6                      i386         Tool for configuring the NVIDIA graphics driver
ventrical@ventrical-Asus-Overclock:~$ 



```

on i386

```

ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.13.0-1-generic #16-Ubuntu SMP Tue Jan 7 19:47:28 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 


```

---

### Post by QDR06VV9 on 2014-01-10
> **ventrical said:**
> It works excellently here on Lubuntu.

```

ventrical@ventrical-Asus-Overclock:~$ dpkg -l | grep nvidia
ii  nvidia-304                           304.116-0ubuntu2                     i386         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current                       304.116-0ubuntu2                     i386         Transitional package for nvidia-current
ii  nvidia-libopencl1-304                304.116-0ubuntu2                     i386         NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304                304.116-0ubuntu2                     i386         NVIDIA OpenCL ICD
ii  nvidia-settings                      331.20-0ubuntu6                      i386         Tool for configuring the NVIDIA graphics driver
ventrical@ventrical-Asus-Overclock:~$ 



```

on i386

```

ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.13.0-1-generic #16-Ubuntu SMP Tue Jan 7 19:47:28 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 


```

Hey Ventrical!
Let me know how the temps are?

---

### Post by Cavsfan on 2014-01-10
What is the differece between ii and rc as it shows on the left side?
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
[COLOR=#ff0000]ii[/COLOR]  nvidia-331                                            331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
[COLOR=#ff0000]rc[/COLOR]  nvidia-331-updates                                    331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
[COLOR=#ff0000]ii[/COLOR]  nvidia-libopencl1-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
[COLOR=#ff0000]rc[/COLOR]  nvidia-libopencl1-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
[COLOR=#ff0000]ii[/COLOR]  nvidia-opencl-icd-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
[COLOR=#ff0000]rc[/COLOR]  nvidia-opencl-icd-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
[COLOR=#ff0000]rc[/COLOR]  nvidia-persistenced                                   331.20-0ubuntu1~xedgers~trusty1                amd64        Load the NVIDIA kernel driver and create device files
[COLOR=#ff0000]ii[/COLOR]  nvidia-prime                                          0.5.3                                          amd64        Tools to enable NVIDIA's Prime
[COLOR=#ff0000]ii[/COLOR]  nvidia-settings                                       331.20-0ubuntu6                                amd64        Tool for configuring the NVIDIA graphics driver
```

I thought that with the "updates" I will get subsequent undated versions and without that I would not. Is that correct?

---

### Post by QDR06VV9 on 2014-01-10
> **Cavsfan said:**
> What is the differece between ii and rc as it shows on the left side?
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
I thought that with the "updates" I will get subsequent undated versions and without that I would not. Is that correct?

Here is all it says
[CODE]                                               

[LIST]
[*]     [“Ubuntu-X” team]("https://launchpad.net/%7Eubuntu-x-swat") 
[*]     X Updates 
[/LIST]
                                                
             
                                                       
                                                                   **PPA description**

   
    Updated versions of X.org drivers, libraries, etc. for Ubuntu.
 This PPA is for stable upstream releases of X.org components.  If  you're looking for something even more bleeding-edge, please see the  xorg-edgers PPA.
 While Ubuntu does not "officially/formally" support these  packages, if you discover problems when installing these debs please  feel free to report bugs to
 launchpad.  However, please make sure to  clearly state that you are running packages from this PPA so we know the  fixes need to come here.
 If you are upgrading from one release to another with this PPA  activated, please install the ppa-purge package and use it to downgrade  everything in 
here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.

```
I just prefer[ xorg-edgers fresh X crack]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") But thats just me..

---

### Post by Cavsfan on 2014-01-10
> **Cavsfan said:**
> What is the difference between ii and rc as it shows on the left side?
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
[COLOR=#ff0000]ii[/COLOR]  nvidia-331                                            331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
[COLOR=#ff0000]rc[/COLOR]  nvidia-331-updates                                    331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
[COLOR=#ff0000]ii[/COLOR]  nvidia-libopencl1-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
[COLOR=#ff0000]rc[/COLOR]  nvidia-libopencl1-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
[COLOR=#ff0000]ii[/COLOR]  nvidia-opencl-icd-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
[COLOR=#ff0000]rc[/COLOR]  nvidia-opencl-icd-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
[COLOR=#ff0000]rc[/COLOR]  nvidia-persistenced                                   331.20-0ubuntu1~xedgers~trusty1                amd64        Load the NVIDIA kernel driver and create device files
[COLOR=#ff0000]ii[/COLOR]  nvidia-prime                                          0.5.3                                          amd64        Tools to enable NVIDIA's Prime
[COLOR=#ff0000]ii[/COLOR]  nvidia-settings                                       331.20-0ubuntu6                                amd64        Tool for configuring the NVIDIA graphics driver
```

I thought that with the "updates" I will get subsequent undated versions and without that I would not. Is that correct?

> **runrickus said:**
> I just prefer[ xorg-edgers fresh X crack]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") But thats just me..

I only added the [ xorg-edgers fresh X crack]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") PPA. Did you think I also added the [X Updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") PPA as well? I'm not a rocket scientist but, I wasn't born yesterday either. :lol:

I was just asking the difference between the ii and the rc to the far left as shown in [COLOR="#FF0000"]red[/COLOR] above in the output of **dpkg -l | grep nvidia**.
Because I am pretty sure I don't need the first 3 packages duplicated.

---

### Post by QDR06VV9 on 2014-01-10
```
I thought that with the "updates" I will get subsequent undated versions and without that I would not. Is that correct?
```
Sorry :oyour output and what I have was different enough I wasnt sure?
So that was the reason I posted the read me.
```
Did you think I also added the [X Updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") PPA as well? I'm not a rocket scientist but, I wasn't born yesterday either. :lol:
```
It is just not in me to run a agenda like that...Always and Only Respect for you and all in this wonderful U+1 :lol:
I'm Sorry if it made you feel or think that.
Regards
You know I have been a little Stressed this week,
Funny how that gets commuted over to text:)

---

### Post by P-I H on 2014-01-11
I have upgraded and it went OK, but there were some problems.
I had installed 3.13.0-rc5 and this was still the first choice after the upgrade.
When I booted with the 3.13.0-1 kernel, the Nvidia driver didn't start OK. The login screen had wrong resolution and after login Launcher and Panel wasn't shown.
After boot with the 3.13.0-rc5 kernel, I change the graphic driver to Nouveau and booted with kernel 3.13.0-1. This time Launcher and Panel was presented OK, but the resolution was still the wrong one. I changed to the nvidia-331-updates driver and rebooted. This time both the login screen and the desktop had the right resolution.
After kernel 3.13.0-rc5 was removed, kernel 3.13.0-1 became the primary one.

---

### Post by Cavsfan on 2014-01-11
> **runrickus said:**
> ```
I thought that with the "updates" I will get subsequent undated versions and without that I would not. Is that correct?
```
Sorry :oyour output and what I have was different enough I wasnt sure?
So that was the reason I posted the read me.
```
Did you think I also added the [X Updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") PPA as well? I'm not a rocket scientist but, I wasn't born yesterday either. :lol:
```
It is just not in me to run a agenda like that...Always and Only Respect for you and all in this wonderful U+1 :lol:
I'm Sorry if it made you feel or think that.
Regards
You know I have been a little Stressed this week,
Funny how that gets commuted over to text:)

No problem runrickus! I didn't mean anything by it. While everything appears to be OK I was just wondering if I should remove the packages in red below since they are duplicates.
Since I just re-installed Trusty last Wednesday I didn't want to screw it up and have to do it again. I mean granted this is still very early in the cycle but, I'd still like to get a few months out of this one. :p

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
[COLOR=#ff0000]ii  nvidia-331                                            331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library[/COLOR]
rc  nvidia-331-updates                                    331.20-0ubuntu9                                amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
[COLOR=#ff0000]ii  nvidia-libopencl1-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library[/COLOR]
rc  nvidia-libopencl1-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL Driver and ICD Loader library
[COLOR=#ff0000]ii  nvidia-opencl-icd-331                                 331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD[/COLOR]
rc  nvidia-opencl-icd-331-updates                         331.20-0ubuntu9                                amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                   331.20-0ubuntu1~xedgers~trusty1                amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                          0.5.3                                          amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu6                                amd64        Tool for configuring the NVIDIA graphics driver
```

Thanks for any feedback.

---

### Post by QDR06VV9 on 2014-01-11
Cavsfan I dont think there is any harm with the dups, I'm still wondering how it so different than mine?:confused:
Maybe just the install process. Did you tick the "nvidia-331-updates" through synaptic or cli? 
Just for Clarification my install is just "sudo apt-get install nvidia-331"
This is on Saucy(Not to much different than trusty)
```
dpkg -l | grep nvidia
ii  nvidia-331                                331.20-0ubuntu1~xedgers~saucy1           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-persistenced                       331.20-0ubuntu1~xedgers~saucy1           amd64        Load the NVIDIA kernel driver and create device files
rc  nvidia-settings-304                       304.88-0ubuntu2                          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-331                       331.20-0ubuntu1~xedgers~saucy1           amd64        Tool for configuring the NVIDIA graphics driver


```
And yes it has been updating itself with any updates.
Hope that Helps.:)

---

### Post by Cavsfan on 2014-01-11
> **runrickus said:**
> Cavsfan I dont think there is any harm with the dups, I'm still wondering how it so different than mine?:confused:
Maybe just the install process. Did you tick the "nvidia-331-updates" through synaptic or cli? 
Just for Clarification my install is just "sudo apt-get install nvidia-331"
This is on Saucy(Not to much different than trusty)
```
dpkg -l | grep nvidia
ii  nvidia-331                                331.20-0ubuntu1~xedgers~saucy1           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-persistenced                       331.20-0ubuntu1~xedgers~saucy1           amd64        Load the NVIDIA kernel driver and create device files
rc  nvidia-settings-304                       304.88-0ubuntu2                          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-331                       331.20-0ubuntu1~xedgers~saucy1           amd64        Tool for configuring the NVIDIA graphics driver


```
And yes it has been updating itself with any updates.
Hope that Helps.:)

Thanks! I think I'll just leave it like it is because it works well. :) And I don't want to risk breaking it. 
I used Synaptic to install nvidia-331-updates I'm pretty sure and it pulled in the rest, but I did not have nvidia-persistenced which judging by the 
description and the fact that there is a bug to have that added to the main repository I thought I might just need that. 
That is when I installed the [ xorg-edgers fresh X crack]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") PPA and the nvidia-persistenced package.
It pulled in the duplicates via **sudo apt-get update && sudo apt-get upgrade** commands. I only use CLI to get my updates.

Some nice person in this forum told me how to set the updates up as aliases in **~/.bashrc** to make it even easier. 
Excuse me if you have seen this before as I have mentioned it a few times but I was told to add this to .bashrc:
**gedit ~/.bashrc**
```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'
```

I added the 3rd one myself for when it says I have packages to remove.
Just enter **ud** and then password and it fetches any updates if there are any to be had.
Then if anything is held back because new packages have to be added in addition to the ones to be upgraded I just enter **ud2** and that does it's thing. Because it has already been updated with the prior command.
I always run them one right after the other if needed.

Guess this thread is finished as I just got the next kernel a few minutes ago.
```
cavsfan@cavsfan-MS-7529:~$ uname -a
Linux cavsfan-MS-7529 3.13.0-2-generic #17-Ubuntu SMP Fri Jan 10 12:14:30 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

It didn't have any problems like the 3.13.0-1-generic kernel did. Maybe it is because I have nvidia-persistenced installed. :)

---

### Post by ventrical on 2014-01-11
> **runrickus said:**
> Hey Ventrical!
Let me know how the temps are?

Running Extreme Tux Racer is bottoms out at 36-37 C. Can't find Lubuntu Screenshot thingy :) lol

Edit:  Runs well at high overclock also. I was using nouveau for overclock.

```

ventrical@ventrical-Asus-Overclock:~$ sudo dmidecode -t processor | grep "Speed"[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5127 MHz
ventrical@ventrical-Asus-Overclock:~$ 

```

---

### Post by ventrical on 2014-01-11
I installed ubuntu-desktop on top of Lubuntu install (with nvidia-current) <3.13.2.x.x> and it is working well @ high overclock here.

Edit:

The reason there is no fan reading is because I am using another power port and not the port on the card.

---

### Post by fjgaude on 2014-01-11
Just curious, Ventrical... what's your time result when running gtkperf?

frank

---

### Post by ventrical on 2014-01-12
> **fjgaude said:**
> Just curious, Ventrical... what's your time result when running gtkperf?

frank

  This one machine is a single core , overclocked Pentium with nVidia G210/218.

Just a side note .. I was able to bypass a lot of other ubuntu-desktop current bugs by loading ubuntu-desktop on top of a Lubuntu alpha .iso.

However, back to topic .. here, on this machine , nvidia-current is running exceptionally well with 3.13.2.x.x kernel under both LDXE and Unity.

---

### Post by QDR06VV9 on 2014-01-12
> **ventrical said:**
> Running Extreme Tux Racer is bottoms out at 36-37 C. Can't find Lubuntu Screenshot thingy :) lol

Edit:  Runs well at high overclock also. I was using nouveau for overclock.

```

ventrical@ventrical-Asus-Overclock:~$ sudo dmidecode -t processor | grep "Speed"[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5127 MHz
ventrical@ventrical-Asus-Overclock:~$ 

```
Sweet! Thanks for posting back, Guess I should have done that myself.lol;)

---

