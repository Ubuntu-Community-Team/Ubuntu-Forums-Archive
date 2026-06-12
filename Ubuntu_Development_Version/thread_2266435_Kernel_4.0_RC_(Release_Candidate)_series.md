---
title: "Kernel 4.0 RC (Release Candidate) series"
date: 2015-02-22
forum: Ubuntu Development Version
---

### Post by Doug S on 2015-02-22
kernel.org has just released 4.0RC1. I assume it will show up on the [Ubuntu page]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") soon.

@Zika: I was hoping we could try one thread for the whole RC series this time. What do you think?

Edit: By the way, I don't know why it is 4.0 instead of 3.20. As recently as Friday I saw git submissions for 3.20RC1

Edit 2: Seems to be running O.K., but haven't stressed it yet.

---

### Post by zika on 2015-02-23
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc1-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc1-vivid/)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc1-vivid/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc1-vivid/CHANGES)

> **zika said:**
> And start looking at 4.0 ... ;)
> **Ian_Worrall said:**
> Actually, it seems Linus has forgotten what he said in 2013, and is opening the window for 3.20.
> **zika said:**
> Nevertheless 4.0 will come eventually... ;)... ;)

---

### Post by zika on 2015-02-23
Ups, it is too early in the morning so I did not notice Your thread. [http://ubuntuforums.org/showthread.php?t=2266440](http://ubuntuforums.org/showthread.php?t=2266440) It would be nice if these threads would be merged. I've reported that as a wish...
> **Doug S said:**
> @Zika: I was hoping we could try one thread for the whole RC series this time. What do you think?Of course, I do not have any reason not to agree... ;)

---

### Post by sandyd on 2015-02-23
Eenie meenie miney mo, which thread shall I merge into...

Lets try this one!

---

### Post by zika on 2015-02-23
> **sandyd said:**
> Eenie meenie miney mo, which thread shall I merge into...
Lets try this one!That's right. As I suggested... ;) Thank You.

---

### Post by VinDSL on 2015-02-23
Running fine here...  ):P

