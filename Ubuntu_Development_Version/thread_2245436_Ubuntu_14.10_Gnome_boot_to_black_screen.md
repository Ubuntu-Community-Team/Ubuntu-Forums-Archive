---
title: "Ubuntu 14.10 Gnome boot to black screen"
date: 2014-09-23
forum: Ubuntu Development Version
---

### Post by crcarson on 2014-09-23
Continue to try to get a 14.10 system running no the SYX desktop I've been using for Ubuntu for many years.  The Gnome build boot to a black screen unless I specify nomodeset and then I get a complete desktop but it runs poorly.  If I try the Unity build the desktop comes up but I'm missing Unity (launcher) and the Ubuntu banner at the top.  Completed many rebuilds of these systems from the Daily Builds but it does not change the results.  Tried to document the Unity failure via ubuntu-bugs (1363421) but have not seen any indication that it has been looked at.  This desktop is currently running 14.04.01 without any problems (nothing added to the boot to get it up).  There must be something unique about this hardware that's causing 14.10 problems.  Don't know what to try next.

---

### Post by oldfred on 2014-09-23
What video card?
If you need nomodeset to get to low quality graphics, you probably have nVidia or AMD and then should install the proprietary graphics.

---

### Post by crcarson on 2014-09-23
Don't need any special video drivers for the 14.04.1 load.  Here is my display lshw output..

       *-display
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:cc00(size=8)

---

### Post by mc4man on 2014-09-23
There's been a host of issues with Intel in 14.10, seems to vary greatly depending on what hardware you have. 
Here got[ black screen ect. on Haswell ]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1357746")(mobile) 4600 until the xorg upgrade to abi-16 (which [screws up a few apps. instead]("https://bugs.launchpad.net/ubuntu/+source/mpv/+bug/1371978")

Until the upgrade could only boot thru recovery to a semi usless session (llvmpipe) or 
downgrade xserver-xorg-video-intel to older version, no longer an easy option due to the abi change
or
remove the xserver-xorg-video-nouveau package, maybe try that

Others with Intel seemed not affected by xserver, they were more kernel based issues

There is also this thread - [http://ubuntuforums.org/showthread.php?t=2244242](http://ubuntuforums.org/showthread.php?t=2244242)

---

### Post by crcarson on 2014-09-23
Thanks for the post, will check into the items you linked.  I've seen several forum post with my same symptoms and tried to follow them.  Several said that an update resolved but I've been keeping up with all the updates and nothing has changed a thing for the past month or so.

---

### Post by crcarson on 2014-09-24
mc4man, since I don't know how to correctly go to a earlier version of xserver-xorg-video-intel I just copied the files I thought necessary (/usr/lib/xorg/modules/drivers/intel_drv.so, /usr/lib/libI810XvMC.so.1.0.0, and /usr/lib/libIntelXvMC.so.1.0.0) from my working 14.04.1 system and I now have a 14.10 Gnome system that boots to a good desktop.  Not sure what to do with this information.  I currently don't have a bug open for this boot failure on Gnome.

---

### Post by mc4man on 2014-09-24
If that works for you ok then stick with replacing xserver-xorg-video-intel's files
(have you tried any video playback to see if having mismatched video-abi is an issue?

As far as a bug report you could file on xserver-xorg-video-intel (ubuntu-bug xserver-xorg-video-intel ) & state your issue, ect.  For mine nothing was going to be done, it just happened to be fixed with the upgrade to xserver 1.16
(- Did you try removing xserver-xorg-video-nouveau before the file replacement workaround?

Also I myself can't really see why anyone would want to actually use 14.10. It's a 9 month dead dog with very little attention/care being placed on desktop installs

---

### Post by crcarson on 2014-09-24
Since this was first on your todo list I didn't try anything else, will do so tomorrow.  In using the system I noticed that the desktop windows are not as smooth as usual.  Have not tried any video yet but will.

---

### Post by mc4man on 2014-09-24
> **crcarson said:**
> Since this was first on your todo list I didn't try anything else, will do so tomorrow.  In using the system I noticed that the desktop windows are not as smooth as usual.  Have not tried any video yet but will.
Sorry if it came off that way, was more referring to what I could do to get a working session..

Definitely try putting back current xserver-xorg-video-intel package/files & removing the xserver-xorg-video-nouveau package, then see if a fresh boot is good
(using the driver meant for video-abi-15 with xserver-xorg-core on  video-abi-16 'feels' wrong even though it apparently works to some extent

---

### Post by crcarson on 2014-09-25
OK, I don't know what the problem was, I reversed the update I made (deleted the 14.04 modules and rename the 14.10 modules to correct names) and I still have a working system.  Will try removing the nouveau package if the problem returns.  Thanks for the help.

---

