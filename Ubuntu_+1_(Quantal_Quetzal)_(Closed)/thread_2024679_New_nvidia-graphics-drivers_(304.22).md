---
title: "New nvidia-graphics-drivers (304.22)"
date: 2012-07-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-07-14
The newest (beta) version of nvidia-graphics-drivers (304.22) is available from the xorg-edgers PPA.
That works just fine in QQ.
And yes, it needs the xserver_1.12

---

### Post by paul_in_london on 2012-07-14
> **harry33 said:**
> the newest (beta) version of nvidia-graphics-drivers (304.22) is available from the xorg-edgers ppa.
That works just fine in qq.
And yes, it needs the xserver_1.12

+1

---

### Post by effenberg0x0 on 2012-07-14
As usual, it is also available from NVIdia FTP at download.nvidia.com. I have tested 304.22 x86_64 on 3.5.0-3-generic Ubuntu (with standard repos/packages, no alternate PPAs) and it's working fine for usual desktop, OpenGL, vdpau. No speed diff from previous on gtkperf/glxgears. Flash video is hell, but then again it has always been.

Regards,
Effenberg

---

### Post by dino99 on 2012-07-14
i've read the phoronix comment & the nvidia changelog too: this update has some fixes and new features that will help a lot  :P

---

### Post by markbl on 2012-07-14
Note that 304.22 still exhibits the seg fault abort. :cry:

Aborted on me after 3 hours so unusable and back to nouveau I go. This affects many people with 8800/8600 GT and similar cards. Bug has been in all nvidia versions since at least 295.33.

304.22 also still exhibits the bug where virtual consoles (alt+ctrl+f1-6) do not work. Again they work fine on nouveau.

---

### Post by dino99 on 2012-07-14
> **markbl said:**
> Note that 304.22 still exhibits the seg fault abort. :cry:

Aborted on me after 3 hours so unusable and back to nouveau I go. This affects many people with 8800/8600 GT and similar cards. Bug has been in all nvidia versions since at least 295.33.

304.22 also still exhibits the bug where virtual consoles (alt+ctrl+f1-6) do not work. Again they work fine on nouveau.

my card is a 8500gt and does not get segfault on i386 installation. (but no compiz/unity here)

---

### Post by markbl on 2012-07-14
> **dino99 said:**
> my card is a 8500gt and does not get segfault on i386 installation. (but no compiz/unity here)
Doesn't affect everybody. Affects me with a 8600 GT driving 2 by 1920x1200 screens. I usually use gnome-shell but it also happens on unity (perhaps it only happens in 3D desktops?). Never had any problem with nvidia drivers with this same hardware for years before 12.04, i.e. started around nvidia v295.33. It is [ubuntu bug 973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096) but it affects people on many other linux distributions, not just ubuntu.

It is depressing to see so little comment and action from nvidia about this problem.

---

### Post by effenberg0x0 on 2012-07-14
> **markbl said:**
> Doesn't affect everybody. Affects me with a 8600 GT driving 2 by 1920x1200 screens. I usually use gnome-shell but it also happens on unity (perhaps it only happens in 3D desktops?). Never had any problem with nvidia drivers with this same hardware for years before 12.04, i.e. started around nvidia v295.33. It is [ubuntu bug 973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096) but it affects people on many other linux distributions, not just ubuntu.

It is depressing to see so little comment and action from nvidia about this problem.

Ah, that bug... I think cprofitt was the first to report it after we tried every possible workaround on IRC hours before release week. Back then I had asked some Gods of the Olympus if it wouldn't be better to remove the broken version and revert to latest stable on PP release, just to avoid the huge bug report. But everyone was sure NVidia was gonna fix it in hours. Yeah, well, not likely. 

I'm on a GTS450, Unity 3D, dual monitor 1920x1080. This particular model is not affected.

Regards,
Effenberg

---

### Post by ELD on 2012-07-15
I don't know if anyone will know but the 304 drivers, when they become the next stable version will it go to 306? Just wandering what version Ubuntu 12.10 will have in the repo to use?

---

### Post by SpaceCeph on 2012-07-15
Have a little problem with this driver. All launcher icons disappeared after installing it. I can use the launcher but I can't see the icons. If I point of them it is written what there was and no problems with opening the programs. But the icons are gone...

---