```
~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Mon Feb 23 07:40:08 UTC 2015
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 4.0.0-040000rc1-generic
Gnome Release: GNOME Shell 3.14.3
Unity Release: unity 7.3.1

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 10.4.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Browser Release: Chromium ver.40.0.2214.111

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1build1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.4.2-2ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.16.2.901-1ubuntu3

Package: xserver-common
  Installed: 2:1.16.2.901-1ubuntu3

Package: xserver-xephyr
  Installed: 2:1.16.2.901-1ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by VinDSL on 2015-02-23
> **Doug S said:**
> Edit 2: Seems to be running O.K., but haven't stressed it yet.

Let's light up this candle...  :twisted:

---

### Post by VinDSL on 2015-02-23
Maybe it's just my imagination, but it seems like I used to get some sort of mysterious udev error, or whatever, when plymouth was initially loading.

Like...

```
starting version 206
```

Then, the next line would contain some kind of an error or warning.

When I checked into it, months ago, the official answer was it had something to do with a kernel bug that didn't hurt anything, so the maintainers weren't in any hurry to fix it.  They had more important things to spend their time fixing - blah, blah, blah.

I ignored it after that, but... I just noticed the warning/error is gone now in the 4.0-rc1 kernel.

Anybody know anything about this?!?!?

---

### Post by Ian_Worrall on 2015-02-23
Apparently, Linus ran a poll on G+.

So kernel will officially be called 4.0, and codenamed "Hurr durr I'ma sheep".

From the commit message:-
[quote=Linus]
.. after extensive statistical analysis of my G+ polling, I've come to the inescapable conclusion that internet polls are bad. 

Big surprise. 

But "Hurr durr I'ma sheep" trounced "I like online polls" by a  62-to-38% margin, in a poll that people weren't even supposed to  participate in. Who can argue with solid numbers like that? 5,796 votes  from people who can't even follow the most basic directions? 

In contrast, "v4.0" beat out "v3.20" by a slimmer margin of 56-to-44%, but with a total of 29,110 votes right now. 

Now, arguably, that vote spread is only about 3,200 votes, which is  less than the almost six thousand votes that the "please ignore" poll  got, so it could be considered noise. 

But hey, I asked, so I'll honor the votes.[/quote]

---

### Post by grahammechanical on 2015-02-23
> [COLOR=#000000]I ignored it after that, but... I just noticed the warning/error is gone now in the 4.0-rc1 kernel.[/COLOR]

That is interesting because right now on my default vivid kernel the error moved on from starting version 208 to starting version 209. So, there is progress somewhere but at what I have no idea. :)

Regards

---

### Post by ventrical on 2015-02-23
Bahahahahahaha.... :)

---

### Post by VinDSL on 2015-02-23
12 hours & counting

Haven't experienced a single prob yet... :)

---

### Post by grahammechanical on 2015-02-23
Well, it was worth a try and I guess that I will never learn. It seemed so simple.

linux-headers failed to install. Trip over Nvidia 304 driver. "bad return status for module build on kernel:"

Kernel 4.0 loaded to a login screen but no desktop. I was able to get in using kernel 3.18. Additional Drivers could not remove Nvidia 304 and apt-get purge also failed. Even Recovery>Resume loaded to the Nvidia 304.

I used Synaptic to completely remove kernel 4.0 and Nvidia 304. I am back on Nouveau but I guess it still has the GPU lock up bug. I am not happy with Nouveau at the moment.

I will try again. This time with the 3.19 kernel but now it is time for a lie down in a darkened room.

---

### Post by VinDSL on 2015-02-23
Interesting!

nVidia 304.x drivers haven't worked for me since 3.18.  I finally gave up on them.

Nouveau drivers, on the other hand, have been working great...


[[img]http://vindsl.com/images/vindsl-desktop-23-feb-2015-1(650x520).png[/img]]("http://vindsl.com/images/vindsl-desktop-23-feb-2015-1.png")


Was the LLVMpipe driver being used?.  LLVMpipe is hideously slow and choppy on this rig - lags out horribly...

---

### Post by grahammechanical on 2015-02-23
> [COLOR=#000000]Was the LLVMpipe driver being used?. LLVMpipe is hideously slow and choppy on this rig - lags out horribly...[/COLOR]

That is the strange thing. I expected recovery>resume to bring in llvmpipe but when I got to the desktop the driver was still Nvidia 304. I never intended to use 304. I switched to it by mistake. I was having GPU lockup with Nouveau and I switched to Nvidia and mistakenly activated 304 instead of the later version and paid the price for being to lazy to change it.

This was the kind of thing that I should have seen coming. A very new kernel and a very old proprietary video driver. Things have cleaned up nicely and I will try again. Install the kernel with Nouveau and then activate the Nvidia driver.

---

### Post by VinDSL on 2015-02-24
Spent the past 5-6 hours in Gnome-Shell.

No probs here either...  ;)

---

### Post by ventrical on 2015-02-24
Flying here :) Gnome Shell

I sometimes use extreme tux racer from USC. I notice that the graphics a much more clear and vivid, no pun intended:)

---

### Post by grahammechanical on 2015-02-24
I must be doing something wrong. Whether it is kernel 4.0 or 3.19 linux-headers is not being installed. With kernel 4.0 it was the old Nvidia driver. With kernel 3.19 it was Makefile no such file or directory.

Is this thread going to be the default rc kernel discussion thread? If so, then I have seen this

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

What else will help me?

Regards.

---

### Post by ventrical on 2015-02-24
> **grahammechanical said:**
> I must be doing something wrong. Whether it is kernel 4.0 or 3.19 linux-headers is not being installed. With kernel 4.0 it was the old Nvidia driver. With kernel 3.19 it was Makefile no such file or directory.

Is this thread going to be the default rc kernel discussion thread? If so, then I have seen this

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

What else will help me?

Regards.


  I downloaded just the two generic amd64 image/headers and of course , all. (Did not choose low-latency)

Then :
```

sudo dpkg --install *.deb

```


Another time I had a problem with another kernel I removed nvidia-current and installed nouveau-firmware.

```
ventrical@ventrical-MS-7798:~$ uname -a
Linux ventrical-MS-7798 4.0.0-040000rc1-generic #201502222235 SMP Mon Feb 23 03:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-MS-7798:~$ 


