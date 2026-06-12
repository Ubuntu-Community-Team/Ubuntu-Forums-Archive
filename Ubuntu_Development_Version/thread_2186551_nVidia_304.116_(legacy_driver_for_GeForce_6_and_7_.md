---
title: "nVidia 304.116 (legacy driver for GeForce 6 and 7 series)"
date: 2013-11-07
forum: Ubuntu Development Version
---

### Post by VinDSL on 2013-11-07
Anyone running this driver on Trusty / Linux 3.12 yet?

[https://devtalk.nvidia.com/default/topic/632711/unix-graphics-announcements-and-news/linux-solaris-and-freebsd-driver-304-116-legacy-for-geforce-6-and-7-series-/](https://devtalk.nvidia.com/default/topic/632711/unix-graphics-announcements-and-news/linux-solaris-and-freebsd-driver-304-116-legacy-for-geforce-6-and-7-series-/)

[http://www.phoronix.com/scan.php?page=news_item&px=MTUwNjk](http://www.phoronix.com/scan.php?page=news_item&px=MTUwNjk)

> Improved compatibility with recent Linux kernels.

---

### Post by kostkon on 2013-11-07
I wonder whether the [nvidia-304-updates]("http://packages.ubuntu.com/saucy/nvidia-304-updates") package will get updated to .116, even trusty is on .108.

---

### Post by paul_in_london on 2013-11-08
> **VinDSL said:**
> Anyone running this driver on Trusty / Linux 3.12 yet?

[https://devtalk.nvidia.com/default/topic/632711/unix-graphics-announcements-and-news/linux-solaris-and-freebsd-driver-304-116-legacy-for-geforce-6-and-7-series-/](https://devtalk.nvidia.com/default/topic/632711/unix-graphics-announcements-and-news/linux-solaris-and-freebsd-driver-304-116-legacy-for-geforce-6-and-7-series-/)

[http://www.phoronix.com/scan.php?page=news_item&px=MTUwNjk](http://www.phoronix.com/scan.php?page=news_item&px=MTUwNjk)

Sorry Vin hadn't seen your thread when I posted about this a minute ago. It claims "improved support for recent Linux kernels" so maybe that includes 3.12. At work so can't try it out right now.

---

### Post by VinDSL on 2013-11-08
No prob, Paul.

I used all the tricks in my bag, trying to get the nVidia installer to build 304.116, but it fails on boot.

This is more or less what I do:  [http://ubuntuhandbook.org/index.php/2013/11/install-nvidia-304-116-legacy-ubuntu/](http://ubuntuhandbook.org/index.php/2013/11/install-nvidia-304-116-legacy-ubuntu/)

The nVidia installer is reporting that all steps were successfully completed, but no joy.

Hopefully, somebody will package it into a deb.  I *suspect* the Linux 3.12 module isn't being compiled correctly.

---

### Post by paul_in_london on 2013-11-08
> **VinDSL said:**
> No prob, Paul.

I used all the tricks in my bag, trying to get the nVidia installer to build 304.116, but it fails on boot.

This is more or less what I do:  [http://ubuntuhandbook.org/index.php/2013/11/install-nvidia-304-116-legacy-ubuntu/](http://ubuntuhandbook.org/index.php/2013/11/install-nvidia-304-116-legacy-ubuntu/)

The nVidia installer is reporting that all steps were successfully completed, but no joy.

Hopefully, somebody will package it into a deb.  I *suspect* the Linux 3.12 module isn't being compiled correctly.

Can see it there now:

[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty](https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty)

Let me know if it works! :)

---

### Post by VinDSL on 2013-11-08
> **paul_in_london said:**
> Can see it there now:

[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty](https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty)

Let me know if it works! :)
Hi Paul,

Well, believe it or not...

I just got home and decided to try the nVidia installer one_last_time.

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Fri Nov  8 22:36:35 UTC 2013
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux 3.12.0-rc7-vindsl-p4ee-ver.004
Gnome Release: GNOME Shell 3.11.1
Unity Release: unity 7.1.2

[B][COLOR="#000080"]OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.116[/COLOR][/B]

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
Installed-Size: 115
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
  Version: 9.2.2-1ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu4

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu4

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu4

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
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

Went smoothly this time.  Practice makes perfect, I guess.  LoL!  :D

Think I'll run it for a few hours, before trying the edgers version.

---

### Post by VinDSL on 2013-11-08
So far, so good...  ;)

[INDENT]**[COLOR="#800080"]  Ubuntu 'Trusty' 14.04 (32 Bit) / Linux 3.12 Kernel / GS 3.11.1 Staging  / nVidia 304.116 / Conky / ConkyWX[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-8-nov-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-nov-2013-1.png")[/INDENT]

---

### Post by QDR06VV9 on 2013-11-09
> **VinDSL said:**
> So far, so good...  ;)[INDENT]**[COLOR=#800080]  Ubuntu 'Trusty' 14.04 (32 Bit) / Linux 3.12 Kernel / GS 3.11.1 Staging  / nVidia 304.116 / Conky / ConkyWX[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-8-nov-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-nov-2013-1.png")[/INDENT]


Been a few hours now with xedgers install, small difference, slight improvement.;)

---

### Post by VinDSL on 2013-11-09
> **runrickus said:**
> Been a few hours now with xedgers install, small difference, slight improvement.;)
I'll probably switch to edgers tomorrow.

I just don't like dealing with the official nVidia driver.  The installer stinks, and it always seems like something or another crops up that requires me to remove the driver -- which is usually as much of a PITA as installing it.

Debs are definitely preferable, for a whole host of reasons, IMO...  ;)

EDIT

BTW, I must admit... Plymouth looks a whole lot better with the official driver.  Oh, well.  Not worth the extra effort.

---

### Post by QDR06VV9 on 2013-11-09
> **VinDSL said:**
> I'll probably switch to edgers tomorrow.

I just don't like dealing with the official nVidia driver.  The installer stinks, _and it always seems like something or another crops up that requires me to remove the driver -- which is usually as much of a [COLOR=#000080]PITA[/COLOR] as installing it._

Debs are definitely preferable, for a whole host of reasons, IMO...  ;)

EDIT

BTW, I must admit... Plymouth looks a whole lot better with the official driver.  Oh, well.  Not worth the extra effort.

Ill be curious to see if you notice any difference between the two.
Thats why I stick with debs on kernels also..:)

