---
title: "ATI Catalyst 8.5 released!"
date: 2008-05-23
forum: The Cafe
---

### Post by olskar on 2008-05-23
ATI Catalyst 8.5 released!


> Resolved Issues

The following section provide a brief description of resolved issues with the latest version of the ATI Catalyst™ Linux software suite. These include:

    * Support for video playback on the second head in dual head mode is now available. Further details can be found in topic number 737-26985
    * Unresolved symbols in Xorg log under RHEL 4u6 32 and 64 bit no longer occur. Further details can be found in topic number 737-34284
    * The desktop background color is no longer displayed incorrectly when using xcommgr. Further details can be found in topic number 737-34285
    * Change VT no longer fails when kernel module is not loaded. Further details can be found in topic number 737-34286
    * Switching to the virtual terminal multiple times no longer results in X displaying corruption. Further details can be found in topic number 737-34287
    * Catalyst Control Center: The Preference page is now localized for all supported languages. Further details can be found in topic number 737-34275
    * The Linux kernel module is no longer installed to wrong location if the Linux kernel is updated. Further details can be found in topic number 737-34288
    * Random system hangs no longer occur when calls to the ATI driver are made from Ring3. Further details can be found in topic number 737-34289
    * X window no longer fails to respond when GoogleEarth is maximized. Further details can be found in topic number 737-34290
    * A segmentation fault no longer occurs when running SPECViewperf on systems containing an ATI FireGL V5100 series product and running SUSE 10.3 x86. Further details can be found in topic number 737-34276
    * Enabling Composite extension no longer displays 8x AA for graphic cards that do not support 8x AA under the Ubuntu 7.10 operating system. Further details can be found in topic number 737-34291
    * Display corruption is no longer noticed at logon when compiz is enabled. Further details can be found in topic number 737-34292
    * Launching the glxgears application no longer results in segmentation faults. Further details can be found in topic number 737-34293
    * GoogleEarth: Launching the application in horizontal mode on a system running X no longer results in corruption being noticed. Further details can be found in topic number 737-34293
    * Specviewperf 8.1 64 bit version: Segmentation faults no longer occurs on IGP systems. Further details can be found in topic number 737-34294
    * Maya 2008: Moving the render window no longer results in the operating system failing. Further details can be found in topic number 737-34295
    * Glxgears corruption is no longer noticed in big desktop mode. Further details can be found in topic number 737-34296 

---

### Post by aaaantoine on 2008-05-23
Last I recall, someone was working on getting 8.4 into Ubuntu 8.04.1.  They should probably work on getting 8.5 in instead, considering the additional bug fixes.  They just have to apply the patch to get rid of the resurfaced watermark, and probably something else.

---

### Post by uraldinho on 2008-05-23
I hate updating my fglrx drivers. It's like a time bomb, I don't know what's gonna break. 

I think I'll stick to what I have. fglrx, compiz, etc, everything is working on my system right now. No need to mess it up.

---

### Post by yatt on 2008-05-23
Hopefully this fixes the mass corruption I get with Compiz on Big Desktop that 8.4 introduced.

---

### Post by olskar on 2008-05-24
> **aaaantoine said:**
> Last I recall, someone was working on getting 8.4 into Ubuntu 8.04.1.  They should probably work on getting 8.5 in instead, considering the additional bug fixes.  They just have to apply the patch to get rid of the resurfaced watermark, and probably something else.


That sounds like a good idea

---

