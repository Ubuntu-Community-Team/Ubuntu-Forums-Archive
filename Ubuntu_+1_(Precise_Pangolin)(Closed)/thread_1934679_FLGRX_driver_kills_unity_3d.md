---
title: "FLGRX driver kills unity 3d"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jonasan Cope on 2012-03-02
copy of last post due to icreased problem....

ok so things are worse... my fault i reckon but still... help would be great.

i unistalled the flgrx driver, downloaded the one from the amd site, tried to install but it said that the driver still remained so could not. i googled some purge commands and tried to clean the driver completely, then rebooted.

now i login to my account and the desktop loads without the launcher or title bar, just the desktop.

i can right click and get the appearance settings up, and can load a terminal window but the command to repair i have found through google dont have any effect.

tried to use recovery mode from grub to load in failsafe graphics mode. gets to the menu for selecting boot once or reconfigure and then hangs.

i am stuck. do i need to completly reinstall or is there some way to fix this from the terminal?

thanks

--------

original post -


hey all,

i am now clear on my problem - the graphics driver for my ATI RADEON MOBILITY HD 4330 - that is the proprietary FGLRX (non post-release updates version) kills unity 3d and starts me always is an ubuntu-2d session.

if i uninstall this driver i get unity 3d back using my onboard intel graphics chip - but it struggles. Using windows 7 catalyst control center lets me switch and the card works great but here in ubuntu no. If i run catalyst from the ubuntu launcher i get the following initialization error:

----

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

-----

Also, I cant install the post-release update driver due to a bug that many are affected by in 12.04.

Is this problem anything to do with the fact that my laptop has switchable graphics?

Any experience of this or help would be appreciated? Cheers

---

### Post by danieluseslinux on 2012-03-02
I've always had problems getting the drivers for my AMD/ATI card through Additional Drivers, so I always get the .run file directly from AMD website, chmod it +x and run it via terminal.

---

### Post by Jonasan Cope on 2012-03-02
ok thanks, downloading now from the ati website... fingers crossed...

---

### Post by Jonasan Cope on 2012-03-03
ok so things are worse... my fault i reckon but still... help would be great.

i unistalled the flgrx driver, downloaded the one from the amd site, tried to install but it said that the driver still remained so could not. i googled some purge commands and tried to clean the driver completely, then rebooted.

now i login to my account and the desktop loads without the launcher or title bar, just the desktop.

i can right click and get the appearance settings up, and can load a terminal window but the command to repair i have found through google dont have any effect.

tried to use recovery mode from grub to load in failsafe graphics mode. gets to the menu for selecting boot once or reconfigure and then hangs.

i am stuck.   do i need to completly reinstall or is there some way to fix this from the terminal?

thanks

---

### Post by Jonasan Cope on 2012-03-03
bumped once .... in hope of divine guidance from the collective...

---

### Post by Stinger on 2012-03-03
Ok I'll help you.