```


Regards..

---

### Post by Doug S on 2015-02-24
> **grahammechanical said:**
> Is this thread going to be the default rc kernel discussion thread?I was proposing one thread for the whole 4.0RC series this time, just to see if we like it or not, as in the past I have found I need to refer back to the previous rcx thread often.> **grahammechanical said:**
> If so, then I have seen this [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)I almost always run the mainline kernel for this leading edge stuff. I was not aware of that page, Thanks.

---

### Post by VinDSL on 2015-02-24
> **Doug S said:**
> I almost always run the mainline kernel for this leading edge stuff. 

Me, too.  I always run mainline kernels on all Linux distros - love them!  Sometimes I compile, some times I don't.

Also, I seldom do fresh installs...

```
vindsl@Zuul:~$ echo && echo -n "Last Fresh Install: " && echo | ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }' && echo

Last Fresh Install: Jan 25 2014

vindsl@Zuul:~$ 
```

... but, that's just me.  :)

---

### Post by VinDSL on 2015-02-24
> **Doug S said:**
> I was proposing one thread for the whole 4.0RC series this time, just to see if we like it or not [...]

While we're all on the same page, so to speak -- and, I'm thinking about it.

Here's the link I use to check the mainline kernel directory for updates...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D")

Saves a little scrolling ;)

---

### Post by grahammechanical on 2015-02-24
I finally worked out what I was doing wrong and Ventrical put me on the path.

I was downloading linux-headers-blah-blah_amd64.deb and linux-image-blah-blah_amd64.deb but not linux-headers-blah-blah_all.deb.

EDIT: This is how I am getting on. Kernel 4.0 and Nouveau work well together but Nouveau has GPU lockup when selecting more than 10 lines of text in a Writer document. And not just on kernel 4.0. So, I move on to Nvidia which does not give GPU lockup but kernel 4.0 does not like Nvidia 340.76. It gives a very large/low screen resolution. 

Oh, well. Such is life.

EDIT 2: I have been thinking. It is as if the Nvidia driver is not loading on kernel 4.0. Well, I did install it on kernel 3.18.13. I am now considering installing a later version Nvidia driver. Living dangerously. It must be spring. Either that or the tablets are having no effect. :)

---

### Post by ventrical on 2015-02-25
Just played a dvd and it left my core cool.

```

ventrical@ventrical-MS-7798:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +103.0°C)
temp2:        +29.8°C  (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +32.0°C  (high = +82.0°C, crit = +102.0°C)
Core 0:         +29.0°C  (high = +82.0°C, crit = +102.0°C)
Core 1:         +32.0°C  (high = +82.0°C, crit = +102.0°C)

ventrical@ventrical-MS-7798:~$ uname -a
Linux ventrical-MS-7798 4.0.0-040000rc1-generic #201502222235 SMP Mon Feb 23 03:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by ventrical on 2015-02-25
nvidia-current will not build against this rc 4.n.n-n kernel. Not Supported; error.

edit: oh .. graham already said that :)

---

### Post by grahammechanical on 2015-02-25
For me getting an Nvidia driver working has gone from interesting to boring. Nvidia 346.35 is in the repositories as this command will reveal

```
sudo apt-cache search "NVIDIA binary driver"
```

So it should install with

```
 sudo apt-get install nvidia-346
```

And it does seem to install but on kernel 4.0 and 3.18.13 (latest stable) Ubuntu loads to very low resolution llvmpipe. The bottom of the Make.log file has this

> make[2]: Target '__build' not remade because of errors.
Makefile:1390: recipe for target '_module_/var/lib/dkms/nvidia-346/346.35/build' failed
make[1]: *** [_module_/var/lib/dkms/nvidia-346/346.35/build] Error 2
make[1]: Target 'modules' not remade because of errors.
make[1]: Leaving directory '/usr/src/linux-headers-4.0.0-040000rc1-generic'
NVIDIA: left KBUILD.
nvidia.ko failed to build!
nvidia-modules-common.mk:248: recipe for target 'module' failed
make: *** [module] Error 1


It becomes really strange because Details will say llvmpipe or Gallium but Additional Drivers will say a proprietary driver is in use. So, the OS is as confused as I am :) Things work fine on Nouveau and I would be happy with it if it did not have that GPU lockup when selecting text in Writer.

---

