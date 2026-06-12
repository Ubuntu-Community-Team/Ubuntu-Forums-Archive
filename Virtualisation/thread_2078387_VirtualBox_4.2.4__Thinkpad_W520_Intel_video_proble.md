---
title: "VirtualBox 4.2.4 / Thinkpad W520 Intel video problem"
date: 2012-10-30
forum: Virtualisation
---

### Post by mattc1170 on 2012-10-30
I've come across what appears to be a strange problem with one of the VirtualBox host drivers.  The behavior I observe is that, on the second reboot after installing VBox on Ubuntu 12.10, xorg will not start due to a drm error with the intel video driver.

Here's the relevant snippet from the Xorg.1.log file:

[   397.887] (WW) Falling back to old probe method for vesa
[   397.887] (WW) Falling back to old probe method for modesetting
[   397.887] (WW) Falling back to old probe method for fbdev
[   397.887] (II) Loading sub module "fbdevhw"
[   397.887] (II) LoadModule: "fbdevhw"
[   397.887] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   397.887] (II) Module fbdevhw: vendor="X.Org Foundation"
[   397.887] 	compiled for 1.13.0, module version = 0.0.2
[   397.887] 	ABI class: X.Org Video Driver, version 13.0
[   397.888] (EE) intel(0): [drm] failed to set drm interface version.
[   397.888] (EE) intel(0): Failed to become DRM master.
[   397.888] (II) UnloadModule: "intel"
[   397.888] (EE) Screen(s) found, but none have a usable configuration.
[   397.888] 
Fatal server error:
[   397.888] no screens found
[   397.888] (EE) 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   397.888] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   397.888] (EE) 
[   397.900] Server terminated with error (1). Closing log file.


The particulars:

Ubuntu 12.10 x86_64 (3.5.0-17-generic kernel)
Thinkpad W520 using Intel integrated video

The problem is 100% reproducible on my Thinkpad when running with Intel video:
1.  Install virtualbox-4.2 from the virtualbox.org repository.
2.  Reboot the computer.  Everything comes up fine and I can log in through lightdm.
3.  Reboot the computer again.  Xorg fails to run.  Text only.
4.  Reboot again.  Same result.  Reboot again. Same result.  Reboot... 
5.  Remove virtualbox-4.2.  Reboot.  Everything is fine again.
6.  Reboot several times to make sure everything is fine.  

If I change the BIOS to use the discrete nVidia video, there are no problems.  For some reason, it looks like the vboxdrv module and the intel drm module don't want to play nice together.  There's no indication of any problem in the dmesg output.  I've compared the "good" configuration output with the "bad" configuration output, and the only additional log messages are those when vboxdrv (and its cousins) are loaded.  Nothing appears amiss in the dmesg log.

Thoughts?

---

