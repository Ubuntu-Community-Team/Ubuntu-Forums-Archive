---
title: "Any idea when Intrepid Ubuntustudio will have the RT kernel?"
date: 2008-11-08
forum: Ubuntu Studio
---

### Post by Ng Oon-Ee on 2008-11-08
Hi all, I've seen the mailing lists/announcement on why Ubuntustudio 8.10 doesn't have the RT kernel. No problem with that.

So I'm starting this thread to ask whether anyone knows when the 2.6.27-rt kernel will be reasonably functional for Ubuntu Studio and when it will be added to the repositories. Alternatively, any Ubuntu Studio specific forums that I've missed in my checks with Mr. Google?

Maybe we could all subscribe to this thread, for info-sharing, so the first person that realizes its out can just post here :D

---

### Post by Stochastic on 2008-11-08
It's in the repos right now (as of writing this, it's version 2.6.27.3.4-rt), it's just not 100% functional/bug-free so it's not included in the ubuntustudio-audio package by default.  I actually have it installed as well as the vanilla and boot into it whenever I need to utilize the realtime functions.

---

### Post by otz070 on 2008-11-08
I myself have been wondering about this too.
Would you happen to have a link to or know of any of major unresolved bugs/unstabilities? As I understand you (Stochastic) are using this now? so are the bugs ect. bad enough that you would recommend waiting for a full fix? In case your wondering I ask because I run rt kernal as default, audio or not. 
Anyone know when or about how long till rtkernal will be fully stable I'd like to run Intrepid but don't want to risk my stability?

---

### Post by Stochastic on 2008-11-08
As I've said here and elsewhere before, I'm no kernel guru.  Here's the linux-rt bug report page in launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux-rt](https://bugs.launchpad.net/ubuntu/+source/linux-rt)
I haven't had the time to run the RT kernel much this month (too many homework deadlines & grant proposals, etc..) so I can't really devise much of a list of issues myself.

I don't see why having two different kernels installed is that big of deal, just use grub to boot the desired kernel when you startup.  I realize for strict DAW computers the RT would be all you need, but because it's lacking some features, throw the vanilla on your box too and switch away in the boot menu.

---

### Post by Ng Oon-Ee on 2008-11-08
I believe the two major issues were only seeing a single core in dual-core systems as well as bad (non-existant) support for hibernate/suspend.

The 2nd isn't that big a deal, the first... Maybe if you're using an older system it won't be that big a deal.

Thing is I'm getting lots of iritating xruns, so maybe I'll give the version in the repos a try.

---

### Post by otz070 on 2008-11-08
> As I've said here and elsewhere before, I'm no kernel guru. Here's the linux-rt bug report page in launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux-rt](https://bugs.launchpad.net/ubuntu/+source/linux-rt)
I haven't had the time to run the RT kernel much this month (too many homework deadlines & grant proposals, etc..) so I can't really devise much of a list of issues myself.
Thanks for the link, and thats quite understandable:D

> believe the two major issues were only seeing a single core in dual-core systems as well as bad (non-existant) support for hibernate/suspend.

The 2nd isn't that big a deal, the first... 

I would have to agree with this, I definitly have to have dualcore support as I often run blender renders during the same session (Rendering is better with more cores) So I will probably be waiting for a newer stable version to come out until I upgrade to intrepid. I'll have to keep watching the bugs lists:)

---