### Post by effenberg0x0 on 2012-07-15
> **SpaceCeph said:**
> Have a little problem with this driver. All launcher icons disappeared after installing it. I can use the launcher but I can't see the icons. If I point of them it is written what there was and no problems with opening the programs. But the icons are gone...

Even after restarting the session?
If so, you should report it on LP mentioning your card model. Unless you are running with non-standard packages (alternative PPAs) or have not dist-upgraded/fully upgraded.

Regards,
Effenberg

---

### Post by SpaceCeph on 2012-07-15
> **effenberg0x0 said:**
> Even after restarting the session?
If so, you should report it on LP mentioning your card model. Unless you are running with non-standard packages (alternative PPAs) or have not dist-upgraded/fully upgraded.

Regards,
Effenberg

It was a fresh install. The first one since alpha 2 which runs without problems. But then I added xorg edges and installed the new driver... 
Ok, I will report it tomorrow, thought it isn't a big problem and easy to solve. 

Regards...

---

### Post by ricotz on 2012-07-16
> **SpaceCeph said:**
> Have a little problem with this driver. All launcher icons disappeared after installing it. I can use the launcher but I can't see the icons. If I point of them it is written what there was and no problems with opening the programs. But the icons are gone...

I actually doubt you are really running nvidia blob, since this issue you are describing is happening with the current mesa git snapshot of xorg-edgers. 
Can be easily checked running: glxinfo | grep "OpenGL "

---

### Post by dino99 on 2012-07-16
this first message logged into .xsession-errors on i386 is:

ERROR: Error parsing configuration file '/home/oem/.nvidia-settings-rc' on
       line 48: '0/XVideoTextureBrightness=0' (Unrecognized attribute name).

---

### Post by t1497f35 on 2012-07-16
> **dino99 said:**
> this first message logged into .xsession-errors on i386 is:

ERROR: Error parsing configuration file '/home/oem/.nvidia-settings-rc' on
       line 48: '0/XVideoTextureBrightness=0' (Unrecognized attribute name).

