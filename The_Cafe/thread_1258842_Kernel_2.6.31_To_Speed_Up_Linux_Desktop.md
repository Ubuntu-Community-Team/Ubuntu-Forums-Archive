---
title: "Kernel 2.6.31 To Speed Up Linux Desktop"
date: 2009-09-05
forum: The Cafe
---

### Post by Excedio on 2009-09-05
[QUOTE=Slashdot]
Dan Jones writes

[I]"As the Linux community [looks forward to another kernel release]("http://lkml.org/lkml/2009/8/27/386"), the kernel hackers have been working on improving the memory management so that the [X desktop responsiveness is doubled under high memory pressure]("http://www.techworld.com.au/article/317416/kernel_2_6_31_speed_up_linux_desktop"). The result is an improved desktop experience. Benchmarks on memory-tight desktops show clock time and major faults reduced by 50 per cent, and pswpin numbers (memory reads from disk) are reduced to about one-third. Another [improvement coming with 2.6.31]("http://kernelnewbies.org/Linux_2_6_31") is kernel mode-setting support for ATI Radeon graphics cards, enabling faster user switching and a more seamless startup experience. Peripheral developments that will also improve the Linux desktop experience include support for the new USB 3.0 specification and a new Firewire stack. Even minor Linux releases have heaps of new features these days!"
[/I][/QUOTE]

Don't know if anyone has heard about this yet. I'm pretty excited about this, seeing at I'm an ATI user.

Thoughts?

---

### Post by snowpine on 2009-09-05
October's release, Karmic Koala, will use 2.6.31.

---

### Post by Copernicus1234 on 2009-09-05
Hadnt heard about this either before. Thats nice. :)

---

### Post by speedwell68 on 2009-09-05
Does that mean that the ATI card on my laptop will finally work properly?

---

### Post by phrostbyte on 2009-09-05
Preliminary synthetic benchmarks show about a 7-12% speedup over Ubuntu 9.04 for most desktop operations. Intel and ATI drivers also have improved significantly. 

:)

