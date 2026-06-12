---
title: "AMD Catalyst 10.1 Driver For Linux Released"
date: 2010-01-27
forum: The Cafe
---

### Post by Pasdar on 2010-01-27
Download it now at:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English)

Release notes: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_101_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_101_linux.pdf)

Thx to: [http://www.phoronix.com](http://www.phoronix.com)

---

### Post by Techsnap on 2010-01-27
Thanks for the heads up. I'll give this a try tomorrow.

---

### Post by Pasdar on 2010-01-27
**New Features**

This release of ATI Catalyst&#8482; Linux introduces support for the following new operating
system:
[LIST]
[*]Ubuntu 9.10 production support
[/LIST]

**Resolved Issues**
The following section provides a brief description of resolved issues with the latest version of the ATI Catalyst&#8482; Linux software suite. These include:
[LIST]
[*][ATI Catalyst&#8482; Control Center] Display Manager Properties tab now properly shows a single mode instead of multiple modes when big desktop mode is enabled
[*]The operating system will no longer fail when switching between virtual desktops
[*][RHEL 5.4 32-bit] [ATI Catalyst&#8482; Control Center] System now functions properly after selecting "Detect Displays" button and hot-plugging a HDMI display
[*][Ubunut 9.10] X no longer fails after executing multiple Xserver generations with Xinerama enabled
[*]Hotplugging a HDMI monitor or toggling between LCD and HDMI no longer causes the system to stop responding
[/LIST]

**Known Issues**
The following section provides a brief description of known issues associated with the latest version of ATI Catalyst&#8482; Linux software suite. These issues include:
[LIST]
[*][RHEL4-U8 32-bit] Corruption may be observed while starting Xserver on some ASICs
[*]Corruption may be observed after 90, 180 or 270 degree desktop rotation on some ASICs
[*]System may stop responding after switching to DC (battery) mode with CrossFire&#8482; enabled and full-screen applications running
[*]System may become unresponsive after executing specific combinations of XRandR reflections and rotations
[*]The output log file may report the Engine Clock or Memory Clock values as 0 MHz on some systems
[*][RHEL 5.4][ ATI Catalyst&#8482; Control Center] Applying customized TV modes might not work properly, pop up message requesting restart will not appear and customized format will not apply
[*][Ubuntu 9.04 x86 64-bit] Some systems may become unresponsive during video playback with certain Dual Head configurations
[*][ATI Catalyst&#8482; Control Center] Specific customized modes under the HDTV page may fail to apply on some systems
[*][Ubuntu 9.04] With one DP monitor and one DVI monitor connected in clone mode, unplugging and re-plugging the DVI monitor may cause the system to deadlock
[*]Xserver may fail to launch after enabling CrossFire&#8482; and restarting on some ASICs
[*][ATI Catalyst&#8482; Control Center] Super Anti-Aliasing (16x) mode may not be available on some display adapters with CrossFire&#8482; is enabled
[*]Display rotation may fail to apply from ATI Catalyst&#8482; Control Center with desktop effects enabled
[*][RHEL] Enabling Xinerama may cause input devices (keyboard and mouse) to become inaccessible after restarting Xserver
[*]System may fail to return to console mode after enabling all adapters and exiting
[*]Xserver for multi GPU configuration on some ASICs
[*]ATI Catalyst&#8482; Control Center may report error when two displays of different maximum resolutions are set in clone mode
[*][SUSE 11.1 64-bit] Enabling CrossFire&#8482; might fail with some ASICs
[*]Scaling setting changes may fail to retain after mode change, reboot or restarting Xserver
[*][SUSE 11.2 x86] CrossFire&#8482; might not be functional under specific configurations
[*][Ubuntu 9.10] CAL test "completemodulelist.txt" might not execute and throws segmentation fault
[*][ATI Catalyst&#8482; Control Center] Some systems may intermittently stop responding when changing the scaling options
[*][ATI Catalyst&#8482; Control Center] Applying "Size and Position" adjustments for Analog Monitors might not work properly
[*][Ubuntu 9.04] Some video cards may stop video output signals when monitor has been powered off
[*][ATI Catalyst&#8482; Control Center] Disabled display will become enabled after Xserver restart
[*]Flickering corruption might be visible while running OpenGL applications with CrossFire&#8482; enabled on specific ASICs
[/LIST]

---

### Post by Ric_NYC on 2010-01-27
Is the **ATI Radeon&#8482; Xpress 1200** included in that new version?

---

### Post by ticklemehomeboi on 2010-01-27
> **Ric_NYC said:**
> Is the **ATI Radeon™ Xpress 1200** included in that realise?

No.

---

### Post by rajeev1204 on 2010-01-27
> **Ric_NYC said:**
> Is the **ATI Radeon™ Xpress 1200** included in that new version?

Thats an older card and has been unsupported for some time now.Use the open radeon HD driver for that card.

---

### Post by Ric_NYC on 2010-01-27
> **rajeev1204 said:**
> Thats an older card and has been unsupported for some time now.Use the open radeon HD driver for that card.

That's strange. I bought my laptop last year.

---

### Post by rajeev1204 on 2010-01-27
> **Ric_NYC said:**
> That's strange. I bought my laptop last year.

1 year is a  long time in the graphics industry.Also,this is an integrated card and some manufacturers still sell with this chipset.

Anything from and above the HD 2400 is what you need.The link gives the release notes where all supported cards are listed.

---

### Post by Ric_NYC on 2010-01-27
> **rajeev1204 said:**
> 1 year is a  long time in the graphics industry.Also,this is an integrated card and some manufacturers still sell with this chipset.

Anything from and above the HD 2400 is what you need.The link gives the release notes where all supported cards are listed.


I'm looking for a Nvidia card next time I buy a computer.

---

### Post by rajeev1204 on 2010-01-27
> **Ric_NYC said:**
> I'm looking for a Nvidia card next time I buy a computer.

Havent you tried the open source driver? It works very well for your card.

---

### Post by Pasdar on 2010-01-27
Here is some more info. I have an ATI 4570, using Kubuntu 9.10 64bit.

ATI 10.1 Drivers:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.2.9252 Compatibility Profile Context
OpenGL shading language version string: 1.50
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4

GLXGEARS:
Composition enabled:
6366 frames in 5.0 seconds
6595 frames in 5.0 seconds
7148 frames in 5.0 seconds
6839 frames in 5.0 seconds
6887 frames in 5.0 seconds = 1377 FPS

Composition disabled:
17509 frames in 5.0 seconds
28745 frames in 5.0 seconds
28785 frames in 5.0 seconds = 5757 FPS

I checked the following issues to see if they still work or if the issues are fixed:
* Video, DVDRips, HD 720p flash, HD 1080p flash: minor video tearing with fast moving video still exists.
* Native games, games mentioned in signature: work great as usual.
* Game via wine: still the same issues (slow).
* Photoshop CS in wine, works great.

Notice the OpenGL version change, now 3.2.9252 as opposed to 3.2.9232 in ATI 9.12. GLXGEARS with ATI 9.12: 28570 frames in 5.0 seconds = 5714 FPS

---

### Post by handy on 2010-01-27
It still doesn't work with xorg-server 1.7 ! That's three releases of Catalyst that don't!

Unbelievable how slow they are to move ahead with the development of critically important open-source packages.

The new Catalyst *_may_* work with the kernel .32.

---

### Post by k64 on 2010-01-27
> **rajeev1204 said:**
> 1 year is a  long time in the graphics industry.Also,this is an integrated card and some manufacturers still sell with this chipset.

Anything from and above the HD 2400 is what you need.The link gives the release notes where all supported cards are listed.

Yeah, the Radeon HD 2400 Pro is what I have. However, I'd really prefer the FOSS drivers over the proprietary ones. Where can I obtain them?

---

### Post by MaxIBoy on 2010-01-27
Almost all distros (including Ubuntu) install the open-source drivers by default. So if you haven't installed Catalyst/FGLRX yet, you already have the open-source drivers.

Otherwise, you can install and run jockey-gtk to switch back to the open-source drivers.

---

### Post by Ric_NYC on 2010-01-27
> **rajeev1204 said:**
> Thats an older card and has been unsupported for some time now.**Use the open radeon HD driver for that card**.


Just installed it... It crashes Chrome and Firefox when I try to play videos in full screen on youtube.

---

### Post by Pasdar on 2010-01-28
> **handy said:**
> It still doesn't work with xorg-server 1.7 ! That's three releases of Catalyst that don't!

Unbelievable how slow they are to move ahead with the development of critically important open-source packages.

The new Catalyst *_may_* work with the kernel .32.

ATI supports only three distros doesn't it, Redhat, Ubuntu and SUSE. None of them has that kernel do they? So they will not add the support until and when one of them does.

---

### Post by handy on 2010-01-28
> **Pasdar said:**
> ATI supports only three distros doesn't it, Redhat, Ubuntu and SUSE. None of them has that kernel do they? So they will not add the support until and when one of them does.

This situation often causes a great deal of trouble for the distros that use more recent versions of packages than those three.  

As of this writing the kernel version is kernel2.6.33-rc5-git4 & .33 is due out in March. 

Which kernel is the next Ubuntu going to be running?

---

### Post by Pasdar on 2010-01-28
> **handy said:**
> This situation often causes a great deal of trouble for the distros that use more recent versions of packages than those three.  

As of this writing the kernel version is kernel2.6.33-rc5-git4 & .33 is due out in March. 

Which kernel is the next Ubuntu going to be running?

They will be using 2.6.32, with backport for higher.
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html)

---

### Post by handy on 2010-01-28
> **Pasdar said:**
> They will be using 2.6.32, with backport for higher.
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html)

I expect a catalyst will be released that runs on both kernel .32 & xorg-server 1.7 to coincide with the next Ubuntu release.

Hopefully they come up with that version of catalyst sooner, for obvious reasons.

***[Edit:]** xorg-server 1.8 will apparently be released soon...*

---

### Post by elect on 2010-02-13
CAL in included? How can i see the version of CAL?

---