[It's probably the new expected behavior:]("http://www.nvidia.com/object/linux-display-ia32-304.22-driver.html")
> 
Removed       controls for XVideo attributes from the "X Server XVideo  Settings" page  of the nvidia-settings control panel. XVideo attributes   can be configured in  XVideo player applications, or through utilities such as xvattr.


---

### Post by VMC on 2012-07-16
> **effenberg0x0 said:**
> As usual, it is also available from NVIdia FTP at download.nvidia.com. I have tested 304.22 x86_64 on 3.5.0-3-generic Ubuntu (with standard repos/packages, no alternate PPAs) and it's working fine for usual desktop, OpenGL, vdpau. No speed diff from previous on gtkperf/glxgears. Flash video is hell, but then again it has always been.

Regards,
Effenberg

I also use the nvidia download and not mess with ppa's.

Regarding the flash problems. Someone suggested using a older flash 'so' file instead of the current one. I did that and it worked. Also on utube, I just have to disable the flash using "about"plugin" and now all utube videos work.

---

### Post by effenberg0x0 on 2012-07-16
> **VMC said:**
> I also use the nvidia download and not mess with ppa's.

Regarding the flash problems. Someone suggested using a older flash 'so' file instead of the current one. I did that and it worked. Also on utube, I just have to disable the flash using "about"plugin" and now all utube videos work.

Thanks for the tip. Things get a little more stable (but blueish) with this:
```

[13:40:41] ahsl@AL-DESK01:[/etc/adobe]: cat /etc/adobe/mms.cfg 
EnableLinuxHWVideoDecode=0
OverrideGPUValidation=true

```
Removing this file or changing values from '0' to '1' or from 'true' to 'false' or commenting either line makes it even less stable. 

I'm using this version of libflash:
```

[13:40:46] ahsl@AL-DESK01:[/etc/adobe]: strings $(locate libflashplayer.so) | egrep -i '^FlashPlayer'\{1,\}[0-9_]*'FlashPlayer$'
FlashPlayer_11_2_202_236_FlashPlayer

```

Which version are you using?

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-07-16
Confirmed: Things are not blue with flash version 10.3 and so far it seems like it's more stable. If anyone else is interested, here's what I did:


```

[14:01:39] ahsl@AL-DESK01:[~]: sudo mv /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.so.old
[14:01:40] ahsl@AL-DESK01:[~]: mkdir $HOME/Downloads/flash && cd $HOME/Downloads/flash 
[14:01:40] ahsl@AL-DESK01:[~/Downloads/flash]: wget http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_plugin_debug.tar.gz
[14:01:41] ahsl@AL-DESK01:[~/Downloads/flash]: tar xvzf flashplayer_10_plugin_debug.tar.gz
[14:01:41] ahsl@AL-DESK01:[~/Downloads/flash]: mv libflashplayer.so /usr/lib/flashplugin-installer
[14:01:42] ahsl@AL-DESK01:[~/Downloads/flash]: sudo chmod 775 /usr/lib/flashplugin-installer/libflashplayer.so && sudo chown root:root /usr/lib/flashplugin-installer/libflashplayer.so
[14:01:42] ahsl@AL-DESK01:[~/Downloads/flash]: sudo kill -s KILL $(ps ax | grep chromi | awk 'BEGIN {FS=" "} {print $1}' | tr '\n' ' ')

```
Then restart chromium, select "restore".

Regards,
Effenberg

EDIT: I thought I should add a note to people that eventually land here. Don't be a bash barbarian like me: use softlinks or update-alternatives, close things normally instead of killing them, use normal stuff like ps/pidof at least, like normal people do, etc.

---

### Post by SevenMachines on 2012-07-16
In terms of the flash blue issue with colour swap, disabling hardware acceleration sends my fan into a heat spiral so I've been using a colour swap fix patch for vdpau. 
[https://aur.archlinux.org/packages.php?ID=59181](https://aur.archlinux.org/packages.php?ID=59181)
It may or not be a good idea but it seems fine here

---

### Post by mc4man on 2012-07-16
regarding blue flash - are you all saying the recent libvdpau hasn't fixed this?, does so here both in 12.10 & 12.04 (the 12.10 package is suitable for 12.04
(no blue here in FF, chromium or google-chrome though flash perf in google-chrome stinks

> libvdpau (0.4.1-6ubuntu1) quantal; urgency=low

  * Merge from Debian Unstable (LP: #1010920). Remaining Changes:
    - Drop gcc-multilib and ia32-libs-dev from build-dependencies
    - Drop lib32vdpau1 binary package from debian/control
    - Drop lib32vdpau1.{lintian-overriders,install,symbols,postinst} files
    - Comment out 32-ARCHS in debian/rules so multilib stuff isn't run
    - Mark Debian VCS links XS-Debian

 -- Vibhav Pant <vibhavp@gmail.com>  Fri, 15 Jun 2012 11:20:31 +0100

libvdpau (0.4.1-6) unstable; urgency=low

  [ Maurizio Avogadro ]
  *[COLOR="Blue"] Apply the wise patch supplied by Stephen Warren to fix Adobe Flash
    insanities. [/COLOR] (Closes: #668512)


---

### Post by SevenMachines on 2012-07-16
No, thats the one. Manual patching not necessary now

---

### Post by ELD on 2012-07-18
Does anyone know how often they release these beta drivers?

---

### Post by markbl on 2012-07-18
> **ELD said:**
> Does anyone know how often they release these beta drivers?
Well I first saw the abort problem when I (cleanly) installed Ubuntu 12.04 in late April 2012 having used nvidia for years without issue on the same hardware. I have tried every driver nvidia have released since then and they have all exhibited the segmentation fault within a few hours. That is versions 295.33, 295.40, 295.49, 295.53, 302.07, 302.11, 302.17, and 304.22. Have tried most of those on 3.2 and 3.5 kernels. So that is a release every few weeks on average, although all useless to us with this seg fault problem.

---

### Post by dino99 on 2012-07-18
[http://www.wired.com/wiredenterprise/2012/06/torvalds-nvidia-linux/](http://www.wired.com/wiredenterprise/2012/06/torvalds-nvidia-linux/)
[http://www.nvidia.com/object/nvidia-update.html](http://www.nvidia.com/object/nvidia-update.html)

---

### Post by effenberg0x0 on 2012-07-18
> **ELD said:**
> Does anyone know how often they release these beta drivers?

Hi, this is an interesting question. I have looked at NVidia FTP, hoping to get timestamps for each driver version directory, sort it to csv and plot it so we could get a nice chart, but their FTP is misconfigured (showing wrong year, dates, etc). The only other option I found (although clearly incomplete) is this page: [http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html)

Regards,
Effenberg

---

### Post by VinDSL on 2012-07-18
> **markbl said:**
> [...] I have tried every driver nvidia have released since then and they have all exhibited the segmentation fault within a few hours. That is versions 295.33, 295.40, 295.49, 295.53, 302.07, 302.11, 302.17, and 304.22. Have tried most of those on 3.2 and 3.5 kernels [...]
Interesting!  I've been following this thread.

I don't know what I'm doing wrong, but I haven't had any probs with (current config):
[LIST]
[*]Linux 3.5-rc7-generic i686
[*]nvidia-current 304.22
[*]2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz
[/LIST]
Actually, this machine has never run better -- Adobe Flash and all.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-18-jul-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-jul-2012-1.png")[/INDENT]


But, I'll keep trying...  :D

<< *See sig (below) for specs on this ancient iron* >>

---

### Post by markbl on 2012-07-18
> **VinDSL said:**
> Interesting!
I don't know what I'm doing wrong, but I haven't had any probs ..
So Vin, if it doesn't happen to you then it doesn't happen to anybody?

The xorg seg fault with nvidia driver occurs for people with **some combination** of nvidia graphics, screens, and hardware, across all linux distros. It happens for me with an (old) 8600 GT driving 2 by 1920x1200 screens. I have spent a lot of time on this problem.

On the plus side, I have discovered that the nouveau driver works very well. I've always switched to proprietary nvidia within seconds of a new install but have found that current (well xorg edgers) open/free nouveau runs 3D unity and gnome shell desktops, and games very well, **at least on my** older hardware.

---

### Post by VinDSL on 2012-07-18
> **markbl said:**
> So Vin, if it doesn't happen to you then it doesn't happen to anybody?
Er... I don't know what you mean.

I seek failure.  That's the whole purpose of testing.  Otherwise, why bother?  

Anybody can succeed.  Just use the last stable release.  ZZZZZZZZzzzzzz...

What am I doing wrong?!?!?

---

### Post by effenberg0x0 on 2012-07-19
> **VinDSL said:**
> Er... I don't know what you mean.

I seek failure.  That's the whole purpose of testing.  Otherwise, why bother?  

Anybody can succeed.  Just use the last stable release.  ZZZZZZZZzzzzzz...

What am I doing wrong?!?!?

I wouldn't go as far as "wrong" but you're not using the default DE (according to your screenshot) :) 

I think many people may be seeing compiz+unity-related crashes, unrelated to NVidia/Xorg/Flash etc. Most of my crashes are like that anyway. Maybe you're escaping those.

Regards,
Effenberg

---

### Post by VinDSL on 2012-07-19
> **effenberg0x0 said:**
> I wouldn't go as far as "wrong" but you're not using the default DE (according to your screenshot) :) 

I think many people may be seeing compiz+unity-related crashes, unrelated to NVidia/Xorg/Flash etc. Most of my crashes are like that anyway. Maybe you're escaping those.

Aha!  Yes, you're right.  I'm using LXDE/Openbox, most of the time, on top of Ubu 12.10.

Sadly, Unity/Compiz is such a mess right now, I can't stand to look at her.  Unity is my true love -- LXDE, an infatuation.

Really, it's an aesthetics-thing for me.  I give Unity a try, every day or so, but it's soooo ugly right now, I cannot stand it.

And, every once in a while, Unity jacks up my machine so badly that I need to reboot, e.g. logout Unity/login LXDE doesn't do the job.

Anyway, I think you solved my non-problem, and shed some light on what's happening to others.  ;)

---

### Post by markbl on 2012-07-19
> **effenberg0x0 said:**
> 
I think many people may be seeing compiz+unity-related crashes, unrelated to NVidia/Xorg/Flash etc.
The nvidia xorg segmentation fault (i.e. abort) I have described here has nothing to do with compiz or unity. I mainly see it in gnome shell, my usual desktop, where neither of those are even running. I've had it happen in unity also though. If you search around you will find the same bug happens on many other distros. I have seen it reported over recent months in Arch, Gentoo, and Fedora at least. It is [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096) on ubuntu. Here is the last kern.log record of mine using 304.22:
```

10057.732360] Xorg[1514]: segfault at b4f25000 ip b4948ec0 sp bfb341a0 error 7 in nvidia_drv.so[b4865000+64d000]

```

This is not a compiz or unity bug!

---

### Post by effenberg0x0 on 2012-07-19
> **effenberg0x0 said:**
> I wouldn't go as far as "wrong" but you're not using the default DE (according to your screenshot) :) 

I think many people may be seeing compiz+unity-related crashes, unrelated to NVidia/Xorg/Flash etc. Most of my crashes are like that anyway. Maybe you're escaping those.

Regards,
Effenberg

> **markbl said:**
> The nvidia xorg segmentation fault (i.e. abort) I have described here has nothing to do with compiz or unity. I mainly see it in gnome shell, my usual desktop, where neither of those are even running. I've had it happen in unity also though. If you search around you will find the same bug happens on many other distros. I have seen it reported over recent months in Arch, Gentoo, and Fedora at least. It is [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096) on ubuntu. Here is the last kern.log record of mine using 304.22:
```

10057.732360] Xorg[1514]: segfault at b4f25000 ip b4948ec0 sp bfb341a0 error 7 in nvidia_drv.so[b4865000+64d000]

```

This is not a compiz or unity bug!

Good morning, let me rephrase it then: 

Let me take this opportunity to note that, despite what I just said (that *many people* report bugs incorrrectly), this is not the case for user markbl. Oh no: He clearly points out that the NVidia XOrg segfault he has described in this thread has nothing to do with compiz or unity. He sees it mainly in the Gnome DE, in which Unity or Compiz are not running. He also sees that problem in Unity. He makes it clear that if I were to search around I'd find that the same bug affect other distros, such as Arch, Gentoo, and Fedora at least. He points out that the bug is reported at [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096) on ubuntu. He also managed to catch a segfault on dmesg: 
```

10057.732360] Xorg[1514]: segfault at b4f25000 ip b4948ec0 sp bfb341a0 error 7 in nvidia_drv.so[b4865000+64d000]

```
Therefore, as he emphatically reminds me, and I fully agree, whatever he is seeing there is not a Unity/Compiz bug! For more details, please contact user markbl. I'm sure he will provide you with this information.

Nonetheless, as I said before, many people report compiz-unity-related bugs as NVidia/Xorg/Flash bugs.

Ok, I think now this is a more suitable useless message :)

Thanks,
Effenberg

---

### Post by VinDSL on 2012-07-19
> **effenberg0x0 said:**
> Ok, I think now this is a more suitable useless message :)
I enjoyed it, thus not a *totally* useless message!  :D

---

### Post by ELD on 2012-07-20
Do you guys think that before 12.10 is released we will see some more nvidia driver releases?

---

### Post by Harry33 on 2012-07-20
> **ELD said:**
> Do you guys think that before 12.10 is released we will see some more nvidia driver releases?

Actually this 304.22 driver is a beta release, not a final release, which we will see later.
New driver versions are commnly released once (or sometimes twice) a month.
The 295.59 is the latest stable release ATM.

---

### Post by Bobhuber on 2012-07-20
Did anyone happen to notice that the new driver now supports automatic DKMS updates. No more reinstalling the driver every time you install a new kernel .

---

### Post by Bobhuber on 2012-07-20
> **markbl said:**
> Note that 304.22 still exhibits the seg fault abort. :cry:

Aborted on me after 3 hours so unusable and back to nouveau I go. This affects many people with 8800/8600 GT and similar cards. Bug has been in all nvidia versions since at least 295.33.

304.22 also still exhibits the bug where virtual consoles (alt+ctrl+f1-6) do not work. Again they work fine on nouveau.
Never had a seg fault problem and found that if you put vga=normal in your grub config file it fixes (at least for me) the VT problem.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=normal"

---

### Post by Cheltspy on 2012-07-21
I have got fed up with anything above 295.59, the Overscan  compensation has been removed on all drivers.:icon_frown:

295.59 can be over installed any of the later drivers from root.

---

### Post by ELD on 2012-07-22
> **Bobhuber said:**
> Did anyone happen to notice that the new driver now supports automatic DKMS updates. No more reinstalling the driver every time you install a new kernel .

About time!

---

### Post by denied on 2012-07-23
well im trying this:

sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update

hopeing it will fix my issues with the gtx 675M.

---

