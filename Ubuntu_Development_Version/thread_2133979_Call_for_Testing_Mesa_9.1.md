---
title: "Call for Testing: Mesa 9.1"
date: 2013-04-09
forum: Ubuntu Development Version
---

### Post by balloons on 2013-04-09
I know many of you are discussing graphical issues in forum threads. Please give this new version of mesa a whirl and report your results on the tracker. The release team will use those results as a basis for allowing the ffe to include mesa 9.1 in raring. This has some nice fixes for intel chips in it! Check out the full details on the ffe:

[https://launchpad.net/bugs/1164093](https://launchpad.net/bugs/1164093)

Here's a link to the testcase itself.

[http://packages.qa.ubuntu.com/qatracker/milestones/266/builds/41730/testcases](http://packages.qa.ubuntu.com/qatracker/milestones/266/builds/41730/testcases)

Thanks everyone!

---

### Post by zika on 2013-04-10
Turned PPA on, updated and upgrade does not show anything to upgrade... GnomeShell PPAs are all on...

---

### Post by dino99 on 2013-04-10
testing the new mesa packages on i386 + nvidia-313-updates + 8500gt  since a few hours, and everything goes well  ):P

---

### Post by balloons on 2013-04-10
> **zika said:**
> Turned PPA on, updated and upgrade does not show anything to upgrade... GnomeShell PPAs are all on...

There's one thing in the ppa, the new mesa package. Hmm.. Is gnomeshell ppa have a version of mesa that's newer?

What's apt-cache show mesa say?

---

### Post by zika on 2013-04-10
> **guitara said:**
> There's one thing in the ppa, the new mesa package. Hmm.. Is gnomeshell ppa have a version of mesa that's newer?

What's apt-cache show mesa say?```
:~$ sudo dpkg -l|grep mesa
ii  libegl1-mesa:amd64                            9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the EGL API -- runtime
ii  libegl1-mesa-drivers:amd64                    9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the EGL API -- hardware drivers
ii  libgl1-mesa-dri:amd64                         9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                         9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:amd64                           9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the GL API -- shared library
ii  libgles2-mesa:amd64                           9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the OpenGL|ES 2.x API -- runtime
ii  libglu1-mesa:amd64                            9.0.0-0ubuntu1                                      amd64        Mesa OpenGL utility library (GLU)
ii  libopenvg1-mesa:amd64                         9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the OpenVG API -- runtime
ii  mesa-utils                                    8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers           amd64        Miscellaneous Mesa GL utilities



```

---

### Post by balloons on 2013-04-10
> **zika said:**
> ```
:~$ sudo dpkg -l|grep mesa
ii  libegl1-mesa:amd64                            9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the EGL API -- runtime
ii  libegl1-mesa-drivers:amd64                    9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the EGL API -- hardware drivers
ii  libgl1-mesa-dri:amd64                         9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                         9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:amd64                           9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the GL API -- shared library
ii  libgles2-mesa:amd64                           9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the OpenGL|ES 2.x API -- runtime
ii  libglu1-mesa:amd64                            9.0.0-0ubuntu1                                      amd64        Mesa OpenGL utility library (GLU)
ii  libopenvg1-mesa:amd64                         9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz       amd64        free implementation of the OpenVG API -- runtime
ii  mesa-utils                                    8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers           amd64        Miscellaneous Mesa GL utilities



```

Yea, look at the it's using a bleeding edge version of mesa.. I wonder why? We're on 9.1.1 in the ppa, hence why your not getting the updates :-) You would have to force install the older version.

sudo dpkg -l|grep mesa
```
ii  libegl1-mesa:amd64                            9.1.1-0ubuntu0.2                                             amd64        free implementation of the EGL API -- runtime
ii  libegl1-mesa-drivers:amd64                    9.1.1-0ubuntu0.2                                             amd64        free implementation of the EGL API -- hardware drivers
ii  libgl1-mesa-dev                               9.1.1-0ubuntu0.2                                             amd64        free implementation of the OpenGL API -- GLX development files
ii  libgl1-mesa-dri:amd64                         9.1.1-0ubuntu0.2                                             amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-dri:i386                          9.1.1-0ubuntu0.2                                             i386         free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                         9.1.1-0ubuntu0.2                                             amd64        free implementation of the OpenGL API -- GLX runtime
ii  libgl1-mesa-glx:i386                          9.1.1-0ubuntu0.2                                             i386         free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa:amd64                           9.1.1-0ubuntu0.2                                             amd64        free implementation of the GL API -- shared library
ii  libglapi-mesa:i386                            9.1.1-0ubuntu0.2                                             i386         free implementation of the GL API -- shared library
ii  libgles2-mesa:amd64                           9.1.1-0ubuntu0.2                                             amd64        free implementation of the OpenGL|ES 2.x API -- runtime
ii  libglu1-mesa:amd64                            9.0.0-0ubuntu1                                               amd64        Mesa OpenGL utility library (GLU)
ii  libglu1-mesa:i386                             9.0.0-0ubuntu1                                               i386         Mesa OpenGL utility library (GLU)
ii  libglu1-mesa-dev                              9.0.0-0ubuntu1                                               amd64        Mesa OpenGL utility library -- development files
ii  libopenvg1-mesa:amd64                         9.1.1-0ubuntu0.2                                             amd64        free implementation of the OpenVG API -- runtime
rc  libosmesa6:amd64                              9.0~git20120903.e1673d20.is.git20120821.c1114c61-0ubuntu1    amd64        Mesa Off-screen rendering extension
rc  libosmesa6:i386                               9.0~git20120903.e1673d20.is.git20120821.c1114c61-0ubuntu1    i386         Mesa Off-screen rendering extension
ii  mesa-common-dev                               9.1.1-0ubuntu0.2                                             amd64        Developer documentation for Mesa
ii  mesa-utils                                    8.0.1+git20110129+d8f7d6b-0ubuntu2                           amd64        Miscellaneous Mesa GL utilities
```

---

### Post by VinDSL on 2013-04-10
> **zika said:**
> Turned PPA on, updated and upgrade does not show anything to upgrade... GnomeShell PPAs are all on...

Me too!

```
~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~
Current Date/Time: Wed Apr 10 10:27:32 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc6-generic
Gnome Release: GNOME Shell 3.8.0.1
Unity Release: unity 7.0.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

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

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

[B][COLOR="#0000CD"]Package: mesa-common-dev
Version: 9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz[/COLOR][/B]

Package: xserver-xorg-core
  Installed: 2:1.13.3-0ubuntu5

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch


```


> **balloons said:**
> You would have to force install the older version.

Heh!  Can't say I see any immediate benefit to doing this...  ;)

---

### Post by Gyokuro on 2013-04-10
This ppa is only interesting for people with built in Intel GPUs  as mentioned by the poster. NVidia blobs are not affected as NVidia is delivering it's own graphic stack with their driver. The developers are more interested for feedback of people with Intel HD3000 and newer HD4000 GPUs. Due to my lack of HD4000 hardware I'm unable to provide the requested feedback.

---

### Post by zika on 2013-04-10
> **balloons said:**
> Yea, look at the it's using a bleeding edge version of mesa.. I wonder why?I do not mind... There is a solid well-thought reason why I stay with some of PPAs I use...
> **balloons said:**
> We're on 9.1.1 in the ppa, hence why your not getting the updates :-) You would have to force install the older version.I know why I'm not getting any upgrades from Your PPA, from the very beginning...
Why would I force that? Any real reason?
Update&#8321;: I was not reading original post in details obviously... Clarification about Intel gave me the answer... Mea culpa.

---

### Post by VinDSL on 2013-04-10
> **Gyokuro said:**
> This ppa is only interesting for people with built in Intel GPUs  as mentioned by the poster.
I see.  Thanks, for the clarification.

I didn't realize it was for Intel GPU users only.

I'll get rid of that PPA, before it goofs up my install... ;)

---

### Post by balloons on 2013-04-12
> **VinDSL said:**
> I see.  Thanks, for the clarification.

I didn't realize it was for Intel GPU users only.

I'll get rid of that PPA, before it goofs up my install... ;)

He's correct in saying that the fixes where mostly for intel users, but we wanted to test amd and nvidia too -- don't want regressions ;-) Regardless, thanks for trying VinDSL, and yes, go ahead and remove that ppa now. Your gnome ppa has already been running the new mesa stuff anyway :-)

---

### Post by ubu-for on 2013-04-13
The fan in my MacBook Pro turns up very often, if play high res videos or flash videos on websites, so I would love to test the newest GPU drivers for my Intel HD 4000. MacOS X keeps the fan silent.
I've only found a [PPA with Mesa 9.0.3]('https://launchpad.net/ubuntu/+source/mesa'). Is there also a PPA with Mesa 9.1.1 for Ubuntu 13.04 available? Have no clue how to compile the driver.

```
~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~
Current Date/Time: Wed Apr 10 10:27:32 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc6-generic
Gnome Release: GNOME Shell 3.8.0.1
Unity Release: unity 7.0.0
```
Could someone post the terminal command for the output above?

---

### Post by Gyokuro on 2013-04-13
> **ubu-for said:**
> The fan in my MacBook Pro turns up very often, if play high res videos or flash videos on websites, so I would love to test the newest GPU drivers for my Intel HD 4000. MacOS X keeps the fan silent.
I've only found a [PPA with Mesa 9.0.3]("https://launchpad.net/ubuntu/+source/mesa"). Is there also a PPA with Mesa 9.1.1 for Ubuntu 13.04 available? Have no clue how to compile the driver.

```
~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~
Current Date/Time: Wed Apr 10 10:27:32 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc6-generic
Gnome Release: GNOME Shell 3.8.0.1
Unity Release: unity 7.0.0
```
Could someone post the terminal command for the output above?

How to enable the ppa is mentioned in the first link but here it is: [http://packages.qa.ubuntu.com/qatracker/milestones/266/builds/41730/downloads](http://packages.qa.ubuntu.com/qatracker/milestones/266/builds/41730/downloads)

and the output looks like user VinDSL has hacked together a script to query some system libs/information but to check unity/mesa you can enter following command:

 sudo /usr/lib/nux/unity_support_test -p -f

---

### Post by ubu-for on 2013-04-13
Thank you very much Gyokuro!

Do I need any further driver updates i.e. Xserver, Xf86 or Vaapi drivers here from [the Intel website]('https://01.org/linuxgraphics/downloads/2013/2013q1-intel-graphics-stack-release')?

---

### Post by dino99 on 2013-04-13
The ubuntu archives is where you get the needed packages/drivers/...

sudo apt-get update

---

### Post by ubu-for on 2013-04-13
> **dino99 said:**
> The ubuntu archives is where you get the needed packages/drivers/...
If I remove the Ubuntu-X-Swat PPA, I only get Mesa 9.0.3.

Edit:

After reboot, my mouse is no longer slow-acting and idle! Thanks again!

---

### Post by Gyokuro on 2013-04-13
> **ubu-for said:**
> If I remove the Ubuntu-X-Swat PPA, I only get Mesa 9.0.3.

Yes that's correct - Mesa 9.0.3 is RRs standard mesa package until it get updated to 9.1. For this reason stick with the ppa until 9.1 is in RR (which I hope should be in the next time and not after the release of RR).

---

### Post by sammiev on 2013-04-13
Tested it for a few days now without any errors.

```
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string:  2.1 Mesa 9.1.1

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
```

---

### Post by ubu-for on 2013-04-13
After few more tests, I have to say that high res videos still bring my notebook fan to max speed.

Any ideas how to reduce heat/fan speed or does my CPU and not the GPU all the work?

---

### Post by Gyokuro on 2013-04-13
> **ubu-for said:**
> After few more tests, I have to say that high res videos still bring my notebook fan to max speed.

Any ideas how to reduce heat/fan speed or does my CPU and not the GPU all the work?

Sounds like that video decoding is CPU bound not via GPU decoding and someone can play with gstreamer-vaapi but I would not recommend it as you need background information about gstreamer/totem. In general to keep your cpu cool you need a video player which is supporting gpu decoding in some form.

---

### Post by ubu-for on 2013-04-13
I thought VLC 2.0.6 uses the GPU instead of the CPU. Tried VLC on MacOS X and the fan didn't turn up. What would you recommend?

---

### Post by icek on 2013-04-13
Hi,
try add this ppa [https://launchpad.net/~sander-vangrieken/+archive/vaapi](https://launchpad.net/~sander-vangrieken/+archive/vaapi)
then install  mplayer-vaapi and gnome-mplayer and set gnome-mplayer to use VAAPI. This worked for me.

---

### Post by Gyokuro on 2013-04-13
> **ubu-for said:**
> I thought VLC 2.0.6 uses the GPU instead of the CPU. Tried VLC on MacOS X and the fan didn't turn up. What would you recommend?

VLC on MaxOS X make use of your GPU and the same for Windows but not on Linux. Icek's hint is the way to go.

---

### Post by Rukiri on 2013-04-13
You sure? could just be the way it's compiled.

You can make use of the GPU, just compile from source, works fine on my end.

---

### Post by zika on 2013-04-13
VLC should be set to use Overlay (Accelerated video output) and try using OpenGL output...
All that is in Tools>Preferences>Video...
In Flash HWAccel. should be checked, etc...

---

### Post by Gyokuro on 2013-04-13
> **zika said:**
> VLC should be set to use Overlay (Accelerated video output) and try using OpenGL output...All that is in Tools>Preferences>Video...In Flash HWAccel. should be checked, etc...Overlay is standard markedOpenGL enabledand Input & Codecs mark  Use GPU accelerated decodingnow on HD3000 CPU is between 22 - 30% not bad but this is now all OT.

---

### Post by VinDSL on 2013-04-13
> **ubu-for said:**
> ```
~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~
Current Date/Time: Wed Apr 10 10:27:32 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc6-generic
Gnome Release: GNOME Shell 3.8.0.1
Unity Release: unity 7.0.0
```
Could someone post the terminal command for the output above?
> **Gyokuro said:**
> [...] the output looks like user VinDSL has hacked together a script to query some system libs/information [...]
Here you go (the whole enchilada):

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo
```

It's a quick n' dirty hack, for sure.  LoL!  :D

I cobbled a lot of commands together, along with appropriate spacing/alignment for copy n' paste in threads.

It's somewhat specific to my rig, and my requirements.

Feel free to pick it apart, to suit your needs...  ;)

