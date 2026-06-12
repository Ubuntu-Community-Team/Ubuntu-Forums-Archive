---
title: "Linux: Finally A Real Fix For Optimus Technology For Notebook Computers"
date: 2016-06-28
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2016-06-28
> **PRIME Synchronization & Double Buffering Land In The X.Org Server**
Phoronix, 28 June 2016

For those making use of DRI PRIME for multi-GPU systems (mainly in the context of iGPU + dGPU notebooks), the xorg-server's PRIME code now has synchronization support and double buffering. 

Alex Goins of NVIDIA has been working on this big PRIME synchronization project for a while now to help reduce tearing in such configurations. That work has gone through many revisions over the months but as of this afternoon it's landed in xserver Git. 

There is the support for PRIME synchronization and double buffering when both drivers support the necessary functions. With this work today are also the modesetting DDX driver changes for being able to support it. NVIDIA is expected to soon release a proprietary driver update to support the needed functionality there too.

[http://www.phoronix.com/scan.php?page=news_item&px=Xorg-PRIME-Sync-Double-Buffer](http://www.phoronix.com/scan.php?page=news_item&px=Xorg-PRIME-Sync-Double-Buffer)

Until now I have been "forced" to use Intel integrated graphics card, **I've been waiting 3 years for this moment!!!**
As much as I know, the kernel-side changes are already merged and released in Linux 4.5, and the nvidia binary driver patch is ready for release.
**The big question: When will this fix ship in Ubuntu, and in what versions of Ubuntu (16.04; 16.10; ...)?**
Big thanks for any info :)

---

### Post by mc4man on 2016-06-28
Can't see it in Ubuntu until 17.04 assuming xorg-xserver 1.19 releases this fall.

---

### Post by pqwoerituytrueiwoq on 2016-06-29
that does not mean you can't use the mainline kernel and the xorg edgers ppa to get it sooner
i think there is a nvidia driver ppa now, that may work instead of the xorg edgers ppa

---

### Post by mc4man on 2016-06-29
> **pqwoerituytrueiwoq said:**
> that does not mean you can't use the mainline kernel and the xorg edgers ppa to get it sooner
i think there is a nvidia driver ppa now, that may work instead of the xorg edgers ppa
That could be an option.  Though  atm the ppa seems inactive. (Xorg ppa

---

### Post by DuckHook on 2016-06-29
> **pqwoerituytrueiwoq said:**
> ...there is a nvidia driver ppa now, that may work instead of the xorg edgers ppa[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

For the benefit of general users, instructions [here]("http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html").

---

### Post by aljosa2 on 2016-06-30
Thanks all for participating in this topic.
> mc4man:
Can't see it in Ubuntu until 17.04 assuming xorg-xserver 1.19 releases this fall.

As we are talking here about quite a long period of time, in the "near" future I would rather use Mir then X.Org Server :) :) :)

> pqwoerituytrueiwoq:
that does not mean you can't use the mainline kernel and the xorg edgers ppa to get it sooner
i think there is a nvidia driver ppa now, that may work instead of the xorg edgers ppa

Currently I'm using Intel integrated graphics card, fortunately I can disable Nvidia in BIOS settings.
I am capable to update kernel to the latest mainline version. I am also capable to install the latest Nvidia driver *(assuming its compatibility with the mainline kernel version)* via new ppa.
I'm using Oibaf ppa for the latest Mesa/X.Org drivers. How can I know when will Oibaf include the mentioned optimus technology fix within their repository?

---

### Post by mc4man on 2016-06-30
> **aljosa2 said:**
> Thanks all for participating in this topic.


As we are talking here about quite a long period of time, in the "near" future I would rather use Mir then X.Org Server :) :) :)

I'm using Oibaf ppa for the latest Mesa/X.Org drivers. How can I know when will Oibaf include the mentioned optimus technology fix within their repository?
Ask him via Lp email. the commits are to the xorg-xserver source, not too sure he currently builds that.., whether the modules he has draw from no idea..

---

### Post by aljosa2 on 2016-07-01
> **mc4man said:**
> Ask him via Lp email. the commits are to the xorg-xserver source, not too sure he currently builds that.., whether the modules he has draw from no idea..