If you want to get an idea of some of the features in Karmic:
[http://d0od.blogspot.com/2009/08/new-features-ubuntu-karmic-910.html](http://d0od.blogspot.com/2009/08/new-features-ubuntu-karmic-910.html)

---

### Post by NormanFLinux on 2009-09-05
Using proprietary ATI drivers with the current kernel renders Linux unbootable.

---

### Post by andrek on 2009-09-05
Proprietary fglrx driver works flawlessly on karmic's 2.6.31, just make sure to use the latest one from the repo.

---

### Post by pt123 on 2009-09-05
I tried Karmic on my other computer, it did feel faster. Even pulse audio was working without a problem, it was quite cool being able to manage the audio volumes of the applications without stuttering from a single interface.

---

### Post by Ric_NYC on 2009-09-05
> **NormanFLinux said:**
> Using proprietary ATI drivers with the current kernel renders Linux unbootable.


Same thing here...

---

### Post by NormanFLinux on 2009-09-05
I have an ATI Radeon Mobility X1300 Card in my Dell Inspiron e1505 notebook and the proprietary ATI driver and fglrx does not seem to go together with Kubuntu Jaunty 9.04. It will simply not boot up to the KDM login screen.

---

### Post by handy on 2009-09-05
> **NormanFLinux said:**
> I have an ATI Radeon Mobility X1300 Card in my Dell Inspiron e1505 notebook and the proprietary ATI driver and fglrx does not seem to go together with Kubuntu Jaunty 9.04. It will simply not boot up to the KDM login screen.

Keep an eye on this thread, I'm attempting to keep it up to date with changes that matter to the ATi GPU's, particularly in regards to the open-source ATi drivers:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by coldReactive on 2009-09-05
Sounds like something we all need.

I just hope that the new kernel has Wifi working for [my netbook]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205") working out of the box.

---

### Post by Excedio on 2009-09-08
never understood why people have so many problems with ATI cards and drivers. I use ATI Radeon HD 3200 and it works flawlessly. Everything worked right out of the box, even the HD...

---

### Post by coldReactive on 2009-09-08
> **Excedio said:**
> never understood why people have so many problems with ATI cards and drivers. I use ATI Radeon HD 3200 and it works flawlessly. Everything worked right out of the box, even the HD...

You should've been here before when this bug was around:

[https://bugs.launchpad.net/fglrx/+bug/296497](https://bugs.launchpad.net/fglrx/+bug/296497)

---

### Post by handy on 2009-09-08
> **Excedio said:**
> never understood why people have so many problems with ATI cards and drivers. I use ATI Radeon HD 3200 and it works flawlessly. Everything worked right out of the box, even the HD...

My impression is that Ubuntu probably gets special attention with regard to Catalyst drivers being matched to the kernel, X.server & other associated package versions being used by a Ubuntu release.

Life is not that easy for the likes of Arch users who run close to the cutting edge & find Catalyst to be an incredibly unreliable thing, that half the time regresses more than it progresses with its releases.

Thankfully there is light at the end of the tunnel, as the open-source drivers are developing fast.  They have the best 2D support available now bar none, & 3D is getting closer every day. :)

---

### Post by Excedio on 2009-09-08
> **coldReactive said:**
> You should've been here before when this bug was around:
 
[https://bugs.launchpad.net/fglrx/+bug/296497](https://bugs.launchpad.net/fglrx/+bug/296497)
 
 
I see...
 
That sucks for those that had ATI when that was going on...but i'm happy that I have had no problems.

---

### Post by HappyFeet on 2009-09-08
I avoid all that nonsense by always buying nvidia.

---

### Post by handy on 2009-09-08
> **HappyFeet said:**
> I avoid all that nonsense by always buying nvidia.

When the question comes up, I too have always recommended nVidia; that is up until the last month. (I own both nVidia & AMD/ATi GPU systems.)

It has become obvious that soonish the AMD/ATi GPU is going to become the darling of the FOSS world.

See the following thread for the ongoing details, the AMD/ATi open-source drivers now have the best 2D available & 3D is coming fast:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by ELD on 2009-09-08
> **phrostbyte said:**
> Preliminary synthetic benchmarks show about a 7-12% speedup over Ubuntu 9.04 for most desktop operations. Intel and ATI drivers also have improved significantly. 

:)

If you want to get an idea of some of the features in Karmic:
[http://d0od.blogspot.com/2009/08/new-features-ubuntu-karmic-910.html](http://d0od.blogspot.com/2009/08/new-features-ubuntu-karmic-910.html)

Didn't catch that one, nice :)

---

### Post by modmadmike on 2009-09-08
Im already running the new kernel lol

---

### Post by MikeTheC on 2009-09-09
With apologies to Elton John...

"Goodbye Ekiga VOIP
Though I never knew you at all
You had the grace to install yourself
While those around you used something else..."

---

### Post by ELD on 2009-09-09
Ekiga will not be missed heh.

---

### Post by Excedio on 2009-09-09
To be honest...I will miss it and I will install it again. I work for a Video Relay Service and I've been playing around with Ekiga a lot to try and make it work as a viable Linux alternative for my company.

I can get it to call our products, but cannot seem to get video to work...only audio...

---

### Post by 3rdalbum on 2009-09-09
> **speedwell68 said:**
> Does that mean that the ATI card on my laptop will finally work properly?

Your ATI graphics is not supported by ATI/AMD on Linux anymore. The new kernel will not change this. You are very likely to see improved open-source support for it, but this is nothing to do with the kernel.

---

### Post by handy on 2009-09-09
Actually, I think there are changes in the kernel which will be of some benefit to the open-source ATi drivers. I can't remember what they are at the moment, if I remember or see a reminder I'll post what they are.

---

### Post by Exodist on 2009-09-09
> **Excedio said:**
> Don't know if anyone has heard about this yet. I'm pretty excited about this, seeing at I'm an ATI user.

Thoughts?

Yea, I am checking kernel.org everyday waiting for it to go stable. :guitar:

---

### Post by Exodist on 2009-09-09
> **NormanFLinux said:**
> Using proprietary ATI drivers with the current kernel renders Linux unbootable.

Say huh?

Which kernel you speaking up. 9.04s 2.6.28, current stable 2.6.30.5 or the unstable 2.6.31?

I have used the AMD/ATI Proprietary (9.7 and 9.8) drivers with both 28 and currently 30.5 kernels without a hitch.

So please clarify.

---

### Post by handy on 2009-09-09
It is complicated by the model GPU.

---

### Post by handy on 2009-09-09
> **handy said:**
> Actually, I think there are changes in the kernel which will be of some benefit to the open-source ATi drivers. I can't remember what they are at the moment, if I remember or see a reminder I'll post what they are.

Here is a good page regarding the changes to the kernel:

[http://www.h-online.com/open/Kernel-Log-Coming-in-2-6-31-Part-2-Graphics-audio-and-video--/news/113958](http://www.h-online.com/open/Kernel-Log-Coming-in-2-6-31-Part-2-Graphics-audio-and-video--/news/113958)

---

### Post by MasterNetra on 2009-09-09
Anyone know if OpenGL 2.0 is supported for Intel Cards in Karmic or will be? Or will I still have to wait to play savage 2?

---