---

### Post by VinDSL on 2013-11-09
Interesting!

I got rid of the official driver -- a great joy, as usual.  Then, I installed the edgers version.

Everything went smoothly, until I tried to install 'nvidia-settings'.  For some reason, apt-get *thought* I had an unmet dependency.  It reported that it required 'screen-resolution-extra' >=0.12.  The odd thing was... I already had 'screen-resolution-extra' 0.16 installed on this box.  Go figure.

After the umpteenth try, I was still getting a screen full of error messages, but somehow it magically worked.

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
nvidia-304:
  Installed: 304.116-0ubuntu1~xedgers~saucy1
  Candidate: 304.116-0ubuntu1~xedgers~saucy1
  Version table:
 *** 304.116-0ubuntu1~xedgers~saucy1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     304.88-0ubuntu8 0
        500 http://archive.ubuntu.com/ubuntu/ devel/restricted i386 Packages
vindsl@Zuul:~$ 
vindsl@Zuul:~$ apt-cache policy nvidia-settings
nvidia-settings:
  Installed: 304.116-0ubuntu1~xedgers~saucy1
  Candidate: 304.116-0ubuntu1~xedgers~saucy1
  Version table:
 *** 304.116-0ubuntu1~xedgers~saucy1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     304.88-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ devel/main i386 Packages
vindsl@Zuul:~$ 
vindsl@Zuul:~$ apt-cache policy screen-resolution-extra
screen-resolution-extra:
  Installed: 0.16
  Candidate: 0.16
  Version table:
 *** 0.16 0
        500 http://archive.ubuntu.com/ubuntu/ devel/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 

```

Isn't testing fun?!?!?  :D

EDIT

Whoops!  Looks like I somehow snagged the Saucy version(s).

Oh, well.  Back to the inkwell...  ;)

---

### Post by QDR06VV9 on 2013-11-09
> **VinDSL said:**
> Interesting!

but somehow it magically worked.:wink:

Yep been seeing some of that magic myself.LOL

```
Whoops! Looks like I somehow snagged the Saucy version(s).


```

Almost did that myself, But the trusty repo works for saucy also.:D
```
Isn't testing fun?!?!?  :grin:

```

Time of my Life!!LMAO

---

### Post by VinDSL on 2013-11-09
Ah!  That looks better...

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
nvidia-304:
  Installed: 304.116-0ubuntu1~xedgers~trusty1
  Candidate: 304.116-0ubuntu1~xedgers~trusty1
  Version table:
 *** 304.116-0ubuntu1~xedgers~trusty1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     304.88-0ubuntu8 0
        500 http://archive.ubuntu.com/ubuntu/ devel/restricted i386 Packages
vindsl@Zuul:~$ 
vindsl@Zuul:~$ apt-cache policy nvidia-settings
nvidia-settings:
  Installed: 304.116-0ubuntu1~xedgers~trusty1
  Candidate: 304.116-0ubuntu1~xedgers~trusty1
  Version table:
 *** 304.116-0ubuntu1~xedgers~trusty1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     304.88-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ devel/main i386 Packages
vindsl@Zuul:~$ 
vindsl@Zuul:~$ apt-cache policy screen-resolution-extra
screen-resolution-extra:
  Installed: 0.16
  Candidate: 0.16
  Version table:
 *** 0.16 0
        500 http://archive.ubuntu.com/ubuntu/ devel/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 

```

Only errors I'm getting now are:  cannot configure 'nvidia-settings' and 'screen-resolution-extra'.

---

### Post by paul_in_london on 2013-11-09
> **VinDSL said:**
> Ah!  That looks better...