### Post by Doug S on 2015-02-25
> **VinDSL said:**
> ```
vindsl@Zuul:~$ echo && echo -n "Last Fresh Install: " && echo | ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }' && echo

Last Fresh Install: Jan 25 2014

vindsl@Zuul:~$ 
```

... but, that's just me.Yes, I am overdue to do a fresh install on my test computer. It is somewhat of a mess right now.```
doug@s15:~/temp$ echo && echo -n "Last Fresh Install: " && echo | ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }' && echo

Last Fresh Install: Mar 14 2012

doug@s15:~/temp$
```

> **VinDSL said:**
> Here's the link I use to check the mainline kernel directory for updates...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

Saves a little scrolling Very cool, I have replaced my bookmark with your version.

---

### Post by VinDSL on 2015-02-25
> **Doug S said:**
> Yes, I am overdue to do a fresh install on my test computer. It is somewhat of a mess right now.

I had to bite_the_bullet last year.  

After testing GS Staging for (like) a year, my rig got to the point where it was impossible to do incremental upgrades, without wiping half the packages off my drive.

I was usually able to pull_a_rabbit_out_of_my_hat when that happened, but it finally got so bad it was easier and less time-consuming to just give-up and do a fresh install.  ;)

---

### Post by Milos_SD on 2015-02-26
To get Nvidia drivers working on this kernel, check this thread on [devtalk.nvidia.com]("https://devtalk.nvidia.com/default/topic/813458/linux/linux-4-0-rc1-346-35-build-error-_cr4-functions-fix/")

It is for 346.xx drivers, but maybe it will work for 304.xx also.

---

### Post by Doug S on 2015-03-03
[4.0RC2 is out.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") (It will be awhile before I can try it.)

---

### Post by fyfe54 on 2015-03-04
Running RC2.  all OK, so far.

---

### Post by VinDSL on 2015-03-04
Everything is working so well right now [4.0-rc2] that it's scary!  :mrgreen:

Ubu 15.04 is turning out to be an epic release IMO.

Guess I'll upgrade some packages, and see if I can break something...

---

### Post by Doug S on 2015-03-05
I have been running 4.0RC2 for about a day now. No issues.

---

### Post by [Neurotic] on 2015-03-07
I'm also running 4.0 RC2 - has been great (other than nvidia won't compile - as we all know) - I can finally use my focaltech touchpad without having to patch and compile kernels.

At some point I may try the supplied NVIDIA patch and see if I can get nvidia-prime back up and running.

---

### Post by VinDSL on 2015-03-07
> **'[Neurotic] said:**
> At some point I may try the supplied NVIDIA patch and see if I can get nvidia-prime back up and running.

For giggles, the other night I went over to the nVidia archives and DL'ed the most recent proprietary version of 304.125

According to the changelog, it was supposed to work with Linux 3.9x, so I thought I'd give it a try.

It turned out to be a 'fail' on 4.0-rc2.  Just saying...

Good luck with the patch!  ;)

---

### Post by Doug S on 2015-03-08
Kernel version 4.0RC3 is out on kernel.org, but has yet to appear [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"). I assume it will soon.

Edit: I have been running 4.0RC3 for a couple of hours now. Seems O.K. I still don't see it on the[ PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") though.

---

### Post by VinDSL on 2015-03-09
> **Doug S said:**
> I have been running 4.0RC3 for a couple of hours now. Seems O.K. I still don't see it on the[ PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") though.

Just checked.

It's there now...


**EDIT**


```
Current Date/Time: Mon Mar  9 11:15:15 UTC 2015
```

Judging by the timestamp, it must have arrived about 7 hours ago - just after you edited your post (above)  :)

---

### Post by zika on 2015-03-15
It looks like mainline is kind of frozen in time... ;)

---

### Post by aljosa2 on 2015-03-17
_Bug 94981:_
[**Kernel 4.0-rc4: ASUS Notebook Elantech Touchpad Completely Dead**]("https://bugzilla.kernel.org/show_bug.cgi?id=94981")

bad luck with nvidia too :(

---

### Post by VinDSL on 2015-03-18
All hail Linux 4.0-rc4  :)

```
~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Wed Mar 18 04:18:17 UTC 2015
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 4.0.0-040000rc4-generic
Gnome Release: GNOME Shell 3.14.3
Unity Release: unity 7.3.1

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 10.5.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Browser Release: Chromium ver.41.0.2272.76

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1build1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.5.0-0ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.17.1-0ubuntu2

