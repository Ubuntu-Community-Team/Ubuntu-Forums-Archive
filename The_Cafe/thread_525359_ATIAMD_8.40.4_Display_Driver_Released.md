---
title: "ATI/AMD 8.40.4 Display Driver Released"
date: 2007-08-14
forum: The Cafe
---

### Post by Dark Star on 2007-08-14
**Image removed - hikaricore says don't use my UGA headers without my permission.**

 A new version of the ATI/AMD Linux display driver was released last night for both x86 and x86_64 platforms. This release brings new features such as: TV Out Functionality and Catalyst Control Center Linux Edition. The TV out functionality was made available under Linux OS for all ATI video cards that support TV Out (composite, component video and S-video). It is also part of the Catalyst Control Center and will provide a variety of TV out adjustments. However, please note that TV size and position functions for the ATI Radeon X1200 series and above are adjusted through the aticonfig command line.
 **Issues resolved in this release:**
 [LIST]
[*] A black screen is no longer observed on some hardware when switching to the console or leaving the X window system when a Vesa framebuffer console driver is used.
[*] Connecting a component Video display device launching X-Server no longer results in X-Server failing to start and the display device displaying a black screen.
[*] The DRI no longer fails to initialize in the second server generation.
[*] Pressing the identify
[*]displays function no longer results in display device 1 and 2 being incorrectly identified.
[*] A Floating Point Exception error no longer occurs when launching amdcccle.[/LIST] **Known issues of this release**
 [LIST]
[*] Corruption may be observed with certain applications on some Linux distributions which enable the Composite extension by default, e.g., RHEL 5. If you are observing application corruption, please disable the Composite extension.
[*] Using the xgl enabled x-server interface disables display switching hot plug support.
[*] There is no support for video playback on the second head in dual head mode.
[*]In order to gain the best performance and ease of use, ATI/AMD recommends the following:
[*] Kernel module build environment &#8211; should include the following: Kernel source code: either the Kernel Source or Kernel Headers packages
[*] ISSE Support enabled in your Linux Kernel (applies to Intel Pentium III and later CPUs only; enabled by default on version 2.4 and later kernels)
[*] The rpm utility should be installed and configured correctly on your system, if you intend to install it via RPM packages;[/LIST] **Requirements:**
 [LIST]
[*] XOrg 6.7, 6.8, 6.9, 7.0, 7.1 or 7.2; XFree86 version 4.3
[*] Linux kernel 2.4 or higher
[*] glibc version 2.2 or 2.3
[*] POSIX Shared Memory (/dev/shm) support is required for 3D applications[/LIST] Download  : [Drivers & Software]("http://ati.amd.com/support/driver.html")
Installation Instruction : [Click Here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.40.4.html")

---

### Post by MaximB on 2007-08-14
Damn !
When would they finally include support for the long waited OpenGL 2.1  ?!
I'm forced to play regnum in safe mode due to ATI not yet have support for it.
And nexuiz is no longer playable in it's latest version...

I'm very sorry for choosing ATI over Nvidia at the time I used only Windows.
now I'm screwed 

**does anyone had luck using the free Mesa drivers which do support OpenGL 2.1 ?**

---

### Post by phrostbyte on 2007-08-14
Yep, still no Composite support. Makes me wonder why Nvidia managed to bring out Composite support so fast and ATI after a year can't even get basic things like video playback right.

---

### Post by FuturePilot on 2007-08-14
> **phrostbyte said:**
> Yep, still no Composite support. Makes me wonder why Nvidia managed to bring out Composite support so fast and ATI after a year can't even get basic things like video playback right.

Because ATI focuses more on Windows support and DirectX and doesn't give too much attention to OpenGL. Nvidia is much nicer when it comes to their drivers as they put a lot more focus into their OpenGL support. Not to mention they seem to be a bit more open when it comes to Linux as they release drivers much faster than ATI.

---

### Post by MaximB on 2007-08-14
> **FuturePilot said:**
> Because ATI focuses more on Windows support and DirectX and doesn't give too much attention to OpenGL. Nvidia is much nicer when it comes to their drivers as they put a lot more focus into their OpenGL support. Not to mention they seem to be a bit more open when it comes to Linux as they release drivers much faster than ATI.

**SAY NO MORE !**
Or I will take my life.
It is bad without those comments.

---

### Post by FuturePilot on 2007-08-14
Sorry:-#

---