### Post by Ng Oon-Ee on 2008-11-09
Just tried out the current kernel. It works in that xruns are just about gone even at 2 ms latency, but single core :(. Also, my X died when I rebooted the first time, but the problem was that my nvidia drivers needed recompiling, I just booted to safe graphics mode and reinstalled. DKMS only works with newer kernels than the current one, I think, not older (for example, from generic-7 to rt-3).

Will dual-boot for a while, till a better one comes along.

---

### Post by Stochastic on 2008-11-09
I feel ironically lucky to have a single core processor and an ATI graphics chip.  Wow, I never thought I'd see the day.;)

---

### Post by sonicmaker on 2008-11-10
Does anyone know whether the lack of dual core support is due to the RT patch, or whether it's a problem of the kernel itself?

I've compiled my own RT kernel to use with UbuntuStudio, as I need to use the proprietary ATI graphics drivers and under the kernel from the repos I can't compile it - GPL-only pointer error or something like that. So not cool.

But yeah, any ideas? If it's just to do with that patch, I'll just compile my own again. A few hours extra effort, but my graphics card works.

---

### Post by Ng Oon-Ee on 2008-11-10
> **sonicmaker said:**
> Does anyone know whether the lack of dual core support is due to the RT patch, or whether it's a problem of the kernel itself?

I've compiled my own RT kernel to use with UbuntuStudio, as I need to use the proprietary ATI graphics drivers and under the kernel from the repos I can't compile it - GPL-only pointer error or something like that. So not cool.

But yeah, any ideas? If it's just to do with that patch, I'll just compile my own again. A few hours extra effort, but my graphics card works.
From the bug-list at launchpad, its due to some incompatibility with the RT patch and the kernel. The reporter surmises that a particular variable has been wrongly set at compile-time. You could try to recompile changing that variable to see if it helps, if it does I'd suggest you submit the update to launchpad so someone can look it over.

I've never done kernel compilation myself before, so can't really offer any help there. Please let me know if it works though, its something I've been meaning to make time for someday (like everything else, come to think of it...).

But a word of caution, this may not be related to the kernel directly, but it may. For example, I think the shutdown/hibernate/suspend problems have been directly traced to misbehaviour between the RT patch and the network manager.

---

### Post by Ng Oon-Ee on 2008-12-17
I assume there's no updates on the above?

---

### Post by Arup on 2008-12-18
I see a real time kernel in my Intrepid x64 repos now.

---

### Post by Ng Oon-Ee on 2008-12-18
> **Arup said:**
> I see a real time kernel in my Intrepid x64 repos now.
Yes, rt-3, which has been there since release of Intrepid. Doesn't use more than one core, though, and has problems with shutting down (disagrees with network manager).

That's the reason its not included in the default Studio install.

---

### Post by Stochastic on 2008-12-18
> **Ng Oon-Ee said:**
> I assume there's no updates on the above?

I'm certain you'll hear an announcement when there's any change to the rt status in Intrepid.  Until then, just keep watching launchpad (you can subscribe to a package to get e-mail updates, or watch its RSS feed to make everything really easy).

The good news is, at the Jaunty UDS there seems to have been a lot of kernel workflow/schedule discussion...  hopefully issues like this one can be avoided in the future.

---

### Post by Ng Oon-Ee on 2008-12-18
> **Stochastic said:**
> I'm certain you'll hear an announcement when there's any change to the rt status in Intrepid.  Until then, just keep watching launchpad (you can subscribe to a package to get e-mail updates, or watch its RSS feed to make everything really easy).

The good news is, at the Jaunty UDS there seems to have been a lot of kernel workflow/schedule discussion...  hopefully issues like this one can be avoided in the future.
Thank you. I was also wondering what would come out of the UDS W.R.T the alternative kernels. The late decision to jump to .27, while arguably the right decision, it really affected the alternative kernels.

---

### Post by Ng Oon-Ee on 2009-01-31
Oh well, by this point in time I'm pretty certain there won't be an RT for Intrepid. Just looking towards Jaunty then. Hardy wasn't very good for me, don't want to go back to tweaking it around =).

---

### Post by raboofje on 2009-01-31
> **Ng Oon-Ee said:**
> I believe the two major issues were only seeing a single core in dual-core systems as well as bad (non-existant) support for hibernate/suspend.

For me, [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/300806](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/300806) is the show-stopper: it makes USB MIDI unusable for 'live' playing.

---

