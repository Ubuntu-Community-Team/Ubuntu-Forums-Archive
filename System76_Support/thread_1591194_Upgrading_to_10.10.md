---
title: "Upgrading to 10.10"
date: 2010-10-08
forum: System76 Support
---

### Post by qkumbers on 2010-10-08
Hello all. I am a first time System76 customer and I'm quite excited about my new system. However, it is a tad bittersweet. I ordered a brand new Serval laptop, which just arrived yesterday. I have yet to even turn it on, but for whatever reason, I decided to browse the System76 site first, only to find that they are already taking orders for new machines with Ubuntu 10.10 installed. Clearly, I should have seen this coming, since the new Ubuntu release is only days away.
Basically, I'm here to ask for advise. What is my best bet? Do I simply do a sudo apt-get dist-upgrade shortly after the official release, or is it better to do a clean install? Are the System76 drivers updated for the new version? Can I update them in place? Since the new systems that are being shipped have 10.10, is there some sort of system CD that I can download and install on my new laptop?
Any advice is greatly appreciated.

---

### Post by nevius on 2010-10-09
> **qkumbers said:**
> Hello all. I am a first time System76 customer and I'm quite excited about my new system. However, it is a tad bittersweet. I ordered a brand new Serval laptop, which just arrived yesterday. I have yet to even turn it on, but for whatever reason, I decided to browse the System76 site first, only to find that they are already taking orders for new machines with Ubuntu 10.10 installed. Clearly, I should have seen this coming, since the new Ubuntu release is only days away.
Basically, I'm here to ask for advise. What is my best bet? Do I simply do a sudo apt-get dist-upgrade shortly after the official release, or is it better to do a clean install? Are the System76 drivers updated for the new version? Can I update them in place? Since the new systems that are being shipped have 10.10, is there some sort of system CD that I can download and install on my new laptop?
Any advice is greatly appreciated.

System76 uses stock ubuntu, but has their own driver repository. You download Ubuntu 10.10 here when it is released tomorrow (10/10/2010): [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I personally would wait a few weeks for new bugs to get squashed (initial releases can be buggy) and for System76 to release 10.10 drivers.

You might want to consider keeping 10.04 unless there is a new feature in 10.10 that you must have. 10.04 is an LTS version, which means it will in the long-run be more stable and will get security updates for a longer period of time. See here: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by nevius on 2010-10-09
You should also check out the following on the System76 Knowledge base:

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by Eyore15 on 2010-10-10
The broader question is whether or not the new 7system76 driver is ready for prime time.  The last two releases, if I recall correctly, there was a lag time between the ubuntu release and a viable driver -- at least for the netbook version of ubuntu used on the Starling.  I've got the new iso ready to go, but want some assurance that once i complete the install, it's going to work.

---

### Post by HotShotDJ on 2010-10-10
> **Eyore15 said:**
> The broader question is whether or not the new 7system76 driver is ready for prime time...I've got the new iso ready to go, but want some assurance that once i complete the install, it's going to work.Firstly, the System76 driver worked just fine on my PanP5.  I can't give you 100% assurance that you'll have no trouble (fortunately, that isn't what you asked for :)).  But I had no trouble doing an in-place upgrade.  I ran into some issues that I discuss [here]("http://ubuntuforums.org/showthread.php?t=1587526").  You might want to try running from the CD to test some things out before committing to the install.  Testing this way isn't fool-proof, but it can save you some hair-pulling if there are some big problems with the upgrade and your hardware.

---

### Post by qkumbers on 2010-10-10
If I understand correctly, it seems like the current System76 drivers will work with Ubuntu 10.10, but how do I know if and when they will release official drivers for 10.10? I looked at the System76 driver repository and they have version numbers, but there is no indication with which version of Ubuntu they are compatible with. Also, is it a single driver package regardless of what system you have (various laptop models, desktop models, etc)?

Finally, since I don't have anything on my system yet, I'm considering just doing a clean install. I noticed a couple of programs that were installed on top of the default (Cheese, GnuCash, etc), but is there anything else I'll need to download or do to my laptop post-install?

---

### Post by jdb on 2010-10-10
> **qkumbers said:**
> If I understand correctly, it seems like the current System76 drivers will work with Ubuntu 10.10, but how do I know if and when they will release official drivers for 10.10? I looked at the System76 driver repository and they have version numbers, but there is no indication with which version of Ubuntu they are compatible with. Also, is it a single driver package regardless of what system you have (various laptop models, desktop models, etc)?

Finally, since I don't have anything on my system yet, I'm considering just doing a clean install. I noticed a couple of programs that were installed on top of the default (Cheese, GnuCash, etc), but is there anything else I'll need to download or do to my laptop post-install?

When Ubuntu 10.10 is officially released, system 76 will then or very shortly thereafter release a driver for it.

If you load Ubuntu 10.10 and then install the system 76 drivers for 10.10, your machine will be exactly like one that ships from system 76. The driver includes GnuCash or anything else extra that they put on their machines.

10.04 being a long term release is a good thing, unless you just have to have the latest & greatest, you may think about sticking with 10.04.

jdb

---

### Post by lue42x on 2010-10-10
I did a fresh install of 10.10 on my Lemur1 and installed the System76 driver.  

What is the difference between the "Restore" button and the "install" button in the System76 Driver software?  I clicked Restore cus I remember the Knowledge76 site said that.

My function keys (for screen brightness) don't seem to be working, and the suspend function for the lemur isn't working either.  I figure I should have waited a little while to give the Sys76 people some time to update the driver (if it is indeed a driver problem, and not just me doing soemthing wrong without realizing it) but I was excited to try the new Ubuntu.  Everything else seems to work well though, laptop is running smoothly.

Should I try clicking "install" in teh Sys76 driver instead of "restore"?

---

### Post by isantop on 2010-10-12
Everything should be working on the Lemur out of the box in 10.10. This may not be the case; we've yet to hear back from customers with feedback about what works and what doesn't I'd create a 10.10 LiveCD and try it from that.

The driver for 10.10 is released. Basically, if it works on a given version of Ubuntu, it's an official release on that version.

"Install" just installs drivers. "Restore" installs drivers and additional applications (Like GnuCash, Cheese, etc.) that otherwise doesn't come with Ubuntu.

---

### Post by lue42x on 2010-10-26
I also did a fresh install of 10.10 on my Lemur 1.  Everything seems to be working fine except for two things I noticed:

(1) brightness function keys are not working
(2) battery meter doesn't work (it appears, but seems stuck at the "(estimating...)" phase

---

### Post by Noah0504 on 2010-10-26
> **lue42x said:**
> I also did a fresh install of 10.10 on my Lemur 1.  Everything seems to be working fine except for two things I noticed:

(1) brightness function keys are not working
(2) battery meter doesn't work (it appears, but seems stuck at the "(estimating...)" phase

I had the battery issue on my PanP6.  I just went back to 10.4.  Everything works there.  :)

---

### Post by thomasaaron on 2010-10-27
We've found a work-around for the battery estimation. Please contact us at support---at---system76---dot---com so we can add you to the list of people we are suggesting it to.

We're hoping it finds its way into the kernel soon.

---

### Post by lue42x on 2010-10-27
Will do Tom, thanks

I'm going to try the gnome top bar applet for dimming the screen brightness for now until the brightness function keys are working again

---