Sample output (entire script):

```
~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~
Current Date/Time: Sat Apr 13 11:51:53 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc6-generic
Gnome Release: GNOME Shell 3.8.0.1
Unity Release: unity 7.0.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

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

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Package: mesa-common-dev
Version: 9.2.0~git20130404+9.1.980f84c3-0ubuntu0ricotz

Package: xserver-xorg-core
  Installed: 2:1.13.3-0ubuntu5

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

```

If you're only interested in the info you posted, it would be:

```
echo && echo "~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo

```

Sample output (snipped):

```
vindsl@Zuul:~$ ~ VinDSL Unity Debug Script 13.04.10 (vindsl.com) ~
Current Date/Time: Sat Apr 13 11:56:59 MST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc6-generic
Gnome Release: GNOME Shell 3.8.0.1
Unity Release: unity 7.0.0

```

Have fun!

Okay, back on topic...  ;)

---

### Post by ubu-for on 2013-04-13
Thanks for all your quick answers! Thanks VinDSL for the script!

I've opened a [new thread]('http://ubuntuforums.org/showthread.php?t=2135225&p=12601787#post12601787') to avoid further off topic posts.

---

### Post by zika on 2013-04-13
> **Gyokuro said:**
> Overlay is standard markedOpenGL enabledand Input & Codecs mark  Use GPU accelerated decodingnow on HD3000 CPU is between 22 - 30% not bad but this is now all OT.I'll have to decode this later... ;)
Update&#8321;:Yes, I forgot to mention I&C Decoding...

---