Thanks for your reply, could you please explain me the same thing for xorg edgers ppa?

---

### Post by aljosa2 on 2016-12-05
**X.Org Server 1.19 Officially Released With A Year's Worth Of Improvements**
*15 November 2016, Phoronix*

X.Org Server 1.19 features a few big features including threaded input support that had been in development for several years (more details), PRIME synchronization support as spearheaded by NVIDIA, XWayland pointer confinement and warping and other XWayland improvements, modesetting driver improvements, Windows DRI extension support, GLAMOR improvements, and more. _PRIME synchronization is big for Optimus/multi-GPU users_, and the other improvements all around are nice. There are also many bug-fixes with X.Org Server 1.19

**NVIDIA 375.20 Adds X.Org Server 1.19 Support**
[I]18 November 2016

[/I]Come on Zesty, let's rock :) :) :)

---

### Post by rogervn on 2016-12-07
Is there any repos with xorg 1.19 packages for Ubuntu 16.10?

---

### Post by mc4man on 2016-12-08
> **Rogrio_Vinhal_Nunes said:**
> Is there any repos with xorg 1.19 packages for Ubuntu 16.10?

No & there never will be, too much work for a 9 month release. 16.04 will probably get next summer & there may be some earlier options.

---

### Post by bart.vanaudenhove on 2016-12-11
A quick question: I'm not a computer expert, just an average Ubuntu 16.04 user with an Optimus HP laptop (Intel / Nvidia GeForce GT 650M). I don't want anything cutting edge or risky, but I would love to use my Nvidia GPU (I use Blender).
Would it be advisable for me to install nvidia-370 in Ubuntu 16.04 from the [Proprietary GPU Drivers PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") so I can use my Nvidia GPU, or is there a substantial risk of breaking my system if I do so?

Also, it says on the Proprietary GPU Drivers PPA page > For GeForce 6 and 7 series GPUs use `nvidia-304` (304.132)
 which probably applies to my card (?), but Prime doesn't switch my video cards with that one... Does that mean I should stick with nvidia-304 anyway, and not upgrade to anything more recent?

What would you advise in my case?

---

### Post by aljosa2 on 2016-12-11
You would like to use your Nvidia GPU on your Optimus laptop? Don't even try - without X.Org Server 1.19 it isn't worth it!

---

### Post by bart.vanaudenhove on 2016-12-11
> **aljosa2 said:**
> You would like to use your Nvidia GPU on your Optimus laptop? Don't even try - without X.Org Server 1.19 it isn't worth it!
So to use X.Org Server 1.19 I would have to enable the [x-org edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa") and update from there, is that correct? And how experimental/risky is that?

---

### Post by dino99 on 2016-12-11
Hello bart

xorg 1.19 is only one step to fix that problem, and as said above, this will not be uploaded until 17.10 release.
but if you grab info on the net you can find some tweaks, like [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1559576/comments/96](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1559576/comments/96)

---

### Post by mc4man on 2016-12-11
> **bart.vanaudenhove said:**
> So to use X.Org Server 1.19 I would have to enable the [x-org edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa") and update from there, is that correct? And how experimental/risky is that?
Of no value in this case as changes relating to prime are in the xserver-xorg-core source package  & no ppa offers that package nor likely to. (possible but would require providing all other packages that would break on new video abi

---

### Post by bart.vanaudenhove on 2016-12-11
Thanks for the info dino99.

I think I'll better wait until something more official comes along then :)

---

### Post by mc4man on 2016-12-11
> **bart.vanaudenhove said:**
> A quick question: I'm not a computer expert, just an average Ubuntu 16.04 user with an Optimus HP laptop (Intel / Nvidia GeForce GT 650M). I don't want anything cutting edge or risky, but I would love to use my Nvidia GPU (I use Blender).
Would it be advisable for me to install nvidia-370 in Ubuntu 16.04 from the [Proprietary GPU Drivers PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") so I can use my Nvidia GPU, or is there a substantial risk of breaking my system if I do so?

Also, it says on the Proprietary GPU Drivers PPA page 
 which probably applies to my card (?), but Prime doesn't switch my video cards with that one... Does that mean I should stick with nvidia-304 anyway, and not upgrade to anything more recent?

What would you advise in my case?
The 304 drivers are for older cards & don't support nvidia-prime so Not for your card. Use anything over 331. As long as you don't mind the lack of any vsync they would work ok with your current hardware.

---

### Post by bart.vanaudenhove on 2016-12-11
> **mc4man said:**
> The 304 drivers are for older cards & don't support nvidia-prime so Not for your card. Use anything over 331. As long as you don't mind the lack of any vsync they would work ok with your current hardware.

OK,that's interesting to know, thanks. However, there's no driver out there that supports nvidia-prime for my card it seems. I mean, I can install nvidia-prime and "use" it, but my graphic card doesn't switch. I'm stuck with the Intel card. (See also [this question of mine]("https://ubuntuforums.org/showthread.php?t=2345327") with more details).

---

### Post by dino99 on 2016-12-11
> **aljosa2 said:**
> _*22 November 2016*_
Fedora 25 ships with X.Org Server 1.19

Ubuntu 17.04 will be released on *_23 April 2017_*.



**This must be a bad joke dino99.**

Nope, read again #11 & #16 posts  ;)

---

### Post by aljosa2 on 2016-12-11
> **Rogrio_Vinhal_Nunes said:**
> Is there any repos with xorg 1.19 packages for Ubuntu 16.10?
> **mc4man said:**
> No & there never will be, too much work for a 9 month release. 16.04 will probably get next summer & there may be some earlier options.

I totally agree with that :)
Pointrelease Ubuntu 16.04.2 will be released on 19 January 2017. It will contain all improvements from Ubuntu 16.10. It is my understanding that on 23 April 2017 Ubuntu 17.04 will ship with X.Org Server 1.19, and later during the summer all the things from 17.04 will appear in Ubuntu Pointrelease 16.04.3.

---

### Post by aljosa2 on 2016-12-14
_*14 December 2016*_
In addition to NVIDIA updating their legacy Linux drivers today (340.101 and 304.134 = **xorg-server 1.19 support**), they have released a new build in their 375 driver series (375.26).

[http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-Legacy-Server-1.19](http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-Legacy-Server-1.19)
[http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-375.26-Released](http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-375.26-Released)

---

### Post by vikram91 on 2016-12-21
I see some manual installation instructions [here]("http://igor-zivkovic.from.hr/BLFS/x/xorg-server.html") for xorg-server 1.19.
Is anybody courageous enough to attempt? 
There HAS to be one of THOSE guys right? Or they are already trying to get it to work? :p

Edit: Also just came across this thread and people solving screen tearing issue: [https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/1](https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/1)

---

### Post by mc4man on 2016-12-23
> **vikram91 said:**
> I see some manual installation instructions [here]("http://igor-zivkovic.from.hr/BLFS/x/xorg-server.html") for xorg-server 1.19.
Is anybody courageous enough to attempt? 
There HAS to be one of THOSE guys right? Or they are already trying to get it to work? :p

Edit: Also just came across this thread and people solving screen tearing issue: [https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/1](https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/1)
For Ubuntu it's not that simple, there is xmir & nvidia-prime, ect. A quick look here on 16.04 allowed 1.19 to be installed, (packaged it)  & works fine with Intel drivers. While nvidia-375 would install it doesn't work, i.e. a login loop. Can't quite figure what the issue is as all the logs look ok. There's just no GLX renderer when switching to nvidia. Most likely I'll not be able to figure out the solution.

So best bet is to wait until Ubuntu gets 1.19 going. If it's not in by end of Jan. then 17.04 may not get it..

(- in screen 1 shows nvidia not good to go, scr. 2 intel is fine whether using Intel driver (shown) or the default of modesetting

---

### Post by aljosa2 on 2016-12-24
Hi guys,
after years and years, **I finally won a battle against Optimus technology**. I got a new laptop. It's a **Non-Optimus laptop** / without integrated graphic. 

*ASUS G752VS-GC063D-CST256*
*17.3" FHD LED 1920x1080, Intel Core i7-6700HQ (3.50Ghz), 16GB DDR4, 256GB M.2 SSD+1TB HDD 7200rpm, DVDRW-DL, Nvidia GTX1070 8GB GDDR5, Wifi 802.11ac+Bluetooth 4.1 (Dual band) 2*2, Gb LAN, HDMI, mDP, Intel WiDi, USB3.0 x4, USB3.1-Type C(Gen2) with Thunderbolt, HD webcam, Illuminated KB, no OS.*

**Unfortunately, situation with Ubuntu 16.04/16.10/17.04 is very bad**, there are many malfunctions. Among other things, I have problems with AC adapter/battery, Fn keys and touchpad doesn't work, it is hard even to try 16.10 and 17.04 because of missing mouse pointer (solvable if one manage to install Nvidia drivers),...

So **I was forced to install Windows 10** on 125GB of NVMe - everything works perfectly and very fast. For now, the other 125GB of space is empty. After the New Year's holidays, I will start a new thread - hoping that until April Zesty can become more compatible with my ASUS G752VS :)

---

### Post by hectorsales on 2017-01-01
Hi, here my setup for those who prefer an "apt" based flavor, debian "testing" (stretch),Ubuntu is based on debian unstable, does have xorg 1.19.

**Initial Requirements**

**Kernel:** 4.8.0-2-amd64
**Xorg:** 1.19.3
**Nvidia Driver:** 375.26

[SIZE=3]
**Step 1: **I followed the instructions from the xrandr guide from the latest driver (375.26)[/SIZE]

**link:** [URL="http://us.download.nvidia.com/XFree86/Linux-x86_64/375.26/README/randr14.html"]http://us.download.nvidia.com/XFree86/Linux-x86_64/375.26/README/randr14.html
[/URL]
```
/etc/X11/xorg.conf

```

> Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID  "PCI:0:2:0"
  **  Option "AccelMethod" "none"**
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Some versions of the **&#8220;modesetting&#8221;** driver try to load a sub-module called &#8220;glamor&#8221;, which conflicts with the NVIDIA GLX implementation. Please ensure that the **libglamoregl.so X** module is not installed.As my xorg server package includes the glamor driver, I added the option** "AccelMethod" "none"** for the Intel driver.

[[IMG]http://i40.photobucket.com/albums/e218/hectorvicentesales/hector%20%20bash%20%20Konsole%20-3-_014_zpsygjr44vf.png[/IMG]]("http://s40.photobucket.com/user/hectorvicentesales/media/hector%20%20bash%20%20Konsole%20-3-_014_zpsygjr44vf.png.html")

[[IMG]http://i40.photobucket.com/albums/e218/hectorvicentesales/Seleccin_013_zpshi1trces.png[/IMG]]("http://s40.photobucket.com/user/hectorvicentesales/media/Seleccin_013_zpshi1trces.png.html")


[B]
[SIZE=3]Step 2:Added the xrandr lines to SDDM config
[/SIZE][/B]

```
/usr/share/sddm/scripts/Xsetup
```

> xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto
xrandr --dpi 96


**link:** [https://wiki.archlinux.org/index.php/NVIDIA_Optimus#SDDM](https://wiki.archlinux.org/index.php/NVIDIA_Optimus#SDDM)

[[IMG]http://i40.photobucket.com/albums/e218/hectorvicentesales/hector%20%20bash%20%20Konsole%20-3-_016_zpsjpq2bw9h.png[/IMG]]("http://s40.photobucket.com/user/hectorvicentesales/media/hector%20%20bash%20%20Konsole%20-3-_016_zpsjpq2bw9h.png.html")


[B][SIZE=3]Step 3:Added on the menu grub the option : [/SIZE]nvidia-drm.modeset=1
[/B]
```
/etc/default/grub
```

> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet **nvidia-drm.modeset=1** acpi_osi="

.
[[IMG]http://i40.photobucket.com/albums/e218/hectorvicentesales/Seleccin_018_zpsnouu7dun.png[/IMG]]("http://s40.photobucket.com/user/hectorvicentesales/media/Seleccin_018_zpsnouu7dun.png.html")

```
sudo update-grub2
```

.after..**reboot**
[B]
Result: [/B]Now the X server starts successfully and I can see two xrandr providers:

```
hector:~$ xrandr --listproviders
```

> Providers: number : 2
Provider 0: id: 0x204 cap: 0x1, Source Output crtcs: 0 outputs: 0 associated providers: 1 name:NVIDIA-0
Provider 1: id: 0x45 cap: 0x2, Sink Output crtcs: 3 outputs: 3 associated providers: 1 name:modesetting

if synchronization is being used but is not desired, it can be disabled with:
```

$ xrandr --output 'eDP-1-1' --set 'PRIME Synchronization' '0'
```

and re-enabled with:
```

$ xrandr --output 'eDP-1-1' --set 'PRIME Synchronization' '1'
```

You can check if the NVIDIA graphics are being used by installing **mesa-demos **and running:

```
hector:~$  glxinfo | grep NVIDIA
```

> server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL core profile version string: 4.5.0 NVIDIA 375.26
OpenGL core profile shading language version string: 4.50 NVIDIA
OpenGL version string: 4.5.0 NVIDIA 375.26
OpenGL shading language version string: 4.50 NVIDIA
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 375.26

[[IMG]http://i40.photobucket.com/albums/e218/hectorvicentesales/Seleccin_019_zpssmz9vuln.png[/IMG]]("http://s40.photobucket.com/user/hectorvicentesales/media/Seleccin_019_zpssmz9vuln.png.html")

[[IMG]http://i40.photobucket.com/albums/e218/hectorvicentesales/hector%20%20bash%20%20Konsole%20-3-_020_zpskc2i6bgy.png[/IMG]]("http://s40.photobucket.com/user/hectorvicentesales/media/hector%20%20bash%20%20Konsole%20-3-_020_zpskc2i6bgy.png.html")

[IMG]http://i40.photobucket.com/albums/e218/hectorvicentesales/hector%20%20bash%20%20Konsole%20-3-_021_zpscuhjxfgc.png[/IMG]



**Note 1:** Ubuntu, Canonical provides a set of scripts enabled by the  &#8216;nvidia-prime&#8217; package that allow you to easily switch PRIME on and off  using an added menu in &#8216;nvidia-settings&#8217;, but these scripts are neither  provided nor officially supported by NVIDIA

[B]Note 2: On my laptop i have installed also Ubuntu 16.04 and Debian Testing (Plasma Desktop). The purpose of this tutorial was to show that synchronization works on Linux, (I hope Ubuntu 17.04 can have X. Org 1.19).Do not forget that Ubuntu is based on Debian  Unstable..

[/B]
[U][B]
Links
[/B][/U][URL="https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchro"]
https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchro[/URL]
[URL="http://us.download.nvidia.com/XFree86/Linux-x86_64/375.26/README/randr14.html"]http://us.download.nvidia.com/XFree86/Linux-x86_64/375.26/README/randr14.html
[/URL][https://wiki.archlinux.org/index.php/NVIDIA_Optimus#SDDM](https://wiki.archlinux.org/index.php/NVIDIA_Optimus#SDDM)

---

### Post by aljosa2 on 2017-01-12
In case they waited for the first minor release after a major release, here it is:
**"X.Org Server 1.19.1 Released"**
*[http://www.phoronix.com/scan.php?page=news_item&px=Xorg-Server-1.19.1-Released](http://www.phoronix.com/scan.php?page=news_item&px=Xorg-Server-1.19.1-Released)*

---

### Post by elbuglione on 2017-01-24
> **aljosa2 said:**
> Hi guys,
after years and years, **I finally won a battle against Optimus technology**. I got a new laptop. It's a **Non-Optimus laptop** / without integrated graphic. 

*ASUS G752VS-GC063D-CST256*
*17.3" FHD LED 1920x1080, Intel Core i7-6700HQ (3.50Ghz), 16GB DDR4, 256GB M.2 SSD+1TB HDD 7200rpm, DVDRW-DL, Nvidia GTX1070 8GB GDDR5, Wifi 802.11ac+Bluetooth 4.1 (Dual band) 2*2, Gb LAN, HDMI, mDP, Intel WiDi, USB3.0 x4, USB3.1-Type C(Gen2) with Thunderbolt, HD webcam, Illuminated KB, no OS.*

**Unfortunately, situation with Ubuntu 16.04/16.10/17.04 is very bad**, there are many malfunctions. Among other things, I have problems with AC adapter/battery, Fn keys and touchpad doesn't work, it is hard even to try 16.10 and 17.04 because of missing mouse pointer (solvable if one manage to install Nvidia drivers),...

So **I was forced to install Windows 10** on 125GB of NVMe - everything works perfectly and very fast. For now, the other 125GB of space is empty. After the New Year's holidays, I will start a new thread - hoping that until April Zesty can become more compatible with my ASUS G752VS :)

ASUS is dead for a pinguins lovers...
just buy a Dell/Alienware or System76 Notebook with Ubuntu pre-installed.

---

### Post by mc4man on 2017-01-28
It would appear that it's not going to show this cycle, maybe next one. Only really matters in regards to 16.04 as it could push back another 6 months (or maybe it never comes to 16.04..

Do have it going on a 16.04 install here & no change in regards to tearing when using nvidia-prime. Could be my fault or could be nvidia-prime needs additional to realize the changes..

```
$ inxi -G -S
System:    Host: doug-Lenovo-IdeaPad-Y510P Kernel: 4.9.0-11-generic x86_64 (64 bit)
           Desktop: Unity 7.5.0  Distro: Ubuntu 16.04 xenial
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK107M [GeForce GT 755M]
           Display Server: X.Org 1.19.0 driver: nvidia
           Resolution: 1920x1080@59.91hz
           GLX Renderer: GeForce GT 755M/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 375.26
```

(- no big deal as there is a  method to remove all tearing when using  nvidia thru nvidia-prime in 16.04 . Somewhat convoluted but quite effective.

---

### Post by tjaalton on 2017-02-06
> **mc4man said:**
> It would appear that it's not going to show this cycle, maybe next one. Only really matters in regards to 16.04 as it could push back another 6 months (or maybe it never comes to 16.04...

If you mean that zesty still doesn't have 1.19.x then it's only because XMir hasn't been ported yet. It's still WIP last I heard, and this can still be pushed post-FF so nothing is "final" yet.

---

### Post by aljosa2 on 2017-02-06
> **tjaalton said:**
> If you mean that zesty still doesn't have 1.19.x then it's only because XMir hasn't been ported yet. It's still WIP last I heard, and this can still be pushed post-FF so nothing is "final" yet.
This is really good news :)

---

### Post by mc4man on 2017-02-09
> **tjaalton said:**
> If you mean that zesty still doesn't have 1.19.x then it's only because XMir hasn't been ported yet. It's still WIP last I heard, and this can still be pushed post-FF so nothing is "final" yet.
Well then that may be a good deal, hopefully before upload/release it's tested on optimus hardware in an ubuntu session for vsync with nvidia drivers via nvidia-prime.

---

### Post by aljosa2 on 2017-03-03
*2 March 2017*
**X.Org Server 1.19.2 Released With Numerous Fixes**
*[http://www.phoronix.com/scan.php?page=news_item&px=X.Org-Server-1.19.2](http://www.phoronix.com/scan.php?page=news_item&px=X.Org-Server-1.19.2)*
Users are encouraged to update to this latest point release.

---

### Post by aljosa2 on 2017-03-10
*10 March 2017:*
**X.Org Server 1.19.2 will be coming to Ubuntu 17.04 and it should officially land in the archive next week.**
Mesa 17.0.1 is also going to be landing as another big update over Mesa 13.0 currently found in Ubuntu 17.04.
*[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.04-X119-Mesa-1701](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.04-X119-Mesa-1701)*

---

### Post by mc4man on 2017-03-11
A staging ppa here - 
[https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging](https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging)

To warn; at least here the above does not work, just boots to low graphic's screen on haswell, on sandybridge doesn't even make it that far, just hangs after fs check

Bug reports go here - [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1671799](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1671799)

edit: If I install nvidia drivers then can boot up to ubuntu session, after that switching to intel works.
At least here vsync (no tearing) with nvidia drivers via nvidia-prime is Not fixed, same as I saw using new xserver in 16.04

---

### Post by aljosa2 on 2017-03-15
*15 March 2017*
**X.Org Server 1.19.3 Released**
[http://www.phoronix.com/scan.php?page=news_item&px=Xorg-Server-1.19.3](http://www.phoronix.com/scan.php?page=news_item&px=Xorg-Server-1.19.3)

---

### Post by fthx on 2017-04-03
Does anybody succeed to launch an application dynamically with Nvidia proprietary driver while using iGPU, as Windows does ?

I'm lost in all that Nvidia stuff :
[https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization](https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization)

I'm running GNOME, I can perfectly right-click on an app to launch it with dGPU, but only using Nouveau driver (and I get somewhat poor performance vs Intel with my computer).
Can I manage to do the same thing running Nvidia proprietary ?

---

### Post by mc4man on 2017-04-03
> **fthx said:**
> Does anybody succeed to launch an application dynamically with Nvidia proprietary driver while using iGPU, as Windows does ?
No, & likely never happen in Linux. From your link, 


> NVIDIA has no plans to support PRIME render offload at this time.
Not sure what Gnome does, sounds like a variation on bumblebee. Ubuntu features nvidia-prime which gives a switchable login of either gpu full time (for rendering, Intel always presents to the display

---

### Post by aljosa2 on 2017-04-05
*5 April 2017,*
this is the big news every Ubuntu user out there wanted to hear, so there you have it:

[B][[SIZE=5]X.Org Server 1.19 Finally Lands in Ubuntu 17.04 (Zesty Zapus)[/SIZE]]("http://news.softpedia.com/news/x-org-server-1-19-finally-lands-in-ubuntu-17-04-zesty-zapus-for-better-gaming-514579.shtml")

[/B]*Mesa 17.0.3 is not yet available in Ubuntu 17.04, but it should come before the operating system's final release on April 13, 2017.*

---

### Post by rogervn on 2017-04-07
So, I just upgraded to 17.04 with Xorg 1.19.3 and nvidia 375.xx drivers. By default, Ubuntu installed a modprobe.d file to set drm modeset = 0 for the nvidia kernel module and that seem to prevent Prime Synchronization to work.

I tried to change the modeset to 1 so I could finally try the synchronization configuration, but that froze the system hard as long as lightdm booted. I installed gnome with gdm3 and I could get to gdm3 and try to login to gnome with no avail. But after a few tries (without changing anything) it just logged in, but prime synchronization was off for both the laptop screen as my TV. I did the "modprobe -v nvidia-drm" to check the modeset and it was 1, but whenever I tried to set the Prime Synchronization via xrandr, the screen went black for a sec and came back, but xrandr --verbose still displayed Prime Synchronization off.

Is there any problem with the nvidia driver in Ubuntu so the drm modeset gives this much problems? Why didn't Prime Synchronization work?

I have a Sager np9130 with a i7 3630qm and a GT 670M card.

---

### Post by mc4man on 2017-04-07
> **Rogrio_Vinhal_Nunes said:**
> So, I just upgraded to 17.04 with Xorg 1.19.3 and nvidia 375.xx drivers. By default, Ubuntu installed a modprobe.d file to set drm modeset = 0 for the nvidia kernel module and that seem to prevent Prime Synchronization to work.

I tried to change the modeset to 1 so I could finally try the synchronization configuration, but that froze the system hard as long as lightdm booted. I installed gnome with gdm3 and I could get to gdm3 and try to login to gnome with no avail. But after a few tries (without changing anything) it just logged in, but prime synchronization was off for both the laptop screen as my TV. I did the "modprobe -v nvidia-drm" to check the modeset and it was 1, but whenever I tried to set the Prime Synchronization via xrandr, the screen went black for a sec and came back, but xrandr --verbose still displayed Prime Synchronization off.

Is there any problem with the nvidia driver in Ubuntu so the drm modeset gives this much problems? Why didn't Prime Synchronization work?

I have a Sager np9130 with a i7 3630qm and a GT 670M card.
Other than 1 user 'reporting' it works with his thinkpad (quadro gpu, unknown bios settings, etc) it just doesn't work in Ubuntu, period**.**
tracking bug, chime in if inclined as generally being ignored by Ubuntu..
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1674304](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1674304)

---

### Post by rogervn on 2017-04-08
Just posted there a well. They didn't seen to notice the option to force modeset to 0 in the modprobe.d file.

---

### Post by ^83%u#@^ on 2017-04-08
Does Ubuntu 17.04 with 4.10 work with this? Or we need newest kernel installed?

---

### Post by rogervn on 2017-04-11
> **user337 said:**
> Does Ubuntu 17.04 with 4.10 work with this? Or we need newest kernel installed?

On the nvidia forums they said that the kernel needed was 4.5 onwards, so I think 4.10 should be fine.

---

### Post by mc4man on 2017-05-03
In 17.10 Prime Synchronization works in UbuntuGnome as one can enable nvidia_drm.modeset. Seen here - 
 > $ sudo cat /sys/module/nvidia_drm/parameters/modeset
[sudo] password for doug: 
Y

xrandr --verbose
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+0 (0x46) normal (normal left inverted right x axis y axis) 345mm x 194mm
	Identifier: 0x42
	Timestamp:  21140
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1 2
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	_MUTTER_PRESENTATION_OUTPUT: 0 
	EDID: 
		00ffffffffffff0030e4d90200000000
		00150103802313780a15d59e59509826
		0e505400000001010101010101010101
		0101010101017e3680b070381f403020
		350059c2100000190000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fe
		004c503135365746312d544c4232004b
	PRIME Synchronization: [COLOR="#0000CD"]1 [/COLOR]
		supported: 0, 1 

However in 17.10 Ubuntu nvidia_drm.modeset can never be enabled so no Prime Synchronization as here, same machine - 
> sudo cat /sys/module/nvidia_drm/parameters/modeset
[sudo] password for doug: 
N

$ xrandr --verbose
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+0 (0x46) normal (normal left inverted right x axis y axis) 345mm x 194mm
	Identifier: 0x42
	Timestamp:  12578
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1 2
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID: 
		00ffffffffffff0030e4d90200000000
		00150103802313780a15d59e59509826
		0e505400000001010101010101010101
		0101010101017e3680b070381f403020
		350059c2100000190000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fe
		004c503135365746312d544c4232004b
	PRIME Synchronization: [COLOR="#FF0000"]0 [/COLOR]
		supported: 0, 1

What's the diff?, not sure. Most obvious is gdm vs. lightdm. Will try next in 16.04 UbuntuGnome by adding 17.10 kernel & upgrading xserver to the 19.x version.
Best test would be to use gdm in a ubuntu session with nvidia drivers but haven't figured how to get that combo to get to the greeter let alone the desktop...( just black screens

---

### Post by aljosa2 on 2017-05-10
There are two new Nvidia drivers within Graphics Drivers Team PPA: 375.66 and 381.22.
Has anyone tried if they are compatible with kernel 4.11?

---

### Post by mc4man on 2017-05-11
> **mc4man said:**
> In 17.10 Prime Synchronization works in UbuntuGnome as one can enable nvidia_drm.modeset. Seen here - 
 

However in 17.10 Ubuntu nvidia_drm.modeset can never be enabled so no Prime Synchronization as here, same machine - 


What's the diff?, not sure. Most obvious is gdm vs. lightdm. Will try next in 16.04 UbuntuGnome by adding 17.10 kernel & upgrading xserver to the 19.x version.
Best test would be to use gdm in a ubuntu session with nvidia drivers but haven't figured how to get that combo to get to the greeter let alone the desktop...( just black screens

Lasted about a week or so. Due to unintended-upgrades no clue as to what broke it, no longer really care..

---