Package: xserver-common
  Installed: 2:1.17.1-0ubuntu2

Package: xserver-xephyr
  Installed: 2:1.17.1-0ubuntu2

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by VinDSL on 2015-03-24
Linux 4.0-rc5 continues to be working fine, here...

```
~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Tue Mar 24 11:05:40 UTC 2015
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 4.0.0-040000rc5-generic
Gnome Release: GNOME Shell 3.14.3
Unity Release: unity 7.3.1

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 10.5.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Browser Release: Chromium ver.41.0.2272.76

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1build1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.5.0-0ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.17.1-0ubuntu3

Package: xserver-common
  Installed: 2:1.17.1-0ubuntu3

Package: xserver-xephyr
  Installed: 2:1.17.1-0ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by [Neurotic] on 2015-03-24
rc5 is good here as well.

I applied the patch to the downloaded driver from Nvidia, and it compiled perfectly, but I couldn't get nvidia-prime to work at all :(

May just have to wait until nvidia supports v4, and then use x-swat to pull the driver in.

---

### Post by Doug S on 2015-03-29
Kernel 4.0RC6 has been released, but I do not see it yet at the [ubuntu PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"). I only just built 4.0RC5, so it will be a bit before I try RC6.

---

### Post by bubble-f on 2015-03-30
It's there now. Seems you were just a bit to fast.

I'll try it in the evening when I get home.

---

### Post by Chanath on 2015-03-30
I just installed kernel 4.0 RC1 on Trusty, amove from 3.13... to this. It appears towork well. Only Plymouth screen didn't appear. Compiz works well with it. I'l work with this for a while and install 4.0 RC6. Have anyone installed kernel 4.0 RC on Trusty?

Later, I'm going to install it on Vivid, but first play with Trusty.

---

### Post by VinDSL on 2015-03-30
Yup!  Kernel 4.0-rc6 is out.

This has been the best/most unremarkable kernel ever.  It just works...  :)

```
~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Mon Mar 30 11:22:19 UTC 2015
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 4.0.0-040000rc6-generic
Gnome Release: GNOME Shell 3.14.4
Unity Release: unity 7.3.1

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 10.5.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Browser Release: Chromium ver.41.0.2272.76

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1build1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.5.0-0ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.17.1-0ubuntu3

Package: xserver-common
  Installed: 2:1.17.1-0ubuntu3

Package: xserver-xephyr
  Installed: 2:1.17.1-0ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by VinDSL on 2015-03-30
> **Chanath said:**
> Have anyone installed kernel 4.0 RC on Trusty?

I haven't tried it on Trusty, but...

For shigles, I installed it on Raring (13.04), which didn't work, of course (kernel panic) :p

---

### Post by Ian_Worrall on 2015-03-30
Hopefully, there won't need to be an rc7, letting it go final before the Kernel Freeze on April 9th.

---

### Post by Doug S on 2015-03-30
> **Chanath said:**
> Have anyone installed kernel 4.0 RC on Trusty?Yes. All of my work with the 4.0RC series has been on an otherwise Ubuntu trusty server.

---

### Post by craig10x on 2015-03-30
@Ian: even if that were the case, kernel 4.0 won't be making the ubuntu 15.04 release because it would still be too close to the freeze...now if it had been ready a month sooner then it would have been...3.19 is going to be the release kernel...ubuntu likes lots of time to run a finalized kernel and do their own patching, etc...so they need at least a month before freeze to consider any newer kernel final releases from mainstream...

By the time 15.10 is released, it will have a even newer kernel then 4.0...the best rule of thumb is, look at which kernel that ubuntu development is using about 2 months before the freeze and THAT is the likely one it's going to get final released with ;)

---

### Post by Chanath on 2015-03-30
> **Doug S said:**
> Yes. All of my work with the 4.0RC series has been on an otherwise Ubuntu trusty server.

No problem yet, other than plymouth screen not working, which is not a big deal, though. Quite uneventful.

---