```
vindsl@Zuul:~$ apt-cache policy nvidia-304
nvidia-304:
  Installed: 304.116-0ubuntu1~xedgers~trusty1
  Candidate: 304.116-0ubuntu1~xedgers~trusty1
  Version table:
 *** 304.116-0ubuntu1~xedgers~trusty1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     304.88-0ubuntu8 0
        500 http://archive.ubuntu.com/ubuntu/ devel/restricted i386 Packages
vindsl@Zuul:~$ 
vindsl@Zuul:~$ apt-cache policy nvidia-settings
nvidia-settings:
  Installed: 304.116-0ubuntu1~xedgers~trusty1
  Candidate: 304.116-0ubuntu1~xedgers~trusty1
  Version table:
 *** 304.116-0ubuntu1~xedgers~trusty1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     304.88-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ devel/main i386 Packages
vindsl@Zuul:~$ 
vindsl@Zuul:~$ apt-cache policy screen-resolution-extra
screen-resolution-extra:
  Installed: 0.16
  Candidate: 0.16
  Version table:
 *** 0.16 0
        500 http://archive.ubuntu.com/ubuntu/ devel/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 

```

Only errors I'm getting now are:  cannot configure 'nvidia-settings' and 'screen-resolution-extra'.

Hi Vin,

Last night when I booted 3.12 generic I was able to install nvidia 304.116 from xorg-edgers without a hitch (have stayed on the saucy branch for now because the trusty branch is still short of some packages).

I don't bother with nvidia-settings any more because I hardly ever used it anyway and it's not a hard dependency. I also purged screen-resolution-extra recently funnily enough.

The fun and games began when the nvidia module failed to build with my custom kernel. This was something I hadn't tried before. I needed a couple of extra configuration steps I didn't know about before rebuilding the kernel:

```
make prepare
make modules_prepare
```

Then I was finally able to install the nvidia driver with the rebuilt kernel. :)

Cheers,

Paul

---

### Post by VinDSL on 2013-11-10
> **paul_in_london said:**
> I don't bother with nvidia-settings any more because I hardly ever used it anyway and it's not a hard dependency.[...]
Only thing(s) I use it for is setting the 'Digital Vibrance'  and the occasional screenshot...  ;)

DVC:  [http://www.nvidia.com/object/feature_dvc.html](http://www.nvidia.com/object/feature_dvc.html)

---

### Post by cariboo on 2013-11-12
I've just done a fresh install of Lubunty Trusty on a fairly ancient system:

[LIST]
[*]Intel(R) Celeron(R) CPU 2.53GHz 
[*]768MiB Ram
[*]NV44A [GeForce 6200] graphics adapter
[*]80GiB hard drive
[/LIST]

I managed to get nvidia-304 installed from he repositories, with out any problems.

[[IMG]http://i.imgur.com/SFwwKz7l.jpg[/IMG]](http://imgur.com/SFwwKz7)

---

### Post by VinDSL on 2013-11-13
> **cariboo907 said:**
> I managed to get nvidia-304 installed from he repositories, with out any problems.
Sweet!

Have you tried 304.116 yet?  It was worth the wait.

---

### Post by mörgæs on 2013-11-17
Irrelevant posts have been moved to the cafe.
Please keep the discussion on topic.

---

### Post by danielr2 on 2014-03-19
I just had a surprisingly successful encounter with the nVidia 304.116 driver. I have recently acquired a new (old) notebook, HP EliteBook 8730w with Quadro FX 2700M graphics. I have put the Linux Mint 13 (12.04 LTS) HDD from my other notebook (HP nc8430 with Radeon x1600) in the new notebook and intended a fresh install. However, I missed the right moment to choose the boot source and the system booted happily from the HDD of the other notebook. I was able to log in to my account and the system was running flawlessly. Since I had nothing to loose, I tried the "Additional Drivers" tool from the Preference menu. Once loaded, I had the choice to activate the drivers for the nVidia graphics. I picked the "nvidia-331 - NVIDIA binary Xorg driver, kernel modules and VDPAU library (331.20)" and "nvidia-304-updates (304.116)" from the list. 

After the installation, a reboot and running the update manager, I had a fully working system with proper 3D acceleration, about 10 times better glmark2 fps than with the x1600 and good 3D gaming performance for Windows games through Wine. Furthermore, all other hardware of the 8730w was instantly recognised including the newly added docking station and the second monitor (see attached NVIDIA X Server Settings). 

I am not sure if this was just fools luck or Linux Mint 13 is particularly well suited for HP hardware. Needless to say, I will stick with this install for now. However, there is one slight drawback with this setup. On system start I get a black screen instead of the login screen. Since login works nevertheless and everything thereafter runs fine, I haven't yet bothered to find a fix. Any suggestions and comments welcome.

---

### Post by cariboo on 2014-03-20
@danielr2, we are currently discussing Trusty development in this sub-forum, so unfortunately the information you have provided really doesn't help much. Have you tried installing one of the Trusty versions to see if you get the same results?

---

### Post by danielr2 on 2014-03-20
@ cariboo907, sorry, I came across this thread while searching for further info on the nVidia 304.116 driver and didn't pay attention to its exclusive Trusty focus. If my post doesn't help much please delete it.

---

