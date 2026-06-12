---
title: "how many people have page tear?"
date: 2009-12-06
forum: The Cafe
---

### Post by nerdy_kid on 2009-12-06
was wondering how many people are bugged by this; i have an NVIDIA and have set up a set of workarounds to fully get rid of it....

---

### Post by phrostbyte on 2009-12-07
Do you mean video tearing with Flash? I used to. But I got a new computer that pretty much brute forces it way out of video tearing. Flash still could suck less though. I won't mind Adobe, I promise. :)

---

### Post by Uncle Spellbinder on 2009-12-07
If you're talking flash and video tearing or jerky playback/lines. I had the same issue. Do you have desktop effects enabled? Seems to be an issue with Compiz and video playback.

What I did was install the 190 nVidia driver using this PPA repo:

```
#### Nvidia Vdpau Team PPA
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
``` 

[[IMG]http://content.imagesocket.com/thumbs/video_nvidia18d5.png[/IMG]](http://imagesocket.com/view/video_nvidia18d5.png) 

Once the 190 driver was installed, rebooted and did the following...

* Open nVidia settings: under "Xserver Xvideo Settings", make sure "Sync to VBlank" is checked. Do the same for "OpenGL Settings".

* Open CompizConfig Settings Manager: Under *General > General Options > Display Settings*, make sure to check "Sync To VBlank"

* Reboot.

Worked wonders for me. All video (avi/divx/mkv as well as online flash)  has been free of jerky playback/lines/flicker.

---

### Post by Crunchy the Headcrab on 2009-12-07
I have an NVIDIA 9800GTM and I haven't noticed screen tear ever.  I just use the default driver from the restricted module/driver tool.  I think it's 185.something.

---

### Post by Exodist on 2009-12-07
I do when using Xinerama since it doesnt have VSync currently working with that.

---

### Post by Psumi on 2009-12-07
> **Uncle Spellbinder said:**
> If you're talking flash and video tearing or jerky playback/lines. I had the same issue. Do you have desktop effects enabled? Seems to be an issue with Compiz and video playback.

What I did was install the 190 nVidia driver using this PPA repo:

```
#### Nvidia Vdpau Team PPA
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
``` 

[[IMG]http://content.imagesocket.com/thumbs/video_nvidia18d5.png[/IMG]](http://imagesocket.com/view/video_nvidia18d5.png) 

Once the 190 driver was installed, rebooted and did the following...

* Open nVidia settings: under "Xserver Xvideo Settings", make sure "Sync to VBlank" is checked. Do the same for "OpenGL Settings".

* Open CompizConfig Settings Manager: Under *General > General Options > Display Settings*, make sure to check "Sync To VBlank"

* Reboot.

Worked wonders for me. All video (avi/divx/mkv as well as online flash)  has been free of jerky playback/lines/flicker.

Sadly, it still flashes from time to time on my nvidia GTS 250, even without desktop effects, etc. Not to mention, recording the desktop also does the same.

---

### Post by handy on 2009-12-07
I get it when watching various types of movies when using the closed,  ATi catalyst drivers.

When I use the open-source drivers, the 2D is faultless, video plays perfectly & everything happens near instantaneously, but the 3D lags.  

Thankfully the ATi open-source 3D problem is in the process of being remedied. :)

---

### Post by nerdy_kid on 2009-12-07
i personally am allergic to page tearing (i use projectm a lot, and seeing a freaking page tear ruins the whole thing), so i did some serious digging to fix mine:

 it turned out on my pc (i was using the 180 drivers, am using the 190 but no change) that the settings i set in nvidia-settings were not applied unless i ran either nvidia-settings or nvidia-settings -l.  So i set it to autostart on login. But compiz/kwin started before nvidia-settings, which means i had too restart my window manager to apply the Sync to VBlank option.  So i ended up replacing the kwin and compiz executibles with scripts that start nvidia-settings -l then the window manager.

kinda cheesy, but it works!

---

### Post by Zoot7 on 2009-12-07
I get a slight bit of tear when I'm using some of the Compiz effects with the fglrx driver from Catalyst 9.9, but other than that nothing.
I don't have any tearing problems with the nVidia driver in my laptop at all.

---

### Post by FuturePilot on 2009-12-07
> **nerdy_kid said:**
> i personally am allergic to page tearing (i use projectm a lot, and seeing a freaking page tear ruins the whole thing), so i did some serious digging to fix mine:

 it turned out on my pc (i was using the 180 drivers, am using the 190 but no change) that the settings i set in nvidia-settings were not applied unless i ran either nvidia-settings or nvidia-settings -l.  So i set it to autostart on login. But compiz/kwin started before nvidia-settings, which means i had too restart my window manager to apply the Sync to VBlank option.  So i ended up replacing the kwin and compiz executibles with scripts that start nvidia-settings -l then the window manager.

kinda cheesy, but it works!

Yes, I've ran into that problem. Here's a better solution.
Create /etc/X11/Xsession.d/56nvidia-settings

Put this in it

```
# This file is sourced by Xsession(5), not executed.

# loads nvidia-settings config
if [ -x /usr/bin/nvidia-settings ]; then
  /usr/bin/nvidia-settings -l
fi
```

This gets run **before** Compiz starts. So no need to modify your startup applications.

---

### Post by nerdy_kid on 2009-12-07
> yes, I've ran into that problem. Here's a better solution.
Create /etc/X11/Xsession.d/56nvidia-settings

Put this in it

 	Code:
 	# This file is sourced by Xsession(5), not executed.

# loads nvidia-settings config
if [ -x /usr/bin/nvidia-settings ]; then
  /usr/bin/nvidia-settings -l
fi 
This gets run **before** Compiz starts. So no need to modify your startup applications.


ahh much better!  thanks a ton, knew there had to be an easier way to do that lol

---

