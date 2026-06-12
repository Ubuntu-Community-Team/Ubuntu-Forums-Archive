---
title: "Real Linux drivers for System76 laptops, NO thanks to System76"
date: 2008-02-19
forum: System76 Support
---

### Post by DRM_free on 2008-02-19
Looks like a Linux user named Cezary Jackiewicz took the initiative to write drivers for System76 hardware. Specifically, the [compal-laptop.c driver he submitted]("http://lkml.org/lkml/2008/2/5/262") to the Linux Kernel Mailing List will control System76's [Pangolin laptops]("http://system76.com/product_info.php?cPath=28&products_id=50"), which are based on Compal FL90/IFL90 models.

Wouldn't it be nice if System76 actually helped upstream communities ([kernel.org]("http://kernel.org/"), [ALSA]("http://www.alsa-project.org/"), [HAL]("http://www.freedesktop.org/wiki/Software/hal")) like Mr. Jackiewicz is doing, so that their hardware works out of the box and is forward-compatible?

The whole idea of the "System76 Driver" is a band-aid: all the functionality of that script should really be ported to the respective upstream projects. The "System76 Driver" should simply not be needed by someone who installs the latest version of Ubuntu.

---

### Post by crichell on 2008-02-19
HI DRM free:

Because we often use the latest hardware components that are not always supported by a Vanilla install we must include the System76 driver.  Any contributions we make go upstream or come from up stream meaning that they eventually make it into Ubuntu vanilla.  System76 also contributes hardware to open source projects for the webcams, embedded controller, fingerprint readers and other components that then enable those devices for all computers that use those devices - not just System76.

Our work each day is to advocate open source and make it availble to more people.  We do this becuase we beleive in the open source movement - or revolution as we prefer to call it.

---

### Post by DRM_free on 2008-02-19
Hi Crichell -- thanks for taking the time to respond. It's understandable that the cutting-edge hardware you sell won't work on old or even current versions of Ubuntu. Obviously you have to patch old drivers, but what I can't understand is why you don't post those patches to the appropriate upstream project so that by the time the next version of Ubuntu comes out, those patches will no longer be needed.

Some concrete examples from the [System76 Feature Matrix]("http://knowledge76.com/index.php/System76_Driver") on your own website (please correct me if they're wrong):

1) The latest Ubuntu (version 7.10) still needs the "System76 Driver" script to enable the **GAZP[SIZE="5"]1[/SIZE]** - 14.1" Silver Gazelle Performance to Restore and have Sound. **Back in early 2007 **you already knew how to patch Ubuntu 6.06 to enable these functionalities, yet from the fact that the **latest Ubuntu still doesn't work**, those changes haven't made their way upstream. Now why could this be? Perhaps because you didn't submit those changes in the first place?

2) PANV2 - 15.4" Silver Pangolin Value: Restore, Microphone were fixed by patch to Ubuntu 6.06 but still don't work in Ubuntu 7.10. Again, that's probably because **you didn't submit the patches upstream to ALSA and other modified drivers**.

It's so, so easy to help upstream projects. When you find yourself fixing a driver, simply make a patch against the original file and **email that patch to the project's mailing list**. It doesn't take more that two minutes, and once it's upstream you can forget about having to modify future versions of the driver. In the end, it will save **you** time.

---

### Post by crichell on 2008-02-19
> **DRM_free said:**
> Hi Crichell -- thanks for taking the time to respond. It's understandable that the cutting-edge hardware you sell won't work on old or even current versions of Ubuntu. Obviously you have to patch old drivers, but what I can't understand is why you don't post those patches to the appropriate upstream project so that by the time the next version of Ubuntu comes out, those patches will no longer be needed.

Some concrete examples from the [System76 Feature Matrix]("http://knowledge76.com/index.php/System76_Driver") on your own website (please correct me if they're wrong):

1) The latest Ubuntu (version 7.10) still needs the "System76 Driver" script to enable the **GAZP[SIZE="5"]1[/SIZE]** - 14.1" Silver Gazelle Performance to Restore and have Sound. **Back in early 2007 **you already knew how to patch Ubuntu 6.06 to enable these functionalities, yet from the fact that the **latest Ubuntu still doesn't work**, those changes haven't made their way upstream. Now why could this be? Perhaps because you didn't submit those changes in the first place?

2) PANV2 - 15.4" Silver Pangolin Value: Restore, Microphone were fixed by patch to Ubuntu 6.06 but still don't work in Ubuntu 7.10. Again, that's probably because **you didn't submit the patches upstream to ALSA and other modified drivers**.

It's so, so easy to help upstream projects. When you find yourself fixing a driver, simply make a patch against the original file and **email that patch to the project's mailing list**. It doesn't take more that two minutes, and once it's upstream you can forget about having to modify future versions of the driver. In the end, it will save **you** time.

The above patches you are referencing come from Alsa.  Often we have to add a line to /etc/modprobe.d/alsa-base describing the exact sound card in a laptop/desktop model.  That's why you see sound provided by the driver in newer versions of Ubuntu.  Of course this type of modification does not and should not go into Ubuntu vanilla.  Also we find that alsa changes at a rate that makes it advantageous to our customers if we include a newer alsa version even if the card is supported by Ubuntu - maybe the MIC has better quality or the controls are better.

I can say that we would like to fund more engineering effort upstream and I'm sure we will as we grow.  That said your accusations are entirely incorrect.

---