First you'll need to purge fglrx.
Use this guide:
[FglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx")

When you have done that, use this guide to install the AMD fglrx driver:
[How To Install The ATI AMD Catalyst 12.1 Driver Under Ubuntu 11.10/11.04]("http://www.upubuntu.com/2012/01/how-to-install-ati-amd-catalyst-121.html")

Should work for precise too (worked for me)
Please remember to do the 'remove old driver' bits in the start of the guide too to remove any remains from your earlier attempts to install the driver.

I tried the jockey driver installer in ubuntu too but had no success with AMD, works fine for Nvidia though.

Last but not least, do yourself a favour, go for a Nvidia card instead, the driver is so much better performance and feature wise.
True, AMD makes the best hardware, but their linux driver leaves room for lot of improvement.
Their windows driver works fine though, no performance issues there.

---

### Post by ventrical on 2012-03-03
I have a 64bit Acer Extnsa with Radeon Xpress1250 and there is just no way that I can get Unity 3D to work. I tried everything , purge, clean , reinstall, frresh install , nomode set .. on and on .. uh ah.. nope .. nada... I was told that is  a kernel/distro regression of some sort. I tired everything on AMDs site... Precise Unity 3D  will just not work in 64bit mode(on that machine).. but it worked great in 32 bit mode.

---

### Post by Jonasan Cope on 2012-03-04
thanks for the help regarding installing the driver. after reinstalling 12.04 yesterday morning I tried to follow the guides. copy and paste exactly, but each time it killed my system, mostly would not even boot to X or even safe graphics mode. Recovery mode left me without a read/writeable hd - so screwed.

simply cannot get the driver to work with 12.04 and my radeon 4330 on a 64bit system. So now I run on my onboard intel chip and wait for support once precise gets a public release.

beta testing it is! and happy I am - unity, with the unity-team ppa including HUD etc... is really really good.

thanks again.

---

### Post by GerMulvey on 2012-03-05
I've had similar:
ati radeon 6790: nomodeset achieves the desktop but can't install via jockey. Didn't try ati driver *.run as I figured ti is likely to be a nightmare from what I read on launchpad.
So I then tried my nvidia 550ti: nomodeset to desktop then driver install via drivers and it then never boots to the desktop, same using nvidia driver.
Seems this one is a head scratcher!

---

### Post by ELD on 2012-03-05
Have they even put out a driver that works with the newest xorg/kernel?

---

### Post by typhoon_tip on 2012-03-05
> **Jonasan Cope said:**
> thanks for the help regarding installing the driver. after reinstalling 12.04 yesterday morning I tried to follow the guides. copy and paste exactly, but each time it killed my system, mostly would not even boot to X or even safe graphics mode. Recovery mode left me without a read/writeable hd - so screwed.

simply cannot get the driver to work with 12.04 and my radeon 4330 on a 64bit system. So now I run on my onboard intel chip and wait for support once precise gets a public release.

beta testing it is! and happy I am - unity, with the unity-team ppa including HUD etc... is really really good.

thanks again.

Please pay attention to this:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

If you are using the x86_64 architecture (64 bit): 1. Install "ia32-libs" before proceeding!
**sudo apt-get install ia32-libs**

... otherwise it doesn't work. The above command will install about 200 MB of libraries.

---

### Post by alphacrucis2 on 2012-03-05
I wouldn't follow any of those guides. When I had AMD graphics, I always installed their driver using the --buildpkg method as per here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Edit. Ok I see the wiki posted by typhoon_tip also recommends the --buildpkg method. Not sure about the ia32-libs part as I never did that.

---

### Post by typhoon_tip on 2012-03-05
> **alphacrucis2 said:**
> I wouldn't follow any of those guides. When I had AMD graphics, I always installed their driver using the --buildpkg method as per here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Edit. Ok I see the wiki posted by typhoon_tip also recommends the --buildpkg method. Not sure about the ia32-libs part as I never did that.

Yeah, NECESSARY :P :P ! Never use the installer, it breaks everything. And if you are unsure, always do a full purge before re-installing. I have installed so many times that I almost remember the entire command sequence. The 32 bit libs are necessary to compile and work correctly.

---

### Post by kurt18947 on 2012-03-05
> **typhoon_tip said:**
> Please pay attention to this:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

If you are using the x86_64 architecture (64 bit): 1. Install "ia32-libs" before proceeding!
**sudo apt-get install ia32-libs**

... otherwise it doesn't work. The above command will install about 200 MB of libraries.

12.04 has discontinued ia32-libs in favor of multiarch, it seems.  Searching for ia-32 in Synaptic brings up nothing.

---

### Post by Gregory Lee on 2012-03-05
> **Jonasan Cope said:**
> 
simply cannot get the driver to work with 12.04 and my radeon 4330 on a 64bit system. 
Since I have a 64 bit AMD system and am running fglrx and Unity 3d, I'm interested in these problems, but I'm having some difficulty understanding what's going on.  The thread title says that fglrx kills unity 3d, but as I read through the thread, it seems that it is the attempt to remove fglrx that causes problems.

But why are you doing that?  I'm sure there's a good reason.  Should I be trying to kill my system, too?  Please help catch a beginner up.
```
# fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6550D
OpenGL version string: 4.1.11251 Compatibility Profile Context

```

---

### Post by alphacrucis2 on 2012-03-05
> **Gregory Lee said:**
> Since I have a 64 bit AMD system and am running fglrx and Unity 3d, I'm interested in these problems, but I'm having some difficulty understanding what's going on.  The thread title says that fglrx kills unity 3d, but as I read through the thread, it seems that it is the attempt to remove fglrx that causes problems.

But why are you doing that?  I'm sure there's a good reason.  Should I be trying to kill my system, too?  Please help catch a beginner up.
```
# fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6550D
OpenGL version string: 4.1.11251 Compatibility Profile Context

```

The reason for purging fglrx is to be able to get a clean install of the latest version of Catalyst/fglrx from the AMD website. It seems that the install process of the new driver is more reliable if the older version is purged first. When you install the new driver, don't do it by just running the installer with defaults. Run it using --buildpkg as per the howto or wiki above. This will create deb packages that you install using dpkg. However, if your system is working fine then no real need to update the latest driver. Stick with what you have if you are unsure. I used to update Catalyst nearly every month as there was a continuing stream of improvements. I did get burned once when AMD released a dud. Had to back it out and reinstall the previous months version.

 It used to be that fglrx would not work at all for most of the testing cycle and you had to wait till near the very end until AMD released an update supporting the newer kernel and or xorg. They seem to be a bit more on the ball with their updates these days.

---

### Post by typhoon_tip on 2012-03-05
The correct procedure for removing the driver in 32 bit mode (ALL commands are necessary !!):
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

64 bit:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

After this sequence, Unity 3D should boot up, unless the open source AMD driver doesn't support your specific card's 2D accelerated OpenGL.

---

