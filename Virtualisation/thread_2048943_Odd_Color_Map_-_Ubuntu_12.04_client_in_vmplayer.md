---
title: "Odd Color Map - Ubuntu 12.04 client in vmplayer"
date: 2012-08-27
forum: Virtualisation
---

### Post by philh42 on 2012-08-27
Hi,
  I run Ubuntu 12.04 (and 10.04) under vmplayer 5.0 on Windows xp.  It is function with one paralyzing quirk.  If I re-size the vmplayer,  the system colormap changes to a strange color map.  Worse yet,  the XP is also degraded so that it is unusable too.   

  On XP,  I fire up the nVidia tools and run a screen calibration (any one) and it repairs both.   This is annoying and time-consuming.   Any suggestions?
Philh42

---

### Post by dcstar on 2012-08-30
> **philh42 said:**
> Hi,
  I run Ubuntu 12.04 (and 10.04) under vmplayer 5.0 on Windows xp.  It is function with one paralyzing quirk.  If I re-size the vmplayer,  the system colormap changes to a strange color map.  Worse yet,  the XP is also degraded so that it is unusable too.   

  On XP,  I fire up the nVidia tools and run a screen calibration (any one) and it repairs both.   This is annoying and time-consuming.   Any suggestions?
Philh42

[LIST=1]
[*]Install VMware Tools in the VM.
[*]Change the "Accelerate 3D Graphics" setting in the VM.
[*]Install the latest nVidia drivers for XP.
[/LIST]

---

### Post by philh42 on 2012-09-04
Hi,
   I did all of that and the problem persists.  I turned off the 3d acceleration and the problem disappeared.  A process list (ps -ef) showed me that compiz is running when the problem occurs and not running when OK.  Generally, I like wobbly windows.   Any insight on settings that might be the issue.  
Thanks,
philh42

---

### Post by dcstar on 2012-09-05
> **philh42 said:**
> 
........
Any insight on settings that might be the issue.  
Thanks,
philh42

VMware's Linux video driver is not fully compatible with all 3D effects, you don't get full functionality as with native hardware.

---

