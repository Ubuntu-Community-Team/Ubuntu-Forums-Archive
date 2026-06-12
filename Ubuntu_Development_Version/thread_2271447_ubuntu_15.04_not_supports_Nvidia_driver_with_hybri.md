---
title: "ubuntu 15.04 not supports Nvidia driver with hybrid Gcard notebook."
date: 2015-03-30
forum: Ubuntu Development Version
---

### Post by KOSKERS on 2015-03-30
[COLOR=#000000][FONT=Lucida Grande]Hi.Every one
   I have installed ubuntu 15.04 64bits  kernel 3.19
Using a[/FONT][/COLOR][FONT=Lucida Grande, Trebuchet MS, Helvetica, Arial, sans-serif][COLOR=#000000]dditional driver function can not boot the ubuntu successfully. Black screen in ubuntu login UI with login sound when using nvidia card.
When i change to use bumblebee, booting ubuntu is normally.But if i use nvidia card to play dota2. Steam gives me error.


[/COLOR][/FONT]Game update: AppID 570 "Dota 2", ProcID 3238, IP 0.0.0.0:0
ERROR: ld.so: object '/home/koskers/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.


When i test the bumblebee, it seems that right.
koskers@koskers:~$ primusrun glxheads 
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0xe605e0
  Window:      0x4600002
  Context:     0x2226fd0
  GL_VERSION:  4.5.0 NVIDIA 346.47
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: GeForce GTX 765M/PCIe/SSE2




Help me. plz. Thanks a lot.
BTW:Neither using 340 nor 346 by active additional driver function was not able to login in ubuntu.

---

### Post by Bucky Ball on 2015-03-30
*Thread moved to **Ubuntu Development Version**.*

All threads and queries regarding 15.04 belong here. It is not released yet and still under development. For a smoother ride, or if you installed this thinking it is the 'latest and greatest' so it's the one to go for, I suggest you try 14.04 LTS. If you installed 15.04 intentionally, know your way around already, are willing to go on a learning curve and are willing to test and possibly work your way through breakages and bugs, by all means, carry on. Good luck. ;)

---

### Post by KOSKERS on 2015-03-30
Thanks for quick replying. Your words is right.
Is there any resolution for me to deal with that?
And following your word, will  15.04 resolve this problem unity 2015/4/23,right?

---

### Post by grahammechanical on 2015-03-30
My advice is to change video driver. You have a much newer video adapter than me. I have a GT220. And I cannot get nvidia 346 to build on the 3.19 kernel. Even nvidia 340 gives me crash reports as Ubuntu loads to the desktop. But nvidia 304 works fine.

I am starting to wonder if Nvidia has dropped support for my card but that cannot be the situation with your card. These things can get fixed over time but the issue with proprietary video drivers is that the Ubuntu developers cannot fix things. They can only be fixed by the owner of the software and in this case it is Nvidia.

From my own experiments I found that changing drivers sometimes got messed up with Additional Drivers actually failing to change the driver. I had to purge the first nvidia driver before I could install another one. So, just in case that happens to you, here is the code.

```
sudo apt-get purge nvidia*
```

Ubuntu will still load as it will revert to using an open source driver.

Regards.

---

### Post by KOSKERS on 2015-03-30
Thanks. But open source have suck performance. it can not run dota2 smoothly.
Thank you indeed.i think i have to wait for ubuntu company resolve this problem by recent updates. :(

---

### Post by Bucky Ball on 2015-03-31
All good, but as grahammechanical mentions:
> 
These things can get fixed over time but the issue with proprietary video drivers is that the Ubuntu developers cannot fix things. They can only be fixed by the owner of the software and in this case it is Nvidia.

... so you could be waiting awhile ...

---

### Post by Andr_Correia on 2015-03-31
well i put it working today, the problem is with libdrm libs, reverting all of them from 2.4.59 to 2.4.56(from trusty resolves the issue) i lock this libs in synaptic untill the someone resolve this.

using default kernel, nvidia-349 from [B]ppa:mamarley/nvidia 
tutorial to systamd ubuntu
[/B][http://rajat-osgyan.blogspot.pt/2015/03/how-to-install-bumblebee-on-ubuntu.html](http://rajat-osgyan.blogspot.pt/2015/03/how-to-install-bumblebee-on-ubuntu.html)[B]

  and with this bumblebee config file

[/B][B]# Configuration file for Bumblebee. Values should **not** be put between quotes

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
Bridge=primus
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
KernelDriver=nvidia-349
PMMethod=bbswitch
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-349:/usr/lib32/nvidia-349
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-349/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

[/B]

---

### Post by oldfred on 2015-03-31
@grahmanmechanical
nVidia made a lot of somewhat newer cards legacy. It looks like your GT220 is legacy with 340.xx

 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by KOSKERS on 2015-04-03
Thank you so much.
u save me.
How can i install the libdrm [COLOR=#000000]2.4.56 ?


For Now.
[/COLOR]koskers@koskers:/etc/apt/sources.list.d$ sudo apt-cache policy  libdrm2
libdrm2:
  &#24050;&#23433;&#35013;&#65306;  2.4.59+git20150318.d20413a7-0ubuntu0ricotz2
  &#20505;&#36873;&#36719;&#20214;&#21253;&#65306;2.4.59+git20150318.d20413a7-0ubuntu0ricotz2
  &#29256;&#26412;&#21015;&#34920;&#65306;
 *** 2.4.59+git20150318.d20413a7-0ubuntu0ricotz2 0
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) vivid/main amd64 Packages
        100 /var/lib/dpkg/status
     2.4.59-0ubuntu1 0
        500 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) vivid/main amd64 Packages


[COLOR=#000000]
[/COLOR]

---

### Post by KOSKERS on 2015-04-03
Hi.
I have download the old version libdrm to install this. ubuntu throws me error.
Now,apt is broken :(
Correcting dependencies... Done
The following extra packages will be installed:
  libdrm2
The following packages will be upgraded:
  libdrm2
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0 B/31.1 kB of archives.
After this operation, 4096 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 221918 files and directories currently installed.)
Preparing to unpack .../libdrm2_2.4.59+git20150318.d20413a7-0ubuntu0ricotz2_amd64.deb ...
Unpacking libdrm2:amd64 (2.4.59+git20150318.d20413a7-0ubuntu0ricotz2) over (2.4.56-1) ...
dpkg: error processing archive /var/cache/apt/archives/libdrm2_2.4.59+git20150318.d20413a7-0ubuntu0ricotz2_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libdrm2/changelog.Debian.gz', which is different from other instances of package libdrm2:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libdrm2_2.4.59+git20150318.d20413a7-0ubuntu0ricotz2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dino99 on 2015-04-03
purge all the ricotz ppa with ppa-purge

using the bleeding edge packages is ok if you know well enough to workaround issues yourself; otherwise stay with the default ubuntu packages its safer for you.
Lot of issues are reported by users not knowing they built themselves :lolflag:

---

### Post by KOSKERS on 2015-04-03
I give up. Ready to reinstall ubuntu 14.10

---

### Post by lrajat on 2015-04-05
Hi,
Please refer to my Bog Post
[http://rajat-osgyan.blogspot.in/2015/03/p-margin-bottom-0.html](http://rajat-osgyan.blogspot.in/2015/03/p-margin-bottom-0.html)
I have successfully been able to make Nviia Drivers work with 15.04 when the first beta came out. Bumbebee works great with my Lenovo Z50 Laptop which Unfortunately Came with Windows8.1. I had to remove Windows8.1.
I was pulling my hair out for 1 week because I was not able to get Ubuntu 15.04 Beta run on it. I managed to get it running, hence Shared the Information via My Blog. If there is any help you need please let me know. You can reply in the Thread or drop a comment on my Blog.

Regards
Rajat

---

### Post by cariboo on 2015-04-05
Please post your answer here, as many of our members will not click on links to external sites.

---

### Post by Andr_Correia on 2015-04-06
you need to download all libdrm2 from launchpad(trusty), then you put all of them in some folder, mount the folder

cd path
sudo dpkg -i *.deb
after that ,block the version in synaptic, with new libdrm from vivid some games like dota 2 simple don t work

---

