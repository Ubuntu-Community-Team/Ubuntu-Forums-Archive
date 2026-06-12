---
title: "Wrong screen size on Wild Dog P9 (nVidia GT 630 HDMI)"
date: 2013-05-11
forum: System76 Support
---

### Post by AlexandreP on 2013-05-11
Hi,

I just received my brand new Wild Dog Performance. My monitor doesn't seem to be adequately recognized when connected to the nVidia GT 630 video card using HDMI. My monitor is a Samsung SMB2330H. I am using nvidia-current-310 driver.

The native resolution found by the graphic card is 1920x1080, which is the correct one. But the Unity Launcher is half off the screen, the top panel also is out of the screen, and there is some part of a maximized window that is out of the screen on the right side and on the bottom. Going to System settings and changing the display resolution to a lower one but with the same ratio (say, 1280x720 [16:9]) provoques the same problem: parts of the display is out of the physical screen.

If a change the display resolution to a different ratio (say, 1680x1050 [16:10]), the display is scaled, and I get black bars (blank space) on the left and right side of the screen.

When looking /var/log/Xorg.0.log, I can see this information:
```
[    16.194] (--) NVIDIA(0): Valid display device(s) on GeForce GT 630 at PCI:1:0:0
[    16.194] (--) NVIDIA(0):     CRT-0
[    16.194] (--) NVIDIA(0):     CRT-1
[    16.194] (--) NVIDIA(0):     DFP-0
[    16.194] (--) NVIDIA(0):     DFP-1
[    16.194] (--) NVIDIA(0):     Samsung SMB2330H (DFP-2) (connected)
[    16.194] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    16.194] (--) NVIDIA(0): CRT-1: 320.0 MHz maximum pixel clock
[    16.194] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    16.194] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    16.194] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    16.194] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    16.194] (--) NVIDIA(0): Samsung SMB2330H (DFP-2): 165.0 MHz maximum pixel clock
[    16.194] (--) NVIDIA(0): Samsung SMB2330H (DFP-2): Internal Single Link TMDS
[    16.194] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    16.194] (**) NVIDIA(0):     device Samsung SMB2330H (DFP-2) (Using EDID frequencies
[    16.194] (**) NVIDIA(0):     has been enabled on all display devices.)
[    16.194] (WW) NVIDIA(GPU-0): The EDID for Samsung SMB2330H (DFP-2) contradicts itself: mode
[    16.194] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    16.194] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-81.000 kHz) would exclude
[    16.194] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    16.194] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    16.195] (WW) NVIDIA(GPU-0): The EDID for Samsung SMB2330H (DFP-2) contradicts itself: mode
[    16.195] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    16.195] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-81.000 kHz) would exclude
[    16.195] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    16.195] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    16.196] (==) NVIDIA(0): 
[    16.196] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    16.196] (==) NVIDIA(0):     will be used as the requested mode.
[    16.196] (==) NVIDIA(0): 
[    16.196] (II) NVIDIA(0): Validated MetaModes:
[    16.196] (II) NVIDIA(0):     "DFP-2:nvidia-auto-select"
[    16.196] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    16.231] (--) NVIDIA(0): DPI set to (304, 304); computed from "UseEdidDpi" X config
[    16.231] (--) NVIDIA(0):     option
```

Any toughts on how I can fix my display problem?

PS: when using a DVI cable between the video card and the monitor, everything is alright, display fits on screen, 1920x1080. But I would prefer to use the HDMI cable, as I hook up the monitor as a second display on another computer.

---

### Post by isantop on 2013-05-13
Look in the monitor settings and make sure overscan is disabled.

EDIT: That is, the settings in the monitor, not the Display Settings in Ubuntu.

---

### Post by OliW on 2014-03-03
Did you ever work around this? I've just plugged a Nvidia 630 into a Samsung TV and it looks like the same problem. Half the screen (vertically) is missing but everything seems to report being at the native resolution. I don't have ant of the EDID contractions though.

It's not overscan. I've cycled through the various modes including the just-make-it-fit-on-the-screen mode. It's very odd.

---

### Post by trash-mail-account on 2014-06-27
Any news here? Still no solution by nvidia. New corrected drivers would be nice, but a work around would be sufficient. :|

---

### Post by houstonbofh on 2014-06-29
This has been a long term nVidia problem.  Look for an ancient post by me where I said "I Love You!" to a guy with an answer.  You might want to try the Nouveau drivers, but performance will hurt.  The other option is a different monitor.

---

### Post by trash-mail-account on 2014-07-09
Actually, another TV is NOT a solution. ;)
Has anyone experienced this issue with other nvidia graphics cards running on the same (current) driver versions?
So would it help to change to a 7xx model?
I fear the noveau driver still has many issues running XBMC...?

Update: I tried GS8400, GT610, GT640 so far, GT240 and GTX650 would be available but I think testing them is wasted time.

---

### Post by houstonbofh on 2015-03-01
In case this comes up again, my thread with an answer that is apparently still relevant is [http://ubuntuforums.org/showthread.php?t=1045106](http://ubuntuforums.org/showthread.php?t=1045106)

---