### Post by QDR06VV9 on 2015-03-30
here is mine [B]Chanath
Runs very well but if you want Nvidia Driver,it has been a no go at least for me here.
Tried several patches finally just gave up.
[/B]```
mate@mate-Aspire-M3300:~$ lsb_release -a && uname -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
Linux mate-Aspire-M3300 4.0.0-040000rc6-lowlatency #201503291935 SMP PREEMPT Sun Mar 29 23:45:24 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Ian_Worrall on 2015-04-07
RC7 has appeared:- [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc7-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc7-vivid/)

Linus has said 4.0 final will drop next week (possibly the week after as he is travelling).

---

### Post by xeizoo on 2015-04-07
The proprietary Nvidia-drivers works! For the first time in a 4.0-RC* kernel, Nvidia 349.12 and GTX680 ....

---

### Post by aljosa2 on 2015-04-07
> **xeizoo said:**
> The proprietary Nvidia-drivers works! For the first time in a 4.0-RC* kernel, Nvidia 349.12 and GTX680 ....
wow, that's a great news :)
can someone confirm that everything is ok with the optimus driver version too?

---

### Post by aljosa2 on 2015-04-07
Ubuntu 14.04.2
Kernel 4.0-rc7
Driver Optimus *_Nvidia 346_* from Xorg-Edgers PPA

**ERROR (dkms apport): kernel package linux-headers-4.0.0-040000rc7-generic is not supported**
**Error! Bad return status for module build on kernel: 4.0.0-040000rc7-generic (x86_64)**

---

### Post by aljosa2 on 2015-04-07
Ubuntu 14.04.2
Kernel 4.0-rc7
Driver Optimus *_Nvidia 349_* from Xorg-Edgers PPA

**FINALLY EVERYTHING OKAY** :)

---

### Post by QDR06VV9 on 2015-04-07
All is good using this ppa:mamarley/nvidia

```
Linux Mate-Aspire-M3300 4.0.0-040000rc7-lowlatency #201504061936 SMP PREEMPT Mon Apr 6 23:46:09 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ii  nvidia-349                                           349.12-100ubuntu100~ppa0~vivid              amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-349                                349.12-100ubuntu100~ppa0~vivid              amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-349                                349.12-100ubuntu100~ppa0~vivid              amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                         0.8.1                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                      349.12-100ubuntu100~ppa0~vivid              amd64        Tool for configuring the NVIDIA graphics driver
```
Only been running this for about 40 mins will report back if issues pop up!

---

### Post by VinDSL on 2015-04-12
Kernel 4.0 Final has arrived...

```
~ VinDSL Unity Debug Script 15.02.13 (vindsl.com) ~
Current Date/Time: Mon Apr 13 02:43:49 UTC 2015
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 4.0.0-040000-generic
Gnome Release: GNOME Shell 3.14.4
Unity Release: unity 7.3.2

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 10.5.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Browser Release: Chromium ver.41.0.2272.76

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1build1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.5.2-0ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.17.1-0ubuntu3

Package: xserver-common
  Installed: 2:1.17.1-0ubuntu3

Package: xserver-xephyr
  Installed: 2:1.17.1-0ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by QDR06VV9 on 2015-04-13
Thanks VinDSL;)

