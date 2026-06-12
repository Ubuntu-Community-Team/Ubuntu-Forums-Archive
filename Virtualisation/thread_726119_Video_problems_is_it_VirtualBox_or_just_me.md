---
title: "Video problems: is it VirtualBox or just me?"
date: 2008-03-16
forum: Virtualisation
---

### Post by employeeno5 on 2008-03-16
Hi.
I have an Intel Core Duo 1.66Ghz with 2GB or RAM . My video card is an ATI Mobility Radeon X1300.
I could easily cut my computer's resources in half and would still have a machine that could run XP or Ubuntu splendidly.

Yet using VirtualBox, my video support is very poor. Even maxing out the virtual machine's video memory, I can't get the sample video clips that come with XP to run correctly, nevermind something streaming over the internet.

Things as simple as basic video playback aren't working correctly.
 My girlfriend has an old 500Mhz G3 ibook and even that can handle video playback and even effects like cover flow without a hiccup. 

I've tried turning off Xgl stuff which gave no improvement in performance. I even tried running VirtualBox in a seperate X server also with no results. I didn't expect much, as it seemed that shouldn't effect the contents virtual machine anyways. I did not know what else to try though to boost my video performance.

I've installed the guest addons and currently the VM is recognizing the virtualbox video adapter. 

Are these results to be expected with my level of machine using VirtualBox? Or have I missed something somewhere in setting it up, or is there something else I can do to improve performance. 

It would be nice to use our Netflix on demand service (among a few specific other Windows apps),  but I can't even play back a local video file correctly. 
Is it just my computer, or should I be able to get better video out of VirtualBox?

---

### Post by Hero of Time on 2008-03-16
Strange, I have about the same hardware specs and no problem whatsoever. My laptop has an Intel T2300 Core Duo 1.66 GHz processor, 2 GB RAM and an ATi x1400 Mobility Radeon. The performance is just fine. I just played an .mkv file h.264 and almost no slowdown. Only slowdown was because it came from my computer through the network. In case it would matter, what driver have you installed in Ubuntu, the restricted driver (aka Open Source) or the Propretary driver from AMD? I have the AMD driver installed. What CPU speed is registered on the system properties window in Windows? I have about 500 MHz (it should be around 500, currently it's 302 MHz) and 512 RAM, video RAM is default (8 MB).

Are you sure it's the CPU that is giving the problems? My CPU supports Virtualisation, thus it can be passed to a VM directly. Don't know if that would change things too.

---