### Post by DRM_free on 2008-02-19
> Often we have to add a line to /etc/modprobe.d/alsa-base describing the exact sound card in a laptop/desktop model....Of course this type of modification does not and should not go into Ubuntu vanilla. Agreed, modifying /etc/modprobe.d/alsa-base is a **hack**, but that doesn't mean it won't help ALSA devs find a good, future-proof solution. But **if the devs don't know there is a problem, they're not going to fix it**. So whenever you resort to a hack like this, open a [bug report in ALSA]("https://bugtrack.alsa-project.org/alsa-bug/login_page.php") and simply say:

*"The only way we got our laptops to play sound and record from the built-in microphone is by applying the attached hack. We would appreciate it if you could find a more permanent solution that works out of the box."* 

That's it! Now sit back and let the driver devs do the work -- most often it's trivial for them to incorporate the info from your hack into the appropriate driver.

Also, **drivers may actually need very detailed information** about the devices they control, and the more people **report** that info, the better the driver will be. For instance, take a look at the PCI ID table in [lines 1976-2017 of the hda_intel.c driver]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=sound/pci/hda/hda_intel.c;h=56f8a30507513563135b62b51d17f0169b3c672e;hb=HEAD").
> we would like to fund more engineering effort upstream I wasn't implying that you should pay anyone, just that you should try to **report** your changes (be they maintainable patches or ugly hacks) to upstream projects.

---

### Post by Vadi on 2008-02-21
Chill, guy.

They're only one of the three OEM's that sell ubuntu pre-installed. Give some appreciation here and offer help, or just go away somewhere. I'm sure they're doing their best.

---

### Post by compholio on 2008-02-21
> **DRM_free said:**
> ...
That's it! Now sit back and let the driver devs do the work -- most often it's trivial for them to incorporate the info from your hack into the appropriate driver.
...
Have you ever done any driver reverse engineering?  Heck, have you ever worked on an open source project?  It is not trivial work, even if you have the hardware.

System76 has an obligation to support its customers and *they are kind enough to give back to the community as well*.  If you have a specific complaint with a piece of hardware then you should ask for help, from System76 if you are a customer or from upstream if you are not.

---

### Post by tedrampart on 2008-02-22
drm_free: if its so easy why not look at the code and report these problems/solutions yourself, then youd know they're submitted.

isn't the whole point of opensource meant to be community driven?  why not step up and take some of the load.  these guys are making laptops that work for people that want a ubuntu pre-install (myself being one of them).  sure they get paid and make money doing it, but you get a laptop that works.  

as far as I see it, they're contributing quite a bit to the community, and I agree they should be given some credit here, and not attacked for their work.

its not perfect, sure, but its fine start to something we can all agree on being needed for linux to become a stable option for average joe user.

I think more appropriate ways of getting your point across could have been used before waving the gun around mate..

---

### Post by steveneddy on 2008-02-22
> **DRM_free said:**
> Agreed, modifying /etc/modprobe.d/alsa-base is a **hack**, but that doesn't mean it won't help ALSA devs find a good, future-proof solution. But **if the devs don't know there is a problem, they're not going to fix it**. So whenever you resort to a hack like this, open a [bug report in ALSA]("https://bugtrack.alsa-project.org/alsa-bug/login_page.php") and simply say:

*"The only way we got our laptops to play sound and record from the built-in microphone is by applying the attached hack. We would appreciate it if you could find a more permanent solution that works out of the box."* 

That's it! Now sit back and let the driver devs do the work -- most often it's trivial for them to incorporate the info from your hack into the appropriate driver.

Also, **drivers may actually need very detailed information** about the devices they control, and the more people **report** that info, the better the driver will be. For instance, take a look at the PCI ID table in [lines 1976-2017 of the hda_intel.c driver]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=sound/pci/hda/hda_intel.c;h=56f8a30507513563135b62b51d17f0169b3c672e;hb=HEAD").
 I wasn't implying that you should pay anyone, just that you should try to **report** your changes (be they maintainable patches or ugly hacks) to upstream projects.

Hey man, most of the stuff we do in Linux is a hack. We hack the xorg.conf, we hack the bluetooth files to get it to work better with our new bluetooth toys.

I understand some of what you are saying and tend to agree partially with your
opinion.

But I have owned a System76 laptop for one year now and through circumstances that I may have brought on myself, I have had to reinstall twice during the ownership of this laptop.

Both times there wasn't a reason to install the System76 driver because most of the hardware worked out of the box.

with the exception of the built-in web cam and the fingerprint reader, there were no issues and the last install I purposely didn't install the sys76 driver for a couple of weeks just to see what the results would be.

I eventually installed it in case there is an update that I might need.

Unless you are submitting code or bug reports on a regular basis, you should not criticize.

**Don't hate, participate.**

Get a launchpad account and submit bugs.

I wonder if Dell is submitting code the kernel.org?

Or other OEM Ubuntu laptop suppliers?

I don't code, but I do submit bugs. I try to help on the forums where I can.

**[COLOR="Red"]What do you do[/COLOR]**?

---

### Post by Vadi on 2008-02-22
> **steveneddy said:**
> 
**[COLOR="Red"]What do you do[/COLOR]**?

^

---

### Post by DRM_free on 2008-02-22
> if its so easy why not look at the code and report these problems/solutions yourself, then youd know they're submitted.

Good point. I'll search for Pangolin V3-specific fixes within the "System76 driver" and report them upstream. If fixes to other hardware  don't require testing I'll report them too.

But it would really be more efficient if the people who came up with the fixes (ie. Sytem76 or even users) would report them as they figure them out rather than making others dig to find them afterward. Having said that, the existing changelog and open source nature of the "System76 driver" are certainly helpful and appreciated.

---