```
 uname -a && sudo lshw -c video
Linux me-Aspire-M3300 4.0.0-999-generic #201504122205 SMP Mon Apr 13 02:06:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
  *-display               
       description: VGA compatible controller
       product: GF119 [GeForce GT 520]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:29 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:fa000000-fbffffff ioport:b800(size=128) memory:fe880000-fe8fffff
dpkg -l | grep nvidia
ii  nvidia-349                                  349.12-100ubuntu100~ppa0~vivid             amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-349-dev                              349.12-100ubuntu100~ppa0~vivid             amd64        NVIDIA binary Xorg driver development files
ii  nvidia-libopencl1-349                       349.12-100ubuntu100~ppa0~vivid             amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-349                       349.12-100ubuntu100~ppa0~vivid             amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.1                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             349.12-100ubuntu100~ppa0~vivid             amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by zika on 2015-04-13
Any news/experiences about/with live kernel patching?

---

### Post by QDR06VV9 on 2015-04-13
_**If your going to attempt to install on trusty**_ here is taste of what will happen.
Bug Reports are plenty.(Lots reported already)
```
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.0.0-040000-lowlatency /boot/vmlinuz-4.0.0-040000-lowlatency
[COLOR=#ff0000]Error! Bad return status for module build on kernel: 4.0.0-040000-lowlatency (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
Error! Bad return status for module build on kernel: 4.0.0-040000-lowlatency (x86_64)
Consult /var/lib/dkms/ndiswrapper/1.59/build/make.log for more information.
Error! Bad return status for module build on kernel: 4.0.0-040000-lowlatency (x86_64)
Consult /var/lib/dkms/nvidia-340/340.76/build/make.log for more information.[/COLOR]
Setting up linux-image-4.0.0-040000-lowlatency (4.0.0-040000.201504121935) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.0.0-040000-lowlatency /boot/vmlinuz-4.0.0-040000-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 4.0.0-040000-lowlatency /boot/vmlinuz-4.0.0-040000-lowlatency
[COLOR=#ff0000]Error! Bad return status for module build on kernel: 4.0.0-040000-lowlatency (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
Error! Bad return status for module build on kernel: 4.0.0-040000-lowlatency (x86_64)
Consult /var/lib/dkms/ndiswrapper/1.59/build/make.log for more information.
Error! Bad return status for module build on kernel: 4.0.0-040000-lowlatency (x86_64)
Consult /var/lib/dkms/nvidia-340/340.76/build/make.log for more information.[/COLOR]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.0.0-040000-lowlatency /boot/vmlinuz-4.0.0-040000-lowlatency
update-initramfs: Generating /boot/initrd.img-4.0.0-040000-lowlatency
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.0.0-040000-lowlatency /boot/vmlinuz-4.0.0-040000-lowlatency
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.0.0-040000-lowlatency /boot/vmlinuz-4.0.0-040000-lowlatency
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 4.0.0-040000-lowlatency /boot/vmlinuz-4.0.0-040000-lowlatency

```
So caution is the word, Unless your not using any of those modules!

---

### Post by Doug S on 2015-04-13
It installed O.K. for me (the same low latency, amd64 version). 

@zika: I am not familiar with "live kernel patching". I would like to learn more.

@all: Did people like this one thread for the whole RC series thing we tried this time, or would you prefer to go back to the one thread for each RC for the 4.1 series?

---

### Post by QDR06VV9 on 2015-04-14
For **Trusty** this one is on lenovo lappy
And all is good quite snappy been running for about 6 hrs now heavy usage!
Did show during the install an old warning about possible missing firmware R618 or something to that!:confused:
But that has been around since 2012  
```
lshw -c video && uname -a
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:25 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
Linux me-Lenovo-B570 4.0.0-040000-generic #201504121935 SMP Sun Apr 12 23:36:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
Also tried on Acer 5750 it brought a kernel panic! Ubuntu Gnome
So I booted to Miint 17 on the Acer I  got success???
```
 lshw -c video && uname -a && lsb_release -a
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:2000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
Linux me-Aspire-5750 4.0.0-040000-generic #201504121935 SMP Sun Apr 12 23:36:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 17 Qiana
```

```
@all: Did people like this one thread for the whole RC series thing we  tried this time, or would you prefer to go back to the one thread for  each RC for the 4.1 series?
```
I thought it was nice to have all info in one thread.
Regards

---

### Post by VinDSL on 2015-04-14
> **Doug S said:**
> @all: Did people like this one thread for the whole RC series thing we tried this time, or would you prefer to go back to the one thread for each RC for the 4.1 series?

The new way is fine by me, Doug! ;)

---

### Post by cariboo on 2015-04-15
+1 to keeping it all in one thread. As many of you may have noticed, many of our members have a problem with version numbers, this may help keep this subject easier to find. :)

---

### Post by irishbandit2 on 2015-04-22
Getting the nvidia drivers to work was a pain and its still not working the way I want it to.
To get it to build for 4.0.0 
sudo dpkg-reconfigure nvidia-349
or install nvidia-349 after you install your kernel...
It works but sometimes you have to boot into a tty with no gui and run the above command.

The way I used to do it was install new kernel then run for example..
sudo dkms install -m nvidia -v 349-349.16 -k 4.0.0-rc1-02232015
which does not work now that uvm was merged into nvidia-349
dont know why...

