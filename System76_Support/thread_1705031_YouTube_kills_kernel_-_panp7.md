---
title: "YouTube kills kernel - panp7"
date: 2011-03-11
forum: System76 Support
---

### Post by tonyyarusso on 2011-03-11
A couple of weeks ago, I started getting what I think are kernel panics when I visit YouTube.  Immediately when the video loads, the display goes bonkers, with multicolored pixel noise at the top of the screen and the rest going black.  I have to either REISUB or hard reset to recover.  Log files contain lots of entries like this:

```

syslog.1:Mar  8 18:52:11 timmins kernel: [52887.289470] radeon 0000:02:00.0:   R_008010_GRBM_STATUS=0xA0003028
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.289475] radeon 0000:02:00.0:   R_008014_GRBM_STATUS2=0x00000002
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.289483] radeon 0000:02:00.0:   R_000E50_SRBM_STATUS=0x200000C0
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.289500] radeon 0000:02:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.289562] radeon 0000:02:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.289624] radeon 0000:02:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.313843] radeon 0000:02:00.0:   R_008010_GRBM_STATUS=0xFFFFFFFF
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.313846] radeon 0000:02:00.0:   R_008014_GRBM_STATUS2=0xFFFFFFFF
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.313849] radeon 0000:02:00.0:   R_000E50_SRBM_STATUS=0xFFFFFFFF
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.364662] [drm:radeon_fence_wait] *ERROR* fence(ffff88022e66f300:0x000C52E0) 1390ms timeout
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.411499] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x000C52E0)
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.465501] [drm:radeon_fence_wait] *ERROR* fence(ffff88022e66f680:0x000C52E1) 1390ms timeout going to reset GPU
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.519198] radeon 0000:02:00.0: GPU softreset 
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.519207] radeon 0000:02:00.0:   R_008010_GRBM_STATUS=0xA0003028
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.519217] radeon 0000:02:00.0:   R_008014_GRBM_STATUS2=0x00000002
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.519227] radeon 0000:02:00.0:   R_000E50_SRBM_STATUS=0x200000C0
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.519244] radeon 0000:02:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.519310] radeon 0000:02:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.519371] radeon 0000:02:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000402
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.543589] radeon 0000:02:00.0:   R_008010_GRBM_STATUS=0xFFFFFFFF
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.543598] radeon 0000:02:00.0:   R_008014_GRBM_STATUS2=0xFFFFFFFF
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.543614] radeon 0000:02:00.0:   R_000E50_SRBM_STATUS=0xFFFFFFFF
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.594493] [drm:radeon_fence_wait] *ERROR* fence(ffff88022e66f680:0x000C52E1) 1530ms timeout
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.641558] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x000C52E1)
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.692969] [drm:radeon_fence_wait] *ERROR* fence(ffff88022e66fac0:0x000C52E2) 1530ms timeout going to reset GPU
syslog.1:Mar  8 18:52:11 timmins kernel: [52887.694486] radeon 0000:02:00.0: GPU softreset

```

Currently this is happening with 100% reproducibility with anything on YouTube, and never on any other video site I've encountered.  YouTube was working fine on this system up until a couple of weeks ago as well.

System:  panp7
Distro:  Ubuntu 10.04
Arch:    amd64
Kernel:  2.6.32.28.32
Driver:  Radeon (free) 1:6.13.0-1ubuntu5

---

### Post by isantop on 2011-03-11
I don't think that's a kernel panic, as you can still REISUB. Do you get any beeping or blinking lights after you reboot?

---

### Post by tonyyarusso on 2011-03-11
Okay, is there a word for "driver is displeased" then?  :P

No, nothing out of the ordinary on reboot.

---

### Post by isantop on 2011-03-11
Let's rule out Flash. Two things for that. First, go to another flash video site (like Hulu) and see if it does the same thing. Also, point put this in the address bar:

about:plugins

Then scroll do and find the section for "Shockwave Flash". Take a screenshot of that section, then send that here.

---

### Post by tonyyarusso on 2011-03-11
Hulu works fine.

Screenshot attached.

---

### Post by tonyyarusso on 2011-03-11
Oh, even weirder:

Embedded YouTube videos on other sites work - it's only when actually on youtube.com that there's a problem.

---

### Post by rmeineke on 2011-03-12
I'm presuming you are using Firefox to browse to Youtube based upon the screenshot previously provided.  I just struggled through a Firefox/flash issue myself on my PanP7.  Here are a couple of ideas:

Get the Firefox add-on called Flash-Aid
[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

It will allow you to easily fetch the latest version of flash for your install.  Also, if you enable "expert mode" in Flash-Aid you can easily switch from the 32-bit compatibility version and the 64-bit version of flash if necessary.

I'd get the latest version of flash -- clear your browser cookies -- and then restart Firefox and see what happens.  After each run of Flash-Aid, be sure to clear your browser cookies prior to restarting Firefox.

Ultimately, it was the cookie-clearing that fixed the problem for me ... and it is being reported in several other places as the appropriate solution to many Youtube problems:

[http://support.mozilla.com/en-US/questions/786499](http://support.mozilla.com/en-US/questions/786499)

[http://ubuntuforums.org/archive/index.php/t-1280836.html](http://ubuntuforums.org/archive/index.php/t-1280836.html)

Good luck.

Regards,
Robert M.

---

### Post by jangat on 2011-03-12
I have been experiencing something similar on my Star1 running 10.04. Recently, when I go to YouTube, the first video I look at is OK, but all subsequent ones look like 1968 psychedelic posters: lots of overlapping images with a definite reddish shift in colors.

Embedded videos are always OK.

I have seen descriptions of similar YouTube problems in other places on the Ubuntu forums. I have done all the following things to no avail:

-downloaded and used flash-aid with FireFox.
-downloaded and used Chromium
-downloaded and used Google Chrome
-un-installed and re-installed flash, several times

All combination yield the same result: one successful viewing, the rest like an LSD trip.

I'm not sure what to do next.

---