### Post by shockdiode on 2009-02-01
I wonder why they don't just ship a kernel with preempt enabled and the interrupt timer set to 1000HZ without the RT patches?

I've tested this out by compiling with these options from the ubuntu kernel sources on 8.10 and it performs very well with jack.

Anyone know?

---

### Post by Ng Oon-Ee on 2009-02-01
> **shockdiode said:**
> I wonder why they don't just ship a kernel with preempt enabled and the interrupt timer set to 1000HZ without the RT patches?

I've tested this out by compiling with these options from the ubuntu kernel sources on 8.10 and it performs very well with jack.

Anyone know?
I've never tried that out, but I did compile a custom kernel (zen kernel), didn't play very nicely with Jack unfortunately, and some other issues with my particular hardware made me go back to the default kernel in Intrepid.

Do you have any numbers concerning 'performs very well'? Latencies etc?

---

### Post by shockdiode on 2009-02-01
> **Ng Oon-Ee said:**
> I've never tried that out, but I did compile a custom kernel (zen kernel), didn't play very nicely with Jack unfortunately, and some other issues with my particular hardware made me go back to the default kernel in Intrepid.

Do you have any numbers concerning 'performs very well'? Latencies etc?

With an M-audio mobile-pre usb box that I use for home recording and the following startup for jack:

 /usr/bin/jackd -R -P70 -u -dalsa -dhw:2 -r48000 -p128 -n3 -H

It runs fine with several tracks in ardour, hydrogen running, etc. Ardour reports the latency as 2.7 ms but I believe that is wrong as I'm using 3 periods for the buffer (-n3) due to it being a usb device and this being recommended. qjackctl reports 8ms for these settings, I'm not sure which is correct as the jackd manual states the capture latency is period/rate which would indeed be 2.7 ms.

At any rate, this matches the lowest latency I've been able to get out of this device without xruns in many kernel/jackd version combinations over the years. 

With the generic kernel shipped with intrepid, i get horrid xruns on this device even with -p at 1024 which is unusable for recording for me. 

Hope that answers your question.

---

### Post by shockdiode on 2009-02-01
FYI, just in case anyone wants to give it a shot. Here's the contents of the config file I used (compiling ubuntu style from ubuntu sources) that differs from config.generic:

CONFIG_DEBUG_PREEMPT=y
CONFIG_DEFAULT_CFQ=y
# CONFIG_DEFAULT_DEADLINE is not set
CONFIG_DEFAULT_IOSCHED="cfq"
CONFIG_HZ=1000
# CONFIG_HZ_100 is not set
CONFIG_HZ_1000=y
# CONFIG_HZ_250 is not set
CONFIG_PREEMPT=y
# CONFIG_PREEMPT_NONE is not set
# CONFIG_PREEMPT_RCU is not set
# CONFIG_PREEMPT_TRACER is not set
# CONFIG_PREEMPT_VOLUNTARY is not set

---

### Post by Ng Oon-Ee on 2009-02-02
I've been checking the Ubuntu-studio-users mailing list, and there's discussion there about 2.6.28-generic working reasonably well WITHOUT the RT patches. Patched 2.6.28 also works, it seems, with a few bugs remaining (the USB MIDI is mentioned).

Looks like I'll be an early adopter for Ubuntu Studio Jaunty then =). Intrepid has been pretty good, really, except for the RT kernel problems and the ffmpeg/medibuntu stuff.

---

### Post by shockdiode on 2009-02-02
Funny you should mention that. I have started seeing some xruns now (weird that I wasn't seeing them initially) with the configuration I mentioned earlier on 2.6.27 kernel compiled with preempt enabled and the interrupt timer set to 1000HZ -doh.

I'm testing out the same configuration on the 2.6.28 kernel sources from Jaunty and so far so good (except onboard hda-intel sound no longer works with this kernel - i think it probably wants a newer alsa-lib or something). Yeah, it looks like waiting on Jaunty is probably the way to go.

---