inxi -GS
System:    Host: desktop Kernel: 4.0.0-04142015 x86_64 (64 bit) Desktop: Cinnamon 2.5.0
           Distro: Ubuntu 15.04 vivid
Graphics:  Card: NVIDIA GF114 [GeForce GTX 560]
           Display Server: X.Org 1.17.1 driver: nvidia Resolution: 1680x1050@60.6hz
           GLX Renderer: GeForce GTX 560/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 349.16

---

### Post by monkeybrain20122 on 2015-04-22
Someone found a bug here [http://ubuntuforums.org/showthread.php?t=2272570](http://ubuntuforums.org/showthread.php?t=2272570)
I have confirmed it on Trusty. I think Vivid would be same.

---

### Post by fooman on 2015-04-22
> **irishbandit2 said:**
> Getting the nvidia drivers to work was a pain and its still not working the way I want it to.
To get it to build for 4.0.0 
sudo dpkg-reconfigure nvidia-349
or install nvidia-349 after you install your kernel...
It works but sometimes you have to boot into a tty with no gui and run the above command.

The way I used to do it was install new kernel then run for example..
sudo dkms install -m nvidia -v 349-349.16 -k 4.0.0-rc1-02232015
which does not work now that uvm was merged into nvidia-349
dont know why...

inxi -GS
System:    Host: desktop Kernel: 4.0.0-04142015 x86_64 (64 bit) Desktop: Cinnamon 2.5.0
           Distro: Ubuntu 15.04 vivid
Graphics:  Card: NVIDIA GF114 [GeForce GTX 560]
           Display Server: X.Org 1.17.1 driver: nvidia Resolution: 1680x1050@60.6hz
           GLX Renderer: GeForce GTX 560/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 349.16

have you tried the drivers from this repo?

[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

they work great for me,  no issues here at all.   thanks @runrickus for pointing those out :D

```
Distro Release: Ubuntu 15.04
Kernel Release: Linux 4.0.0-040000-generic
Gnome Release: GNOME Shell 3.14.4
Unity Release: unity 7.3.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.5.0 NVIDIA 349.16
```

---

### Post by QDR06VV9 on 2015-04-23
> **fooman said:**
> have you tried the drivers from this repo?

[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

they work great for me,  no issues here at all.   thanks @runrickus for pointing those out :D

I'm Glad you tried it:D  with positive results..If I could get Cavsfan to see if it helps him?
But I have not had any of the Quirks with that PPA that I had with xedgers.
Kind Regards

---

### Post by irishbandit2 on 2015-04-25
> **fooman said:**
> have you tried the drivers from this repo?

[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

they work great for me,  no issues here at all.   thanks @runrickus for pointing those out :D

```
Distro Release: Ubuntu 15.04
Kernel Release: Linux 4.0.0-040000-generic
Gnome Release: GNOME Shell 3.14.4
Unity Release: unity 7.3.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.5.0 NVIDIA 349.16
```


I didnt use all of the files from the ppa...
copying /usr/src/nvidia-349-349.16/uvm to /usr/src/nvidia-349-uvm-349.16 using nvidia-349 installed from [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa) .
Then downloading and extracting  the dkms files from [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia/+files/nvidia-349_349.16-100ubuntu100%7Eppa0%7Evivid_amd64.deb](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia/+files/nvidia-349_349.16-100ubuntu100%7Eppa0%7Evivid_amd64.deb)
and the dkms from [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia/+files/nvidia-349-uvm_349.16-100ubuntu100%7Eppa0%7Evivid_amd64.deb](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia/+files/nvidia-349-uvm_349.16-100ubuntu100%7Eppa0%7Evivid_amd64.deb) copied into /usr/src/nvidia-349-uvm-349.16
dkms builds both the nvidia and the nvidia-uvm modules correctly
sudo dkms install -m nvidia -v 349-349.16 -k 4.0.0-rc1-02232015
sudo dkms install -m nvidia-349-uvm -v 349.16 -k 4.0.0-rc1-02232015

trying to figure out how to patch the original dkms file from xorg-edgers gave me a headache... so if some one could build upon what mamarley has fixed in his release we could get a fix added to xorg-edgers that would take care of a bunch of bugs on the tracker.

---

