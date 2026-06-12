---
title: "ATi Open drivers are coming of age... :)"
date: 2009-08-12
forum: The Cafe
---

### Post by handy on 2009-08-12
* - deleted redundant data 24-August-10. Added Gallium link 26-October-10. Added Fan Control 15-November-10. Power Management how-to re-added on 22-November-10. Refined the Ubuntu Stuff how-to & updated due to progress on the North Island GPU 13-3-11. Made note of the acceptance of Gallium as the default open-source AMD driver stack, & added link to benchmark & discussion on the topic - 9-June-11. Updated text, added a links which provides detailed Catalyst removal instructions; courtesy of Temüjin - 11-June-11. Over the last couple of months I've picked up about 400fps in (the not a benchmark) glxgears, on my HD2600 Pro, which is nice - 24-August-11.*

[B][I]For anyone interested in seeing just how the open-source support is coming along for the various ATi cores, this is the easiest way to get the picture:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)[/I][/B]

The following link is available on the above page but here is the **Gallium** stuff anyway:

[http://www.x.org/wiki/GalliumStatus](http://www.x.org/wiki/GalliumStatus)

**[edit:]** Now that the Gallium driver stack has taken over, the information on the "Classic Mesa" stack is basically redundant for the many.

Following is a link to a very worthwhile read from the Phoronix site. At the current time of writing, it brings us up to date:

**May 2011: Gallium3D vs. Classic Mesa vs. Catalyst**

[http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011](http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011) 
_________________________


I thought that I probably should put the following information out here in a dedicated thread, for those that aren't aware of what is going on with the AMD/ATi open-source drivers:

Because AMD/ATi's Catalyst drivers have been so unreliable, it has caused & is causing a great deal of work to go into the ATi open-source drivers & associated packages.

*The oft neglected reality, is that AMD have been releasing technical info' on the ATi GPUs, & contributing some code. Without AMD having done this, the open-source ATi drivers would not be developing at the rapid rate that they currently are.  So in this regard, gratitude to AMD is most certainly in order.*

The current open-source ATi GPU drivers are giving many people the best 2D performance they have ever had on their ATi GPU's, I can verify this because I'm one of them. At this stage the 3D is working well but still too slow for games with sophisticated 3D graphics & lots of movement. Though the quake engined games play quite well with the open source packages.

Since AMD released the tech' info' for the ***_Evergreen_*** & now the (current) ***_North Island_*** series of GPUs, work has been moving fast & now at last the open-source support for the current ATi GPUs is starting to manifest. 

Ubuntu 11.4. is using the Gallium driver stack, the classic Mesa is now deprecated.
For users that want to use later versions of the kernel &/or the Gallium driver stack, there is a simple how-to in the "Ubuntu Stuff:" section further down the page.
___________________________

[SIZE="3"]**I'll continue to put any links that I find to be useful on this topic here:**

[/SIZE]

**X.org:**

_[http://www.x.org/wiki/GalliumStatus](http://www.x.org/wiki/GalliumStatus)_

_[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)_

_[http://wiki.x.org/wiki/RadeonProgram](http://wiki.x.org/wiki/RadeonProgram)_


**Arch stuff:**

Arch ATi how-to from the wiki, quite informative:

[http://wiki.archlinux.org/index.php/Ati#](http://wiki.archlinux.org/index.php/Ati#)


**Ubuntu stuff:**
[I]========================================
For Ubuntu users, this is a how-to for upgrading your kernel & the rest of the driver stack so you can use the latest git versions, which usually offer added features & better performance than those supplied in the most current Ubuntu version. 

This how-to is now followed by another for getting Power Management working courtesy of a post in this thread by Untitled_No4: :)

**Do the following in the order listed:**

1. System -> Hardware Drivers -> Deactivate any ATI drivers and restart. (If you need more detailed instructions on this go [here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx").)

2. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
& pick the version of the kernel you want to use, (I am on Arch & using the current kernel .**-git & the -git versions of the other required packages with no problems. So keeping an eye on the last parts of this thread should let you know if there are any current problems).

3. Download and execute the following (in this order, switch to 64 if need be)
- linux-headers...all.deb
- linux-headers..generic..i386.deb
- linux-image....i386.deb

4. Restart

5. Add the xorg-edgers PPA ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)) 

6. **update & upgrade**:

```
sudo apt-get update
sudo apt-get dist-upgrade

```
7. Reboot.

8. Profit. :)


**Power Managment:**
========================================[/I]

**With KMS:**
   There are two sys-files in /sys/class/drm/card0/device:
       power_method: Here you can switch between dynpm and profile method.
       power_profile: If you have enabled profile method you can choose between default low, high and auto (select between low and high based on ac/dc state)
   For example: echo profile > /sys/class/drm/card0/device/power_method
[B]
Without KMS:[/B]
    In your xorg.conf file, add 2 lines to "Device" Section:
            Option      "DynamicPM"                   "on"
            Option      "ClockGating"                  "on"
    --------
    If the two options are enabled successfully, you will see following lines in /var/log/Xorg.0.log:
            (**) RADEON(0): Option "ClockGating" "on"
            (**) RADEON(0): Option "DynamicPM" "on"
            ......
            Static power management enable success
            (II) RADEON(0): Dynamic Clock Gating Enabled
            (II) RADEON(0): Dynamic Power Management Enabled
    --------
    If you desire low power cost, you can add an extra line to "Device" Section of xorg.conf:
            Option      "ForceLowPowerMode"   "on"


Thanks to Perry3D at the Arch forum for the above.
________________________


**A Free Way to Cool OFF Your Stock ATi/AMD GPU:**

[http://forums.amd.com/forum/messageview.cfm?catid=13&threadid=109000&messid=970779&parentid=970616&FTVAR_FORUMVIEWTMP=Single](http://forums.amd.com/forum/messageview.cfm?catid=13&threadid=109000&messid=970779&parentid=970616&FTVAR_FORUMVIEWTMP=Single)

*(thanks to tomazzi & olof_ for bringing the above to my attention :))*
____________________


**About/identify your AMD/ATi GPU:**

[http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units](http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units)


This page contains information about Radeon chipset naming, and some other, possibly outdated information:

[http://dri.freedesktop.org/wiki/ATIRadeon#head-a2d41d14a2c9b0da964aa1b7226ebab238532abe](http://dri.freedesktop.org/wiki/ATIRadeon#head-a2d41d14a2c9b0da964aa1b7226ebab238532abe)

---

### Post by xir_ on 2009-08-12
i got a new laptop with a hd4330 and the binary drivers are horrid, really just horrid.

i'm considering going back to the open source drivers. but i hear the power management is poorer on these. What are your experiences?

---

### Post by Barrucadu on 2009-08-12
Unfortunately I still have awful performance with the FOSS drivers - OpenGL is completely unusable.

---

### Post by stwschool on 2009-08-12
I'm certainly curious to see where this leads. I've got one NVidia box and an ATI laptop and I have intel machines at work so I want to see excellent drivers on all. At 9.04's release I'd say only NVIDIA was any good. The intel drivers were reliable and you could play Wine games on them but they were slow (and still are).

The ATI situation is interesting though. I downloaded and installed the new drivers directly from ATI and found a massive improvement in quality, reliability and performance, obviously your mileage may vary. Now if that's rocking and the open-source drivers are getting good too then that's a winner for all of us. So, all we need is better intel drivers and we'll have very high quality across all 3 platforms.

---

### Post by racerraul on 2009-08-12
I'll jump ship when things get where they need to be for ATI drivers to provide all the power the HW is capable of...

By then it may be time to upgrade my Nvidia cards.

---

### Post by handy on 2009-08-12
> **xir_ said:**
> i got a new laptop with a hd4330 and the binary drivers are horrid, really just horrid.

I'm considering going back to the open source drivers. but I hear the power management is poorer on these. What are your experiences?

Sorry man, I'm no expert on the open-source ATi stuff.  I don't use a notebook so I can't comment from personal experience.  It wouldn't surprise me if the power management wasn't up to par, it is very likely (to my mind anyway) one of the things you would deal with later rather than earlier. 

To find out about what is being worked on, on the cutting edge on this subject is not an easy thing to do on the web, if you have a look at this site it may be the easiest solution, if you do I'd head for the last 5 pages or so:

[http://bbs.archlinux.org/viewtopic.php?id=57084&p=1](http://bbs.archlinux.org/viewtopic.php?id=57084&p=1)

> **Barrucadu said:**
> Unfortunately I still have awful performance with the FOSS drivers - OpenGL is completely unusable.

It has very recently got great for 2D for many cards, 3D is just starting to happen for many cards, as those who are using packages from .git are finding. I think it would be a good idea to keep an eye on it Barrucadu as it is changing quickly.

> **stwschool said:**
> 
I'm certainly curious to see where this leads. I've got one NVidia box and an ATI laptop and I have intel machines at work so I want to see excellent drivers on all. 

Intel see their major market being in Asia, so their graphics hardware is middle of the road at best.  Though they are offering better Linux driver support lately.

> **stwschool said:**
> 
The ATI situation is interesting though. I downloaded and installed the new drivers directly from ATI and found a massive improvement in quality, reliability and performance, obviously your mileage may vary. 

The way it is with the AMD/ATi Catalyst drivers, is that you take pot luck every time a new Catalyst version is released; sometimes they are better, other times they are worse... 

> **stwschool said:**
> 
Now if that's rocking and the open-source drivers are getting good too then that's a winner for all of us. So, all we need is better intel drivers and we'll have very high quality across all 3 platforms.

The open-source drivers are getting better & really quickly lately.  Intel will get better as their perceived market in Asia demands/can afford it.

The bottom line is that people with ATi GPU's should keep an ear to the ground as the FOSS people have got some momentum on for you at the moment.

---

### Post by CharmyBee on 2009-08-12
> **Barrucadu said:**
> OpenGL is completely unusable.

Same here. The driver isn't very good if it's treating your card as an expensive 2D overlay. You might as well stick a s3 Trio 64v in there, it's just as good.

---

### Post by spoons on 2009-08-12
It seems to be getting better and better but by the time some decent 3D appears it'll probably be a good 6-12 months before a distro has it, as we have to wait until the next Mesa build and then hope it comes in the Ubuntu right after that.

---

### Post by Regenweald on 2009-08-12
Thanks for the update handy, from what I've been reading on Phoronix, for a next build I'd gamble on a full AMD platform. I could live without 3d for a bit :)

---

### Post by Barrucadu on 2009-08-12
> **handy said:**
> It has very recently got great for 2D for many cards, 3D is just starting to happen for many cards, as those who are using packages from .git are finding. I think it would be a good idea to keep an eye on it Barrucadu as it is changing quickly.

As soon as another kernel (or whatever) upgrade breaks Catalyst again I'll check out the git version :)

---

### Post by tcturner on 2009-08-12
tormod volden ppa is excellent google it

---

### Post by Firestem4 on 2009-08-12
I'm not sure why but my ATI 1950Pro 512mb from DaimondMM runs perfectly on Kubuntu 9.04 (performance, KWin effects, etc). Haven't tried any actual games yet because i haven't been able to get sound to work so i didn't wanna do too much to it before I did anything.

(also i have added no extra drivers..did a vanilla install of Kubuntu 9.04 and it works OoTB)

Glad to hear the ATI drivers are improving though as I am a huge ATI fan. With them releasing the specs on so many of their chipsets/GPU's it should help tremendously with the development of ATI drivers.

---

### Post by Ranax on 2009-08-12
I wish I could agree with this, but I find the total opposite to be true. I have been using bleeding edge Radeon OPSO drivers for about 3 months now and they have been pretty bad. They serve 2D ok, but for 3D they are useless. I know this will hopefully improve in the future, but at the minute they may as well just be called Compiz enablers.

---

### Post by Methuselah on 2009-08-12
For a long time I used ATI open drivers and passed on 3D.
When I needed 3D I had no choice but to go with NVidia despite hating binary blobs.
Unfortunately, I would have had to use ATI's blob to get 3D and NVidia's was the lesser of two evils.
This time, I'll wait until ATI's open drivers are ready before going with them again.

---

### Post by Ranax on 2009-08-12
> **Methuselah said:**
> For a long time I used ATI open drivers and passed on 3D.
When I needed 3D I had no choice but to go with NVidia despite hating binary blobs.
Unfortunately, I would have had to use ATI's blob to get 3D and NVidia's was the lesser of two evils.
This time, I'll wait until ATI's open drivers are ready before going with them again.

I can only hope that they improve to a level beyond the horrible Intel linux drivers.

---

### Post by handy on 2009-08-13
I just read over on the Arch forums, that there was an update yesterday to the development drivers & people were commenting on the speed increase in 3D.

They are really happy with just how fast the dev's are working on this stuff.

---

### Post by kk0sse54 on 2009-08-13
I've been using the open source driver for the last few months because 1) There's no proprietary ATI driver for FreeBSD and 2) ATI dropped support for my card anyways, but overall I've been quite impressed. I've been getting better video performance with my Fbsd gnome + compiz setup than before with the closed source drivers. Although other than compiz I don't really need 3D as I don't play games or anything else of that nature.

---

### Post by madjr on 2009-08-14
> **handy said:**
> I just read over on the Arch forums, that there was an update yesterday to the development drivers & people were commenting on the speed increase in 3D.

They are really happy with just how fast the dev's are working on this stuff.

how can we try this on ubuntu?

---

### Post by handy on 2009-08-14
> **madjr said:**
> how can we try this on ubuntu?

Someone else will have to give you that run down.

Personally, if you can, I'd wait a while, as, as far as 3D support is concerned you will most likely be disappointed; 2D is great, though it is possible that some ATi GPU's aren't supported, on this I can't say for sure.  

The best I can do is tell you that I've not heard any complaints in the Arch thread in regard to 2D.

3D seems to be moving along quickly, but that "quickly" is a relative term, as it is closely bound with the perceptions of quality. :)  

Some people are far more impatient than others...

The later posts in the link below will give you info' regarding what the Arch guys are using, how you deal with that in Ubuntu is your business, though I do ask, if anyone does apply those packages in Ubuntu, could you please post how you did it, & your experience here in this thread?

*_[http://bbs.archlinux.org/viewtopic.php?id=57084&p=1](http://bbs.archlinux.org/viewtopic.php?id=57084&p=1)_*

---

### Post by ssri on 2009-08-14
> **madjr said:**
> how can we try this on ubuntu?

You can check the latest of the latest from obtaining the source from git and compiling yourself

[http://ubuntuforums.org/showthread.php?t=1017975&highlight=ati+xserver-video-ati+slow](http://ubuntuforums.org/showthread.php?t=1017975&highlight=ati+xserver-video-ati+slow)

Tormod Voldon's packages tries to keep up with the latest developments:

[https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)

For more stable upstream releases try:

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by rocknrolf77 on 2009-08-14
Personally, I'm sick of the catalyst driver. 1 month everything works fine and the next nothing works. Why the hell can't they support the newest kernel like nvidia does? Bought an ati card, because amd never let me down earlier and I always support the underdog + you get most bang for your buck with ati cards. Can't afford nvidia's prices. 

But it's nice to hear the good news about the open driver these days.

---

### Post by tom66 on 2009-08-14
Unfortunately my Mobility Radeon HD 3400 in 3D is only supported for proprietary drivers. Accelerated 2D support is available. But at the rate that development is happening, a working FOSS driver should be available within 1 year.

Edit: Just read some info, it says that they've got 3D support for my hardware but it's very buggy right now... looks like it might be sooner than I thought. :)

---

### Post by handy on 2009-08-14
In future, I'll add any useful sites I come across, regarding this topic, at the bottom of [**_Post_1_**]("http://ubuntuforums.org/showthread.php?t=1238129") of this thread:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

[http://wiki.x.org/wiki/RadeonProgram](http://wiki.x.org/wiki/RadeonProgram)

[http://bbs.archlinux.org/viewtopic.php?id=57084&p=1](http://bbs.archlinux.org/viewtopic.php?id=57084&p=1)

[http://www.phoronix.com/scan.php?page=category&item=Display%20Drivers](http://www.phoronix.com/scan.php?page=category&item=Display%20Drivers)

---

### Post by handy on 2009-08-18
Catalyst 9.8, has been quite recently released.

It is working with the .30 kernel, without patches & is behaving much better than it has been lately.

It still has problems of course.

Many think it has been produced for the upcoming Ubuntu release?

---

### Post by sideaway on 2009-08-18
What about us obsolete folk? :(

I'm sitting on an x1400, and they've ditched me, rejected me for the younger model. I feel like an old worn out hoo... Won't go there. Anyways, I want proprietary support! Or atleast open the source code of the drivers so we can get some decent ones.

---

### Post by handy on 2009-08-18
As previously stated in this thread; the open-source ATi driver development is moving fast.  

There are links at the bottom of the first post which should hopefully verify that your card has an open-source future dawning soonish...

---

### Post by ssri on 2009-08-19
> **handy said:**
> As previously stated in this thread; the open-source ATi driver development is moving fast.  

There are links at the bottom of the first post which should hopefully verify that your card has an open-source future dawning soonish...

If soonish means by next summer, then you are correct.  As for TVOut though, it is still unworkable in R500s.  That means I have to reboot to winxp in order to make my presentations or watch video from my laptop on my TV.

---

### Post by handy on 2009-08-19
> **ssri said:**
> If soonish means by next summer, then you are correct.  As for TVOut though, it is still unworkable in R500s.  That means I have to reboot to winxp in order to make my presentations or watch video from my laptop on my TV.

I don't personally know when, soonish means what, & for which GPU?

All I know is that it is all in the works, not on the backboard.

I, as does most every other user of a Linux/BSD system endowed with an ATi GPU, live in perpetual hope, that the open-source solutions to our many GPU problems will appear today. :)

---

### Post by ssri on 2009-08-19
> **handy said:**
> I, as does most every other user of a Linux/BSD system endowed with an ATi GPU, live in perpetual hope, that the open-source solutions to our many GPU problems will appear today. :)

I completely agree with you 100%.  Although, my hope is tempered by a dash of realism ;).  Still, the drivers are undoubtedly improving and have come a long way.  Hopefully we ATI users will reach the promise land someday.

---

### Post by handy on 2009-08-19
> **ssri said:**
> I completely agree with you 100%.  Although, my hope is tempered by a dash of realism ;).  Still, the drivers are undoubtedly improving and have come a long way.  Hopefully we ATI users will reach the promise land someday.

As previously stated, I no longer rely on the Catalyst drivers, as I don't need 3D on my Arch install, & the open-source drivers now provide me with the snappiest 2D the machine has ever experienced.  

That change just happened one day.

I only use the public release packages not the pre-release versions.

The same thing is going to happen with 3D & the open-source drivers, it is already happening for some GPU's using the pre-release packages.

---

### Post by nomnomnom on 2009-08-23
nutkinnz waz ere' init

---

### Post by yodermk on 2009-08-31
Any chance that Karmic will have newer ATi 3D support? (I have a 3200HD.)

I refrained from installing the proprietary blob in Jaunty in hope that open source support would be ready for Karmic. Not sure if I can wait for the L release ...

---

### Post by handy on 2009-08-31
> **yodermk said:**
> Any chance that Karmic will have newer ATi 3D support? (I have a 3200HD.)

I refrained from installing the proprietary blob in Jaunty in hope that open source support would be ready for Karmic. Not sure if I can wait for the L release ...

I don't know, check out the links at the end of the first post in this thread, you should learn something useful with regard to the open-source drivers & your GPU, there.

Most people find the current Catalyst version 9.8 is reasonably good from what I read.

Quite a few people think that the reason the current Catalyst version is working better, is due the upcoming Ubuntu release.

Use Catalyst if you have to, to meet your 3D needs.  Though the day is fast approaching when you won't need Catalyst.  

It is wise to temper the above statement with an understanding for the range of various values that people will place on the pertinent variable "fast". :)

---

### Post by madjr on 2009-08-31
> **yodermk said:**
> Any chance that Karmic will have newer ATi 3D support? (I have a 3200HD.)

I refrained from installing the proprietary blob in Jaunty in hope that open source support would be ready for Karmic. Not sure if I can wait for the L release ...

they better

---

### Post by BuffaloX on 2009-08-31
I'm on Ubuntu 9.04 with a Radeon 4770.
My Nvidia Gforce 7950 GX2 which cost a gazillion burned out, exactly one month after my wifes identical card burned out.
That's two Gazzilions out the windows after only 2½ years of use!
I Didn't want to reward Nvidia by buying more of their defective designs.
So we both went ATI, she use Ubuntu 8.10 because she need realtime Kernel.
With the Nvidia Realtime didn't work unless she used Ubuntu 8.04, Ati was one step up in that regard.

For me I'm very happy, My computer is now almost completely silent, because the Radeon 4770 use very little power the fan doesn't have a lot of work to do. The card was cheap too, and works fine for games in Windows.

I installed latest ATI drivers at the time, and it works fine with Compiz.
I don't do a lot of 3D stuff, but I haven't noticed any problems.

We both wanted to try ATI, especially because we hope the opened specs will help accelerate the development of good open source drivers.

I'm very happy to see this positive thread about it. :)

---

### Post by racerraul on 2009-08-31
> **yodermk said:**
> ... (I have a 3200HD.)


Same here... I have 9.8 on my laptop and Compiz support isn't quite right yet.  I have not tried any games on it though since I don't have a need to game on my laptop.

---

### Post by handy on 2009-09-05
Here is a quote from a post by *Mazur* in the Arch forums that may interest some of you:
[I]
I have installed mesa-git with xf86-video-ati-git and other packages and I need to say that I am looking forward to get full 3d support. It works awesome on simple games like supertux etc. but Quake Live still got bugs. I didn't tried Compiz. ANybody know if radeonhd-git works better? I got HD3200.[/I]

---

### Post by toupeiro on 2009-09-05
Over the years, I think ATi has proven itself time and time again to have better hardware than NVidia, but crappier drivers.  This is true not only in linux space, but windows as well.  ATi card owners can enjoy much longer performance lifespans with their cards because as the drivers mature, the cards perform better.  At least, in windows, this has always been the case.  NVidia's cards have more drastic decline over time in the performance market, and you will be replacing hardware more frequently for the next noticeable performance boost.  Better ATI drivers, open or closed, is wonderful news, but even better because the progress is being seen in the open drivers.

---

### Post by handy on 2009-09-05
AMD/ATi have released Catalyst 9.10 for Ubuntu 9.10.

[https://lists.ubuntu.com/archives/karmic-changes/2009-September/008022.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/008022.html)

---

### Post by DougieFresh4U on 2009-09-06
> **handy said:**
> AMD/ATi have released Catalyst 9.10 for Ubuntu 9.10.

[https://lists.ubuntu.com/archives/karmic-changes/2009-September/008022.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/008022.html)

Using it with my Karmic 64bit. I have the ATI Radeon HD3200 and seems to be running smooth. Played around with compiz some and all was good.
'Hardware Drivers' installed fglrx, rebooted with out any drama.

---

### Post by Exodist on 2009-09-06
On my 4850 the drivers from ATI/AMD website are super fast and rock solid.
The drivers Ubuntu says are proprietary and wants to install after installing ubuntu are complete garbage. IF those drivers are from ATI then they must be old. Very old..

Catalyst drivers from ATI tho, running 9.8 on 2.6.30.5 kernel. Super Fast and Rock Solid!

---

### Post by handy on 2009-09-06
Of late, the versions of kernel & Catalyst have been critical. If you don't have a matching pair you are in trouble, if you do have a matching pair you are in a lot less, just how much less all comes down to the particular pair.

We have been finding that regression is unfortunately far too often a part of the Catalyst progression. :(

Meaning, empirically people are experiencing the situation where a not perfect, but still a happy working situation, can be shot to pieces by the next Catalyst (or kernel, or X.server) upgrade!?

---

### Post by ELD on 2009-09-08
I have as of today done a fresh install of Jaunty with the latest drivers from amd's ati site and so far it seems to be a lot better (before my pc would totaly freeze up half the time, been about 3 hours now and not a single lockup, things are looking up :D). I hope i don't jinx this heh.

I think as someone said before through the hardware drivers manager it must have a quite old version of the ati drivers, i think that is actually what caused my freezing issues before!

---

### Post by handy on 2009-09-09
Catalyst 9.10 leaked, is being installed & tested by some Arch users.  

At this early stage it has been found to be better in some areas, worse than 9.8 in others.

---

### Post by matthew1471 on 2009-09-09
I wonder if the new Catalyst will work with my 200m.

I don't suppose they'd re-add support for older hardware after they've already removed it.

If they did re-add support, maybe it would fix this odd problem [http://ubuntuforums.org/showthread.php?t=1251849](http://ubuntuforums.org/showthread.php?t=1251849)

---

### Post by handy on 2009-09-09
I'd certainly be extremely surprised if they add support for something that they have previously stopped supporting.

---

### Post by handy on 2009-09-09
Reportedly Flash is still as bad or worse than it was with Catalyst 9.8.

---

### Post by racerraul on 2009-09-09
> **BuffaloX said:**
> 
I Didn't want to reward Nvidia by buying more of their defective designs.


I don't blame you for being upset with your HW going bad.  I would be too.
But unless you have some scientific data to support a known design flaw in a specific product, I wouldn't go rambling around about it.

I think you were a victim of rotten luck for sure. But would question if this is a common trait of the 7950 Gx2 product line or perhaps the outcome of improper cooling or power supply, rather than chucking it up as Nvidia's product somehow being flawed.

I have an Nvidia 4200 (from 2002), a 7600, 9500 & 9600 that are working just fine.

I did have an Nvidia Quadro m135 take a crap on a laptop, but I know for a fact that met its death due to over heating, and I consider that my fault because I noticed too late that the fan for the card was clogged with dust.  I've managed to kill a few procs that way as well...

Just a heads up... if you are taking care of all that then, yeah it sucks to have rotten luck... but if you have some concrete proof that Nvidia designs nothing but flawed products... lets have the test data. I genuinely want to see it.

---

### Post by racerraul on 2009-09-09
> **handy said:**
> Reportedly Flash is still as bad or worse than it was with Catalyst 9.8.

I wasn't aware that flash used 3d acceleration.

That said, flash is bad on anything and worse on everything :P

---

### Post by misfitpierce on 2009-09-09
The proprietary ones for ubuntu were giving me trouble in 9.04 but the newest opensource one is quite good... Seen huge improvments in it and its doing great... Cant even really tell difference any more... I give it another 6 months or so and ATI opensource drivers will be amazing. Opensource ATI drivers are coming along very nicely!

---

### Post by BuffaloX on 2009-09-09
> **racerraul said:**
> I don't blame you for being upset with your HW going bad.  I would be too.
But unless you have some scientific data to support a known design flaw in a specific product, I wouldn't go rambling around about it.

I think you were a victim of rotten luck for sure. But would question if this is a common trait of the 7950 Gx2 product line or perhaps the outcome of improper cooling or power supply, rather than chucking it up as Nvidia's product somehow being flawed.

I have an Nvidia 4200 (from 2002), a 7600, 9500 & 9600 that are working just fine.

I did have an Nvidia Quadro m135 take a crap on a laptop, but I know for a fact that met its death due to over heating, and I consider that my fault because I noticed too late that the fan for the card was clogged with dust.  I've managed to kill a few procs that way as well...

Just a heads up... if you are taking care of all that then, yeah it sucks to have rotten luck... but if you have some concrete proof that Nvidia designs nothing but flawed products... lets have the test data. I genuinely want to see it.

You gotta be kidding me, Nvidias defective GPUs are a well known fact, a problem that spanned entire lines and generations of GPUs.
Unfortunately many just made it through the warranty period, like mine did, almost 2000$ out the window, my two cards burned out like they were on a clock, and the problem is officially acknowledged.

Just google Nvidia defective, and you get results already on first page about official reports on entire lines of Dell, Sony and HP computers affected by the defective Nvivia GPUs.

On top of that, I actually knew about this problem early on, and I took extra care to keep both coolers clean on each card, monitored temperatures regularly, and both cases are big towers with very good air flow. There is absolutely no good reason these cards should die so soon.

---

### Post by handy on 2009-09-09
Good info' on this page regarding changes to the .31 kernel (& beyond). Of particular interest to the topic of this thread due to changes that relate to the AMD/ATi GPU:

[http://www.h-online.com/open/Kernel-Log-Coming-in-2-6-31-Part-2-Graphics-audio-and-video--/news/113958](http://www.h-online.com/open/Kernel-Log-Coming-in-2-6-31-Part-2-Graphics-audio-and-video--/news/113958)

---

### Post by PurposeOfReason on 2009-09-12
Does anyone know if it is possible to have one monitor in portrait mode and another in landscape for a dual monitor setup.

---

### Post by handy on 2009-10-12
The .31 kernel came out of testing for Arch yesterday.

After installing it, I experienced a regression (slow down in graphic drawing speed) due to the newly incorporated kernel mode-setting (KMS) capacity.

It was easily fixed as follows:

[I]The solution is to disable experimental KMS and fall back to the old behavior. Add the **radeon.modeset=0** into the kernel append line in **/boot/grub/menu.lst**
[/I]

***[Edit:]** I probably should mention (again) that I'm using the open-source ATi drivers.  There is more detailed info' on this subject for both open & the catalyst drivers to be found [**_here_**]("http://wiki.archlinux.org/index.php/ATI#AMD.2FAti_cards_and_KernelModeSetting_.28KMS.29"). /edit*

---

### Post by Exodist on 2009-10-12
good info.. Many thanks.

---

### Post by handy on 2009-10-23
It looks like Catalyst 9.10 is trying to get out into the wild:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

---

### Post by edin9 on 2009-10-23
> **BuffaloX said:**
> You gotta be kidding me, Nvidias defective GPUs are a well known fact, a problem that spanned entire lines and generations of GPUs.
Unfortunately many just made it through the warranty period, like mine did, almost 2000$ out the window, my two cards burned out like they were on a clock, and the problem is officially acknowledged.

Just google Nvidia defective, and you get results already on first page about official reports on entire lines of Dell, Sony and HP computers affected by the defective Nvivia GPUs.

On top of that, I actually knew about this problem early on, and I took extra care to keep both coolers clean on each card, monitored temperatures regularly, and both cases are big towers with very good air flow. There is absolutely no good reason these cards should die so soon.

That's true. As much as I dislike ATi, they're stuff lives longer than nVIDIA's.

---

### Post by MisfitI38 on 2009-10-23
> **handy said:**
> The .31 kernel came out of testing for Arch yesterday.

After installing it, I experienced a regression (slow down in graphic drawing speed) due to the newly incorporated kernel mode-setting (KMS) capacity.

It was easily fixed as follows:

[I]The solution is to disable experimental KMS and fall back to the old behavior. Add the **radeon.modeset=0** into the kernel append line in **/boot/grub/menu.lst**
[/I]

***[Edit:]** I probably should mention (again) that I'm using the open-source ATi drivers.  There is more detailed info' on this subject for both open & the catalyst drivers to be found [**_here_**]("http://wiki.archlinux.org/index.php/ATI#AMD.2FAti_cards_and_KernelModeSetting_.28KMS.29"). /edit*

I too experienced a regression in glxgears with KMS+xf86-video-ati vs. without KMS. (~300fps vs ~1200fps.)
However, I have not disabled it, as it is still functional and I quite like the efficient use of my entire monitor's real estate via the framebuffer. X also starts up very quickly. 2d acceleration still works great.
Still waiting.....................

---

### Post by edin9 on 2009-10-23
> **MisfitI38 said:**
> I too experienced a regression in glxgears with KMS+xf86-video-ati vs. without KMS. (~300fps vs ~1200fps.)
However, I have not disabled it, as it is still functional and I quite like the efficient use of my entire monitor's real estate via the framebuffer. X also starts up very quickly. 2d acceleration still works great.
Still waiting.....................

glxgears is not reliable. It gives my laptop on the opensource Radeon drivers 6000+, but on my 8800 SLi it gives 300.

---

### Post by MisfitI38 on 2009-10-23
> **edin9 said:**
> glxgears is not reliable. It gives my laptop on the opensource Radeon drivers 6000+, but on my 8800 SLi it gives 300.

Heh. [FONT="Arial Black"][COLOR="Red"][The old "glxgears is not a benchmark" spiel.]("http://bbs.archlinux.org/viewtopic.php?pid=430212#p430212")[/COLOR][/FONT] ;)
It is quite possible to use glxgears scientifically, especially on the same machine with the only difference being the enabling/disabling of KMS.

---

### Post by handy on 2009-10-23
> **MisfitI38 said:**
> I too experienced a regression in glxgears with KMS+xf86-video-ati vs. without KMS. (~300fps vs ~1200fps.)
However, I have not disabled it, as it is still functional and I quite like the efficient use of my entire monitor's real estate via the framebuffer. X also starts up very quickly. 2d acceleration still works great.
Still waiting.....................

For me, the scrolling of web pages in Firefox was quite jerky, which was the primary problem for me, the moving around of any windows & scrolling in them was also jerky.

So, I'm still waiting too...... :)

---

### Post by Pasdar on 2009-10-24
> **handy said:**
> For me, the scrolling of web pages in Firefox was quite jerky, which was the primary problem for me, the moving around of any windows & scrolling in them was also jerky.

So, I'm still waiting too...... :)

Install Chromium... I never looked back again!

---

### Post by handy on 2009-10-26
> **Pasdar said:**
> Install Chromium... I never looked back again!

I like Firefox, & am dependent on one of its add-ons too.

The problem had nothing to do with Firefox anyway; it is to do with the ongoing development of the open-source support for ATi GPUs.

---

### Post by handy on 2009-10-26
Really positive feedback on the Arch forum regarding the ATi R600 & R700 with the latest open-source drivers, kernel & associated packages.

The best 2D/3D performance ever experienced on this category of ATi GPU!

This is what all of us with ATi GPUs are now patiently standing in line waiting for.

Most excellent news indeed. :guitar:


Here is some how-to info' from the Arch forum, for anyone interested:

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

---

### Post by handy on 2009-10-26
Here is a good link from Phoronix, it is well worth reading:

[http://www.phoronix.com/scan.php?page=article&item=fedora_r600_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=fedora_r600_3d&num=1)

---

### Post by handy on 2009-10-28
I've personally just installed the catalyst 9.10 packages, for no other reason (& it is fortunately a good one :)) than I have started going through the games presented by [**_DJL_**]("http://en.djl-linux.org/") (which is available for Ubuntu in the repo's too I believe).

I now, have a strong desire for 3D, which can not be met (easily, if at all) by any other means at the moment (for my ATi GPU) than by using the catalyst clump.

This is not like a defeat or anything... lol!  

What it is, is just exactly what you do whilst waiting for the inevitable, desired solution to manifest. :) 

& manifesting it is, it just takes a while to do it for all those that desire it... :D  

I certainly take my hat off (that means respect for you young dude's) to ALL of the people that have been involved over the years in creating the wonderful change that we ATi GPU users (& others in the end) are starting to be treated to!!!

Thank you.

---

### Post by handy on 2009-11-01
For anyone who upgrades beyond the standard Ubuntu systems, or uses Arch or similar; it has been found that catalyst 9.10, is not compatible with the newly released xorg 1.7.

So don't upgrade if you want to see anything via X.

There are no patches or anything available, & no catalyst upgrade is expected for some time unfortunately.

---

### Post by xir_ on 2009-11-01
thanks for keeping this topic up-to date.

i think that the fglxr driver will start to become redundant from lucid (seeing as there should be a good couple of kernel version between now and then.

Makes sense from the POV of amd, far less work for them if the community is willing to drive development.

---

### Post by kasm on 2009-11-01
How do you enable KMS in Ubuntu?

---

### Post by handy on 2009-11-01
> **kasm said:**
> How do you enable KMS in Ubuntu?

It is on by default in the .31 kernel.  Which I believe Ubuntu 9.10 is using.

---

### Post by handy on 2009-11-01
Further on the xorg 1.7, catalyst 9.10 incompatibility;- the following site is carrying a working list of the files that need to NOT be allowed to upgrade if you want to maintain compatibility with catalyst 9.10:

[http://hpaste.org/fastcgi/hpaste.fcgi/view?id=11386#a11386](http://hpaste.org/fastcgi/hpaste.fcgi/view?id=11386#a11386)

From experience, this list is a fully functional workaround, though it is all in all a very clumsy situation.

Bring on the open-source solution so we can be rid of ridiculous situations like this one. :(

---

### Post by xir_ on 2009-11-02
> **handy said:**
> Further on the xorg 1.7, catalyst 9.10 incompatibility;- the following site is carrying a working list of the files that need to NOT be allowed to upgrade if you want to maintain compatibility with catalyst 9.10:

[http://hpaste.org/fastcgi/hpaste.fcgi/view?id=11386#a11386](http://hpaste.org/fastcgi/hpaste.fcgi/view?id=11386#a11386)

From experience, this list is a fully functional workaround, though it is all in all a very clumsy situation.

Bring on the open-source solution so we can be rid of ridiculous situations like this one. :(

i'm currently playing around with the zen .32 kernel from git and am going to try to see if my full-screen video performance is improved by DRII.

To be fair you have to give credit to amd for giving us the specifications, nvidia have stated that they have no intention of doing the same.

---

### Post by handy on 2009-11-02
> **xir_ said:**
> i'm currently playing around with the zen .32 kernel from git and am going to try to see if my full-screen video performance is improved by DRII.

To be fair you have to give credit to amd for giving us the specifications, nvidia have stated that they have no intention of doing the same.

In this thread I have given AMD credit for that multiple times. Many are very grateful for AMDs help in that regard.

Let us know what happens with your test? 

Is it possible in Zen to add an "ignorepkg =" list to your upgrades as in Arch, or does Zen use an individual install type system?

---

### Post by xir_ on 2009-11-03
simple as it didn't work. I even compiled messa so that it would support it.

as far as ignorepkg = goes i'm not sure to what you are referring.

I'm using the Zen kernel only inside ubuntu and I'm compiling from source, i felt like trying out their claimed Linux kernel for the desktop, so far its exactly the same.

My hope was that there would be improved drivers in the 32 kernel branch but every time i try to enable compiz it fails.

---

### Post by togo59 on 2009-11-03
> **handy said:**
> For anyone who upgrades beyond the standard Ubuntu systems, or uses Arch or similar; it has been found that catalyst 9.10, is not compatible with the newly released xorg 1.7.

So don't upgrade if you want to see anything via X.

There are no patches or anything available, & no catalyst upgrade is expected for some time unfortunately.
Could you clarify what you mean by "beyond the standard Ubuntu"? 

(I was just about to install AMD/ATI Catalyst 9:10 (version 8.661) in order to get decent 2D support for my Radeon HD 3400.)

---

### Post by Pasdar on 2009-11-03
> **togo59 said:**
> Could you clarify what you mean by "beyond the standard Ubuntu"? 

(I was just about to install AMD/ATI Catalyst 9:10 (version 8.661) in order to get decent 2D support for my Radeon HD 3400.)

It means dont change major parts of the system... its nothing any normal user should worry about... because many users here have no idea on how to (for example) manually update their kernel or other such things...

---

### Post by handy on 2009-11-03
> **xir_ said:**
> simple as it didn't work. I even compiled messa so that it would support it.

as far as ignorepkg = goes i'm not sure to what you are referring.

I'm using the Zen kernel only inside ubuntu and I'm compiling from source, i felt like trying out their claimed Linux kernel for the desktop, so far its exactly the same.

My hope was that there would be improved drivers in the 32 kernel branch but every time i try to enable compiz it fails.

My understanding (from what I've read) is that these days, due to the way the kernel is made (which I take to mean an inbuilt efficiency that did not exist in the past), it is uncommon for someone to notice any performance difference after recompiling the kernel to suit their system perfectly.

Those in the know say it is actually a waste of time. 

> **togo59 said:**
> 
Could you clarify what you mean by "beyond the standard Ubuntu"? 

If you are going to start playing with different kernels, .git packages, or going with one of the 2 open-source ATi GPU systems.  Or if you are using a system other than Ubuntu, such as Arch for example.

> **togo59 said:**
> 
(I was just about to install AMD/ATI Catalyst 9:10 (version 8.661) in order to get decent 2D support for my Radeon HD 3400.)

If you want decent 2D support, you will be best served by the open-source packages, they are far superior to Catalyst in 2D.

The best performance is generally found with the xf86-video-ati package.

You may have to do some research regarding the installation & setup of this on Ubuntu.  I can't help you with that, as I have only used it on Arch.

---

### Post by handy on 2009-11-03
[I]**AMD Loses Its Linux Core Engineering Manager, Matthew Tippett**

AMD's Catalyst Linux driver has improved substantially over the past few years. Years ago the Catalyst Linux driver was in shambles with its performance being utterly poor, it lacked enthusiast-oriented features like CrossFire and OverDrive, and ATI customers had to wait months -- sometimes in excess of a year -- for any driver support in Linux. All of this though has changed with AMD now providing same-day Linux support, a near feature parity to the Windows Catalyst driver, and first-rate performance. Playing a critical role in improving the ATI Linux support has been Matthew Tippett, serving as the engineering manager for Linux Core Engineering since joining ATI Technologies in 2003. To put it in perspective, when Matthew started work at ATI, only the FireGL graphics cards were supported under Linux. However, today will be his last day serving ATI / Advanced Micro Devices.[/I]

The rest of this very informative article can be found here:

[http://www.phoronix.com/scan.php?page=article&item=amd_matthew_tippett&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_matthew_tippett&num=1)

---

### Post by xir_ on 2009-11-03
Dont get me wrong the zen kernel is OK (of course i compile for my cpu, might as well), i've got rid of a lot of stuff and am using BFS (which is really nice), but as far as zen vs the bfs kernel available on launchpad, theres none.

i managed to get the radeon drivers working, they are so much better for watching movies on my laptop. i used to get lagg when starting up a video, now i get a real snappy viewing, open arena is a dream to run as well and cairo-dock finally works with opengl.

two thumbs up

---

### Post by handy on 2009-11-03
> **xir_ said:**
> 
i managed to get the radeon drivers working, 

xf86-video-radeonhd ?

---

### Post by handy on 2009-11-03
Here's an update on the the list of files that we need to prevent from being upgraded to maintain compatibility between catalyst 9.10, & xorg1.7. 

The number of files has come down somewhat from the previous list of approx' 60 files that I linked to in a previous post in this thread.

64bit users can use the *upgraded* lib32-* packages, (I've tested this), if you have a notebook then you will most likely want to add ***xf86-input-synaptics***.

If you were using Arch you would add the following line in */etc/pacman.conf*

***IgnorePkg = xf86-video-vesa xorg-server xf86-input-evdev xf86-input-keyboard xf86-input-mouse***

With the number diminished from 60 to 5 or 6 files that need to be held back from upgrade, this workaround has certainly become far less of a pain to instigate.

---

### Post by xir_ on 2009-11-03
> **handy said:**
> xf86-video-radeonhd ?


According to synaptic i only have the radeon driver installed, but now that u mention it i will give the radeonhd a try.

what is the difference (i normally just skip to the binary blobs with installations for compiz).

Do you know which acceleration method is used by default with the radeon drivers (i'm wondering if theres any tweaks i can do for better performance).


One thing to note is that my power consumption has gone up from ~12 watts to 20 watts. this has cut my battery life by two hours. I assume this is down to ati having much more fine grained control over powersettings.

---

### Post by handy on 2009-11-03
My understanding is that with the open-source drivers usually the xf86-video-ati is the better, though some people do find the xf86-video-radeonhd better, but they are definitely in a minority.

I have been using until very recently the xf86-video-ati package, & the 2D performance is actually miles better than that provided by the catalyst package.  The desktop, scrolling, movies, everything is the snappiest it has ever been.

I just went back to catalyst the other day, because I've been checking out games provided by the DJL games manager (kind of like steam for Linux) & needed better 3D for some of the games.

So moving back to catalyst, has really made it quite clear that even though the catalyst drivers have better to vastly superior 3D quality over the open-source drivers, their 2D is crap.

I'll give you a link to a method for getting the most out of the open-source drivers in Arch, you may learn some that you can apply in Ubuntu (I've not bothered with the following method as yet, as with Arch I expect that there may be too much upkeep, due to the rolling release, I could be wrong of course:)):

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

If you do manage to get improved results from your endeavours, please post a how-to in the how-to section for other Ubuntu users, I'm sure that quite a few would be very grateful? :)

---

### Post by handy on 2009-11-04
[I]**AMD's UVD2-based XvBA Finally Does Something On Linux**

For a year now we have been talking about XvBA, which stands for X-Video Bitstream Acceleration and is designed to implement AMD's Unified Video Decoder 2 (UVD2) engine on Linux systems for improving the video decoding and playback process on desktop systems. AMD has been shipping an XvBA library with their ATI Catalyst Linux driver since last year, but they have yet to release any documentation on the XvBA API or any patches to implement the support within any Linux media players. Heck, AMD has not even officially confirmed XvBA with Phoronix being the lone source of information for the past year. Today though, XvBA has finally become useful under Linux. But it is not what you may be thinking...[/I]

[http://www.phoronix.com/scan.php?page=ar...aapi&num=1](http://www.phoronix.com/scan.php?page=ar...aapi&num=1)

---

### Post by handy on 2009-11-12
Catalyst 9.11 has been leaked.

It doesn't solve the incompatibility with xorg 1.7 though. :(

[http://www.phoronix.com/forums/showthread.php?p=99647](http://www.phoronix.com/forums/showthread.php?p=99647)

[http://news.ati-forum.de/index.php/news/34-amdati-grafikkarten/840-download-catalyst-911-fuer-linux-exklusiv](http://news.ati-forum.de/index.php/news/34-amdati-grafikkarten/840-download-catalyst-911-fuer-linux-exklusiv)

---

### Post by handy on 2009-12-03
kernel .32 is out. 

ViOLO has compiled it without KMS & tested it with catalyst.  It is of course incompatible.  

So those of us who are using catalyst & blocking the upgrade of 5 (or 6 for notebook) packages have to add **kernel26** to the list not to be upgraded as well.

---

### Post by Pasdar on 2009-12-04
I just reinstalled kubuntu on my laptop and i'm willing to give the ati open-source drivers a try. Will it work with ATI 4570?

What I would expect of it are that my desktop environment runs fast, that I can enable desktop composition (kwin), and I want to be able to watch my movies/series (divx/dvd/streaming/whatever). Can it deliver the mentioned things?

If yes, I'd like to know where I could download the drivers and also get the latest updates from.

---

### Post by u.b.u.n.t.u on 2009-12-04
I wish the 9.12 drivers would come of age!

Hopefully this month I would think.

---

### Post by Pasdar on 2009-12-04
Stupid AMD has so many people, yet they're unwilling to make propper drivers for linux. Though I'm happy they at least release drivers each month. It would be great if they just supported every kernel update/xorg/etc... ahh... the dreams of an ati user... lol

---

### Post by handy on 2009-12-04
**@Pasdar:** Have a look at some of the links at the bottom of the first post in this thread.

One of them goes into quite some detail (on the Arch forum) for getting the best 3D out of the open-source drivers.

You will be able to find out whether your GPU is well supported, & you'll also find out which open-source package route you need to follow.

As mentioned often, previously, the 2D is superb for most ATi GPUs, via the open-source drivers, glitch free, 3D, is what we are waiting for. :)  AMD are helping by offering technical help where they legally can.

---

### Post by sdowney717 on 2009-12-04
i have an x1300 sitting around and cant use it. i need svideo out and they dont offer it on r500 chipset

---

### Post by rajeev1204 on 2009-12-04
What exactly is the point of open drivers for 3d ? for example, games use proprietary technologies and the open source driver is incapable of running them.

For example, in id's games, there is a module called s3tc, tc is for texture compression and s3 has the patents for it,so it will never make it to the open source driver.And so, will never run a game with that .

Give me the proprietary drivers anyday.

@handy,which 2d applications are you talking about really? What is this 2D?

Iam sorry to say handy,but many have not probably understood why just opening a driver wont solve anything.

If by 3d you mean compiz, then we dont buy expensive graphics cards with shader model 4 for just that,do we?

good day.Sorry for the harsh post.Just opened my eyes when i reached point of no return with the open source driver.And on top of it,AMD dropped support for older cards so no proprietary drivers for me either.That means no gaming either.

Due to the reasons mentioned above, the drivers can never be fully functional.Will never come of age unless every single app using it and many other things we probably miss out are also open .COuld be hardware,software running on them and other legalese.

rajeev

---

### Post by forrestcupp on 2009-12-04
> **rajeev1204 said:**
> 
For example, in id's games, there is a module called s3tc, tc is for texture compression and s3 has the patents for it,so it will never make it to the open source driver.And so, will never run a game with that .

Anything can be reverse engineered with time.  The Wine team has reverse engineered most of the features in DirectX, and I doubt if s3tc is more complicated than that.

---

### Post by Hyporeal on 2009-12-04
> **rajeev1204 said:**
> What exactly is the point of open drivers for 3d ? for example, games use proprietary technologies and the open source driver is incapable of running them.

For example, in id's games, there is a module called s3tc, tc is for texture compression and s3 has the patents for it,so it will never make it to the open source driver.And so, will never run a game with that .

Why can't open source drivers use patented techniques? You can already download the proprietary drivers for free, so there's no issue with fees. The patent publicly describes the technique, so there's no issue with secrecy. Why would S3 care whether ATI's drivers are open source or not, as long as the licensing fees get paid as usual?

---

### Post by u.b.u.n.t.u on 2009-12-04
I think ATI and Nvidia should open source their drivers and work closely with the linux community.

I buy their hardware, and a customer ought to be able to expect a fully working product on linux.

---

### Post by jrusso2 on 2009-12-04
Any video card should be able to do excellent 2d.  Its 3d performance that counts.  I have ten year old cards here that do great in 2d.

---

### Post by handy on 2009-12-04
> **rajeev1204 said:**
> 
What exactly is the point of open drivers for 3d ? for example, games use proprietary technologies and the open source driver is incapable of running them. 

As mentioned above by *forrestcupp*, reverse engineering is alive & well in the open-source community.  Wireless users may be most aware of this.

The point of having open-source drivers, is that the code is open for all. It can be kept up to date with the kernel, mesa (which is where the GPU open-source is intended to reside & is in the process of being developed now) & the xorg-server.

Those who have been putting up with the terrible ATi driver support over the last years will be free of that burden.

> **rajeev1204 said:**
> 
Give me the proprietary drivers anyday. 

That is your choice.  

Though it is possible in the future that the only drivers provided by AMD for the ATi GPUs used by the distros will only be for their newest GPUs, due to the competition between AMD & nVidia.  

I've not read that anywhere, it just seems like good business sense to me.

Time will tell.

> **rajeev1204 said:**
> 
@handy,which 2d applications are you talking about really? What is this 2D?  

When I run the open-source drivers on my 24" iMac running an HD2600Pro GPU, the refresh speed of everything (opening, closing app's resizing & moving windows, scrolling in intensive graphic screens, the Firefox refresh speed - scrolling - on any site with many tabs open) is near instantaneous. Watching any form of video is perfect, as there is not the slightest hint of lag ever.

Using catalyst there is lag, in all of the above.

> **rajeev1204 said:**
> 
Iam sorry to say handy,but many have not probably understood why just opening a driver wont solve anything. 

Actually, I think you have the bull by the horns.  You will find as time goes by, that the open-source GPU drivers that are currently being worked on will do all & more than the proprietary ones.  I know you won't take my word for it, though the proof will be in the pudding as 2010 goes by there will be some serious changes occur re. the support provided by the open-source drivers for many GPUs.

There are people already using the ATi open-source drivers for 3D games, though not the most demanding of them.  I have used the open-source drivers & run some 3D, without any graphic aberrations, but with too much lag. 

> **rajeev1204 said:**
> 
If by 3d you mean compiz, then we dont buy expensive graphics cards with shader model 4 for just that,do we? 

I never use compiz or the like, I don't even have icons on my desktop, or a screen background.  I personally consider that beyond making things as easy on your eyes as possible, anything else is a waste of resources.  I know, there is no accounting for taste. :)

> **rajeev1204 said:**
> 
good day.Sorry for the harsh post.Just opened my eyes when i reached point of no return with the open source driver.And on top of it,AMD dropped support for older cards so no proprietary drivers for me either.That means no gaming either. 

It is a drag when support disappears. I can't say for sure, hopefully there will be useful open-source support for your GPU?
Everything does reach an age where it is no longer supported though, hopefully your GPU is not there yet.

> **rajeev1204 said:**
> 
Due to the reasons mentioned above, the drivers can never be fully functional.Will never come of age unless every single app using it and many other things we probably miss out are also open .COuld be hardware,software running on them and other legalese.

rajeev

I think you will find that you are wrong on this. As I said before, keep an eye on the progress of the open-source ATi drivers over the coming year or so.

All the best.

---

### Post by handy on 2009-12-04
> **rajeev1204 said:**
> What exactly is the point of open drivers for 3d ? for example, games use proprietary technologies and the open source driver is incapable of running them.

For example, in id's games, there is a module called s3tc, tc is for texture compression and s3 has the patents for it,so it will never make it to the open source driver.And so, will never run a game with that . 

I just happened to be poking about on the Neverwinter Nights Linux forum & read about a little Linux tool for handling S3TC:

*Quote: Posted 08/11/09 14:02 (GMT) by CainGG*

*If it's the S3TC issue, you can install a program called driconf that will let you force S3TC to "on" for practically any video system...it worked for my Intel GM45 and it might work for you too. *

There are always more than one way to skin a cat, especially in the FOSS world. ;)

---

### Post by holastickboy on 2009-12-05
I have always seemed to have Nvidia cards on my linux pc's because the software just seemed to run much better.  I managed to get a video card upgrade the other day to a Ati Radeon 3650 and was appalled about how primitive the ati drivers were, and what a big fuss it was to get my dual screens working properly (and not stretch games across both screens).   I hadn't used an ATI card on linux for years, and I thought that in my hiatus that things would have improved, which they have to a small degree.  I commend the people working had to make the open source drivers better!

---

### Post by rajeev1204 on 2009-12-05
> **handy said:**
> I just happened to be poking about on the Neverwinter Nights Linux forum & read about a little Linux tool for handling S3TC:

*Quote: Posted 08/11/09 14:02 (GMT) by CainGG*

*If it's the S3TC issue, you can install a program called driconf that will let you force S3TC to "on" for practically any video system...it worked for my Intel GM45 and it might work for you too. *

There are always more than one way to skin a cat, especially in the FOSS world. ;)

This is good information thanks.And thanks for the replies to my long post,i appreciate that you took it positively.I still dont know how to multiquote so i didnt reply to that post of yours.

BTW,I finally got a brand new AMD RADEON 4850  :D.And the proprietary drivers are working great.

But i have read that Radeon HD open drivers are catching up soon so thats good news.But it still wont solve the s3tc or other issues without a little R and D.

Anyways,lets hope for the best.

T.C.
rajeev

---

### Post by Nerd King on 2009-12-06
So I've been having nightmares with 2.6.31 and tried 2.6.30 with the same problem, my wi-fi kept locking the system. 2.6.32 fixes that, but even better, it gives me open source ATI drivers and lovely 3D with no proprietary driver. Absolutely superb it is too, Compiz is flying around nicely, will test some games later but it feels very snappy. Btw it's not compatible with the proprietary ATI drivers which is why I tried the open ones. I'm glad I did now!

I've run the usual crash conditions and it coped fine so it looks good.

Procedure:
1. System -> Hardware Drivers -> Deactivate any ATI drivers and restart
2. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/")
3. Download and execute the following (in this order, switch to 64 if need be)
  - linux-headers...all.deb
  - linux-headers..generic..i386.deb
  - linux-image....i386.deb
4. Restart
5. Add the xorg-edgers PPA ([https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")), update, upgrade.
6. Reboot.
7. Profit.

---

### Post by SunnyRabbiera on 2009-12-06
Yeh I think this might be what most ATI users have been waiting for.
Its about time we got some progress from ATI

---

### Post by Nerd King on 2009-12-06
An hour in, still no sign of a freeze or crash so people on Atheros Wi-Fi getting the lock-up will find 2.6.32 very useful. Rock solid performance on SuperTuxKart, an occasional black band flashing in and out caused by Gnome-Do Docky (resolved by a quick killall 'gnome-do') so it looks like it'll handle 3D games as well.

BTW my hardware is ASUS F81 laptop running a ATI HD4570 card.

---

### Post by Pasdar on 2009-12-06
Could you run what you get from glxgears, I have the same videocard with proprietary drivers installed atm.

---

### Post by Nerd King on 2009-12-06
ryan@ryan-laptop:~$ glxgears
IRQ's not enabled, falling back to busy waits: 2 0
8460 frames in 5.0 seconds = 1691.881 FPS
9108 frames in 5.0 seconds = 1821.436 FPS
9585 frames in 5.0 seconds = 1916.847 FPS
9597 frames in 5.0 seconds = 1919.266 FPS
8473 frames in 5.0 seconds = 1694.577 FPS
9387 frames in 5.0 seconds = 1877.321 FPS
7942 frames in 5.0 seconds = 1588.364 FPS
9333 frames in 5.0 seconds = 1866.436 FPS


Not sure how accurate a measure that is. Compiz was running at the time.

---

### Post by doorknob60 on 2009-12-06
I'm eagerly awaiting 2.6.32 to hit [core] in Arch, so I can try it. I don't want to use [testing], that never turns out well :P I'm in no huge hurry though since Catalyst is working well for me right now. I've heard great things about the 3D support in 2.6.32 though :)

---

### Post by Nerd King on 2009-12-06
> **doorknob60 said:**
> I'm eagerly awaiting 2.6.32 to hit [core] in Arch, so I can try it. I don't want to use [testing], that never turns out well :P I'm in no huge hurry though since Catalyst is working well for me right now. I've heard great things about the 3D support in 2.6.32 though :)
I thought Arch was supposed to be cutting-edge ;) Only mucking about. Seriously though, you'll be very impressed with the new 3D support, and the obvious advantage of not having to wait for ATI to put out compatible versions of catalyst for every new version of X and the Kernel. Should make Archer's lives much easier.

---

### Post by Nerd King on 2009-12-06
> **Nerd King said:**
> I thought Arch was supposed to be cutting-edge ;) Only mucking about. Seriously though, you'll be very impressed with the new 3D support, and the obvious advantage of not having to wait for ATI to put out compatible versions of catalyst for every new version of X and the Kernel. Should make Archer's lives much easier.
Btw will test some games with Wine when I get home, to see how it copes.

---

### Post by Pasdar on 2009-12-06
Weird but I dont have glxgears, maybe its part of the ubuntu reps and not kubuntu... is there a place to download it?

---

### Post by Pasdar on 2009-12-06
Found it, its in mesa-utils.

:~$ glxgears
9848 frames in 5.0 seconds
10246 frames in 5.0 seconds
10213 frames in 5.0 seconds
10196 frames in 5.0 seconds
9816 frames in 5.0 seconds
10209 frames in 5.0 seconds
10074 frames in 5.0 seconds

The difference could be due to other factors. All in all the free drivers seem like a great alternative.

---

### Post by Pasdar on 2009-12-06
What does
glxinfo | grep version
give you, mine:

server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 2.1.9016
OpenGL shading language version string: 1.40

---

### Post by AllRadioisDead on 2009-12-06
Will this work for my HD 4850?

---

### Post by Nerd King on 2009-12-06
IRQ's not enabled, falling back to busy waits: 2 0
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 1.5 Mesa 7.7-rc1


Can't vouch for the 4850 specifically but mine's a pretty close model so it's worth a try.

---

### Post by mmix on 2009-12-06
yes, getting interesting.

---

### Post by Nerd King on 2009-12-06
Tried Football Manager in wine but no luck. However, at this rate I'm sure it wont be long.

---

### Post by antenna on 2009-12-06
I would be interested in knowing if Quake Live works in full screen ;)

---

### Post by tom66 on 2009-12-06
What card you using? Does anyone know if my Mobility Radeon HD 3450 will work?

---

### Post by Chame_Wizard on 2009-12-06
Going to be good.:P

---

### Post by handy on 2009-12-06
> **rajeev1204 said:**
> 
... I still dont know how to multiquote so i didnt reply to that post of yours. 

There are some more variations than what I'll post here now, but this will get you going with multi-quote.  You have to close a quoted section with the following command "**[/quote]**" (without the inverted commas) this is what I did to break your text above so I could type this.

After which then I copy the persons quote=name line as follows "**> **rajeev1204 said:**
> **", (once again without the inverted commas) & place it at the start of the next part of the other person's (in this case your) text that you want to display, as follows:

[QUOTE=rajeev1204;8445398]
BTW,I finally got a brand new AMD RADEON 4850  :D.And the proprietary drivers are working great. 

That is great news. :)

> **rajeev1204 said:**
> 
But i have read that Radeon HD open drivers are catching up soon so thats good news.But it still wont solve the s3tc or other issues without a little R and D.

Anyways,lets hope for the best.

T.C.
rajeev

I do. :)


Just a note on the keyboard shortcuts for copying, cutting & pasting, which is particularly useful when you want to reuse a persons quote=name (as mentioned earlier in this post) to break up their post so as to add your replies. 

Drag the mouse cursor with the left mouse button depressed, to highlight the desired text, then manipulate it with the following keyboard shortcuts:

copy = "**Ctrl**" & "**c**" 
paste = "**Ctrl**" & "**v**" 
cut = "**Ctrl**" & "**x**" 

you can of course paste what you have cut.  You probably know that stuff, but it is not hard for me to type it & it just might be useful.

All the best. :)

---

### Post by Nerd King on 2009-12-06
Far as I know HD3000 and 4000 series is good but the only way is to try it and see. Maybe install on a flash drive (clean) and run from there, see how it goes. If it plays nice, then try it on your main box. As I say, it's bumped stability right up for me, 32 is a fantastic kernel, and could be a real big deal for linux, the time when all 3 graphics cards have quality driver support.

---

### Post by Nerd King on 2009-12-06
Probably should have posted on this thread but I was excited.. anyway [http://ubuntuforums.org/showthread.php?p=8450093#post8450093](http://ubuntuforums.org/showthread.php?p=8450093#post8450093) for some info on getting 3D under open-source drivers. Tested in Karmic on a ATI HD4570 and I think it'll probably work on anything HD3000/4000 series. Good luck chaps..

[quote="Me, on the other thread"]Procedure:
1. System -> Hardware Drivers -> Deactivate any ATI drivers and restart
2. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/")
3. Download and execute the following (in this order, switch to 64 if need be)
  - linux-headers...all.deb
  - linux-headers..generic..i386.deb
  - linux-image....i386.deb
4. Restart
5. Add the xorg-edgers PPA ([https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")), update, upgrade.
6. Reboot.
7. Profit.[/quote]

---

### Post by AllRadioisDead on 2009-12-06
> **Nerd King said:**
> Far as I know HD3000 and 4000 series is good but the only way is to try it and see. Maybe install on a flash drive (clean) and run from there, see how it goes. If it plays nice, then try it on your main box. As I say, it's bumped stability right up for me, 32 is a fantastic kernel, and could be a real big deal for linux, the time when all 3 graphics cards have quality driver support.
 Maybe I'll get around to testing it on my 4850 sometime soon. Looks promising.

---

### Post by Ylon on 2009-12-06
Unluckly, this don't fix the situation for some legacy ATI.. my [Radeon Mobility 7500] still crashes Googleeart and so, go on (blender&co).

I had to force a revert back to x-retro ppa repository.


Now I've a problem, each time I try a apt-get upgrade it ask me to update all the xorg from ~xorg-edgers repository.
How can I avoid that?
```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-retro/ubuntu karmic main
#deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
```

These are the ppa lines in my sources.list.

---

### Post by diaa on 2009-12-06
I'd appreciate any info about gaming performance with ATI HD 3xxx, I have ATI HD 3300(not high-end I know) and I'm not satisfied with the performance of ATI's proprietary Linux drivers(FPS is significantly better on Windows using the same card)

---

### Post by Chame_Wizard on 2009-12-06
> **Nerd King said:**
> So I've been having nightmares with 2.6.31 and tried 2.6.30 with the same problem, my wi-fi kept locking the system. 2.6.32 fixes that, but even better, it gives me open source ATI drivers and lovely 3D with no proprietary driver. Absolutely superb it is too, Compiz is flying around nicely, will test some games later but it feels very snappy. Btw it's not compatible with the proprietary ATI drivers which is why I tried the open ones. I'm glad I did now!

I've run the usual crash conditions and it coped fine so it looks good.

Procedure:
1. System -> Hardware Drivers -> Deactivate any ATI drivers and restart
2. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/")
3. Download and execute the following (in this order, switch to 64 if need be)
  - linux-headers...all.deb
  - linux-headers..generic..i386.deb
  - linux-image....i386.deb
4. Restart
5. Add the xorg-edgers PPA ([https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")), update, upgrade.
6. Reboot.
7. Profit.

Thanks by the way

---

### Post by Xbehave on 2009-12-06
I need more crack on my cornflakes^H^H^H xorg, is there a way to get mpx on karmic?

BTW is the 2.6.32 important? I'm still struggling with an audio problem (custom kernel, probably my fault), but i get ~100/200FPS on 2.6.31 on an old internal card (RS482 [Radeon Xpress 200M])

---

### Post by PaulInBHC on 2009-12-06
I'm typing this in Windows. I installed and rebooted. I get a boot screen, a very small text error at the bottom, then a black screen.

Guess I'll have to reinstall Ubuntu.

---

### Post by toupeiro on 2009-12-06
I'm sorry, but I think KSM was a MUCH more important addition to this kernel than anything else.


my .02

---

### Post by Xbehave on 2009-12-06
> **toupeiro said:**
> I'm sorry, but I think KSM was a MUCH more important addition to this kernel than anything else.


my .02
KSM has got a lot of hype but the performance difference between 2.6.32 and 2.6.31 for graphics is minimal. KSM is only being used to stopping flickering when you switch to/from xorg (with the downside being an xorg lockup can now lock up your kernel). It's the work being done on the xorg-radeon drivers that makes all the difference. Don't get me wrong ksm is a nice feature but IMHO it's getting way too much hype.

---

### Post by handy on 2009-12-06
> **Nerd King said:**
> Probably should have posted on this thread but I was excited.. anyway [http://ubuntuforums.org/showthread.php?p=8450093#post8450093](http://ubuntuforums.org/showthread.php?p=8450093#post8450093) for some info on getting 3D under open-source drivers. Tested in Karmic on a ATI HD4570 and I think it'll probably work on anything HD3000/4000 series. Good luck chaps..

This is where you should have posted, it is what this thread is all about! :)

The incorporation of the GPU suport into the kernel & mesa started happening in the .31 kernel, & will continue in coming kernels.

Most of us don't know just what results to expect for our ATi GPU until the kernel is released & people like you report on the experience.

Great news. :D

I'll investigate at to whether the 2000 series (which I'm using) has support.

---

### Post by waynefoutz on 2009-12-06
> **sideaway said:**
> What about us obsolete folk? :(

I'm sitting on an x1400, and they've ditched me, rejected me for the younger model. I feel like an old worn out hoo... Won't go there. Anyways, I want proprietary support! Or atleast open the source code of the drivers so we can get some decent ones.

I'm in the same boat. My laptop has a ATI radeon x1270, RS695 chip. The last version of Catalyst that works is 9.3. Basically, I can't upgrade past Intrepid, or I lose 3d.  Anyone have a clue if this new kernel update will let me upgrade to Karmic and have 3d?


Think I found the answer!

this link:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=771fe6b912fca54f03e8a72eb63058b582775362](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=771fe6b912fca54f03e8a72eb63058b582775362)

scroll down to the bottom and it lists the affected chipsets...Mine is on the list!

---

### Post by handy on 2009-12-06
I've added a couple of links to the others at the bottom of OP in this thread.

Thanks for them. :)

---

### Post by toupeiro on 2009-12-06
> **Xbehave said:**
> KSM has got a lot of hype but the performance difference between 2.6.32 and 2.6.31 for graphics is minimal. KSM is only being used to stopping flickering when you switch to/from xorg (with the downside being an xorg lockup can now lock up your kernel). It's the work being done on the xorg-radeon drivers that makes all the difference. Don't get me wrong ksm is a nice feature but IMHO it's getting way too much hype.

uuhh, KSM is page memory deduplication, which has the ability to exponentially extend the life of similar data types loaded into RAM, which affects EVERYTHING, not just ATi owners..  Thus, it deserves all the hype.  For example, Imagine getting 12GB worth of traditional application space into RAM in a 3GB footprint?  Do you virtualize at all?  Guess what, your memory footprint of identical pages amongst your VM's is now shared.  You can recover huge percentages of available memory for other tasks.  Overall, IMO, this is vastly more important to the future of Linux based OSes than Open ATI drivers, which I will admit is very important for ATi users.

---

### Post by handy on 2009-12-06
2010, really does look to be shaping up as quite a year for the Linux kernel... =D>

---

### Post by Xbehave on 2009-12-06
> **toupeiro said:**
> uuhh, KSM is page memory deduplication, which has the ability to exponentially extend the life of similar data types loaded into RAM, which affects EVERYTHING, not just ATi owners..  Thus, it deserves all the hype.  For example, Imagine getting 12GB worth of traditional application space into RAM in a 3GB footprint?  Do you virtualize at all?  Guess what, your memory footprint of identical pages amongst your VM's is now shared.  You can recover huge percentages of available memory for other tasks.  Overall, IMO, this is vastly more important to the future of Linux based OSes than Open ATI drivers, which I will admit is very important for ATi users.
KSM != KMS my bad i miss read your post as the thread was about ATI drivers.

Also AFAIK KSM only affects VMs (possibly only those that make used of KSM), so unless you do lots of virtualisation you wont notice it. I mean i think KSM is great but your average desktop user will not notice it.

---

### Post by doorknob60 on 2009-12-06
I just upgraded to [testing] and installed all the new stuff. SOme stuff work, some stuff doesn't. I can't tell whether it's using hardware acceleration or software. World of Goo works normally, but Wine is very very slow. Glxgears works fine in 64 bit and 32 bit. It could be my 32 bit chroot isn't set up right byut my 64 bit is. I installed the same stuff in the chroot as in my 64 bit Arch though. I'll reboot and see if that fixes it :)

EDIT: After restarting and running glxinfo again, it became clear that my stuff is working correctly on 64 bit, but not in my 32 bit chroot (which I need...). With catalyst all I had to do was install the catalyst package in the chroot (the exact same way I installed it in my 64 bit main system), but do I have to do anything special with this?

EDIT2: Oh wait, I forgot to install libdrm-git, good, it should work now :)

EDIT3: Except that it doesn't fix it :/

EDIT4: Fixed, works nice, I'll stick with it unless something gives me problems. So far so good.

---

### Post by toupeiro on 2009-12-06
> **Xbehave said:**
> KSM != KMS my bad i miss read your post as the thread was about ATI drivers.

Also AFAIK KSM only affects VMs (possibly only those that make used of KSM), so unless you do lots of virtualisation you wont notice it. I mean i think KSM is great but your average desktop user will not notice it.

Well, I think what you are seeing is a product of writers using as many top buzzwords as possible. :)  Virtualization has been a buzz topic for the last two years, and in storage, deduplication has been a buzzword for quite some time as well.  So, when you talk about RAM dedup, one of the first big wins for the technology is DEFINITELY virtualization, but to say that it will **only** effect virtualization is not true based on what I've read about the technicalities about that technology.

The KSM code scans through memory to find pairs of pages holding identical data; when such pairs are found, they are merged into a single page mapped into both locations. The pages are marked copy-on-write, so the kernel will automatically separate them again should one process modify its data.  There is nothing about this that is specific to VM's, but as you can imagine, it would be very highly effective in VM environments, and those environments would most likely be the first to utilize the functionality.  Databases. web-services, and intensive work such as Audio and Video production and rendering, Content Streaming, as well as certain types of graphics work will also benefit.  I could also see this helping backend gaming services which are run on linux.  e.g., World of Warcrafts realm servers.

EDIT: And the thread was about the .32 kernel as well, which was merged with a thread that was strictly ATI drivers, which honestly was a bad merge by whichever mod merged them... :)

---

### Post by Nerd King on 2009-12-06
> **PaulInBHC said:**
> I'm typing this in Windows. I installed and rebooted. I get a boot screen, a very small text error at the bottom, then a black screen.

Guess I'll have to reinstall Ubuntu.
If you choose an older kernel from grub at bootup you can get back in and undo what you did.

---

### Post by Nerd King on 2009-12-06
> **toupeiro said:**
> Well, I think what you are seeing is a product of writers using as many top buzzwords as possible. :)  Virtualization has been a buzz topic for the last two years, and in storage, deduplication has been a buzzword for quite some time as well.  So, when you talk about RAM dedup, one of the first big wins for the technology is DEFINITELY virtualization, but to say that it will **only** effect virtualization is not true based on what I've read about the technicalities about that technology.

The KSM code scans through memory to find pairs of pages holding identical data; when such pairs are found, they are merged into a single page mapped into both locations. The pages are marked copy-on-write, so the kernel will automatically separate them again should one process modify its data.  There is nothing about this that is specific to VM's, but as you can imagine, it would be very highly effective in VM environments, and those environments would most likely be the first to utilize the functionality.  Databases. web-services, and intensive work such as Audio and Video production and rendering, Content Streaming, as well as certain types of graphics work will also benefit.  I could also see this helping backend gaming services which are run on linux.  e.g., World of Warcrafts realm servers.

EDIT: And the thread was about the .32 kernel as well, which was merged with a thread that was strictly ATI drivers, which honestly was a bad merge by whichever mod merged them... :)
Actually a good merge as the .32 kernel post (mine) was mostly about how good the support for ATI opensource 3d was. I then realised I should have posted here, posted the procedure, and linked to the thread for anyone who wanted, a mod subsequently did what I should have done in the first place. Mod did good.

---

### Post by PaulInBHC on 2009-12-06
Thanks for the tip. I still have 9.10 installed. I thought about it later and should have tried the recovery mode as well or the LiveCD.

---

### Post by toupeiro on 2009-12-07
> **Nerd King said:**
> Actually a good merge as the .32 kernel post (mine) was mostly about how good the support for ATI opensource 3d was. I then realised I should have posted here, posted the procedure, and linked to the thread for anyone who wanted, a mod subsequently did what I should have done in the first place. Mod did good.

Fair enough.  Your opening title to your thread was a bit misleading then.  If you didn't care about the other features of the .32 kernel, perhaps it shouldn't have been the first part of your subject line, which would have kept me from talking more about ... the .32 kernel.  Please continue your ATi conversations, I'll find another thread about the .32 kernel, and wont post them here anymore.

---

### Post by Nerd King on 2009-12-07
> **toupeiro said:**
> Fair enough.  Your opening title to your thread was a bit misleading then.  If you didn't care about the other features of the .32 kernel, perhaps it shouldn't have been the first part of your subject line, which would have kept me from talking more about ... the .32 kernel.  Please continue your ATi conversations, I'll find another thread about the .32 kernel, and wont post them here anymore.
Not misleading as such. .32 kernel + open drivers produce win. It came with the 32 kernel and the xorg updates to match it, and without the 32 kernel you don't get the ATI coolness. For me it also fixed my wi-fi problem, so it was a story of a good upgrade as such, that turned into a "Wow this open ATI driver rocks" as that was my only way to get the kernel working and it turned out to be a pleasant surprise. Hope that makes sense.

---

### Post by PaulInBHC on 2009-12-07
I did recovery mode and safe-upgrade, all is well now. I'm thinking there may have been another problem not related to this ATI driver.

---

### Post by handy on 2009-12-08
From what I've been reading, the development of the ATi open-source drivers really is moving along much faster than I expected.

People are getting great 2D, very usable (though still slower than catalyst) 3D, using kernel .32, & a combination of .git & testing packages.

Kernel .33 is expected to not only bring increased 3D performance but also the much anticipated & greatly desired by the notebook users in particular, power management.  

Just how polished & universal the ATi GPU power management will be in the kernel .33 release is of course something we won't really know until it arrives?

Here is a link on the power management topic:

[http://www.phoronix.com/scan.php?page=news_item&px=NzcyNw](http://www.phoronix.com/scan.php?page=news_item&px=NzcyNw)

---

### Post by handy on 2009-12-08
Here is great graphic representation of just where the xf86-video-ati open-source xf86-video-ati drivers are *_currently_* up to.  Very impressive:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

---

### Post by Nerd King on 2009-12-09
> **handy said:**
> From what I've been reading, the development of the ATi open-source drivers really is moving along much faster than I expected.

People are getting great 2D, very usable (though still slower than catalyst) 3D, using kernel .32, & a combination of .git & testing packages.

Kernel .33 is expected to not only bring increased 3D performance but also the much anticipated & greatly desired by the notebook users in particular, power management.  

Just how polished & universal the ATi GPU power management will be in the kernel .33 release is of course something we won't really know until it arrives?

Here is a link on the power management topic:

[http://www.phoronix.com/scan.php?page=news_item&px=NzcyNw](http://www.phoronix.com/scan.php?page=news_item&px=NzcyNw)
Gotta say that it's holding up brilliantly for me. The 3D is responsive, 2D is fast (World Of Goo is smoother than ever) and it's coping with Linux 3D games just fine. Wine 3D is the next step I guess. Seriously, I'm hugely impressed because I remember when even the proprietary drivers were rubbish.

---

### Post by handy on 2009-12-09
> **Nerd King said:**
> Gotta say that it's holding up brilliantly for me. The 3D is responsive, 2D is fast (World Of Goo is smoother than ever) and it's coping with Linux 3D games just fine. Wine 3D is the next step I guess. Seriously, I'm hugely impressed because I remember when even the proprietary drivers were rubbish.

All of a sudden, there is this sudden building up of excitement within the Linux (& any system that uses X :D) communities with regard to the actual realisation that the ATi open-source drivers, are actually starting to cross the line.  

After so long, & so much work, we ARE starting to get the results of this combination of mammoth projects.

It really is finally actually coming together.  Many months sooner than I expected, & I follow this stuff daily! (Hmm, shows you how much I know! ;))

I think that kernel .33 has an extremely good chance of allowing most Linux, ATi GPU users to kiss the catalyst drivers goodbye (hopefully) forever.  

Which is an awesome achievement. Especially for those of us who have spent years trying to get some sense out of fglrx/catalyst, & having spent so much time being danced about backwards & forwards & then backwards again during that time.

I'm not bitching about AMD, I'm really grateful to them, they have contributed hugely with technical information that has been (I think) absolutely essential to the open-source support actually being realised for the ATi GPUs.

Fantastic!!! :KS

---

### Post by Nerd King on 2009-12-09
Some further info, not sure if this relates to the newer kernel, newer x or the driver, but I dual-screened the open driver today (my laptop+projector) and it was beautifully seamless. Monitors arranged side-by-side, stuff moving accross the two monitors perfectly. It was an absolute piece of cake and worked wonderfully. Whoever's responsible, thank you, I never got the bloody thing working on Catalyst without half-killing my laptop!

---

### Post by LinuxFanBoi on 2009-12-09
> **racerraul said:**
> I'll jump ship when things get where they need to be for ATI drivers to provide all the power the HW is capable of...

By then it may be time to upgrade my Nvidia cards.

By then your GPU will be able to handle all the processing requirements of your PC.

---

### Post by Xbehave on 2009-12-09
> **Nerd King said:**
> Some further info, not sure if this relates to the newer kernel, newer x or the driver, but I dual-screened the open driver today (my laptop+projector) and it was beautifully seamless. Monitors arranged side-by-side, stuff moving accross the two monitors perfectly. It was an absolute piece of cake and worked wonderfully. Whoever's responsible, thank you, I never got the bloody thing working on Catalyst without half-killing my laptop!
It's the radeon guys, since ATI gave them the spec, they have been working their butts off to get everything working, the kernel is acting as an enabler but it's the radeon guys (i think theres only about a dozen of them) that are ones selling the crack. Next up on their crack stand is power-saving, but that needs KMS to support it, so will require 2.6.33 and the latest version of the xorg ati drivers to take advantage of it.

---

### Post by Pasdar on 2009-12-09
ATI 4570
Hmm, I have a ten fold drop in performance.

$ uname -a
Linux iRUNiX 2.6.32-020632-generic #020632 SMP Thu Dec 3 10:58:45 UTC 2009 i686 GNU/Linux

$ glxinfo | grep version
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 2.1 Mesa 7.7-rc2
OpenGL shading language version string: 1.20

$ glxgears
1258 frames in 5.0 seconds = 251.428 FPS
1304 frames in 5.0 seconds = 260.755 FPS
1304 frames in 5.0 seconds = 260.762 FPS
1307 frames in 5.0 seconds = 261.271 FPS
1305 frames in 5.0 seconds = 260.864 FPS

---

### Post by Xbehave on 2009-12-09
check that```
sudo cat /sys/module/radeon/parameters/modeset
``` gives 1
And ```
glxinfo | grep -i render
``` says you are direct rendering.

If it's still slow it's probably a bug with the xorg your using are you on crack?

---

### Post by Pasdar on 2009-12-10
Are you talking to me?

> sudo cat /sys/module/radeon/parameters/modeset
I only have radeontools in /sys/module .... so I cant check this

> glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer


I also enabled Xrender for desktop composition because openGL would not work.

---

### Post by handy on 2009-12-10
Check out the first post, & then the last few pages of this thread?

[http://bbs.archlinux.org/viewtopic.php?id=79509&p=1](http://bbs.archlinux.org/viewtopic.php?id=79509&p=1)

As far as I'm concerned it is where it is all happening...

Though there are certainly some other threads here & there that add some spice to the topic. :)

---

### Post by handy on 2009-12-10
Following is a link to some very interesting info' re. kernel .33, & the ATi open-source support in particular:

[http://www.phoronix.com/scan.php?page=news_item&px=Nzc4OQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzc4OQ)

---

### Post by Yvan300 on 2009-12-10
I can now play urban terror with the open source drivers. A feat that could not be accomplished with the ones packaged with jaunty and ibex.

---

### Post by Patapalo on 2009-12-10
Ati Radeon 9600

With 2.6.31

5864 frames in 5.0 seconds
5979 frames in 5.0 seconds
5805 frames in 5.0 seconds
6312 frames in 5.0 seconds
6303 frames in 5.0 seconds
6297 frames in 5.0 seconds
6325 frames in 5.0 seconds
6321 frames in 5.0 seconds
6307 frames in 5.0 seconds
6359 frames in 5.0 seconds
6338 frames in 5.0 seconds
6308 frames in 5.0 seconds
6332 frames in 5.0 seconds
6313 frames in 5.0 seconds
6309 frames in 5.0 seconds
6312 frames in 5.0 seconds
6328 frames in 5.0 seconds
6277 frames in 5.0 seconds

With **2.6.32**

3011 frames in 5.0 seconds
3072 frames in 5.0 seconds
3291 frames in 5.0 seconds
3287 frames in 5.0 seconds
3281 frames in 5.0 seconds
3288 frames in 5.0 seconds
3286 frames in 5.0 seconds
3055 frames in 5.0 seconds
2948 frames in 5.0 seconds
2676 frames in 5.0 seconds
2827 frames in 5.0 seconds
2319 frames in 5.0 seconds

what i do wrong?

---

### Post by handy on 2009-12-10
Patapalo, are both of your fps from using the open-source radeon drivers?

From what I have read, the open-source drivers are still slower than the catalyst drivers in 3D.

---

### Post by Suky on 2009-12-13
I just want to update my result.

ATI xpress 1250 + Kernel 2.6.31-16 ~ 1250 frames in 5.0 second

After upgrade to 2.6.32 ~ 1750 frames in 5.0 second 

But when i update by added [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) to my repository and ran upgrade

my result down to 1250 frames in 5.0 second. 

Now, I removed [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) out and came back to 2.6.31 but the result still around 1250 frames.

:(

---

### Post by Xbehave on 2009-12-14
removing a ppa will not downgrade the packages, you need ppa-purge or pinning or manually downgrading (if ppa is gone they will not upgrade)

I think dri2/later drivers/mesa support more calls so even if it gives less FPS on glxgears you should get better performance out of real world apps.

---

### Post by kreggz on 2009-12-14
I removed my ATI card in disgust with the ATI drivers and I will no longer purchase any ATI cards in the future.
:(

---

### Post by Suky on 2009-12-14
> **Xbehave said:**
> removing a ppa will not downgrade the packages, you need ppa-purge or pinning or manually downgrading (if ppa is gone they will not upgrade)

I think dri2/later drivers/mesa support more calls so even if it gives less FPS on glxgears you should get better performance out of real world apps.


Thanks for your suggestion but i don't know how to downgrade!!! :(

---

### Post by handy on 2009-12-14
> **kreggz said:**
> I removed my ATI card in disgust with the ATI drivers and I will no longer purchase any ATI cards in the future.
:(

That's your choice of course, but your timing is not too good, as the best is yet to come, & it is happening fast... :)

---

### Post by Xbehave on 2009-12-14
> **Suky said:**
> Thanks for your suggestion but i don't know how to downgrade!!! :(
The easiest way is to install ppa-purge

_Pinning_ (not 100% sure if this works exactly as i describe, harder than ppa-purge but lets you keep the repo (just not use anything from it by default)
1) Fine the ppa name (i think you need the ppa installed) apt-cache policy, gives a line like
```
 500 http://ppa.launchpad.net karmic/main Packages                                                             
     release v=9.10,o=**LP-PPA-xorg-edgers**,a=karmic,n=karmic,l=Ubuntu,c=main                                     
     origin ppa.launchpad.net                                         
```
2) sudo nano /etc/apt/preferences/00pinning (file name can be anything)
add ```
Package: *
Pin: release o=LP-PPA-xorg-edgers
Pin-Priority: 50 #default is 500, 50 is lower so other packages will install over it

```

_Manual_ (trickiest but gives you explicit control)
1) Fire up aptitude (its doable with gui tools, but i know aptitude best)
2) Find the package (/ packacagename or / part of package name ,n until you get the right one), and select it (enter) (see image)
3) scroll to the bottom of the box and install the version you want (+ key)
4) press g to review changes as downgrading may have knock on effects ("fixing breakages" is done using e ! , . but a red bar comes up if you need to do that)
5) press g to apply (it may now prompt for your
 password, if you ran aptitude as user, which is a good practice)

btw there is a new version out today which may be better

---

### Post by Nerd King on 2009-12-15
Hopefully this info will interest some. It seems that while performance isn't there yet, overall the implementation is cleaner in this driver than the catalyst driver. I say this as until the last 2 or 3 versions gaming + compiz was impossible, and even now some games work in NVIDIA and not ATI. One example of this is Plants Vs Zombies. On NVIDIA it's flawless, on ATI it's just a mess. With the open drivers it runs perfectly. It's slow, but it's perfect. No rendering issues at all, even with compiz enabled. Overall I'm pretty happy with that, and I can assume the current pace of development will see performance catch up soon enough. So the future of Wine gaming looks to be good for ATI users. Enjoy it, these are exciting times.

---

### Post by Pasdar on 2009-12-15
I see it differently, but I hope I'm wrong.

The proprietary drivers just have annoying bugs that will be fixed in time. Most of these bugs in the latest version will even go unnoticed by many. The performance is top notch. Fixing bugs is just a matter of time.

However the open-source drivers perform below standard, but have no noticeable bugs that I could find. Now I haven't checked the source, so I don't know... however I think this means that the source is too much redundancy, and is simply inefficient... that's why its so slow compared to the proprietary drivers. Fixing an inefficiently written program, will require a complete re-check/re-do, to make it better and will take much more time..

Again, I don't know the source code, im just guessing.

---

### Post by Grenage on 2009-12-15
> That's your choice of course, but your timing is not too good, as the best is yet to come, & it is happening fast... 

ATI fans have been saying that for years, but the drivers are still junk compared to Nvidia.

---

### Post by handy on 2009-12-15
> **Pasdar said:**
> 
I see it differently, but I hope I'm wrong.

The proprietary drivers just have annoying bugs that will be fixed in time. Most of these bugs in the latest version will even go unnoticed by many. The performance is top notch. Fixing bugs is just a matter of time. 

If you use distro that is not supported by AMD such as Arch, which is a distro that uses a rolling release package management system, which provides very new software, you would find that one (as we are currently experiencing) problem with the Catalyst drivers, is that they don't keep up with the Linux system development. i.e. the last two versions of Catalyst are not compatible with the current version of the xorg-server > 1.6.

Also, the 2D performance of the open-source drivers are vastly superior to that provided by Catalyst. With Catalyst the video tears, & screen refresh lags, scrolling windows lags also.

> **Pasdar said:**
> 
However the open-source drivers perform below standard, but have no noticeable bugs that I could find. Now I haven't checked the source, so I don't know... however I think this means that the source is too much redundancy, and is simply inefficient... that's why its so slow compared to the proprietary drivers. Fixing an inefficiently written program, will require a complete re-check/re-do, to make it better and will take much more time..

Again, I don't know the source code, im just guessing.

The open-source GPU support system is in the process of being completely rewritten;- it is moving into the kernel & mesa.

I think you should hold your judgement & observe the improvements that are coming in the .32 & beyond kernels, actually kernel .33, is looking particularly good for many ATi GPUs, the 3D speed will just keep on getting better... :)



> **Grenage said:**
> ATI fans have been saying that for years, but the drivers are still junk compared to Nvidia.

If you spend the time & have a read up on what's happening re, the open-source drivers, you may learn a thing or two?

There are some links at the bottom of the first post in this thread, that would be a good place to start.

---

### Post by Pasdar on 2009-12-15
The 3distro support thing is indeed one of the major flaws of the proprietary drivers, it should definitely be on their list to change that. Its just not at the linux drivers are not anywhere near the top of their priority list unfortunately.

I hope the open-source drivers will one day out-do the proprietary drivers in 3D performance, but I am very skeptical. Its one thing to write drivers to something work, its another to actually outdo the company's own drivers in performance.

---

### Post by Grenage on 2009-12-15
> If you spend the time & have a read up on what's happening re, the open-source drivers, you may learn a thing or two?

I've been trying out the proprietary and open drivers as and when new versions come out.  Each and every time (across multiple cards), the system has either become unstable or at best given poor performance.

Compared to the Nvidia offerings, there is no contest at the moment.  I'd love more competition and choice, but it looks like it's going to be a very long time until ATI get their *** in gear (if they ever do).

---

### Post by Xbehave on 2009-12-15
1) ATI only released the specs for their stuff about a year ago so, it's not year**s** people have been claiming this, but **a** year.

2) The radeon drivers are in much better shape than the noveu drivers (this is a thread about the open drivers), but if you care more about openness or run a cutting edge setup closed drivers often arn't an option (I switched to radeon because full screen 64_bit flash was tearing)

3)It's not about ATI, the development is mostly done by the opensource community (I think it's something like 2 hobyists, 2 red hat, 2 novell and 2 ATI/AMD, guys).

Regarding perfomance v bugs, needed a ground up rewrite to improve performance is the exception not the rule. Generally you see rewrites only when the project has significantly outgrown itself and become a bit of a mess. As examples of non-rewrites, Firefox has significantly improved since 2.0, kde4 is a lot faster in 4.4 than 4.0, webkit(WebCore) has never had a rewritten since khtml, now things like BTRFS (which at it's core is a rewritten reiserFS) or webkit(JavaScriptCore) do happen but in  every case i can think of it's due to the project outgrowing itself. Perhaps I'm biased as I'm mainly interested in python but I'm a fan of getting "everything" working, then optimizing not the other way around.

---

### Post by aspiredfang on 2009-12-15
I'm using the proprietary drivers and have never had a single problem to be honest, maybe it's the specific cards people use which cross the line in terms of reliability I don't know. 

Simply slating the development work that has gone in to them is not "cool" though. Imagine how many varieties of Linux there actually are and the different set-ups one package has to work with. I consider it pretty impressive they do work as they do considering how complex GPUs are these days!

On the flip side where people talk about how great the Nvidia ones are, on a media center set up I have, there have been many problems, installation just being one of them. So, what I'm trying to say is chill out :P 

Rome wasn't built in a day and we should have some thanks for the open source folks, AMD and Nvidia. Until I come across a problem with the proprietary drivers or read that the open source ones have become mature enough to use across both 2D and 3D (I am no driver dev) this is a stance I will stick to. I can understand them not wanting to give away their "secrets" to the competitor in such a competitive market.

---

### Post by Grenage on 2009-12-15
Don't get me wrong; I appreciate the FOSS driver project and the work that's gone into it. I also *want* the ATI drivers to be a good option, that's why I keep coming back to try new releases.

It's just my personal opinion that after trying a handful of cards with many driver releases, the performance and stability are terribly lacking compared to Nvidia.

---

### Post by Kazade on 2009-12-15
> **Pasdar said:**
>  Now I haven't checked the source, so I don't know... however I think this means that the source is too much redundancy, and is simply inefficient... that's why its so slow compared to the proprietary drivers. Fixing an inefficiently written program, will require a complete re-check/re-do, to make it better and will take much more time..

Again, I don't know the source code, im just guessing.

Nope, it's not the quality of the source that is the problem. Graphics cards are extraordinarily complex, there are many different ways of doing the "same" thing, but some are more efficient than others, but the more efficient stuff that pushes the hardware to it's full potential, tends to be more difficult to do. So performance is only really an issue until the drivers are feature complete. It's the traditional "make it work, then make it fast".

As a simple example, you can render an a 3D model by using "immediate mode" and sending the vertices one at a time (which is fundamentally quite simple), which would render perfectly, it would just be slow as hell. Then you can use "vertex arrays" (store the data in RAM) to speed that up, but "vertex buffer objects" (store the data in VRAM) are even faster. Each of these things need to be implemented, and at the low level, each is more complicated and takes longer to develop than the last. Give it time, it'll get there.

---

### Post by sdowney717 on 2009-12-15
[http://wiki.x.org/wiki/radeonTV?highlight=%28tv%29|%28out%29](http://wiki.x.org/wiki/radeonTV?highlight=%28tv%29|%28out%29)

how is the performance of tv out for R500 cards?

---

### Post by handy on 2009-12-15
> **Pasdar said:**
> The 3distro support thing is indeed one of the major flaws of the proprietary drivers, it should definitely be on their list to change that. Its just not at the linux drivers are not anywhere near the top of their priority list unfortunately.

I hope the open-source drivers will one day out-do the proprietary drivers in 3D performance, but I am very skeptical. Its one thing to write drivers to something work, its another to actually outdo the company's own drivers in performance.

AMD are giving the open-source dev team all of the support they legally can.  There are some problems due to the GNU license that make it difficult from time to time.

The open-source drivers will be better than the closed ones not only as they already are in 2D, but quite soon in 3D as well.

There are momentous changes in this area well under way.  Kernel .32 is already a milestone.  There are people getting great results in the R600 & R700 GPU trees now, using combinations of this kernel, & packages in testing & .git.

We are right on the edge of these changes coming into mainstream. :D

---

### Post by handy on 2009-12-15
> **Grenage said:**
> I've been trying out the proprietary and open drivers as and when new versions come out.  Each and every time (across multiple cards), the system has either become unstable or at best given poor performance.

Compared to the Nvidia offerings, there is no contest at the moment.  I'd love more competition and choice, but it looks like it's going to be a very long time until ATI get their *** in gear (if they ever do).

You obviously still haven't caught on to what is happening with regard to the enormous amount of change that is currently in progress.  The results of which are only really just starting to become worthwhile re. 3D & some of the ATi GPU trees, & again only to people who are prepared to be using packages that are still in development or testing. 

As I've previously stated, these changes are on the verge of hitting mainstream, starting with the kernel .32, & dramatically improving in .33, & on.  Power management is already available in a limited form via a patch, & will apparently be out in .33 as well.

It's ok not to like the ATi GPUs from your past experience.  I own both ATi & nVidia, & having always been an nVidia proponent, it is only inside of the last 4 or 5 months, since I became aware of what is happening with AMD/ATi GPUs & open-source that I realised that ATi had a very different open-source future being created.

It's all good. ;)

---

### Post by Xbehave on 2009-12-15
> **handy said:**
> AMD are giving the open-source dev team all of the support they legally can.  There are some problems due to the GNU license that make it difficult from time to time.
Xorg is under the MIT/X11 license (a BSD like license), the problems are simply to do with intellectual property and the fact that ATI don't own all the IP to make their cards but license a lot of it from other companies (something like the Internal+Discrete graphics card in laptops is licensed between at least intel,amd and nvidia, so amd can't release any details without permission from intel and nvidia). Associated with this problem is the fact that AMD aren't actually sure on what they own or what documentation is relevant (because when all they released where binary drivers it didn't matter)

---

### Post by handy on 2009-12-15
> **Xbehave said:**
> Xorg is under the MIT/X11 license (a BSD like license), the problems are simply to do with intellectual property and the fact that ATI don't own all the IP to make their cards but license a lot of it from other companies (something like the Internal+Discrete graphics card in laptops is licensed between at least intel,amd and nvidia, so amd can't release any details without permission from intel and nvidia). Associated with this problem is the fact that AMD aren't actually sure on what they own or what documentation is relevant (because when all they released where binary drivers it didn't matter)

Yep, that's the story I read too.

---

### Post by bluelamp999 on 2009-12-15
Hi Handy

Firstly, thanks for your continued posts on this topic - it's heartening to see the advances being made.

I'm saddled with a Mobility Radeon X300 on my Dell laptop and would *lurve* to finally have some hardware 3D goodness...

Is it best to wait for for .32/.33 kernels or is there some way to jump the gun and get the enhanced GPU functionality now?

Either way, thanks again...

---

### Post by Xbehave on 2009-12-15
> **bluelamp999 said:**
> Hi Handy

Firstly, thanks for your continued posts on this topic - it's heartening to see the advances being made.

I'm saddled with a Mobility Radeon X300 on my Dell laptop and would *lurve* to finally have some hardware 3D goodness...

Is it best to wait for for .32/.33 kernels or is there some way to jump the gun and get the enhanced GPU functionality now?

Either way, thanks again...
You can jump the gun, but your system will no longer be supported so you may run into bugs. Also with .32+latest xorg, things are better but 3d is still not great.

add one of the following to /etc/apt/sources.lst
deb    [http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu](http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu)      karmic                  main
deb     [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)         karmic                  main
I have the latter, so i have no idea what the former does

Then install the latest kernel (2.6.32) either manually or from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") (there may be a ppa but i just downloaded and installed manually), there are also drm-next and daily build but i wouldn't recomend using them as they are less tested than 2.6.32 (which is pretty untested).

If you choose to do this, it's at your own risk and not my fault if you computer starts to crash more.My computer is running fine following my advice but yours may not.

> **handy said:**
> Yep, that's the story I read too.
It's just that you said "There are some problems due to the GNU license that make it difficult from time to time.", but (as i understand it) the kernel code isn't really affected by ATI IP so GNU/GPL is not the problem. But perhaps i misunderstood the situation/your post.

---

### Post by bluelamp999 on 2009-12-15
> **Xbehave said:**
> You can jump the gun, but your system will no longer be supported so you may run into bugs. Also with .32+latest xorg, things are better but 3d is still not great.

add one of the following to /etc/apt/sources.lst
deb    [http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu](http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu)      karmic                  main
deb     [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)         karmic                  main
I have the latter, so i have no idea what the former does

Then install the latest kernel (2.6.32) either manually or from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") (there may be a ppa but i just downloaded and installed manually), there are also drm-next and daily build but i wouldn't recomend using them as they are less tested than 2.6.32 (which is pretty untested).

If you choose to do this, it's at your own risk and not my fault if you computer starts to crash more.My computer is running fine following my advice but yours may not.

Wow! Thanks Xbehave!

I've got a stable Karmic install running right now so I probably shouldn't but I doubt I'll be able to resist the temptation...

---

### Post by handy on 2009-12-15
**@bluelamp999:** I'm far from an expert on this topic, I have just been following it consistently for about 5 months, apart from also putting up with the fglrx/catalyst drivers on Arch (which is constantly upgrading its packages). Because AMD/ATi doesn't support Arch (as it does Ubuntu), Arch ATi users have really had some ups & downs, I've only been on Arch since March 2008, & there has certainly been some fun & games in that period due to the unreliable & too slowly upgraded fglrx/catalyst drivers.  At least for Ubuntu users, AMD try to have catalyst working with the 6 monthly Ubuntu release.

You may have seen this page, which is linked to on the first page of this thread:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

Looking at that, should give you hope with regard to your R300 cored GPU I think. :)

I'm using an Radeon HD2600Pro, which uses the R600 core. I know people are getting good results with the R600 & R700 cores right now, due to what I read on this forum thread, the first post of which is basically kept up to date with the software developments:

[http://bbs.archlinux.org/viewtopic.php?id=79509&p=1](http://bbs.archlinux.org/viewtopic.php?id=79509&p=1)

As you can see by reading the first post on that page; by jumping through hoops you can get the best performance with the open-source solution on Arch.

I'm personally content to wait at least until kernel .32 comes out of [testing] on Arch (any day now) before I even think about starting to fiddle about with the open-source packages from [testing] & .git.
I'm really not in a big hurry, though I do look forward to having the great movie playback that the open-source drivers allowed me, last time I used them. :)

So my recommendation to you would be to continue patiently waiting, the day is coming when it will be an easy install & setup for your open-source ATi GPU solution.

If your hungry to have a go though, there is info' further back in this thread where someone has upgraded their Ubuntu to kernel .32 & installed the open-source packages, it may be worth reviewing, there was a link or two as well from memory.

Good luck. :)

---

### Post by bluelamp999 on 2009-12-15
Many thanks for the reply and the advice. You're a star!

---

### Post by handy on 2009-12-15
> **bluelamp999 said:**
> Many thanks for the reply and the advice. You're a star!

:lolflag: I've been called a lot of things before, but that's a first. Thanks. ;)

---

### Post by Nerd King on 2009-12-16
That would be me then.. easy enough really.

1. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/) download and install headers_all, headers_i386/x64, image_i386/x64.
2. Add PPA xorg-edgers [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) for details on how.

It's fast and stable for me with linux games and compiz, a little slow on Wine gaming at this stage, but constantly improving it seems.

---

### Post by handy on 2009-12-16
> **Nerd King said:**
> That would be me then.. easy enough really.

1. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/) download and install headers_all, headers_i386/x64, image_i386/x64.
2. Add PPA xorg-edgers [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) for details on how.

It's fast and stable for me with linux games and compiz, a little slow on Wine gaming at this stage, but constantly improving it seems.

Thanks for popping up again Nerd King, I think I'll put your links in the OP, for a while so we don't loose your very valuable input. :)

[I]**[Edit:]** I found that I already had a link to your page in the Ubuntu section of this threads OP.

I just added these links from your most recent post anyway, as it may help your truly valuable contribution to the Ubuntu ATi community sink in... :)[/I]

---

### Post by Nerd King on 2009-12-16
My contribution is zero. It's the devs who've done amazing things. They are gods whose shrines we should worship every day!

---

### Post by handy on 2009-12-16
> **Nerd King said:**
> My contribution is zero. It's the devs who've done amazing things. They are gods whose shrines we should worship every day!

I agree on both counts, to a point.

If no one communicates about the new changes; or their personal experiences with these changes, then far fewer people learn anything new. 

Nor, if we keep following this train; do the people who actually created these changes to start with, get to find out what is wrong with their changes & how they can improve on them.

Your input Nerd King, has been incredibly valuable, particularly for Ubuntu users, as most of my information sources are Arch based or Linux system specific.

---

### Post by handy on 2009-12-18
Read following link for details on a hotfix that has allowed Catalyst 9.12 to work with kernel .32, it also brings openCL support:

[http://bbs.archlinux.org/viewtopic.php?pid=673866#p673866](http://bbs.archlinux.org/viewtopic.php?pid=673866#p673866)

Not compatible with xorg-server 1.7 yet though.

---

### Post by slonlt on 2009-12-20
Hello, I'm running 3ghz dualcore 4gb ram and ati 3600. I want to play warcraft3 but it is very laggy. I'm using 2.6.32.2 kernel(the same was with 2.6.32) with XorgOnTheEdge. I have no lagg in linux games and no problems with compiz. 

Maybe someone knows how to fix that lagg in wine(tried both stable and newest release)?

---

### Post by AllRadioisDead on 2009-12-20
> **slonlt said:**
> Hello, I'm running 3ghz dualcore 4gb ram and ati 3600. I want to play warcraft3 but it is very laggy. I'm using 2.6.32.2 kernel(the same was with 2.6.32) with XorgOnTheEdge. I have no lagg in linux games and no problems with compiz. 
 
Maybe someone knows how to fix that lagg in wine(tried both stable and newest release)?
 I'm surprised you can run wine games with the native drivers, I'm impressed actually. When I heard progress was being made I never thought this much was being done.

---

### Post by Nerd King on 2009-12-20
2D Wine games are good, 3D accelerated a little slow. It's a matter of waiting for performance to pick up. Given the pace of development I'd say it'll catch Catalyst in the very near future (ie ready for 10.10).

---

### Post by slonlt on 2009-12-21
How to enable KMS? I want to have opengl 2.0 :)

---

### Post by Xbehave on 2009-12-21
> **slonlt said:**
> How to enable KMS? I want to have opengl 2.0 :)

run glxgears -info to see if you have it already (it will say DRI2 if you do)

---

### Post by slonlt on 2009-12-21
IRQ's not enabled, falling back to busy waits: 2 0
GL_RENDERER   = Mesa DRI R600 (RV635 9598) 20090101  TCL
GL_VERSION    = 1.5 Mesa 7.7-rc3
GL_VENDOR     = Advanced Micro Devices, Inc.

So no DRI2 :(

---

### Post by Xbehave on 2009-12-21
add this to your kernel line 
```
radeon.modeset=1
```
e.g it should looks something like

> kernel          /vmlinuz-2.6.32-020632-generic root=UUID=3541b994-5510-4be5-bbe9-9fef4ffc0a86 ro quiet radeon.modeset=1 
(i have grub1 read docs/ask somebody how to do this for grub2 if you need to.

---

### Post by slonlt on 2009-12-21
Done that and now I dont have any 3d acceleration it give me Software Renderer. Why is that?

---

### Post by Ubuntiac on 2009-12-22
I'm trying to get KMS / OGL 2.0 running as well with:

Lucid + xorg-edgers ppa + drm-next (2.6.32.996) + radeon.modeset=1 kernel line + an ATI HD4850

glxgears -info gives me:
```
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
GL_RENDERER   = Mesa DRI R600 (RV770 9440) 20090101  TCL DRI2
GL_VERSION    = 2.0 Mesa 7.8-devel
GL_VENDOR     = Advanced Micro Devices, Inc.
```

Wierd thing is, that all the drm sections of dmesg sound happy:
```
[    1.918483] [drm] radeon kernel modesetting enabled.                                                               
[    1.918866] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                        
[    1.918872] radeon 0000:01:00.0: setting latency timer to 64                                                       
[    1.920616] [drm] radeon: Initializing kernel modesetting.                                                         
[    1.920659] [drm] register mmio base: 0xFE9F0000                                                                   
[    1.920660] [drm] register mmio size: 65536                                                                        
[    1.921316] ATOM BIOS: Wekiva                                                                                      
[    1.921322] [drm] Clocks initialized !                                                                             
[    1.924029] [drm] Detected VRAM RAM=256M, BAR=256M                                                                 
[    1.924033] [drm] RAM width 256bits DDR                                                                            
[    1.924143] [TTM] Zone  kernel: Available graphics memory: 2029056 kiB.                                            
[    1.924157] [drm] radeon: 256M of VRAM memory ready                                                                
[    1.924159] [drm] radeon: 512M of GTT memory ready.                                                                
[    1.924202] [drm] Loading RV770 CP Microcode                                                                       
[    1.924281] platform radeon_cp.0: firmware: requesting radeon/RV770_pfp.bin                                        
[    1.926869] platform radeon_cp.0: firmware: requesting radeon/RV770_me.bin                                         
[    1.929048] [drm] GART: num cpu pages 131072, num gpu pages 131072                                                                    
[    1.970762] [drm] ring test succeeded in 1 usecs                                                                   
[    1.970823] [drm] radeon: ib pool ready.                                                                           
[    1.970877] [drm] ib test succeeded in 0 usecs                                                                     
[    1.970990] [drm] Radeon Display Connectors                                                                        
[    1.970991] [drm] Connector 0:                                                                                     
[    1.970992] [drm]   DVI-I                                                                                          
[    1.970994] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c                                   
[    1.970995] [drm]   Encoders:                                                                                      
[    1.970996] [drm]     DFP1: INTERNAL_UNIPHY                                                                        
[    1.970997] [drm]     CRT2: INTERNAL_KLDSCP_DAC2                                                                   
[    1.970998] [drm] Connector 1:                                                                                     
[    1.970999] [drm]   DIN                                                                                            
[    1.971000] [drm]   Encoders:                                                                                      
[    1.971001] [drm]     TV1: INTERNAL_KLDSCP_DAC2                                                                    
[    1.971002] [drm] Connector 2:                                                                                     
[    1.971003] [drm]   DVI-I                                                                                          
[    1.971004] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c                                   
[    1.971005] [drm]   Encoders:                                                                                      
[    1.971006] [drm]     CRT1: INTERNAL_KLDSCP_DAC1                                                                   
[    1.971007] [drm]     DFP2: INTERNAL_KLDSCP_LVTMA                                                     
[    2.146110] [drm] fb mappable at 0xD0141000                                                                        
[    2.146112] [drm] vram apper at 0xD0000000                                                                         
[    2.146113] [drm] size 7257600                                                                                     
[    2.146114] [drm] fb depth is 24                                                                                   
[    2.146115] [drm]    pitch is 6912                                                                                 
[    2.146167] fb0: radeondrmfb frame buffer device                                                                   
[    2.146168] registered panic notifier                                                                              
[    2.146172] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0                                    
[    2.147228] vga16fb: initializing                                                                                  
[    2.147230] vga16fb: mapped to 0xffff8800000a0000                                                                  
[    2.147260] fb1: VGA16 VGA frame buffer device                                                                     
[    2.170460] executing set pll                                                                                      
[    2.220035] executing set crtc timing                                                                              
[    2.220066] [drm] TV-13: set mode 1680x1050 25 
```


Any ideas anyone?

---

### Post by handy on 2009-12-22
Have a look at this thread, as these guys are non-stop working with the cutting edge Linux based open-source ATi software.

On the first post you will get the current stuff as it is kept up to date, on the last 2 or 3 pages, depending on how fast things are moving at the time, you will get nitty-gritty details on just what is happening right now:

[http://bbs.archlinux.org/viewtopic.php?id=79509&p=1](http://bbs.archlinux.org/viewtopic.php?id=79509&p=1)

---

### Post by Xbehave on 2009-12-22
> **Ubuntiac said:**
> I'm trying to get KMS / OGL 2.0 running as well with:

Lucid + xorg-edgers ppa + drm-next (2.6.32.996) + radeon.modeset=1 kernel line + an ATI HD4850

glxgears -info gives me:
```
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
GL_RENDERER   = Mesa DRI R600 (RV770 9440) 20090101  TCL DRI2
GL_VERSION    = 2.0 Mesa 7.8-devel
GL_VENDOR     = Advanced Micro Devices, Inc.
```

Wierd thing is, that all the drm sections of dmesg sound happy:
The fact it says dri2 suggests you do have everything running, what sort of FPS do you get? The bug may be because your too cutting edge, do you have a plain old 2.6.32 lying around?

> Done that and now I dont have any 3d acceleration it give me Software Renderer. Why is that? 
what is the output of
```
glxgears -info
```
```
sudo cat /sys/module/radeon/parameters/modeset
```

edit: read the last couple of pages of handy's link (hey it's a long thread and i'm lazy) [thx for link]
1) there is an issue with kms and kernel 2.6.32.2
2) somebody has the exact same problem as Ubuntiac, but the post sort of got lost in the thread so i didn't see anything useful

---

### Post by Ubuntiac on 2009-12-22
I just realised that part of my problem was I got mixed up and that dmesg was from when I was in my vanilla .32 kernel, not the drm-next one.

DRM next with the modesetting variable does, infact give me errors about the firmware not being found;

```
[   17.590185] [drm] Loading RV770 Microcode
[   17.590188] platform radeon_cp.0: firmware: requesting radeon/RV770_pfp.bin
[   17.635441] platform radeon_cp.0: firmware: requesting radeon/RV770_me.bin
[   17.637929] platform radeon_cp.0: firmware: requesting radeon/R700_rlc.bin
[   17.639727] r600_cp: Failed to load firmware "radeon/R700_rlc.bin"
[   17.639732] [drm:rv770_startup] *ERROR* Failed to load firmware!
```

So where does one get this file R700_rlc.bin? I tried doing a find by file name in the package manager, but it didn't turn up anything...

---

### Post by Xbehave on 2009-12-22
[http://www.phoronix.com/forums/showpost.php?p=104897&postcount=26](http://www.phoronix.com/forums/showpost.php?p=104897&postcount=26)

that seams to offer the files and where you have to put them

---

### Post by Ubuntiac on 2009-12-22
Thanks!

I think I'm really close now... I don't see any (EE) errors, although my screen goes black and the kernel seems to hang when X starts if I use radeon.modeset=1 (it's fine without it though)

The only things that look anything like errors are:

[    0.168010] (II) RADEON(0): Not using mode "1680x1050" (bad mode clock/interlace/doublescan)

[    0.359177] (II) AIGLX: Screen 0 is not DRI2 capable


and much later:
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x46ecf8]
1: /usr/bin/X (0x400000+0x6d6fd) [0x46d6fd]
2: /lib/libpthread.so.0 (0x7f5d36b9a000+0xf190) [0x7f5d36ba9190]
3: /usr/bin/X (0x400000+0x3a04b) [0x43a04b]
4: /usr/bin/X (0x400000+0x3a35b) [0x43a35b]
5: /usr/bin/X (0x400000+0x3aede) [0x43aede]
6: /usr/bin/X (xf86PostMotionEventP+0x87) [0x47a027]
7: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f5d0e85b000+0x53df) [0x7f5d0e8603df]
8: /usr/bin/X (0x400000+0x778c7) [0x4778c7]
9: /usr/bin/X (0x400000+0x10fd24) [0x50fd24]
10: /lib/libpthread.so.0 (0x7f5d36b9a000+0xf190) [0x7f5d36ba9190]
11: /lib/libpthread.so.0 (__open64+0x10) [0x7f5d36ba8940]
12: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f5d0e85b000+0x32d1) [0x7f5d0e85e2d1]
13: /usr/bin/X (0x400000+0x7a577) [0x47a577]
14: /usr/bin/X (NewInputDeviceRequest+0x1ca) [0x47a97a]
15: /usr/bin/X (0x400000+0x10a12a) [0x50a12a]
16: /usr/bin/X (0x400000+0x10a3be) [0x50a3be]
17: /usr/bin/X (config_init+0x9) [0x45f109]
18: /usr/bin/X (0x400000+0x260a5) [0x4260a5]
19: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f5d35b1aadd]
20: /usr/bin/X (0x400000+0x25c99) [0x425c99]
Segmentation fault at address (nil)



Full Xorg.o.log for context is:
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.7.99.2
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-26-xen x86_64 Ubuntu
Current Operating System: Linux morpheus 2.6.32-996-generic #200912181514 SMP Fri Dec 18 15:19:26 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-996-generic root=UUID=ac91a2d9-31be-4b85-bf96-9eaf0d87b6b4 ro quiet splash
Build Date: 20 December 2009  12:32:38AM
xorg-server 2:1.7.99.2~git20091220.0cb638dc-0ubuntu0tormod (buildd@) 
Current version of pixman: 0.16.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.000000] (--) probed, [    0.000007] (**) from config file, [    0.000010] (==) default setting,
	[    0.000014] (++) from command line, [    0.000017] (!!) notice, [    0.000020] (II) informational,
	[    0.000024] (WW) warning, [    0.000027] (EE) error, [    0.000030] (NI) not implemented, [    0.000033] (??) unknown.
[    0.000066] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 22 04:22:39 2009
[    0.000093] (==) Using config file: "/etc/X11/xorg.conf"
[    0.000134] (==) No Layout section.  Using the first Screen section.
[    0.000139] (**) |-->Screen "Default Screen" (0)
[    0.000143] (**) |   |-->Monitor "<default monitor>"
[    0.000290] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    0.000293] (**) |   |-->Device "Default Device"
[    0.000296] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    0.000309] (==) Automatically adding devices
[    0.000312] (==) Automatically enabling devices
[    0.000329] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.000359] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.000362] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.000366] (II) Cannot locate a core pointer device.
[    0.000369] (II) Cannot locate a core keyboard device.
[    0.000371] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    0.000375] (II) Loader magic: 0x7cb400
[    0.000378] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
[    0.015323] (--) PCI:*(0:1:0:0) 1002:9440:1002:0502 ATI Technologies Inc RV770 [Radeon HD 4870] rev 0, Mem @ 0xd0000000/268435456, 0xfe9f0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    0.015381] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.015386] (II) "extmod" will be loaded by default.
[    0.015389] (II) "dbe" will be loaded by default.
[    0.015391] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    0.015394] (II) "record" will be loaded by default.
[    0.015397] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    0.015399] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    0.015403] (II) LoadModule: "glx"
[    0.015549] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    0.015655] (II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.015671] (==) AIGLX enabled
[    0.015675] (II) Loading extension GLX
[    0.015684] (II) LoadModule: "dri"
[    0.015730] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    0.015827] (II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.015842] (II) Loading extension XFree86-DRI
[    0.015846] (II) LoadModule: "dri2"
[    0.015882] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    0.015926] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
[    0.015939] (II) Loading extension DRI2
[    0.015942] (II) LoadModule: "extmod"
[    0.015975] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    0.016042] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.016057] (II) Loading extension MIT-SCREEN-SAVER
[    0.016059] (II) Loading extension XFree86-VidModeExtension
[    0.016061] (II) Loading extension XFree86-DGA
[    0.016064] (II) Loading extension DPMS
[    0.016066] (II) Loading extension XVideo
[    0.016069] (II) Loading extension XVideo-MotionCompensation
[    0.016071] (II) Loading extension X-Resource
[    0.016074] (II) LoadModule: "dbe"
[    0.016111] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    0.016155] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.016168] (II) Loading extension DOUBLE-BUFFER
[    0.016171] (II) LoadModule: "record"
[    0.016214] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    0.016253] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.016266] (II) Loading extension RECORD
[    0.016269] (II) LoadModule: "ati"
[    0.016449] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    0.016490] (II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
[    0.016508] (II) LoadModule: "radeon"
[    0.016663] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    0.016825] (II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
[    0.016849] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
[    0.018335] (++) using VT number 7

[    0.019517] (II) Primary Device is: PCI 01@00:00:0
[    0.019587] (II) [KMS] drm report modesetting isn't supported.
[    0.019638] (II) RADEON(0): Built from git commit 6e1f5553c6d7e3b5d089af2e3d587efe95936855
[    0.019644] (II) RADEON(0): TOTO SAYS 00000000fe9f0000
[    0.019647] (II) RADEON(0): MMIO registers at 0x00000000fe9f0000: size 64KB
[    0.019684] (II) RADEON(0): PCI bus 1 card 0 func 0
[    0.019697] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    0.019701] (**) RADEON(0): Depth 24, [    0.019704] (--) framebuffer bpp 32
[    0.019707] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    0.019712] (==) RADEON(0): Default visual is TrueColor
[    0.019729] (II) Loading sub module "vgahw"
[    0.019732] (II) LoadModule: "vgahw"
[    0.019935] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    0.019990] (II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
[    0.020013] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    0.020018] (==) RADEON(0): RGB weight 888
[    0.020021] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    0.020027] (--) RADEON(0): Chipset: "ATI Radeon 4800 Series" (ChipID = 0x9440)
[    0.020033] (--) RADEON(0): Linear framebuffer at 0x00000000d0000000
[    0.020071] (II) RADEON(0): PCIE card detected
[    0.020087] (II) Loading sub module "int10"
[    0.020090] (II) LoadModule: "int10"
[    0.020278] (II) Loading /usr/lib/xorg/modules/libint10.so
[    0.020336] (II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
[    0.020349] (II) RADEON(0): initializing int10
[    0.025556] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    0.026282] (II) RADEON(0): ATOM BIOS detected
[    0.026290] (II) RADEON(0): ATOM BIOS Rom: 
[    0.026292] 	SubsystemVendorID: 0x1002 SubsystemID: 0x0502
[    0.026296] 	IOBaseAddress: 0xc000
[    0.026299] 	Filename: B3B50701.100
[    0.026301] 	BIOS Bootup Message: 
Wekiva RV770 B50701 Board                                                   

[    0.026307] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    0.026310] (II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffec
[    0.026313] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    0.026316] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffec
[    0.026319] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    0.026331] (II) RADEON(0): Default Engine Clock: 750000
[    0.026334] (II) RADEON(0): Default Memory Clock: 900000
[    0.026337] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    0.026340] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    0.026342] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 16000
[    0.026345] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 6000
[    0.026348] (II) RADEON(0): Maximum Pixel Clock: 400000
[    0.026350] (II) RADEON(0): Reference Clock: 100000
[    0.026380] drmOpenDevice: node name is /dev/dri/card0
[    0.028745] drmOpenDevice: open result is 11, (OK)
[    0.031066] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    0.031099] drmOpenDevice: node name is /dev/dri/card0
[    0.033404] drmOpenDevice: open result is 11, (OK)
[    0.033455] drmOpenByBusid: drmOpenMinor returns 11
[    0.033467] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    0.035791] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.31.0
[    0.035826] (==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

[    0.035840] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    0.035847] (II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
[    0.035851] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[    0.035856] (II) RADEON(0): Color tiling disabled
[    0.035862] (II) Loading sub module "ddc"
[    0.035864] (II) LoadModule: "ddc"
[    0.035876] (II) Module "ddc" already built-in
[    0.035879] (II) Loading sub module "i2c"
[    0.035881] (II) LoadModule: "i2c"
[    0.035886] (II) Module "i2c" already built-in
[    0.035906] (II) RADEON(0): PLL parameters: rf=10000 rd=12 min=60000 max=120000; xclk=40000
[    0.035928] (II) RADEON(0): Output DVI-1 has no monitor section
[    0.035936] (II) RADEON(0): I2C bus "DVI-1" initialized.
[    0.035940] (II) RADEON(0): Output DVI-0 has no monitor section
[    0.035943] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    0.035947] (II) RADEON(0): Port0:
  XRANDR name: DVI-1
  Connector: DVI-I
  CRT2: INTERNAL_KLDSCP_DAC2
  DFP1: INTERNAL_UNIPHY
  DDC reg: 0x7e60
[    0.035969] (II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_KLDSCP_DAC1
  DFP2: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7e20
[    0.035996] (II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
Dac detection success
[    0.046204] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
finished output detect: 0
[    0.046221] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    0.048117] (II) RADEON(0): I2C device "DVI-0:DDC control interface" registered at address 0x6E.
[    0.101665] (II) RADEON(0): EDID for output DVI-0
[    0.101669] (II) RADEON(0): Manufacturer: SAM  Model: 30c  Serial#: 1296380466
[    0.101672] (II) RADEON(0): Year: 2007  Week: 41
[    0.101675] (II) RADEON(0): EDID Version: 1.3
[    0.101677] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.101684] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
[    0.101692] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.101697] (II) RADEON(0): Gamma: 2.20
[    0.101707] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    0.101712] (II) RADEON(0): First detailed timing is preferred mode
[    0.101715] (II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
[    0.101721] (II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
[    0.101727] (II) RADEON(0): Supported established timings:
[    0.101729] (II) RADEON(0): 720x400@70Hz
[    0.101732] (II) RADEON(0): 640x480@60Hz
[    0.101734] (II) RADEON(0): 640x480@67Hz
[    0.101737] (II) RADEON(0): 640x480@72Hz
[    0.101739] (II) RADEON(0): 640x480@75Hz
[    0.101741] (II) RADEON(0): 800x600@56Hz
[    0.101743] (II) RADEON(0): 800x600@60Hz
[    0.101746] (II) RADEON(0): 800x600@72Hz
[    0.101748] (II) RADEON(0): 800x600@75Hz
[    0.101750] (II) RADEON(0): 832x624@75Hz
[    0.101753] (II) RADEON(0): 1024x768@60Hz
[    0.101755] (II) RADEON(0): 1024x768@70Hz
[    0.101758] (II) RADEON(0): 1024x768@75Hz
[    0.101760] (II) RADEON(0): 1280x1024@75Hz
[    0.101762] (II) RADEON(0): 1152x864@75Hz
[    0.101765] (II) RADEON(0): Manufacturer's mask: 0
[    0.101767] (II) RADEON(0): Supported standard timings:
[    0.101769] (II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    0.101772] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    0.101775] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.101778] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.101781] (II) RADEON(0): Supported detailed timing:
[    0.101784] (II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    0.101790] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    0.101795] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    0.101799] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
[    0.101809] (II) RADEON(0): Monitor name: SyncMaster
[    0.101812] (II) RADEON(0): Serial No: HVCPA10751
[    0.101815] (II) RADEON(0): EDID (in hex):
[    0.101819] (II) RADEON(0): 	00ffffffffffff004c2d0c033232454d
[    0.101824] (II) RADEON(0): 	291101030e2f1e782ad515a455499a27
[    0.101828] (II) RADEON(0): 	145054bfef80b30081808140714f0101
[    0.101832] (II) RADEON(0): 	0101010101017c2e90a0601a1e403020
[    0.101836] (II) RADEON(0): 	3600da281100001a000000fd00384b1e
[    0.101841] (II) RADEON(0): 	510e000a202020202020000000fc0053
[    0.101845] (II) RADEON(0): 	796e634d61737465720a2020000000ff
[    0.101849] (II) RADEON(0): 	00485643504131303735310a20200009
[    0.101853] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    0.101856] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.101859] (II) RADEON(0): Manufacturer: SAM  Model: 30c  Serial#: 1296380466
[    0.101862] (II) RADEON(0): Year: 2007  Week: 41
[    0.101864] (II) RADEON(0): EDID Version: 1.3
[    0.101867] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.101872] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
[    0.101880] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.101885] (II) RADEON(0): Gamma: 2.20
[    0.101888] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    0.101893] (II) RADEON(0): First detailed timing is preferred mode
[    0.101895] (II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
[    0.101901] (II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
[    0.101906] (II) RADEON(0): Supported established timings:
[    0.101908] (II) RADEON(0): 720x400@70Hz
[    0.101911] (II) RADEON(0): 640x480@60Hz
[    0.101913] (II) RADEON(0): 640x480@67Hz
[    0.101915] (II) RADEON(0): 640x480@72Hz
[    0.101917] (II) RADEON(0): 640x480@75Hz
[    0.101920] (II) RADEON(0): 800x600@56Hz
[    0.101922] (II) RADEON(0): 800x600@60Hz
[    0.101924] (II) RADEON(0): 800x600@72Hz
[    0.101927] (II) RADEON(0): 800x600@75Hz
[    0.101929] (II) RADEON(0): 832x624@75Hz
[    0.101931] (II) RADEON(0): 1024x768@60Hz
[    0.101933] (II) RADEON(0): 1024x768@70Hz
[    0.101936] (II) RADEON(0): 1024x768@75Hz
[    0.101938] (II) RADEON(0): 1280x1024@75Hz
[    0.101940] (II) RADEON(0): 1152x864@75Hz
[    0.101943] (II) RADEON(0): Manufacturer's mask: 0
[    0.101945] (II) RADEON(0): Supported standard timings:
[    0.101948] (II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    0.101950] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    0.101953] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.101956] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.101959] (II) RADEON(0): Supported detailed timing:
[    0.101961] (II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    0.101966] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    0.101971] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    0.101975] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
[    0.101979] (II) RADEON(0): Monitor name: SyncMaster
[    0.101982] (II) RADEON(0): Serial No: HVCPA10751
[    0.101984] (II) RADEON(0): EDID (in hex):
[    0.101988] (II) RADEON(0): 	00ffffffffffff004c2d0c033232454d
[    0.101992] (II) RADEON(0): 	291101030e2f1e782ad515a455499a27
[    0.101997] (II) RADEON(0): 	145054bfef80b30081808140714f0101
[    0.102001] (II) RADEON(0): 	0101010101017c2e90a0601a1e403020
[    0.102005] (II) RADEON(0): 	3600da281100001a000000fd00384b1e
[    0.102009] (II) RADEON(0): 	510e000a202020202020000000fc0053
[    0.102013] (II) RADEON(0): 	796e634d61737465720a2020000000ff
[    0.102017] (II) RADEON(0): 	00485643504131303735310a20200009
finished output detect: 1
finished all detect
before xf86InitialConfiguration
Dac detection success
[    0.112213] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
[    0.112227] (II) RADEON(0): EDID for output DVI-1
[    0.167633] (II) RADEON(0): EDID for output DVI-0
[    0.167637] (II) RADEON(0): Manufacturer: SAM  Model: 30c  Serial#: 1296380466
[    0.167640] (II) RADEON(0): Year: 2007  Week: 41
[    0.167643] (II) RADEON(0): EDID Version: 1.3
[    0.167645] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.167651] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
[    0.167658] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.167664] (II) RADEON(0): Gamma: 2.20
[    0.167669] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    0.167674] (II) RADEON(0): First detailed timing is preferred mode
[    0.167676] (II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
[    0.167682] (II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
[    0.167687] (II) RADEON(0): Supported established timings:
[    0.167690] (II) RADEON(0): 720x400@70Hz
[    0.167692] (II) RADEON(0): 640x480@60Hz
[    0.167694] (II) RADEON(0): 640x480@67Hz
[    0.167697] (II) RADEON(0): 640x480@72Hz
[    0.167699] (II) RADEON(0): 640x480@75Hz
[    0.167701] (II) RADEON(0): 800x600@56Hz
[    0.167704] (II) RADEON(0): 800x600@60Hz
[    0.167706] (II) RADEON(0): 800x600@72Hz
[    0.167708] (II) RADEON(0): 800x600@75Hz
[    0.167711] (II) RADEON(0): 832x624@75Hz
[    0.167713] (II) RADEON(0): 1024x768@60Hz
[    0.167715] (II) RADEON(0): 1024x768@70Hz
[    0.167718] (II) RADEON(0): 1024x768@75Hz
[    0.167720] (II) RADEON(0): 1280x1024@75Hz
[    0.167722] (II) RADEON(0): 1152x864@75Hz
[    0.167725] (II) RADEON(0): Manufacturer's mask: 0
[    0.167727] (II) RADEON(0): Supported standard timings:
[    0.167730] (II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    0.167732] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    0.167735] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.167738] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.167741] (II) RADEON(0): Supported detailed timing:
[    0.167744] (II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    0.167749] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    0.167753] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    0.167758] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
[    0.167762] (II) RADEON(0): Monitor name: SyncMaster
[    0.167765] (II) RADEON(0): Serial No: HVCPA10751
[    0.167767] (II) RADEON(0): EDID (in hex):
[    0.167771] (II) RADEON(0): 	00ffffffffffff004c2d0c033232454d
[    0.167776] (II) RADEON(0): 	291101030e2f1e782ad515a455499a27
[    0.167780] (II) RADEON(0): 	145054bfef80b30081808140714f0101
[    0.167784] (II) RADEON(0): 	0101010101017c2e90a0601a1e403020
[    0.167788] (II) RADEON(0): 	3600da281100001a000000fd00384b1e
[    0.167792] (II) RADEON(0): 	510e000a202020202020000000fc0053
[    0.167797] (II) RADEON(0): 	796e634d61737465720a2020000000ff
[    0.167801] (II) RADEON(0): 	00485643504131303735310a20200009
[    0.167804] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    0.167806] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.167809] (II) RADEON(0): Manufacturer: SAM  Model: 30c  Serial#: 1296380466
[    0.167812] (II) RADEON(0): Year: 2007  Week: 41
[    0.167814] (II) RADEON(0): EDID Version: 1.3
[    0.167817] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.167822] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
[    0.167829] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.167835] (II) RADEON(0): Gamma: 2.20
[    0.167838] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    0.167843] (II) RADEON(0): First detailed timing is preferred mode
[    0.167845] (II) RADEON(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
[    0.167850] (II) RADEON(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
[    0.167859] (II) RADEON(0): Supported established timings:
[    0.167861] (II) RADEON(0): 720x400@70Hz
[    0.167863] (II) RADEON(0): 640x480@60Hz
[    0.167866] (II) RADEON(0): 640x480@67Hz
[    0.167868] (II) RADEON(0): 640x480@72Hz
[    0.167870] (II) RADEON(0): 640x480@75Hz
[    0.167873] (II) RADEON(0): 800x600@56Hz
[    0.167875] (II) RADEON(0): 800x600@60Hz
[    0.167877] (II) RADEON(0): 800x600@72Hz
[    0.167880] (II) RADEON(0): 800x600@75Hz
[    0.167882] (II) RADEON(0): 832x624@75Hz
[    0.167884] (II) RADEON(0): 1024x768@60Hz
[    0.167887] (II) RADEON(0): 1024x768@70Hz
[    0.167889] (II) RADEON(0): 1024x768@75Hz
[    0.167891] (II) RADEON(0): 1280x1024@75Hz
[    0.167894] (II) RADEON(0): 1152x864@75Hz
[    0.167896] (II) RADEON(0): Manufacturer's mask: 0
[    0.167898] (II) RADEON(0): Supported standard timings:
[    0.167901] (II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    0.167904] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    0.167907] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.167909] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.167912] (II) RADEON(0): Supported detailed timing:
[    0.167915] (II) RADEON(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    0.167920] (II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    0.167924] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    0.167928] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
[    0.167932] (II) RADEON(0): Monitor name: SyncMaster
[    0.167935] (II) RADEON(0): Serial No: HVCPA10751
[    0.167937] (II) RADEON(0): EDID (in hex):
[    0.167942] (II) RADEON(0): 	00ffffffffffff004c2d0c033232454d
[    0.167946] (II) RADEON(0): 	291101030e2f1e782ad515a455499a27
[    0.167950] (II) RADEON(0): 	145054bfef80b30081808140714f0101
[    0.167954] (II) RADEON(0): 	0101010101017c2e90a0601a1e403020
[    0.167958] (II) RADEON(0): 	3600da281100001a000000fd00384b1e
[    0.167963] (II) RADEON(0): 	510e000a202020202020000000fc0053
[    0.167967] (II) RADEON(0): 	796e634d61737465720a2020000000ff
[    0.167971] (II) RADEON(0): 	00485643504131303735310a20200009
[    0.167977] (II) RADEON(0): EDID vendor "SAM", prod id 780
[    0.168010] (II) RADEON(0): Not using mode "1680x1050" (bad mode clock/interlace/doublescan)
[    0.168015] (II) RADEON(0): Printing probed modes for output DVI-0
[    0.168019] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    0.168025] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    0.168030] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    0.168035] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    0.168040] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    0.168045] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    0.168051] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    0.168056] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.168061] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    0.168066] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    0.168071] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    0.168076] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.168084] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    0.168089] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    0.168094] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    0.168099] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    0.168105] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.168110] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    0.168116] (II) RADEON(0): Output DVI-1 disconnected
[    0.168119] (II) RADEON(0): Output DVI-0 connected
[    0.168123] (II) RADEON(0): Using exact sizes for initial modes
[    0.168126] (II) RADEON(0): Output DVI-0 using initial mode 1680x1050
[    0.168136] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    0.168145] (==) RADEON(0): DPI set to (96, 96)
[    0.168148] (II) Loading sub module "fb"
[    0.168150] (II) LoadModule: "fb"
[    0.168265] (II) Loading /usr/lib/xorg/modules/libfb.so
[    0.168376] (II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    0.168390] (II) Loading sub module "ramdac"
[    0.168393] (II) LoadModule: "ramdac"
[    0.168400] (II) Module "ramdac" already built-in
[    0.168404] (==) RADEON(0): Will attempt to use R6xx/R7xx EXA support if DRI is enabled.
[    0.168407] (II) Loading sub module "exa"
[    0.168409] (II) LoadModule: "exa"
[    0.168605] (II) Loading /usr/lib/xorg/modules/libexa.so
[    0.168659] (II) Module exa: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 2.5.0
	ABI class: X.Org Video Driver, version 6.0
[    0.168768] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    0.168778] (--) Depth 24 pixmap format is 32 bpp
[    0.168810] (II) RADEON(0): RADEONScreenInit d0000000 0 0
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
[    0.277662] (II) RADEON(0): Dynamic Power Management Disabled
[    0.277673] (==) RADEON(0): Using 24 bit depth buffer
mc fb loc is 00ef00d0
[    0.277684] (II) RADEON(0): RADEONInitMemoryMap() : 
[    0.277686] (II) RADEON(0):   mem_size         : 0x20000000
[    0.277689] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0
[    0.277692] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    0.277694] (II) RADEON(0): Depth moves disabled by default
[    0.277704] (II) RADEON(0): Allocating from a screen of 262080 kb
[    0.277708] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00b7c000
[    0.277711] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00b80000
[    0.277714] (II) RADEON(0): Will use 11760 kb for front buffer at offset 0x00000000
[    0.277755] (II) RADEON(0): Will use 64 kb for PCI GART at offset 0x0fff0000
[    0.277758] (II) RADEON(0): Will use 11760 kb for back buffer at offset 0x00b84000
[    0.277761] (II) RADEON(0): Will use 11760 kb for depth buffer at offset 0x01700000
[    0.277764] (II) RADEON(0): Will use 112640 kb for textures at offset 0x0227c000
[    0.277766] (II) RADEON(0): Will use 114128 kb for X Server offscreen at offset 0x0907c000
[    0.277789] drmOpenDevice: node name is /dev/dri/card0
[    0.280129] drmOpenDevice: open result is 11, (OK)
[    0.282457] drmOpenDevice: node name is /dev/dri/card0
[    0.284814] drmOpenDevice: open result is 11, (OK)
[    0.287117] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    0.287150] drmOpenDevice: node name is /dev/dri/card0
[    0.289456] drmOpenDevice: open result is 11, (OK)
[    0.289486] drmOpenByBusid: drmOpenMinor returns 11
[    0.289497] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    0.289524] (II) [drm] DRM interface version 1.3
[    0.289558] (II) [drm] DRM open master succeeded.
[    0.289572] (II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
[    0.289576] (II) RADEON(0): [drm] framebuffer handle = 0xd0000000
[    0.289598] (II) RADEON(0): [drm] added 1 reserved context for kernel
[    0.289608] (II) RADEON(0): X context handle = 0x1
[    0.289631] (II) RADEON(0): [drm] installed DRM signal handler
[    0.300742] (II) RADEON(0): [pci] 32768 kB allocated with handle 0x1152e900
[    0.300795] (II) RADEON(0): [pci] ring handle = 0x2b7ff000
[    0.300811] (II) RADEON(0): [pci] Ring mapped at 0x7f5d37738000
[    0.300816] (II) RADEON(0): [pci] Ring contents 0x00000000
[    0.300820] (II) RADEON(0): [pci] ring read ptr handle = 0x1b800000
[    0.300824] (II) RADEON(0): [pci] Ring read ptr mapped at 0x7f5d37737000
[    0.300828] (II) RADEON(0): [pci] Ring read ptr contents 0x00000000
[    0.300832] (II) RADEON(0): [pci] vertex/indirect buffers handle = 0x2b800000
[    0.300847] (II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0x7f5d22e1f000
[    0.300854] (II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
[    0.300858] (II) RADEON(0): [pci] GART texture map handle = 0x2b801000
[    0.300863] (II) RADEON(0): [pci] GART Texture map mapped at 0x7f5d2119f000
[    0.300935] (II) RADEON(0): [drm] register handle = 0x2fff8000
[    0.300955] (II) RADEON(0): [dri] Visual configs initialized
[    0.301038] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.301041] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x001f0000
[    0.301046] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    0.311147] (==) RADEON(0): Backing store disabled
[    0.311173] (II) RADEON(0): [DRI] installation complete
[    0.346779] (II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
[    0.346801] (II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
[    0.346816] (II) RADEON(0): [drm] dma control initialized, using IRQ 18
[    0.346820] (II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
[    0.346836] (WW) RADEON(0): DRI init changed memory map, adjusting ...
[    0.346839] (WW) RADEON(0):   MC_FB_LOCATION  was: 0x00ef00d0 is: 0x00ef00d0
[    0.346842] (WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0x00030000
[    0.346848] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.346851] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
[    0.346853] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00030000
[    0.346859] (II) RADEON(0): Direct rendering enabled
[    0.346867] (II) RADEON(0): Setting EXA maxPitchBytes
[    0.346886] (II) EXA(0): Offscreen pixmap area of 116867072 bytes
[    0.346894] (II) EXA(0): Driver registered support for the following operations:
[    0.346897] (II)         Solid
[    0.346899] (II)         Copy
[    0.346901] (II)         Composite (RENDER acceleration)
[    0.346903] (II)         UploadToScreen
[    0.346905] (II)         DownloadFromScreen
[    0.346916] (II) RADEON(0): Acceleration enabled
[    0.346921] (==) RADEON(0): DPMS enabled
[    0.346926] (==) RADEON(0): Silken mouse enabled
[    0.346968] (II) RADEON(0): Set up textured video
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 1680x1050 - 1840 1080 9
[    0.351103] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.351106] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
[    0.351109] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00030000
before 11900
after 11900
ffreq: 119000.000000
best_freq: 119000
best_feedback_div: 83.3
best_ref_div: 7
best_post_div: 10
[    0.351147] (II) RADEON(0): crtc(0) Clock: mode 119000, PLL 119000
[    0.351150] (II) RADEON(0): crtc(0) PLL  : refdiv 7, fbdiv 0x53(83), fracfbdiv 3, pdiv 10
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
[    0.354235] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 1680x1050 - 1840 1080 9
[    0.354395] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.354398] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
[    0.354401] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00030000
before 11900
after 11900
ffreq: 119000.000000
best_freq: 119000
best_feedback_div: 83.3
best_ref_div: 7
best_post_div: 10
[    0.354430] (II) RADEON(0): crtc(0) Clock: mode 119000, PLL 119000
[    0.354433] (II) RADEON(0): crtc(0) PLL  : refdiv 7, fbdiv 0x53(83), fracfbdiv 3, pdiv 10
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
[    0.354837] (--) RandR disabled
[    0.354843] (II) Initializing built-in extension Generic Event Extension
[    0.354846] (II) Initializing built-in extension SHAPE
[    0.354849] (II) Initializing built-in extension MIT-SHM
[    0.354851] (II) Initializing built-in extension XInputExtension
[    0.354853] (II) Initializing built-in extension XTEST
[    0.354855] (II) Initializing built-in extension BIG-REQUESTS
[    0.354858] (II) Initializing built-in extension SYNC
[    0.354860] (II) Initializing built-in extension XKEYBOARD
[    0.354862] (II) Initializing built-in extension XC-MISC
[    0.354864] (II) Initializing built-in extension SECURITY
[    0.354866] (II) Initializing built-in extension XINERAMA
[    0.354868] (II) Initializing built-in extension XFIXES
[    0.354871] (II) Initializing built-in extension RENDER
[    0.354873] (II) Initializing built-in extension RANDR
[    0.354875] (II) Initializing built-in extension COMPOSITE
[    0.354877] (II) Initializing built-in extension DAMAGE
record: RECORD extension enabled at configure time.
record: This extension is known to be broken, disabling extension now..
record: http://bugs.freedesktop.org/show_bug.cgi?id=20500
[    0.359177] (II) AIGLX: Screen 0 is not DRI2 capable
[    0.359190] drmOpenDevice: node name is /dev/dri/card0
[    0.359205] drmOpenDevice: open result is 12, (OK)
[    0.359216] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    0.359219] drmOpenDevice: node name is /dev/dri/card0
[    0.359225] drmOpenDevice: open result is 12, (OK)
[    0.359228] drmOpenByBusid: drmOpenMinor returns 12
[    0.359233] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    0.367580] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    0.367593] (II) AIGLX: enabled GLX_SGI_make_current_read
[    0.367596] (II) AIGLX: enabled GLX_texture_from_pixmap with driver support
[    0.367615] (II) AIGLX: Loaded and initialized /usr/lib/dri/r600_dri.so
[    0.367618] (II) GLX: Initialized DRI GL provider for screen 0
[    0.367822] (II) RADEON(0): Setting screen physical size to 444 x 277
[    0.381112] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    0.382092] (II) config/udev: Adding input device "Power Button" (/dev/input/event1)
[    0.382106] (II) LoadModule: "evdev"
[    0.382186] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    0.382250] (II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.2, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
[    0.382279] (**) "Power Button": always reports core events
[    0.382284] (**) "Power Button": Device: "/dev/input/event1"
[    0.423455] (II) "Power Button": Found keys
[    0.423467] (II) "Power Button": Configuring as keyboard
[    0.423481] (II) XINPUT: Adding extended input device ""Power Button"" (type: KEYBOARD)
[    0.423490] (**) Option "xkb_rules" "evdev"
[    0.423497] (**) Option "xkb_model" "pc105"
[    0.423502] (**) Option "xkb_layout" "us"
[    0.423789] (II) config/udev: Adding input device "Power Button" (/dev/input/event0)
[    0.423805] (**) "Power Button": always reports core events
[    0.423809] (**) "Power Button": Device: "/dev/input/event0"
[    0.483441] (II) "Power Button": Found keys
[    0.483452] (II) "Power Button": Configuring as keyboard
[    0.483459] (II) XINPUT: Adding extended input device ""Power Button"" (type: KEYBOARD)
[    0.483463] (**) Option "xkb_rules" "evdev"
[    0.483469] (**) Option "xkb_model" "pc105"
[    0.483474] (**) Option "xkb_layout" "us"
[    0.483792] (II) config/udev: Adding input device "Logitech USB-PS/2 Optical Mouse" (/dev/input/event4)
[    0.483806] (**) "Logitech USB-PS/2 Optical Mouse": always reports core events
[    0.483809] (**) "Logitech USB-PS/2 Optical Mouse": Device: "/dev/input/event4"
[    0.563455] (II) "Logitech USB-PS/2 Optical Mouse": Found 12 mouse buttons
[    0.563466] (II) "Logitech USB-PS/2 Optical Mouse": Found scroll wheel(s)
[    0.563469] (II) "Logitech USB-PS/2 Optical Mouse": Found relative axes
[    0.563471] (II) "Logitech USB-PS/2 Optical Mouse": Found x and y relative axes
[    0.563474] (II) "Logitech USB-PS/2 Optical Mouse": Configuring as mouse
[    0.563481] (**) "Logitech USB-PS/2 Optical Mouse": YAxisMapping: buttons 4 and 5
[    0.563484] (**) "Logitech USB-PS/2 Optical Mouse": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    0.563490] (II) XINPUT: Adding extended input device ""Logitech USB-PS/2 Optical Mouse"" (type: MOUSE)
[    0.563526] (**) "Logitech USB-PS/2 Optical Mouse": (accel) keeping acceleration scheme 1
[    0.563532] (**) "Logitech USB-PS/2 Optical Mouse": (accel) acceleration profile 0
[    0.563540] (II) "Logitech USB-PS/2 Optical Mouse": initialized for relative axes.
[    0.563912] (II) config/udev: Adding input device "Aiptek" (/dev/input/event6)
[    0.563929] (**) "Aiptek": always reports core events
[    0.563932] (**) "Aiptek": Device: "/dev/input/event6"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x46ecf8]
1: /usr/bin/X (0x400000+0x6d6fd) [0x46d6fd]
2: /lib/libpthread.so.0 (0x7f5d36b9a000+0xf190) [0x7f5d36ba9190]
3: /usr/bin/X (0x400000+0x3a04b) [0x43a04b]
4: /usr/bin/X (0x400000+0x3a35b) [0x43a35b]
5: /usr/bin/X (0x400000+0x3aede) [0x43aede]
6: /usr/bin/X (xf86PostMotionEventP+0x87) [0x47a027]
7: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f5d0e85b000+0x53df) [0x7f5d0e8603df]
8: /usr/bin/X (0x400000+0x778c7) [0x4778c7]
9: /usr/bin/X (0x400000+0x10fd24) [0x50fd24]
10: /lib/libpthread.so.0 (0x7f5d36b9a000+0xf190) [0x7f5d36ba9190]
11: /lib/libpthread.so.0 (__open64+0x10) [0x7f5d36ba8940]
12: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f5d0e85b000+0x32d1) [0x7f5d0e85e2d1]
13: /usr/bin/X (0x400000+0x7a577) [0x47a577]
14: /usr/bin/X (NewInputDeviceRequest+0x1ca) [0x47a97a]
15: /usr/bin/X (0x400000+0x10a12a) [0x50a12a]
16: /usr/bin/X (0x400000+0x10a3be) [0x50a3be]
17: /usr/bin/X (config_init+0x9) [0x45f109]
18: /usr/bin/X (0x400000+0x260a5) [0x4260a5]
19: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f5d35b1aadd]
20: /usr/bin/X (0x400000+0x25c99) [0x425c99]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

[    0.723443] (II) "Power Button": Close
[    0.723466] (II) UnloadModule: "evdev"
[    0.803441] (II) "Power Button": Close
[    0.803461] (II) UnloadModule: "evdev"
[    0.963444] (II) "Logitech USB-PS/2 Optical Mouse": Close
[    0.963460] (II) UnloadModule: "evdev"
[    0.963494] (II) AIGLX: Suspending AIGLX clients for VT switch
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
[    0.971244] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.971247] (II) RADEON(0):   MC_FB_LOCATION   : 0x001f0000 0x00ef00d0
[    0.971250] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
[    0.981333] (II) RADEON(0): avivo_restore !
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
 ddxSigGiveUp: Closing log

```

---

### Post by handy on 2009-12-22
This is where they are up to in Arch with this lot; I though that it may help someone with version compatibility here:

[I]With the recent release of Mesa 7.7 and some new package entering testing, I wonder what packages are now required to be build from git?


As far I know :
* kernel26 from testing is 2.6.32.2 and breaks KMW so we need either 2.6.32.1 or 2.6.33-rc1
* libdrm in testing is 2.4.17 and it's enough (at least) for my need (KMS, compositing with Kwin)
* xf86-video-ati in testing is 6.12.99.git20091221-1, and that's ok too

so it left :
* glproto : extra version is 1.4.10 so we need to compile it from git I believe
* dri2proto : 2.1 in extra, same as above
* mesa: 7.6 in extra but 7.7 is released (today), so we need to wait for it to enter testing I guess
* libgl: 7.6 in extra but should become 7.7 with mesa
* ati-dri: same as above

That left us to compile the last five from git for now but soon only glproto and dri2proto?[/I]


Moving along beautifully eh! :)

---

### Post by Xbehave on 2009-12-23
xorg requirements are met by [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa:
libdrm = 2.4.17+git20091221
mesa = 7.7.0~git20091221
xserver-xorg video-ati =6.12.99+git20091222 (do you know which git revision? is needed because the standard karmic one is 20090929)

For the kernel I know 2.6.32 (.nothing) as provided [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/") works fine (radeon.modeset=1 may be required), however 2.6.31/2.6.33-* should work fine as long as radeon.modeset=1 is specified.

If you want to compile from git [this guide]("http://turqee.tumblr.com/post/230394871/dri2-for-radeon-r600-700-chipsets-on-ubuntu-9-10") covers xorg and kernel, I played about and had mesa from git for a while but something went wrong on an update, so now I'm back, i think performance was slightly better with mesa 7.8 but that's speculative as i didn't do benchmarks (which IMO are often stupid for mesa because your feature set is changing).

---

### Post by JeMaCheHi on 2009-12-23
Hi there...
I'm new in this great forum and this is my first post. I'd been in ubuntu since 8.10 but I'm new in graphic acceleration cause I never needed. I've reading this thread, but my english isn't the best in the world and I can't understand everything... -.-'
My question is: I have installed karmic with an ATI Radeon X1600PRO (512MB). I tried to install the proprietary drivers but envy says that isn't compatible. I don't know if the open driver enables 3D acceleration. Am I in the correct thread?
So sorry if I asked stupid questions...
Thanks and greetings

---

### Post by handy on 2009-12-23
Apparently xf86-video-ati 6.12.99.git20091221-1 is fine.

kernel 2.6.32.2 is no good .31 & .33-rc1 are ok.

---

### Post by Xbehave on 2009-12-23
> **JeMaCheHi said:**
> Hi there...
I'm new in this great forum and this is my first post. I'd been in ubuntu since 8.10 but I'm new in graphic acceleration cause I never needed. I've reading this thread, but my english isn't the best in the world and I can't understand everything... -.-'
My question is: I have installed karmic with an ATI Radeon X1600PRO (512MB). I tried to install the proprietary drivers but envy says that isn't compatible. I don't know if the open driver enables 3D acceleration. Am I in the correct thread?
So sorry if I asked stupid questions...
Thanks and greetings
ATI open drivers support some 3D acceleration but they are generally slower than envy drivers (I can run desktop effects but some are slow and i don't think you can do 3d gaming, but these may be due to my card being rubbish)
The open drivers are installed by default but can be a bit slow if the version installed is old.
The latest version is a bit tricky to get working and you may run into problems, but if you want it, you need to use [this ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") and enable KMS. 

To enable KMS add radeon.modeset=1 to your kernel line in grub (you will need a recent kernel >= 2.6.31 (but not 2.6.32), the default one in 9.10 should be new enough), then check it is enabled after a reboot run
```
sudo cat /sys/module/radeon/parameters/modeset
```
1 means its working, 0 means it's not

to find out if you have DRI working run glxgears -info
it will return something like
```
GL_RENDERER   = Mesa DRI R300 (RS400 5975) 20090101  NO-TCL DRI2 #KMS is working
GL_RENDERER   = Mesa DRI R300 (RS400 5975) 20090101  NO-TCL DRI  #KMS is not working but you have some hardware acceleration
GL_RENDERER   = Software rasterising                             #KMS is not working and you have no hardware acceleration
```

---

### Post by handy on 2009-12-23
> **JeMaCheHi said:**
> Hi there...
I'm new in this great forum and this is my first post. I'd been in ubuntu since 8.10 but I'm new in graphic acceleration cause I never needed. I've reading this thread, but my english isn't the best in the world and I can't understand everything... -.-'
My question is: I have installed karmic with an ATI Radeon X1600PRO (512MB). I tried to install the proprietary drivers but envy says that isn't compatible. I don't know if the open driver enables 3D acceleration. Am I in the correct thread?
So sorry if I asked stupid questions...
Thanks and greetings

Welcome to the forum JeMaCheHi, I hope it serves you well. :)

In addition to what Xbehave said; in case you are unaware, your X1000 series is using the R520 core, which is usually referred to as the R500 (& sometimes X500).  It may help you to know that when you look at something like the following table, which I think you will find quite encouraging:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

Due to the speed of development of the open-source support for ATi GPUs in particular at the moment, if you do find that the 3D speed you are getting is not good enough, or it just won't work for your card; please be patient, as it won't be too long & it will be easy to set up, as well as the speed is (almost) consistently increasing every week. :)

The open-source ATi 2D has for months been vastly superior to the 2D offered by Catalyst.  3D will do the same in the coming months. For many of the ATi GPUs.

---

### Post by JeMaCheHi on 2009-12-23
I runned glxgears -info and it returned this:
```

GL_RENDERER   = Mesa DRI R300 (RV530 71C2) 20090101  TCL
GL_VERSION    = 1.5 Mesa 7.6
GL_VENDOR     = DRI R300 Project

```
(I don't understand anything... -.-')
I've got kernel 2.6.31-9-rt as default cause I need it to use jackd :guitar:
Handy, I don't understand what must do with the R500 core... Sorry but I'm an ignorant
Oh, and thanks for the welcome

---

### Post by Ubuntiac on 2009-12-23
Ola JeMaCheHi!

If you're using Ubuntu... and JACK... and you're able to speak more than one language... and you're asking questions here politely... then you are *not* ignorant *or* stupid.

You're learning, just like everyone in the community. Be nice to yourself. One of the things that unites nearly every person here is that we're all enjoying learning more. I'm learning, like you, how to get open source 3d on my ATI card. I'll be so excited when I get there. I've been dreaming of this for years!

Anyway, just ask a lot of questions and help anyone who's learning what you know, and most importantly HAVE FUN! :)



Cheers

Ubuntuiac

---

### Post by Ubuntiac on 2009-12-23
Where do most people actually get the 2.6.33-rc1 kernel from, or is this the same as the 2.6.32.996 one in DRM-Next ppa?

I'm wondering if this might be the cause of my segfault as all the kernel options I'm starting are either 2.6.32 or 2.6.32.996...

---

### Post by handy on 2009-12-23
> **JeMaCheHi said:**
> ...
Handy, I don't understand what must do with the R500 core... Sorry but I'm an ignorant
Oh, and thanks for the welcome

Just know that, [**_R500 core_**]("http://en.wikipedia.org/wiki/Radeon_R520") is what you have, as you will see *reference* to various core series,particularly on technical sites like X.org.  

Here is more info on the ATi Rxx core's:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units) 

The link I included in my previous post to you is a really good example, as you scroll down you will see all of the core numbers running from left to right, find the R500 column & then as you scroll down you will see what has been accomplished so far by the part of the X.org team that are working on the open-source ATi GPU driver support.

---

### Post by handy on 2009-12-23
> **Ubuntiac said:**
> Where do most people actually get the 2.6.33-rc1 kernel from, or is this the same as the 2.6.32.996 one in DRM-Next ppa?

I'm wondering if this might be the cause of my segfault as all the kernel options I'm starting are either 2.6.32 or 2.6.32.996...

Being an Arch user I access packages in a very different way than you do in Ubuntu. 

You'll find your Ubuntu kernels here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

[I]**[Edit:]** Are you aware of this post from Nerd King?:

[http://ubuntuforums.org/showpost.php?p=8450155&](http://ubuntuforums.org/showpost.php?p=8450155&)[/I]

---

### Post by handy on 2009-12-23
I decided it's about time that I gave the open-source drivers another go, as I think they are now more than good enough for my needs, as I use a HD2600 Pro, which is based on the R600 core which is not particularly fast 3D wise when using the currently "stable" open-source support. 

By using kernel26-2.6.33-rc1 & other recent versions of packages it is possible to get a worthwhile improvement in the 3D performance.

So I have just deleted the Catalyst packages on my Arch box, edited the pacman.conf to allow the upgrading of xorg-server after having had to keep it limited to ver 1.6 for Catalyst.  

I also modified my xorg.conf in preparation for the xf86-video-ati (The radeon driver). I don't think I can do away with xorg.conf on my system yet.

I upgraded my system the Arch way, then started the installation - compilation of kernel26-2.6.33-rc1 

It is a time consuming process requiring the downloading of both the .32 kernel source & the .33-rc1 patch source, (the downloading is the quick part) then .32 has to be patched to bring it up to .33-rc1 & then the compilation process which is certainly the most time consuming part of the process.  Having used Arch for so long, I'm not used to having to wait like this. ;)

Hopefully my system has no problems with .33-rc1, & I can then move onto the next step of installing the other 7 (I think) packages, 5 of which will also need to be compiled, but they are all tiny in comparison to the kernel. :)

I'll post an update when I get a chance to move on...:-\"

***[Edit:**] I had to install the kernel .32 firmware before .33-rc1 would install, which it has done without problem thus far... as in it has rebooted. :)*

---

### Post by handy on 2009-12-24
Following is a slightly modified version of what I posted in the Arch forum:


I've finally got around to following [**_Perry's great guide_**]("http://bbs.archlinux.org/viewtopic.php?id=79509&p=1") (many thanks Perry :)) in the OP of this thread, with the following results:

Hardware:
24" 2007 iMac
GPU: HD 2600 Pro

Packages:
kernel26-2.6.33-rc1
all installed in order re, threads OP, using mesa-full also.


I don't call HAL in the rc.conf DAEMON line; as I use the Worker dirutil & handle devices using commands from inside of Worker, hopefully HAL is only required if I wanted to do without an xorg.config? I actually have hotplugging turned off in xorg.conf.

Prior to beginning installation I had prepared my xorg.conf (see bottom of post) prior to the installation & removed Catalyst & utils, organised pacman.conf to now be able to upgrade the X.org stuff also.

After installation, I found that 2D performance was brilliant in colour, definition & refresh speed, but glxgears failed to work, spitting out an error.

So I turned on KMS in menu.lst as I had turned it off in the past, turning KMS on again certainly made some changes:

Now I had laggy 2D refresh & glxgears now worked. 

After running glxgears multiple times each time after at least a restart of X, the speeds were slow as 150fps & once was into the 300fps, mostly around 230fps, but with quite some inconsistency in the speed of its performance per session.

Then I set KMS for early start. During the process there was an error that fbcon could not be found?  I let it go considering to possibly be a bug due to the cutting edge nature of the packages.

After having set KMS to early start my glxgears speeds are now very consistent & somewhat higher, as follows:

2195 frames in 5.0 seconds = 438.920 FPS

The system in 2D is fine, .mp4 & such play perfectly (as only the open-source drivers can do :))

I get the following error, which the wiki says (if I understand it correctly) means that KMS is not working even though since I implemented the KMS early start, the performance of both 2D/3D have dramatically improved.

```

 handy ~  $  dmesg | egrep "drm|radeon"
Command line: root=/dev/sda3 ro   ##radeon.modeset=0 turn off KMS if slow display refresh problem
Kernel command line: root=/dev/sda3 ro   ##radeon.modeset=0 turn off KMS if slow display refresh problem
Unknown boot option `##radeon.modeset=0': ignoring
[drm] Initialized drm 1.1.0 20060810
[drm] radeon default to kernel modesetting.
[drm] radeon kernel modesetting enabled.
radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
radeon 0000:01:00.0: setting latency timer to 64
[drm] radeon: Initializing kernel modesetting.
[drm:radeon_driver_load_kms] *ERROR* Failed to initialize radeon, disabling IOCTL
radeon 0000:01:00.0: PCI INT A disabled
radeon: probe of 0000:01:00.0 failed with error -22
```


Dramatic may sound like a big word for such a small gain in glxgears (around 200fps) but that 200fps really made the 2D side better than it has ever been with catalyst, whereas before that 200fps it certainly was not.

I've posted some details below in the hope that someone will pick up something that I'm unaware of that could bring me some more 3D speed.  In the past glxgears would run well over 3000fps on catalyst.  

Not that I'm impatient ;) I'm absolutely stoked with what the dev' team has accomplished so far with ATi GPU support, & I have complete confidence that the open-source solution will blow the catalyst 3D performance away, as it already has done with the 2D. :D


Here is some more info:


```
handy ~  $  glxinfo |grep -i opengl
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.8-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
```

I've pulled the errors out of xorg.0.log, the first one I'm sure is due to my recent editing of xorg.conf, the 2nd is also inconsequential with regard to the topic at hand:


```
(EE) Failed to load module "freetype" (module does not exist, 0)

(EE) Failed to load module "record" (module does not exist, 0)

(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM

(EE) RADEON(0): Acceleration initialization failed
```

Here is my roughly edited xorg.conf, sorry for the mess, its a work in progress:


```
#Section "ServerLayout"

##       PS/2 Mouse not detected
##       Serial Mouse not detected
#	Identifier     "Xorg Configured"
#	Screen      0  "aticonfig-Screen[0]" 0 0
#	InputDevice    "Keyboard0" "CoreKeyboard"
#	InputDevice    "USB Mouse" "CorePointer"
#EndSection

#Section "Files"

##   Additional fonts: Locale, Gimp, TTF...
##	FontPath     "/usr/share/lib/X11/fonts/latin2/75dpi"
##	FontPath     "/usr/share/lib/X11/fonts/latin2/100dpi"
##   True type and type1 fonts are also handled via xftlib, see /etc/X11/XftConfig!
##	FontPath     "/usr/share/fonts/Type1"
##	RgbPath      "/usr/share/X11/rgb"
#	ModulePath   "/usr/lib/xorg/modules"
#	FontPath     "/usr/share/fonts/misc:unscaled"
#	FontPath     "/usr/share/fonts/misc"
#	FontPath     "/usr/share/fonts/75dpi:unscaled"
#	FontPath     "/usr/share/fonts/75dpi"
#	FontPath     "/usr/share/fonts/100dpi:unscaled"
#	FontPath     "/usr/share/fonts/100dpi"
#	FontPath     "/usr/share/fonts/PEX"
#	FontPath     "/usr/share/fonts/cyrillic"
#	FontPath     "/usr/share/fonts/ttf/western"
#	FontPath     "/usr/share/fonts/ttf/decoratives"
#	FontPath     "/usr/share/fonts/truetype"
#	FontPath     "/usr/share/fonts/truetype/openoffice"
#	FontPath     "/usr/share/fonts/truetype/ttf-bitstream-vera"
#	FontPath     "/usr/share/fonts/latex-ttf-fonts"
#	FontPath     "/usr/share/fonts/defoma/CID"
#	FontPath     "/usr/share/fonts/defoma/TrueType"
#EndSection

Section "Module"

#	Load  "type1"
	Load  "ddc"  # ddc probing of monitor
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "bitmap" # bitmap-fonts
	Load  "freetype"
	Load  "record"
	Load  "drm"	# this one was added for OPEN ATi driver support
EndSection

Section "ServerFlags"
	Option	    "AutoAddDevices" "False" # this turns off hotplugging which needs HAL to work
	Option	    "AllowMouseOpenFail" "true"
EndSection

#Section "InputDevice"
#	Identifier      	"Keyboard0"
#	Driver          	"keyboard"
#	Option	        "CoreKeyboard"
#	Option	        "XkbRules" "xorg"
#	Option	        "XkbModel" "pc105"
#	Option	        "XkbLayout" "us"
##	Option          	"XkbVariant" ""
#EndSection

#Section "InputDevice"
#	Identifier  	"USB Mouse"
#	Driver      	"mouse"
#	Option	    	"Device" "/dev/input/mice"
#	Option	    	"SendCoreEvents" "true"
#	Option	    	"Protocol" "IMPS/2"
#	Option	    	"ZAxisMapping" "4 5 6 7"
#	Option	    	"Buttons" "5"
#EndSection

#Section "Monitor"
#	Identifier  	"aticonfig-Monitor[0]"
#       Option      	"VendorName" "iMac-24"  ## for open driver, may not be needed?
#	Option	    	"VendorName" "ATI Proprietary Driver"
#	Option	    	"ModelName" "Generic Autodetecting Monitor"
#	Option	    	"DPMS" "true"
#EndSection

Section "Device"
##	Identifier  	"aticonfig-Device[0]"       # ATi's closed driver
##	Driver      	"fglrx"				# ATi's closed driver	
	Identifier  	"iMacRadeon"			# Handy's alias for OPEN ATi driver
	Driver	    	"radeon"    			# Handy's installed OPEN ATi driver - radeon NOT radeonhd
	Option		"DRI" 		"on"
	Option      	"DynamicPM" 	"on"      	# Dynamic powersaving.
       	Option     	"ClockGating"  "on"    	# Assisting option for powersaving.
       	Option      	"AccelMethod" "EXA"   	# EXA should fit most cases.
       	Option      	"EXAVSync" 	"on"       	# EXAVSync is explained above.
       	Option      	"RenderAccel" "on"    	# Optional. It should be enabled by default.
	Option 		"AGPMode" 	"8"		# Sets AGP speed may help speed up even non AGP systems
	Option 		"ColorTiling" 	"on"		# 
## 	Option      	"AccelDFS" 	"on"       	#Optional. See the man page.
## 	Option      	"EnablePageFlip" "on" 	# It will not be enabled on R5xx cards.
##	Option 		"AccelMethod" "EXA"
## 	Option      	"DMAForXv" 	"on"       	# Forced option in order to enable Xv overlay. 
## 	Option      	"ScalerWidth" "2048"  	# That should fix some very rare bugs.
      	BusID       	"PCI:1:0:0"
EndSection

#Section "Screen"
#	Identifier 	"aticonfig-Screen[0]"
#	Device     	"aticonfig-Device[0]"
#	Monitor    	"aticonfig-Monitor[0]"
#	DefaultDepth 	24
#	SubSection 	"Display"
#	Viewport   	0 0
#	Depth    		 24
#	EndSubSection
#EndSection

#Section "DRI"
#	Group           "video"  #  commented out for OPEN driver
#	Mode            0666	#  remove when using OPEN driver instructions, though may possibly be userful, time will tell?
#EndSection

```

---

### Post by handy on 2009-12-24
I have a DRM problem, which is pretty obvious to anyone who knows what they are doing, even me, once its pointed out. ;)

So I'm installing a different version of libdrm & building it all on top of that, which should be quicker now, because all the packages are in my cache at least.

---

### Post by Ubuntiac on 2009-12-24
ZOMG! I just noticed that without changing *anything* for the last couple of days, that I now seem to have compositing in Kwin! I think it must have been an update to Xorg-Edgers or something.

I missed it because I alternate between using a stable Karmic+FGLRX and an experimental Lucid+Radeon install and I assumed I was on Karmic because of the desktop effects. It all seems to work perfectly other than a rare odd patch of colour around some windows when they pop up.

All I've done is boot to the drm-next kernel (2.6.32.996) with Xorg-edgers PPA and no radeon.modeset done at all.

Nice!

---

### Post by Xbehave on 2009-12-24
> **Ubuntiac said:**
> ZOMG! I just noticed that without changing *anything* for the last couple of days, that I now seem to have compositing in Kwin! I think it must have been an update to Xorg-Edgers or something.
Are you using kde4.4 betas if so there was a bug in 4.4b1 that was fixed in 4.4b2 , it is impressive that radeon drivers now support desktop effects, but i think your change is a kde improvement.

handy, did you manage to get it working? your setup is so different to mine (hal + binary installs) that I can't really suggest any help other than the stuff that stands for ubuntu
1) test modesettings via sysfs to know if it's on
2) test xorg once you know KMS is setup, dri1 = KMS support, dri2 = KMS, software = radeon drivers messed up
3) If you know KMS is working on all kernels, try switch kernels when you run into an xorg bug just to make sure it's not kernel related.

---

### Post by spoons on 2009-12-24
How nicely do the open drivers play with WINE?

---

### Post by handy on 2009-12-24
> **Xbehave said:**
> 
handy, did you manage to get it working? your setup is so different to mine (hal + binary installs) that I can't really suggest any help other than the stuff that stands for ubuntu
1) test modesettings via sysfs to know if it's on
2) test xorg once you know KMS is setup, dri1 = KMS support, dri2 = KMS, software = radeon drivers messed up
3) If you know KMS is working on all kernels, try switch kernels when you run into an xorg bug just to make sure it's not kernel related.

From the feedback I'm getting on the Arch forum, it would seem like the problem is very likely the .33-rc kernel.

I set everything bar kernel .33-rc back to versions that were in testing or core repo's last night before I went to bed, & still had identical performance. So that kind of makes the .33-rc kernel look even more likely.

This morning I'll change to the kernel .32.1, which seems to be the best for the job at the moment & I'll build all the other packages from .git & see how it goes.

The amount of time that goes into organising this stuff when you have to compile (kernels especially) is why have been holding off from going down the cutting edge path.  But I have the bit between my teeth now. :lolflag:
Really it isn't hard, it is just time consuming waiting for compilation.  I'm glad I'm not using a 386! ](*,)

P.S. Something else I found out about last night that you have to include firmware with kernel .33-rc, "*radeon_ucode*" I added the firmware but it made no difference.

---

### Post by handy on 2009-12-24
> **spoons said:**
> How nicely do the open drivers play with WINE?

I can't speak for Ubuntu, but there are people who have been getting their 2D/3D working very well over on the Arch forum, say Wine is not working well, due the *lib32-mesa-git* to be upgraded, as they can only get software rasterizer currently when using Wine, though they have full hardware 3D when out of Wine.  

I'm sure it won't take long to sort that one out.  The above may only apply to people who are using cutting edge versions of packages, I really don't know for sure.

[I]**[Edit:]**
Perhaps Nerd King or Xbehave, will be able to tell you what the story is re. Ubuntu, Wine & the OSS support for the ATi GPUs?[/I]

---

### Post by handy on 2009-12-25
With kernel26-2.6.32.2-1 & using no .git packages, only those from [testing] & the standard repo's, I'm still getting the following error (as expected, this kernel doesn't work properly with 3D, but the .32.1 kernel does):

*OpenGL renderer string: Software Rasterizer*

But my glxgears speeds are consistent & up around the following speed:

*3388 frames in 5.0 seconds = 677.430 FPS*

I think I'll hang where I am & wait for an improvement in the kernel that will hopefully open the door to decent 3D speeds for my machine.

As it is 2D is great for everything; the desktop & movies are vastly superior to catalyst. 3D is not really good enough to play World of Goo. But I can live without that for a while yet. :)

I could battle it out some more & get 2 or 3 times the 3D speed I am getting now; but really don't have a pressing need at the moment. I expect that the kernel will fix the problem for me inside a month, & I'm a patient person, usually... ;)

My foray into the cutting edge was educational, I have learned some more about my beloved Arch. I really like how I can totally mess it up, & then just spend the time undoing & modifying the mess in varieties of ways. Sometimes not undoing at all but making it even worse. 

Then when things get really bad, (due to compiling strange kernels) you boot the Arch install disk, *chroot*, then */etc/rc.d/network restart*, & then get in there & kick some package RRRs! lol

I've had a lot of fun over the last couple of days with this stuff. But I'm over it now. Bring it down from upstream I say, & let my system now be at peace again... lol

---

### Post by Xbehave on 2009-12-25
> **handy said:**
> [I]**[Edit:]**
Perhaps Nerd King or Xbehave, will be able to tell you what the story is re. Ubuntu, Wine & the OSS support for the ATi GPUs?[/I]
Don't do gaming here but this may help:
[http://wiki.x.org/wiki/RadeonProgram](http://wiki.x.org/wiki/RadeonProgram)

> P.S. Something else I found out about last night that you have to include firmware with kernel .33-rc, "radeon_ucode" I added the firmware but it made no difference.
by default a kernel will not compile any firmware, this may be why just adding the firmware didn't help

---

### Post by handy on 2009-12-25
> **Xbehave said:**
> ...
by default a kernel will not compile any firmware, this may be why just adding the firmware didn't help

In Arch you just have to install the firmware package for it to become part of & available to the system.

I'm thinking I might have another go with the 32.1 kernel.  If I can't get the best results out of it, then I'll just wait for the kernel .33 to get its act together.

---

### Post by Ubuntiac on 2009-12-25
Has anyone tried the new .33-beta2 kernel with Radeon yet?

---

### Post by handy on 2009-12-25
> **Ubuntiac said:**
> Has anyone tried the new .33-beta2 kernel with Radeon yet?

I tried 33-rc1 yesterday, on Arch, it didn't work. Occasionally it works, it seems that there exists a kernel problem at this point.

32.1 seems to be the preferred kernel (most likely to work) with the Arch users at this point.

I'm currently in the process of recompiling it in the hope that I will get the best performance out of the open-source solution.

If I fail, I'll just wait for more kernel development & try again then.

---

### Post by Ubuntiac on 2009-12-26
Thanks Handy,

I was actually wondering about the second beta that was just released.

---

### Post by handy on 2009-12-26
> **Ubuntiac said:**
> Thanks Handy,

I was actually wondering about the second beta that was just released.

No word on the Arch threads as yet, they are probably sleeping off a day of over indulgence... :lolflag:

---

### Post by Ubuntiac on 2009-12-26
No rest for the wicked! None! ;)

---

### Post by handy on 2009-12-27
Thanks to the user *aline* over on the Arch forum, I think I now understand why my past 2 attempts at using the *kernel26-vanilla-2.6.32.2*, & modifying the PKGBUILD so it would download the source & a patch & build the .32.1 kernel, failed to boot.

After both attempts, the install went without error, but when I tried to boot, I was stopped directly after the GRUB menu with a file not found error.  

So I was forced to boot with the Arch install CD, get a bash prompt, *chroot*, get network with */etc/rc.d/network restart* then install the .32.2 kernel that is still in the Arch [testing] repo.

The reason for all of this time being wasted (twice!) was because I didn't go into the */boot/grub/menu.lst* & change the name of the kernel from this:

```
kernel /boot/vmlinuz26 root=/dev/sda3 ro
initrd /boot/kernel26.img

```

To this:

```
kernel /boot/vmlinuz26-vanilla root=/dev/sda3 ro
initrd /kernel26-vanilla.img
.
```

Makes perfect sense once you know about it eh! <palm to forehead!>

So, I guess I will just have to do it a third time...

At least for the next attempt I won't have to compile the kernel, as I've kept the .pkg.tar.gz packages in my cache for the kernel & firmware. 

I've also got the libdrm-git, mesa-full (which is a variety of .git packages in .pkg.tar.gz format, so if I don't stuff up somewhere along the line I could save many hours in the next install. (I think)

Fingers & toes crossed. ;)

---

### Post by handy on 2009-12-27
Some good news here on the kernel26-2.6.33:

[http://www.phoronix.com/scan.php?page=news_item&px=NzgyMQ](http://www.phoronix.com/scan.php?page=news_item&px=NzgyMQ)

More that is relevant to the .33 & beyond kernels - KMS Page-Flipping Ioctl:

[http://www.phoronix.com/scan.php?page=news_item&px=NzY5OA](http://www.phoronix.com/scan.php?page=news_item&px=NzY5OA)

---

### Post by shane2peru on 2009-12-28
ok, this is like the ATI master thread!  I have Radeon HD3100 ATI card, in my Toshiba Satellite laptop.  I installed the proprietary driver trying to find some relief for this card.  It overheats at the drop of a hat, and it isn't the ventilators, or fans, it has everything to do with ATI drivers.   So my question is, I have proprietary drivers installed, and want to return to the open source drivers and try them.  How can I do that safely, or semi-safely?

Shane

---

### Post by Ubuntiac on 2009-12-28
uninstall everything that has fglrx in the packagename and if you have a /etc/X11/xorg.conf file make sure  driver "fglrx" is changed to driver "ati"

You may just beable to open restricted driver manager from the start menu and deactivate from there though.

---

### Post by shane2peru on 2009-12-28
ok, I got it.  That is what I did.  Got rid of everything fglx then installed libgl1-mesa stuff and radeonhd thing, and removed my xorg.conf file (it had ati stuff in it) and all works fine.  I suppose I'm working the open source drivers now, and they have been greatly improved from when I first tried them.  Thanks!

Shane

---

### Post by Ubuntiac on 2009-12-28
> **shane2peru said:**
> I suppose I'm working the open source drivers now, and they have been greatly improved from when I first tried them.  Thanks!

You're welcome! (From someone who'd love to live in Peru one day!) Love the ogg video on your site. :)

---

### Post by handy on 2009-12-29
> **shane2peru said:**
> ok, I got it.  That is what I did.  Got rid of everything fglx then installed libgl1-mesa stuff and radeonhd thing, and removed my xorg.conf file (it had ati stuff in it) and all works fine.  I suppose I'm working the open source drivers now, and they have been greatly improved from when I first tried them.  Thanks!

Shane

You could try using the radeon (xf86-video-ati) driver as opposed to the radeonhd, as it is usually the best choice, it is the one that is getting most of the development work done on it.

Also power-management is being worked on & from memory will begin to be incorporated in kernel .33.  There is actually a patch available that some are using.

[I]**[Edit:]** I went back some pages & found the link that discusses the power-management situation some:

[http://www.phoronix.com/scan.php?page=news_item&px=NzcyNw](http://www.phoronix.com/scan.php?page=news_item&px=NzcyNw)[/I]

---

### Post by handy on 2009-12-30
I've just done a daily upgrade on Arch, (not using the [testing] repo) & due to the versions of the kernel & other packages that are now in the [core] & [extra] repo's I now have the best results ever from using the open-source packages, & ALL from stable packages like kernel26-2.6.32.2-2:

[I]handy ~  $  glxinfo |grep -i opengl
IRQ's not enabled, falling back to busy waits: 2 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL
OpenGL version string: 1.5 Mesa 7.7
OpenGL extensions:
handy ~  $  glxgears
IRQ's not enabled, falling back to busy waits: 2 0
6757 frames in 5.0 seconds = 1351.209 FPS
6755 frames in 5.0 seconds = 1350.827 FPS
6754 frames in 5.0 seconds = 1350.612 FPS
6754 frames in 5.0 seconds = 1350.800 FPS
6758 frames in 5.0 seconds = 1351.450 FPS

[/I]
The GPU 3D hardware is working & my glxgears are over twice as fast as the best I had been able to manage previously (OpenGL renderer string: Software Rasterizer).

KMS is turned off by default but it easy to turn on, which I have done.

To test some new features (for example: irq support = tear free opengl) you have to update some packages & go down the .git path.

The 3D performance is just going to keep on improving as the kernel, mesa & the other associated packages continue to be developed.

Today (well yesterday actually) is a great day for open-source ATi GPU 3D support; it is happening & it has gone mainstream.  You don't have to get into the testing repo's & .git, it is starting to be easily available for general users.  Unfortunately not all [**_radeon core's_**]("http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units") are supported yet, I think that the R500 is, I know that the R600 & R700 are.

P.S. World of Goo now works great. :)

A great end to the year for the team that has been working so hard on this for us for so many months.

My hearty congratulations & gratitude to them all.=D>

---

### Post by handy on 2009-12-30
Here is a little more on the kernel26-2.6.32.2 & the KMS in particular:

[http://www.archlinux.org/news/477/](http://www.archlinux.org/news/477/)

---

### Post by Nerd King on 2010-01-04
Just tested out 2.6.33-rc2 and 2D speed is flying obviously. 3D compiz is good, 3D in wine is a little buggy compared to 32 as one would expect of a rc, but speed does seem to be faster, so presuming that the bugs will be fixed, 33 should be a nice release.

---

### Post by handy on 2010-01-10
There was a nice xmas (22-12-09) present from AMD, they released 362 pages; the Evergreen shader documents.

This info' is required for the open-source drivers to be able to give great 2D/3D for the current series of ATi GPUs.

Great news again for the ATi open-source driver scene:

[http://www.phoronix.com/scan.php?page=news_item&px=NzgzMg](http://www.phoronix.com/scan.php?page=news_item&px=NzgzMg)

Because as it stands, next to nothing has been able to be done for the Evergreen series of GPUs:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

& now it can be. :)

---

### Post by Nerd King on 2010-01-10
Coolness :) I'm starting to like AMD.

---

### Post by Ubuntiac on 2010-01-10
> **Nerd King said:**
> Coolness :) I'm starting to like AMD.

After getting desktop effects running with an all open-source graphics stack more easily than the proprietry drivers on my Nvidia card... I'm **loving** AMD! I wish more FOSS peeps would start supporting them. They made a crap proprietry driver, but dang, if they're not treating the community right, now.

---

### Post by phredbull on 2010-01-12
Well unfortunately, I'm using a laptop w/a Radeon 7500 card. I'm using drivers from xorg/edgers and 2.6.32 kernel. I had previously tweaked my xorg.conf settings, but have since trashed it. (Is it still necessary to generate an xorg.conf and to tweak it?)

Since updating my kernel, Open Arena is now playable, so that's an obvious improvement in my 3d performance, but in Firefox, scrolling is dragging. I feel like 2d performance in Firefox is better when I boot into XP.

I was hoping that as the drivers matured, all that would be needed is the correct kernel, and drivers themselves. Am I missing something?

---

### Post by handy on 2010-01-12
> **phredbull said:**
> 
Well unfortunately, I'm using a laptop w/a Radeon 7500 card. I'm using drivers from xorg/edgers and 2.6.32 kernel. I had previously tweaked my xorg.conf settings, but have since trashed it. (Is it still necessary to generate an xorg.conf and to tweak it?) 

I still have to use an abbreviated xorg.conf.  It seems to depend on the hardware you are using.

> **phredbull said:**
> 
Since updating my kernel, Open Arena is now playable, so that's an obvious improvement in my 3d performance, but in Firefox, scrolling is dragging. I feel like 2d performance in Firefox is better when I boot into XP. 

I find the open-source 2D performance to be really snappy, miles ahead of what I experience when I use Catalyst.

As far as comparisons with XP are concerned, I can't help you, as I haven't used it for over 4 years. :) 

> **phredbull said:**
> 
I was hoping that as the drivers matured, all that would be needed is the correct kernel, and drivers themselves. Am I missing something?

I think the only thing that you are missing, is the understanding that the open-source drivers are far from mature. They are still in their infancy, & will continue to improve with each kernel, mesa & associated packages, release. (With the occasional regression I'm sure. :))

[I]**[Edit:]** I've added my xorg.conf in the hope it may save you some time:
[/I]

```
Section "Module"
#	Load  	"type1"
	Load  	"ddc"  
	Load  	"dbe"
	Load  	"dri"
	Load  	"extmod"
	Load  	"glx"
	Load  	"bitmap" 
	Load  	"freetype"
	Load  	"record"
	Load  	"drm"	# this one was added for OPEN ATi driver support
EndSection

Section "Device"
##	Identifier  		"aticonfig-Device[0]"       	# ATi's closed driver
##	Driver      		"fglrx"				# ATi's closed driver	
	Identifier  		"iMacRadeon"			# Handy's alias for OPEN ATi driver
	Driver	    	"radeon"    			# Handy's installed OPEN ATi driver - radeon NOT radeonhd
	Option		"DRI" 		"on"
	Option      		"DynamicPM" 	"on"      	# Dynamic powersaving.
       	Option     		"ClockGating"  	"on"    	# Assisting option for powersaving.
       	Option      		"AccelMethod" 	"EXA"   	# EXA should fit most cases.
       	Option      		"EXAVSync" 	"on"       	# EXAVSync is explained above.
       	Option      		"RenderAccel" 	"on"    	# Optional. It should be enabled by default.
	Option 		"AGPMode" 	"8"		# Sets AGP speed may help speed up even non AGP systems
	Option 		"ColorTiling" 	"on"		# 
## 	Option      		"AccelDFS" 	"on"       	#Optional. See the man page.
## 	Option      		"EnablePageFlip" "on" 		# It will not be enabled on R5xx cards.
##	Option 		"AccelMethod" 	"EXA"
## 	Option      		"DMAForXv" 	"on"       	# Forced option in order to enable Xv overlay. 
## 	Option      		"ScalerWidth" 	"2048"  	# That should fix some very rare bugs.
      	BusID       		"PCI:1:0:0"
EndSection
```

*The layout tabbing is a bit messy, but that's easily sorted out. ;)*

---

### Post by handy on 2010-01-12
Just out of interest, I started running the HAL daemon again (after well over a year of not) & renamed my xorg.conf.bak & tested & I found I don't currently need to use an xorg.conf.

I didn't include it in the previous post's xorg.conf but I have had to use the following firstly due to a bug, (which is now long gone) & secondly because I haven't been using HAL:

```
Section "ServerFlags"
	Option	    "AutoAddDevices" "False" # this turns off hotplugging which needs HAL to work
	Option	    "AllowMouseOpenFail" "true"
EndSection
```

Anyhow, I'll play with HAL again for a while & see how we get on these days... ;)

---

### Post by markbuntu on 2010-01-12
hal has been deprecated in favor of udev so don't bother.

---

### Post by Techsnap on 2010-01-12
2.6.32 + Mesa 7.7 has given GREAT results with my HD4850, I'm very impressed, I'm getting usable 3D which is good enough for kwin compositing and games.

I've tried it on Arch, but Slackware -current doesn't have Mesa 7.7 yet, so I'll either wait for it to be updated in the package tree or compile it.

---

### Post by Frak on 2010-01-12
Thank you AMD for being cool and stuff.

---

### Post by Xbehave on 2010-01-12
> **markbuntu said:**
> hal has been deprecated in favor of udev so don't bother.
True but the effect is the same as using HAL, the result is a move away from static hardware dependent config files and a move to XML files containing potential parameter changes that are invoked on demand. TBH while this is great for distros like ubuntu/live*s i'm not sure what the advantage is for arch were users are expected to setup their own config files anyway.

---

### Post by handy on 2010-01-12
> **Xbehave said:**
> True but the effect is the same as using HAL, the result is a move away from static hardware dependent config files and a move to XML files containing potential parameter changes that are invoked on demand. TBH while this is great for distros like ubuntu/live*s i'm not sure what the advantage is for arch were users are expected to setup their own config files anyway.

I'm on Arch, & if I don't run the HAL daemon in rc.conf, I get no mouse or keyboard, I'll have to look into whether I can run UDEV as a daemon, if so it should be as easy as that to use it instead.

[I]**[Edit:]** I just read up on UDEV, & I already had "MOD_AUTOLOAD = yes" set in my rc.conf.

Perhaps if I place the exact name of the modules needed to load my mouse & keyboard in the MODULES line of rc.conf I may be able to do without loading the HAL daemon again?

**[Edit:2]** I just stuck "keyboard" & "mouse" next to last (before radeon) in the rc.conf MODULES = () line & removed @hal from the DAEMONS = () line & restarted X, & mouse & keyboard work fine. :D 

I like it when the Ubuntu forums help me find ways to improve my Arch configuration. ;)[/I]

---

### Post by Xbehave on 2010-01-13
Upgraded to 2.6.33-rc4 (and fixed a kde config problem) and WOW i don't just get higher FPS on glxgears but the graphics feel faster even though they are now doing more (i added some transparency to menus and stuff)

> **handy said:**
> **[Edit:2]** I just stuck "keyboard" & "mouse" next to last (before radeon) in the rc.conf MODULES = () line & removed @hal from the DAEMONS = () line & restarted X, & mouse & keyboard work fine. :D
erm did you restart the PC otherwise the hal daemon will still be running (unless you changed the daemons manually)

note to self: glxgears is about 625/331

---

### Post by handy on 2010-01-13
> **Xbehave said:**
> 
Upgraded to 2.6.33-rc4 (and fixed a kde config problem) and WOW i don't just get higher FPS on glxgears but the graphics feel faster even though they are now doing more (i added some transparency to menus and stuff) 

Good stuff. :)

> **Xbehave said:**
> 
erm did you restart the PC otherwise the hal daemon will still be running (unless you changed the daemons manually)


Yes the machine has been cold booted.

***[Edit:]** Hmm, maybe I just thought it was? I just cold booted after a couple of days running & I had no mouse/keyboard in X, so I had to add @hal back into the rc.conf. Oh well, at least I don't have to have an xorg.conf. :)*

---

### Post by handy on 2010-01-16
More good news for R600/700 series owners with the incorporation of Blit support into the Mesa 7.8 Driver, which should go mainstream by the end of March:

[http://www.phoronix.com/scan.php?page=news_item&px=Nzg4NQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzg4NQ)

---

### Post by n0dix on 2010-01-16
The driver is fine for those users that don't use games. I have much more fps in the private driver in my ATI mobility X1400. It's painfull but is the true :( .However, i hope a better performance in the future. I'm optimistic.

---

### Post by Xbehave on 2010-01-16
> **handy said:**
> ***[Edit:]** Hmm, maybe I just thought it was? I just cold booted after a couple of days running & I had no mouse/keyboard in X, so I had to add @hal back into the rc.conf. Oh well, at least I don't have to have an xorg.conf. :)*
Well after a reboot my impressive performance increase turned to a general failure to boot correctly and the screen mangling itself when it does boot
```
[drm:radeon_fence_wait] *ERROR* fence(ffff880048c41a40:0x0003D105) 510ms timeout going to reset GPU
[drm:r300_ga_reset] *ERROR* VAP & CP still busy (RBBM_STATUS=0x8400C100)                                                    
[drm:r300_ga_reset] *ERROR* Failed to reset GA ! (RBBM_STATUS=0x84100140)                                                    
[drm:r300_gpu_reset] *ERROR* Failed to reset GPU (RBBM_STATUS=0x84100140)                                                    
[drm:radeon_fence_wait] *ERROR* fence(ffff880048c41a40:0x0003D105) 672ms timeout going to reset GPU
[drm] GA reset succeed (RBBM_STATUS=0x00000140)
[drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[drm:radeon_fence_wait] *ERROR* fence(ffff880048c41a40:0x0003D105) 684ms timeout      
[drm:radeon_fence_wait] *ERROR* last signaled fence(0x0003D105)
[drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(5).
[drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB!
[drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[drm] LVDS-11: set mode 1280x800 1a
[drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(5).  
[drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB ! 
```
Anybody else seen an error like this, maybe i just messed up my kernel compile. 

I also found out that cat /sys/blah/modeset, is pointless as it just shows the parameters the kernel got and the only way to find out if KMS is working is to trawl through /var/log/xorg.0 or look in /proc/fb, neither of which is 100% reliable.

---

### Post by handy on 2010-01-17
> **n0dix said:**
> The driver is fine for those users that don't use games. I have much more fps in the private driver in my ATI mobility X1400. It's painfull but is the true :( .However, i hope a better performance in the future. I'm optimistic.

On the current stable versions of the kernel, mesa et al, packages, that Arch is using, I have terrific 2D & 3D is good enough to play World of Goo without fault.

The people (not just Arch users), who are experimenting with the .git packages are currently getting great results on the R600/R700 series ATi GPUs. 

I just read a report where Quake Live is running at full speed (their words not mine).  :) 

You don't need optimism, just a little patience. ;)

---

### Post by handy on 2010-01-27
AMD Catalyst 10.1 Driver For Linux Released:

[http://www.phoronix.com/scan.php?page=news_item&px=NzkzMQ](http://www.phoronix.com/scan.php?page=news_item&px=NzkzMQ)

Basically, it still doesn't work with xorg-server 1.7, which is truly a shocker, as now the last 3 versions of Catalyst haven't.  It is such a pain for people who use distros that use more current versions of software than Ubuntu.

All in all it is another mediocre release.

---

### Post by BuffaloX on 2010-01-27
No they are not coming of age here.
I get relics all over the place, and no 3D :frown:

Actually I'm pretty annoyed with ATI/AMD right now.
I have a Radeon 4770, proprietary drivers just got their third upgrade since Karmic was launched, and I still get relics.

My wife has an 4850 which works fine, why is this?
Aren't they essentially the same GPU, Just with different RAM databus-width and number of stream processors?

I'm pretty sure it's the drivers, since I have no problems in Win XP.

---

### Post by AllRadioisDead on 2010-01-27
> **BuffaloX said:**
> No they are not coming of age here.
I get relics all over the place, and no 3D :frown:

Actually I'm pretty annoyed with ATI/AMD right now.
I have a Radeon 4770, proprietary drivers just got their third upgrade since Karmic was launched, and I still get relics.

My wife has an 4850 which works fine, why is this?
Aren't they essentially the same GPU, Just with different RAM databus-width and number of stream processors?

I'm pretty sure it's the drivers, since I have no problems in Win XP.
You are using the proprietary driver. The open drivers don't give relics.

---

### Post by BuffaloX on 2010-01-27
No I just tried the open source drivers through ppa.
Much more relics than the closed one, so I'm back on proprietary driver.

The reason I tried the open source drivers, was because I got tired of the closed source driver having a few relics.

It looks like a RAM error, but since everything works in Windows, and this bug has been confirmed, I believe it's the drivers.

---

### Post by handy on 2010-01-27
The title & the truth of the matter is that the ATi open-source drivers ARE coming of age.

They are NOT mature yet, far from it.

But boy are they growing up/developing fast.  Due to AMD opening up the technical spec's to the public & due to the incredibly hard work of the small team of dev's that are coding for it.

People on the Arch forum are reporting great speed from the kernel .33.git, there will still be bugs when kernel .33 is released.

Some cards won't work. KMS will work for some & not others, power management is not there yet.  There is still lots to do.  BUT it IS being done & those with a little patience, are going to end up with a brilliant reliable well maintained open-source integration of the ATi (amongst other brands) GPUs.

On another tack, the word from those that have been tackling the new catalyst driver in distros that use more recent packages than Ubuntu, can be wrapped up in this comment taken from the AUR catalyst user comments:


*No [xorg-server] 1.7 support? :X what a cruel joke ATi is... massively disappointed.*

---

### Post by bluelamp999 on 2010-01-27
Ok. I finally bit the bullet and upgraded my kernel to 2.6.32 and added the xorg-edgers PPA.

I followed the instructions from here:
> **Nerd King said:**
> So I've been having nightmares with 2.6.31 and tried 2.6.30 with the same problem, my wi-fi kept locking the system. 2.6.32 fixes that, but even better, it gives me open source ATI drivers and lovely 3D with no proprietary driver. Absolutely superb it is too, Compiz is flying around nicely, will test some games later but it feels very snappy. Btw it's not compatible with the proprietary ATI drivers which is why I tried the open ones. I'm glad I did now!

I've run the usual crash conditions and it coped fine so it looks good.

Procedure:
1. System -> Hardware Drivers -> Deactivate any ATI drivers and restart
2. Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/")
3. Download and execute the following (in this order, switch to 64 if need be)
  - linux-headers...all.deb
  - linux-headers..generic..i386.deb
  - linux-image....i386.deb
4. Restart
5. Add the xorg-edgers PPA ([https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")), update, upgrade.
6. Reboot.
7. Profit.

I added the **xorg-edgers/drivers-only** PPA, is this the right one?

While everything appears to be working OK, I'm not really seeing any noticeable graphics performance increase.

glxgears before was ~4700 frames per 5s, it's ~4720 after.

I'm running an ATI M22 [Mobility Radeon X300] on a dual display (3200 x 1200)

Is this to be expected? Did I add the correct PPA?

Cheers!

---

### Post by handy on 2010-01-27
**@bluelamp999:** I expect that you have installed the correct package, though really I can't help you with this one. 

Nerd King, or one of the others that are using the xorg-edgers stuff will be able to give you the run down.

Were you using the open-source solution previously?

& those speeds are still very usable, I'm only getting about 1,350fps using the stable stuff in Arch, on a HD2600Pro.  I'll be very happy when I can get 4,500fps. :)

Have you tested the machine in a game to see if you are getting better fps?  The glxgears is really a limited way to test a GPU, as it sometimes doesn't show that there in reality exist improvements in performance.

---

### Post by Shibblet on 2010-01-27
Handy,

I'm sure if you've read through the forums, like all of us little addicts, you'd see that I'm having trouble with an ATI legacy device, the x1250.

This is for a notebook PC, and I don't really need a lot of performance, just enough for video playback without flickering.  The rest is mostly 2d performance for web-browsing and such.  

Are the open source drivers going to have legacy support?  If not, what can I do to get Ubuntu on this notebook?

Thanks.

---

### Post by AugeIN on 2010-01-27
> **Shibblet said:**
> Handy,

I'm sure if you've read through the forums, like all of us little addicts, you'd see that I'm having trouble with an ATI legacy device, the x1250.

This is for a notebook PC, and I don't really need a lot of performance, just enough for video playback without flickering.  The rest is mostly 2d performance for web-browsing and such.  

Are the open source drivers going to have legacy support?  If not, what can I do to get Ubuntu on this notebook?

Thanks.

Ditto X1250. BTW Lucid appears to be using KMS by default for ATI now, and KMS doesn't work with the X1250.

---

### Post by Xbehave on 2010-01-27
deleted did not see other replies [could an admin just remove this post?]

---

### Post by handy on 2010-01-27
**@Shibblet:** If you have a look here you will find info on your GPU & its code, like say RS690 I think:

[http://dri.freedesktop.org/wiki/ATIRadeon#head-a2d41d14a2c9b0da964aa1b7226ebab238532abe](http://dri.freedesktop.org/wiki/ATIRadeon#head-a2d41d14a2c9b0da964aa1b7226ebab238532abe)

Then have a look here & see roughly where the development is up to:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

From the previous link it looks pretty good to me, for all but the Evergreen (current GPUs) & AMD have recently released the tech' info' for Evergreen, so that will change for sure. :)

Everyone that I'm aware of (including myself) gets better video & 2D with the open-source drivers, the 3D is slow, but getting faster. Kernel .33, looks to have a lot of improvements from what I read of the guys currently using the .git packages.

If KMS is a problem, you can turn it off.

---

### Post by handy on 2010-01-28
Apparently catalyst 10.1 has more problems than just not supporting xorg-server 1.7 (1.8 will be out soon!), an important symlink to libatiuki.so.1.0 has been missed, most of the (currently 7) pages of this forum are worth reading, particularly for Ubuntu users:

[http://www.phoronix.com/forums/showthread.php?t=21739](http://www.phoronix.com/forums/showthread.php?t=21739)

---

### Post by Techsnap on 2010-01-28
Ah, They spent ages on this driver and from what I read they were doing some huge improvements with 10.1 on Linux, that's a bugger. The Windows side of things are definitely a lot smoother though, it did improve FPS on games, especially GTA IV.

---

### Post by handy on 2010-01-28
I'm hanging out for the stable release of kernel .33, I expect some 3D speed improvements in the open-source drivers.

More 3D speed, is all I need. :)

The power management is on its way if not in kernel .33, then hopefully .34 will nail it, which is particularly good news for the battery powered crew.

It will take a bit longer to get to mainstream Ubuntu due to older packages that it uses, but at least those that are into it can upgrade via the use of xorg-edgers PPA.

---

### Post by AllRadioisDead on 2010-01-28
> **handy said:**
> I'm hanging out for the stable release of kernel .33, I expect some 3D speed improvements in the open-source drivers.

More 3D speed, is all I need. :)

The power management is on its way if not in kernel .33, then hopefully .34 will nail it, which is particularly good news for the battery powered crew.

It will take a bit longer to get to mainstream Ubuntu due to older packages that it uses, but at least those that are into it can upgrade via the use of xorg-edgers PPA.
When can we expect those to be released?

---

### Post by handy on 2010-01-28
> **ihermit said:**
> When can we expect those to be released?

To the best of my knowledge kernel .33 is due out in March, it is at rc5 currently.

I make my predictions on the power management due to what I see here:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

Which says that power management is mostly done for all but the Evergreen series.

---

### Post by bluelamp999 on 2010-01-28
> **handy said:**
> **@bluelamp999:** I expect that you have installed the correct package, though really I can't help you with this one. 

Nerd King, or one of the others that are using the xorg-edgers stuff will be able to give you the run down.

Were you using the open-source solution previously?

& those speeds are still very usable, I'm only getting about 1,350fps using the stable stuff in Arch, on a HD2600Pro.  I'll be very happy when I can get 4,500fps. :)

Have you tested the machine in a game to see if you are getting better fps?  The glxgears is really a limited way to test a GPU, as it sometimes doesn't show that there in reality exist improvements in performance.

Hi Handy,

Thanks, as ever, for the response...

It might not be entirely clear in my post but, unfortunately, it's 4700 frames per every *5* seconds. That's the way glxgears in Ubuntu 9.10 measures frame rates.

What I wouldn't give (except a load of money for a new laptop) to have frame rates of 1,350 ps!

Thanks again

---

### Post by handy on 2010-01-28
> **bluelamp999 said:**
> Hi Handy,

Thanks, as ever, for the response...

It might not be entirely clear in my post but, unfortunately, it's 4700 frames per every *5* seconds. That's the way glxgears in Ubuntu 9.10 measures frame rates.

What I wouldn't give (except a load of money for a new laptop) to have frame rates of 1,350 ps!

Thanks again

Sorry, unfortunately I made a brain typo.  I expect you probably guessed that. :)

I'll edit my original post, changing fps to f/5s.

---

### Post by handy on 2010-01-30
Well I relented & got the Arch .git(s) again. :)

I've spent about 5 hours on the whole job, which included downloading configuring & building the kernel which takes forever, then installing the additional firmware files that don't ship with the kernel via the **radeon_ucode** pkg.

Then removing & reinstalling with the .git version of packages, in just the right order as follows:

libdrm-git, glrptoto-git, dri2proto-git, removing these files - mesa, libgl, glut, ati-dri & replacing them with mesa-full (which includes all of the last 4 but in their .git state; then add last but not least xf86-vide-ati-git. Whew!

I rebooted with baited breath, it's such a drag when there's a problem & the thing won't boot, so you have to boot with a LiveCD chroot & fix it.

Anyway it booted fine (which is good, 'cause I took a LOT of things out of the kernel = risky when you don't know what you are doing ;)).

I checked glxgears & there was really no change. :(  I input *"glxinfo |grep -i opengl"* & things were looking good but there was no DRI2.  Which again I didn't understand, I then turned KMS back on, rebooted & during the boot the fonts all of a sudden got very small (this is good, KMS is working :)), Openbox looked the same as usual, I did a speed test & such & the results follow:

[I]```
handy ~  $  glxgears
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
9436 frames in 5.0 seconds = 1887.164 FPS
9434 frames in 5.0 seconds = 1886.770 FPS
9437 frames in 5.0 seconds = 1887.396 FPS
9437 frames in 5.0 seconds = 1887.336 FPS
9438 frames in 5.0 seconds = 1887.534 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 152130 requests (152127 known processed) with 0 events remaining.
handy ~  $  glxinfo |grep -i opengl
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL **DRI2**
OpenGL version string: 2.0 Mesa 7.8-devel
OpenGL shading language version string: 1.10
OpenGL extensions:
```[/I]

So for the 5 hours work, I picked up KMS, OpenGL 2.0, DRI2, blitter support & about 550 fps in glxgears.  Which is ok, though I was hoping for more 3D speed.  It ain't over, I have a question on the Arch forums & maybe there is more I can do.

Anyway, now I've got the .git(s), but I'll do my best to remain stable... :rolleyes:

P.S. I'm using the Radeon HD2600Pro 256MB.

& I followed [*Perry3D's great Arch how-to*]("http://bbs.archlinux.org/viewtopic.php?id=79509&p=1") again, though I downloaded all but the kernel-git from elsewhere as binaries, which saved a heap of time.

---

### Post by Frak on 2010-01-30
> **handy said:**
> So for the 5 hours work, I picked up KMS, DRI2, & about 550 f/5s in glxgears.  Which is ok, though I was hoping for more 3D speed.  It ain't over, I have a question on the Arch forums & maybe there is more I can do.

Anyway, now I've got the .git(s), but I'll do my best to remain stable... :rolleyes:

glxgears should still require the --glxgearsisnotabenchmark flag. Don't use GLXGears to see if your card is more efficient, as it's not a good indicator, and can be sporadic at times.

---

### Post by handy on 2010-01-30
> **Frak said:**
> glxgears should still require the --glxgearsisnotabenchmark flag. Don't use GLXGears to see if your card is more efficient, as it's not a good indicator, and can be sporadic at times.

We all(?) know that Frak. :)

It is a good indicator on the same machine, it is **not** an accurate indicator between machines.  

Glxgears is far from perfect, it has a history of being able to create wonderfully strange anomalies.

Though that said; if I turn KMS off, my glxgears f/5s will return to where it was before I turned it on, & visa versa.  

That tells Me something valuable about what is going on, in my machine.  

We are all relating to glxgears as a loose indicator over in the two Arch forum threads that are dedicated to open-source ATi, GPU support, & catalyst. Game performance, both visually (artefacts) & fps are far more valuable.

---

### Post by Frak on 2010-01-30
> **handy said:**
> We all(?) know that Frak. :)

It is a good indicator on the same machine, it is **not** an accurate indicator between machines.  

Glxgears is far from perfect, it has a history of being able to create wonderfully strange anomalies.

Though that said; if I turn KMS off, my glxgears f/5s will return to where it was before I turned it on, & visa versa.  

That tells Me something valuable about what is going on, in my machine.  

We are all relating to glxgears as a loose indicator over in the two Arch forum threads that are dedicated to open-source ATi, GPU support, & catalyst. Game performance, both visually (artefacts) & fps are far more valuable.
Well, when I used GLXGears the first time, say on the Catalyst driver, I'd start up Tremulous and see I get 190fps and GLXGears give me 3000fps (guestimation). When I used the Open Source driver, GLXGears went over 3500fps, but my fps on tremulous, same map, went down to 140fps.

That's really because it only measures GL between OpenGL and X, not the true cards capability.

---

### Post by handy on 2010-01-30
> **Frak said:**
> Well, when I used GLXGears the first time, say on the Catalyst driver, I'd start up Tremulous and see I get 190fps and GLXGears give me 3000fps (guestimation). When I used the Open Source driver, GLXGears went over 3500fps, but my fps on tremulous, same map, went down to 140fps.

That's really because it only measures GL between OpenGL and X, not the true cards capability.

It is also only doing a small, simple & consistent animation.  

It is just an easy, freely available indicator, that generally tells you the truth as to whether your changes have been positive or not.  It also has the ability to usually give you an idea of roughly just how much of a change.  

It is far from comprehensive or infallible, but most of us are grateful that it exists, as we don't have anything better that is small & freely downloadable & therefore accessible by all of the FOSS community.  

Maybe one day someone will make glxgears an accurate benchmark, or create one for us?  

Until then it's the de-facto paradox in that it is the OpenGL benchmark that most everyone knows is not really a benchmark. :popcorn:

---

### Post by Frak on 2010-01-30
> **handy said:**
> It is also only doing a small, simple & consistent animation.  

It is just an easy, freely available indicator, that generally tells you the truth as to whether your changes have been positive or not.  It also has the ability to usually give you an idea of roughly just how much of a change.  

It is far from comprehensive or infallible, but most of us are grateful that it exists, as we don't have anything better that is small & freely downloadable & therefore accessible by all of the FOSS community.  

Maybe one day someone will make glxgears an accurate benchmark, or create one for us?  

Until then it's the de-facto paradox in that it is the OpenGL benchmark that most everyone knows is not really a benchmark. :popcorn:
I do believe the [Phoronix Test Suite]("http://www.phoronix-test-suite.com") contains an OpenGL benchmark.

---

### Post by handy on 2010-01-30
> **Frak said:**
> I do believe the [Phoronix Test Suite]("http://www.phoronix-test-suite.com") contains an OpenGL benchmark.

Thanks for telling me.

---

### Post by handy on 2010-01-30
I changed to the .git open-source kernel & related ATi open-source driver files yesterday, which bought me improvements in 3D speed.

Today I did a system upgrade, which only had a few files in it, but one of them was the libdrm-git, it had interesting effects:

I've lost over 1,100 fps on glxgears  & I'm back to software rasteriser, but I now no longer have the IRQ error, the OpenGL version has moved to 2.1 & shading version is now up at 1.20 as follows:


[I]```

handy ~  $  glxgears
3534 frames in 5.0 seconds = 706.678 FPS
3539 frames in 5.0 seconds = 707.689 FPS
3540 frames in 5.0 seconds = 707.906 FPS
3543 frames in 5.0 seconds = 708.582 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 31348 requests (39 known processed) with 0 events remaining.
handy ~  $  glxinfo |grep -i opengl
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.8-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
handy ~  $
```[/I]

A rather momentous set of changes in that libdrm-git upgrade.

---

### Post by Xbehave on 2010-01-30
> **handy said:**
> A rather momentous set of changes in that libdrm-git upgrade.
Well at least an update didn't leave you with KMS that brings down the system. I **think** if you disable KMS, you'll drop back to dri 1 (not sure why that isn't done when xorg fails to load drm w/ kms), which has improved significantly for me since the last time i resorted to it (can handle desktop effects). 

p.s I'm jealous your software rendering gets almost as high as dri 1 for me (dri 2 is about 1300 though IIRC)
```
glxgears -info | grep -v EXTENSIONS
GL_RENDERER   = Mesa DRI R300 (RS400 5975) 20090101  NO-TCL
GL_VERSION    = 1.5 Mesa 7.8-devel
GL_VENDOR     = DRI R300 Project
4326 frames in 5.0 seconds = 865.105 FPS
4473 frames in 5.0 seconds = 894.538 FPS
4622 frames in 5.0 seconds = 924.274 FPS
4594 frames in 5.0 seconds = 918.762 FPS
4608 frames in 5.0 seconds = 921.482 FPS
4375 frames in 5.0 seconds = 874.967 FPS
```

If you compile from recent mainline sources (2.6.33-rc5) that has correct firmware right?
Do errors in dmesg that start with [drm, e.g [drm],[drm:radeon_fence_wait],[drm:radeon_ib_schedule],etc suggest a kernel bug or an xorg/libdrm one?

---

### Post by JDShu on 2010-01-30
Any chance you guys can try running one of the phoronix openGL benchmarks like lightsmark or unigine? I would be really interested in more information about the current oss driver performance.

---

### Post by Xbehave on 2010-01-30
> **JDShu said:**
> Any chance you guys can try running one of the phoronix openGL benchmarks like lightsmark or unigine? I would be really interested in more information about the current oss driver performance.
Once i get my setup working i'll give software/dri/dri2 and maybe a couple of different kernels a test, but until I actually have a working setup it seams silly to time doing proper tests and while not benchmarks glxgears does give numbers indicative of performance.

---

### Post by Xbehave on 2010-02-01
Good news everybody, [http://www.phoronix.com/scan.php?page=news_item&px=Nzk0Ng](http://www.phoronix.com/scan.php?page=news_item&px=Nzk0Ng) ATI has release open drivers (with not much working, but hey it's a star and i'm sure radeon code can be made to work with it) for Evergreen/R8xx/HD 5600+ cards.

---

### Post by Ubuntiac on 2010-02-02
> **Xbehave said:**
> Good news everybody

After the first three words of this post, I couldn't help hearing the rest of it read out by Professor Farnsworth of Futurama... Futurama buffs will know what I'm talking about! :D

---

### Post by Shibblet on 2010-02-02
I was thinking of giving the xf86-video-ati driver a run, does it function better than the xorg-edgers?

---

### Post by sideaway on 2010-02-02
> **Ubuntiac said:**
> After the first three words of this post, I couldn't help hearing the rest of it read out by Professor Farnsworth of Futurama... Futurama buffs will know what I'm talking about! :D

Haha, I didn't upon first read, but I do know what you're talking about :P

My next GPU I plan to be HD5 series... oerhaps this is a sign to hurry and buy it already :P

---

### Post by shane2peru on 2010-02-02
> **Xbehave said:**
> Good news everybody, [http://www.phoronix.com/scan.php?page=news_item&px=Nzk0Ng](http://www.phoronix.com/scan.php?page=news_item&px=Nzk0Ng) ATI has release open drivers (with not much working, but hey it's a star and i'm sure radeon code can be made to work with it) for Evergreen/R8xx/HD 5600+ cards.

That is good news, but very late, they have burnt me on ATI and I will never buy another ATI card.  I know of many others in the same boat.  However there are new comers still switching over (or trying to) and that is good news for them, hope it comes quickly before they get burnt too!

Shane

---

### Post by Xbehave on 2010-02-02
> **Shibblet said:**
> I was thinking of giving the xf86-video-ati driver a run, does it function better than the xorg-edgers?
xorg-edgers is a ppa that gives you the latest xf86-video-ati. It runs slower than flgrx but I've had very few problems with it. In order slowest to fastest
xf86-video-ati (without xorg-edgers)
xf86-video-ati (with xorg-edgers)
xf86-video-ati (with xorg-edgers and a new kernel (from ppa or built yourself))

The last setup is running KMS and so a bit more experimental (also a fair bit faster about ~2x here) and so you might run into problems, but most are easy to workaround.

> My next GPU I plan to be HD5 series... oerhaps this is a sign to hurry and buy it already 
ATM you'd still need flgrx to do anything useful with the card, this is just a sign that in a few months it will be as good as the rest of the radeon drivers, which are catching up (already handle everyday stuff but not quite gaming)

---

### Post by Kazade on 2010-02-02
> **shane2peru said:**
> That is good news, but very late, they have burnt me on ATI and I will never buy another ATI card.  I know of many others in the same boat.  However there are new comers still switching over (or trying to) and that is good news for them, hope it comes quickly before they get burnt too!

Shane

Comments like this don't make sense to me... ATI is being incredibly open source friendly now, and it's a WIP but in a year or two people will be saying "don't buy Nvidia, their cards aren't even supported out of the box". I once got burnt by Ubuntu Breezy, doesn't mean I never tried Ubuntu again.

Even fglrx has improved hugely over the past year. Saying you'll never buy from them again despite the obvious turn around since they've been bought by AMD just seems silly and a little short sighted. If it didn't work out for you the first time, just give the OSS guys a little time and then try again. ATI is winning my vote, and just because of their openness, and willingness to be part of the open source ecosystem (in comparison to Nvidia) I recommend them every time. If you care about an open, stable, high performance driver and graphics ecosystem, you'd support them too.

---

### Post by shane2peru on 2010-02-02
> **Kazade said:**
> Comments like this don't make sense to me... ATI is being incredibly open source friendly now, and it's a WIP but in a year or two people will be saying "don't buy Nvidia, their cards aren't even supported out of the box". I once got burnt by Ubuntu Breezy, doesn't mean I never tried Ubuntu again.

Even fglrx has improved hugely over the past year. Saying you'll never buy from them again despite the obvious turn around since they've been bought by AMD just seems silly and a little short sighted. If it didn't work out for you the first time, just give the OSS guys a little time and then try again. ATI is winning my vote, and just because of their openness, and willingness to be part of the open source ecosystem (in comparison to Nvidia) I recommend them every time. If you care about an open, stable, high performance driver and graphics ecosystem, you'd support them too.

With all due respect I'm 8 months into still trying to get my Radeon HD3100 ATI card working.  It doesn't work with Linux period.  I have put it up for sale, because I am a Linux die hard, and refuse to use Windows.  I have installed over a half a dozen distros trying to get this to work.  Tried many both proprietary drivers and open source drivers.  The laptop overheats every time with either driver installed.  I can run it with Vista (it came with it) and it never overheats.  I have narrowed it down to the ATI Radeon graphics card.  After 8 months of complete un-usability for this laptop, I have decided never to buy another ATI card.  I wholeheartedly support the open source guys and applaud their work, if AMD/ATI had co-operated a little bit, given up some drivers or put out something that worked, I would understand.  But that was not the case.  There were several times when their proprietary drivers didn't even work correctly and I had to go back to the older driver.  I'm simply saying, that I won't buy from them.  I'm not upset at Linux for this, I'm upset at the company that puts out the product and doesn't support Linux.  Even though now they are, they had to learn from the terrible experience of other users like myself to change their mind.  I buy HP printers because they have released or at least put out drivers for their product.  That is all I'm saying.  If you want to chance using ATI and live through 8 months of absolute terror, be my guest.  I also know that not everyone has that experience, my wifes computer uses ATI (older ones) and has never had a problem.  My laptop is semi-usable with Linux now, but I'm done with trying, I'm done with it overheating on a daily basis, I refuse to use it, and am selling it.  For a windows person it would be a fine machine.  I'm not a noob with Linux either, as I have been using exclusively Linux for several years now, I'm no pro either.  I have learned research before you buy, and that is what I'll do from now on. 

Shane

---

### Post by Kazade on 2010-02-02
> **shane2peru said:**
> With all due respect I'm 8 months into still trying to get my Radeon HD3100 ATI card working.  It doesn't work with Linux period.  I have put it up for sale, because I am a Linux die hard, and refuse to use Windows.  I have installed over a half a dozen distros trying to get this to work.  Tried many both proprietary drivers and open source drivers.  The laptop overheats every time with either driver installed.  I can run it with Vista (it came with it) and it never overheats.  I have narrowed it down to the ATI Radeon graphics card.  After 8 months of complete un-usability for this laptop, I have decided never to buy another ATI card.  I wholeheartedly support the open source guys and applaud their work, if AMD/ATI had co-operated a little bit, given up some drivers or put out something that worked, I would understand.  But that was not the case.  There were several times when their proprietary drivers didn't even work correctly and I had to go back to the older driver.  I'm simply saying, that I won't buy from them.  I'm not upset at Linux for this, I'm upset at the company that puts out the product and doesn't support Linux.  Even though now they are, they had to learn from the terrible experience of other users like myself to change their mind.  I buy HP printers because they have released or at least put out drivers for their product.  That is all I'm saying.  If you want to chance using ATI and live through 8 months of absolute terror, be my guest.  I also know that not everyone has that experience, my wifes computer uses ATI (older ones) and has never had a problem.  My laptop is semi-usable with Linux now, but I'm done with trying, I'm done with it overheating on a daily basis, I refuse to use it, and am selling it.  For a windows person it would be a fine machine.  I'm not a noob with Linux either, as I have been using exclusively Linux for several years now, I'm no pro either.  I have learned research before you buy, and that is what I'll do from now on. 

Shane

I didn't mean to have a go. I agree, their closed drivers aren't fantastic (although in the past year I've had more trouble with the Nvidia drivers than the AMD ones). What I was getting at is AMD has given the open source devs what they wanted; the specifications. And they continue to do so. In a year or two AMD will be the better choice on Linux. Good performing chips with open drivers that integrate with all the good stuff in the open stack (KMS, Gallium, Xrandr etc.). Nvidia have done absolutely nothing to help the Nouveau devs, no specs, no code, zip, and they have no intention of helping at all.

Things change, and although you have trouble now (and it's inexcusable), you shouldn't banish AMD forever. 

I guess what I'm trying to say is, give them one more chance - just in a couple of years :)

Sorry if I caused offense, that wasn't my intention.

---

### Post by shane2peru on 2010-02-02
> **Kazade said:**
> I didn't mean to have a go. I agree, their closed drivers aren't fantastic (although in the past year I've had more trouble with the Nvidia drivers than the AMD ones). What I was getting at is AMD has given the open source devs what they wanted; the specifications. And they continue to do so. In a year or two AMD will be the better choice on Linux. Good performing chips with open drivers that integrate with all the good stuff in the open stack (KMS, Gallium, Xrandr etc.). Nvidia have done absolutely nothing to help the Nouveau devs, no specs, no code, zip, and they have no intention of helping at all.

Things change, and although you have trouble now (and it's inexcusable), you shouldn't banish AMD forever. 

I guess what I'm trying to say is, give them one more chance - just in a couple of years :)

Sorry if I caused offense, that wasn't my intention.

I didn't take it as your intention to flame me, lest I would have just ignored it. ;) So no offense taken, just felt I needed to clarify my situation, it wasn't a quick or sloppy decision on my part.  And perhaps in the future after they have been tried and true I may reconsider.  On the other hand I researched Nvidia this time around and bought Nvidia specifically after all my hard-ache with ATI.  Perhaps they are not opensource, but they seem to function well with the proprietary drivers.  Perhaps I'm not a 100% open source fellow, and I certainly do appreciate open source stuff, but don't mind some proprietary stuff. A few years down the road, I'm sure a lot of stuff will be different.

Shane

---

### Post by mickie.kext on 2010-02-02
Same thing here, I had HD4670 which was horrible. I sold it for like half or paid price after one month of headaches. Now have GeForce 8800GT and no problems.

---

### Post by shane2peru on 2010-02-02
> **mickie.kext said:**
> Same thing here, I had HD4670 which was horrible. I sold it for like half or paid price after one month of headaches. Now have GeForce 8800GT and no problems.

Well, as I stated ATI is not my favorite anymore, however for the sake of Linux I really do hope they get it all worked out and fixed.  

Shane

---

### Post by handy on 2010-02-03
> **Xbehave said:**
> Well at least an update didn't leave you with KMS that brings down the system. I **think** if you disable KMS, you'll drop back to dri 1 (not sure why that isn't done when xorg fails to load drm w/ kms), which has improved significantly for me since the last time i resorted to it (can handle desktop effects). 

p.s I'm jealous your software rendering gets almost as high as dri 1 for me (dri 2 is about 1300 though IIRC)
```
glxgears -info | grep -v EXTENSIONS
GL_RENDERER   = Mesa DRI R300 (RS400 5975) 20090101  NO-TCL
GL_VERSION    = 1.5 Mesa 7.8-devel
GL_VENDOR     = DRI R300 Project
4326 frames in 5.0 seconds = 865.105 FPS
4473 frames in 5.0 seconds = 894.538 FPS
4622 frames in 5.0 seconds = 924.274 FPS
4594 frames in 5.0 seconds = 918.762 FPS
4608 frames in 5.0 seconds = 921.482 FPS
4375 frames in 5.0 seconds = 874.967 FPS
```

If you compile from recent mainline sources (2.6.33-rc5) that has correct firmware right?
Do errors in dmesg that start with [drm, e.g [drm],[drm:radeon_fence_wait],[drm:radeon_ib_schedule],etc suggest a kernel bug or an xorg/libdrm one?

I've been away since the day I posted the interesting upgrade/downgrade post.

Perry3D told be I just have to recompile mesa-full and xf86-video-ati-git.  

Which makes perfect sense.  I didn't have time to spend on it, as I was quickly getting out of town. :)

I'll do the .git compile thing tomorrow, & report back. If there are any problems I expect it/they will only be short-lived bugs, not user error based on ignorance as my problem is.

---

### Post by handy on 2010-02-03
> **shane2peru said:**
> 
...Perhaps I'm not a 100% open source fellow, and I certainly do appreciate open source stuff, but don't mind some proprietary stuff. A few years down the road, I'm sure a lot of stuff will be different.

Shane

I appreciate where you are coming from Shane.  Up until a bit past the middle of last year I would NEVER recommend an ATi GPU to anyone, as it just didn't make sense, their drivers always suck.

What has been happening during the period since AMD bought ATi, is that AMD have been opening up (source wise) the tech' info' on the ATi GPUs.  They have even, quite recently opened up the documentation on the Evergreen series.

This has made it possible for the ATi open-source support to move ahead incredibly fast. Especially when compared to the speed of development when the poor dev's have to reverse engineer everything.

So things really, truly, are changing; & incredibly fast for the ATi GPUs.

Though not overnight.

As the kernels & associated packages develop during this year, Ubuntu will see BIG changes in ATi support.

Other systems that use more up to date versions will benefit from these changes quicker.

It is all good.

Don't throw your ATi card away? :)


Here is a little on Evergreen:

[http://www.botchco.com/agd5f/?p=48](http://www.botchco.com/agd5f/?p=48)

---

### Post by Nerd King on 2010-02-03
I can confirm it's still solid as a rock, more stable than my 31-kernel proprietary nvidia setup at the moment. Games are still poor (I'm using 32.7 and testing out 33latestrc at the moment with xorg-edgers, easy to set up, thanks lovely ppa people) but it's letting me get my work done, compiz is flying, I couldn't ask for a better work system.

---

### Post by stark222000 on 2010-02-09
So I have a Radeon x1250 and I have pretty bad support for simple flash games and stuff and I attempted to play portal (bad idea) and it was incapable of working at all. I kind of understand what I have read in this forum but am I to understand 3d support for Karmic and my card will be coming some time this year? any estimates or just sometime this year?

---

### Post by JDShu on 2010-02-09
> **stark222000 said:**
> So I have a Radeon x1250 and I have pretty bad support for simple flash games and stuff and I attempted to play portal (bad idea) and it was incapable of working at all. I kind of understand what I have read in this forum but am I to understand 3d support for Karmic and my card will be coming some time this year? any estimates or just sometime this year?

I don't use ati, but... waiting for Lucid is probably the easiest thing to do for newer kernels, though I'm not sure if Portal would work even with the latest updates in the oss drivers.

The phoronix guys did some tests with r600 cards recently:
[http://www.phoronix.com/scan.php?page=article&item=ati_r600_mesa_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r600_mesa_3d&num=1)

---

### Post by mushwars on 2010-02-09
I posted this a while ago:
> HOW TO GET 3d with the XF86-ati-driver

install from source the 2.6.32-r2 kernel
upgrade Xorg-server to 2.17.999
install from git libDRM-2.4.17
install from git mesa-7.7
install from git the xf86-ati-driver-9999

:popcorn:unless you **KNOW** what you are doing dont do this, you will also have to recompile KDE/gnome ( so I guess you have to install that from git as well )

ooo I forgot the reason why I posted this. Doing this is NOT worth it, I did it and when I went to play a 3d game ***it renders shadows poorly and some reflections are rendered upside down.***

The reason why you are reading this is...
**If you want 3d accelleration with an ATI card, you MUST install the FGLRX proprietary driver.**

so the drivers really are not of age yet, but hell if I could do better. The reason the propitiatory ones are so good is that they do that their whole life it is their living not some thing they do on the side.

---

### Post by linux4life88 on 2010-02-09
Right now I have an ATI R700 card an I'm really looking forward to getting battery support in the future. I buy ATI because at least they are willing to help the open source community.

---

### Post by michael37 on 2010-02-09
Just a quick testimony.

I am running Karmic 9.10 on a laptop with ATI R520 (Mobility X1400) and I decided to tweak my performance settings.

After some experimentation with xorg.conf settings, I found [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) page, deleted /etc/X11/xorg.conf and enabled radeon.modeset.

Compiz, Video playback, 3D games, everything works like a charm.

---

### Post by handy on 2010-02-10
If you want to go somewhere near cutting edge with the software required for ATi GPU support have a look at the OP in the **Ubuntu Stuff:** section, the links there really should give you a good start.

I'm running the .git packages via Arch, & it is working very nicely, but still too slow for complex 3D games.

Kernel .33 may have some power management features incorporated, if not .34 really should be a sitter.  

Each kernel & associated packages will bring us more 3D speed & power management, which is all most of us need.

---

### Post by markbuntu on 2010-02-10
I am running lucid on an old box with a 200M and it is working great OOB, 3D and everything, lol. I will most likely be putting a HD3650 in this box soon (soon as I get a 5750) and we will see how that works out.

---

### Post by phredbull on 2010-02-10
> **handy said:**
> If you want to go somewhere near cutting edge with the software required for ATi GPU support have a look at the OP in the **Ubuntu Stuff:** section, the links there really should give you a good start.

Hmm, this procedure worked ok with my old Wubi install, but since I've switched to a full partitioned install, when I tried the same thing, I couldn't log in to Gnome at all. I've gotten the login issues sorted out, but now have no compositing or 3d. 2d is fine.
:-k

---

### Post by handy on 2010-02-10
> **phredbull said:**
> Hmm, this procedure worked ok with my old Wubi install, but since I've switched to a full partitioned install, when I tried the same thing, I couldn't log in to Gnome at all. I've gotten the login issues sorted out, but now have no compositing or 3d. 2d is fine.
:-k

Perhaps Nerd King, or someone who is using Ubuntu will be able to help you out...?

---

### Post by Xbehave on 2010-02-10
> **phredbull said:**
> Hmm, this procedure worked ok with my old Wubi install, but since I've switched to a full partitioned install, when I tried the same thing, I couldn't log in to Gnome at all. I've gotten the login issues sorted out, but now have no compositing or 3d. 2d is fine.
:-k
Could you attach

xorg.log
dmesg.log
and gdm/xdm.log

and i will give the files a read to see if you have a simple problem (probably not til Saturday though)

---

### Post by phredbull on 2010-02-10
> **michael37 said:**
> ...I found [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) page, deleted /etc/X11/xorg.conf and enabled radeon.modeset.

This fixed my problems! I'm still using the 2.6.32 kernel, but now I can use Emerald and AWN.
:D

edit: I deleted my xorg.conf and so far, so good!

---

### Post by handy on 2010-02-11
> **phredbull said:**
> This fixed my problems! I'm still using the 2.6.32 kernel, but now I can use Emerald and AWN.
:D

edit: I deleted my xorg.conf and so far, so good!

Glad to hear it.

On the day I could do without the xorg.conf, I was so happy. :)

xorg.conf has been one of the mind benders, & back to windows senders of the Linux world for so long.

Knowing that xorg.conf is in the process of disappearing, for ALL of us, is such a BIG step in the right direction. Most especially, when the life & minds, of new Linux recruits is taken into consideration.

---

### Post by michael37 on 2010-02-12
> **handy said:**
> Glad to hear it.

On the day I could do without the xorg.conf, I was so happy. :)

xorg.conf has been one of the mind benders, & back to windows senders of the Linux world for so long.

Knowing that xorg.conf is in the process of disappearing, for ALL of us, is such a BIG step in the right direction. Most especially, when the life & minds, of new Linux recruits is taken into consideration.

Certainly.  I still remember pain getting Fiesty working on this same laptop: it required fglrx, xgl (nested under xorg xserver) and uncanny tweaking of xorg.conf.

FOSS driver is the way to go.  Now, to get better 3D performance and I'll be blissfully happy.

---

### Post by handy on 2010-02-13
I downloaded & installed the [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/),  yesterday.

I ran it this morning, even though Firefox was running with 13 tabs open, 2 torrents were happening with Transmission, Worker was open, & there were 4 tabs going in Sakura; one of them being htop. The machine had been running for 50 hours plus, & there is still a memory leak in Ghostery, so I had a little more than half of the 1GB of RAM available. Both CPUs were just about idling before the tests though.

Here are the results on the Phoronix website (I should have given it a more appropriate name than 1st.phoronix.test though! :oops: I wasn't aware that it was going to be published when I named the test):

[http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834](http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834)

The first 3 games running at an average of around 30 fps, really presented incredibly well. I was surprised at the speed of game-play & the quality of the 3D.

The last one, Nexuiz, ran too slow to be playable, looked good, though there were display aberrations flashing on the screen from time to time.

My glxgears is currently a little over 1600 fps.

Hardware is a 2007 model, alu' 24" iMac, technical spec's can be found here:

[http://support.apple.com/kb/SP16](http://support.apple.com/kb/SP16)

The only change to the above spec's is that I upgraded the 320GB drive to a 1.5TB WD Green, with 32MB cache.

All of the related Radeon open-source packages are .git 20100129 & kernel26-git 20100117-1, on Arch 64bit, this is a kernel26.2.6.33. version (Phoronix mistook it for .32?)

---

### Post by JDShu on 2010-02-13
Wow, awesome handy! I bookmarked your results for reference :D

---

### Post by yodermk on 2010-02-15
Nice to see this discussion is still happening.

I'm thinking of upgrading to Lucid soon in hopes of having 3D working without replacing xorg packages, etc., from unofficial sources. Card is 3200 HD.

---

### Post by handy on 2010-02-16
Radeon KMS Gets Faster X-Video Support:

[http://www.phoronix.com/scan.php?page=news_item&px=Nzk4NA](http://www.phoronix.com/scan.php?page=news_item&px=Nzk4NA)

:)

---

### Post by handy on 2010-02-17
It's possible that Catalyst 10.2 is compatible with xorg-server 1.7?

Still waiting for the .pdf file to become available.

Some people say it does work with 1.7 some say it still doesn't?

Stay tuned? 

[http://www2.ati.com/drivers/linux/catalyst_102_linux.pdf](http://www2.ati.com/drivers/linux/catalyst_102_linux.pdf)

Hopefully when you get to click on the above link it works for you? :-|

---

### Post by handy on 2010-02-17
No, it's currently not looking good for Catalyst 10.2. 

At least not for all of the unsupported distro's, & particularly not for those that use the cutting edge stable versions of packages.

By the time of the next Ubuntu release I'm sure it will be somewhat more cohesive.

Whether that means it will be able to handle a version of xorg-server that is over 3 months old or not remains to be seen?

---

### Post by Xbehave on 2010-02-17
> **handy said:**
> No, it's currently not looking good for Catalyst 10.2. 

At least not for all of the unsupported distro's, & particularly not for those that use the cutting edge stable versions of packages.

By the time of the next Ubuntu release I'm sure it will be somewhat more cohesive.

Whether that means it will be able to handle a version of xorg-server that is over 3 months old or not remains to be seen?
I apreciate this is essentially your thread and all but could we keep it about the OSS drivers, I for one care little about flgrx but i'm subscribed to this thread for the informative updates you provide about KMS+radeon developement.

---

### Post by rajeev1204 on 2010-02-17
> **handy said:**
> It's possible that Catalyst 10.2 is compatible with xorg-server 1.7?

Still waiting for the .pdf file to become available.

Some people say it does work with 1.7 some say it still doesn't?

Stay tuned? 

[http://www2.ati.com/drivers/linux/catalyst_102_linux.pdf](http://www2.ati.com/drivers/linux/catalyst_102_linux.pdf)

Hopefully when you get to click on the above link it works for you? :-|

Hi handy,

I think the servers are overloadedwith the driver release today.But dont think it supports xorg 1.7 yet.Didnt read in the notes.

Also do you remember the s3tc support in open driver which doesnt work with the R600 and above cards,i have one and i cant play the only game i ever play, quake4.

I spoke to the devs and they aint too bothered anyway.So i have to use prop driver ,but its so appaling with window management etc you know.

---

### Post by handy on 2010-02-17
> **Xbehave said:**
> I apreciate this is essentially your thread and all but could we keep it about the OSS drivers, I for one care little about flgrx but i'm subscribed to this thread for the informative updates you provide about KMS+radeon developement.

Anything worthwhile, open or closed source, to do with the ATi GPUs that comes my way I throw into this thread.

I am, & this thread is, primarily interested in the open-source drivers for the ATi GPUs. 

If anything comes to hand regarding the Catalyst drivers I'll throw it in here too. 

Some of it (at least) may not ever become available in the UF & some of it is important. I think.

I don't want to start another thread for the Catalyst stuff. It just comes in, in occasional bursts (with their releases) anyway.

---

### Post by handy on 2010-02-17
@rajeev1204: If you have the space on you HDD, install the & run the Phoronix Test Suit?

I think you will find it incredibly educational, I know I did.

You will need about 2GB of drive space from memory.

The link is about 9 posts back. ;)

---

### Post by handy on 2010-02-17
Catalyst 10.2 is not compatible with xorg-server 1.7. :(

There are a pile of other problems with this release as well, as usual.

---

### Post by handy on 2010-02-18
AMD Catalyst 10.2 For Linux Gets Direct2D:

[http://www.phoronix.com/scan.php?page=news_item&px=Nzk5MQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzk5MQ)

Also of interest in the linked to page:

*With the X.Org Server 1.7-using Ubuntu 10.04 LTS coming in April, Catalyst 10.3 or 10.4 will support this updated X.Org Server finally. However, at the end of March this cycle will be restarted all over again once X Server 1.8 has been released.*

---

### Post by Nerd King on 2010-02-19
Present status from my end.. kernel 2.6.32-8 is running wonderfully though still doesn't have the speed for a good 3d gaming session in a wine game. Accuracy is solid. 2.6.33-rc8 is giving me regressions in terms of 3d speed.

Incidentally I tested gnome-shell on 2.6.32-8 and found it unusably slow (1 frame every 7 seconds or so) where compiz flies, hinting at either a feature not fully ported or hobbile coding by the Gnome devs.

---

### Post by Nerd King on 2010-02-25
So I downloaded the .33 drivers from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) but it seems not to be working in terms of 3D. Maybe I'll have to wait for further updates to xorg-edgers.

---

### Post by Ubuntiac on 2010-02-26
Is anyone getting random coloured borders occasionally popping up around windows with the open ati driver? They mainly happen when switching from one window to another, occasionally when resizing a window, but never when moving a window. From time to time a smaller QT element in the window will get a colour fill like this too:

[IMG]http://img28.imageshack.us/img28/7219/windowborder.jpg[/IMG]

I'm using xorg edgers with 2.6.32-14 on Kubuntu Lucid + KDE 4.4.0

---

### Post by Nerd King on 2010-02-26
It may well be a kde thing as I'm mostly on gnome and not getting that. Having said that I do occasionally boot into kde (latest 4.4 if that helps) and don't get that issue, albeit it's not my primary desktop.

---

### Post by handy on 2010-02-26
I'm on Openbox & get no problems in the display.  There has been talk on the Arch forum with regard to kwin, but I don't follow it as I don't use KDE so I don't know what they are talking about.

---

### Post by Ayuthia on 2010-02-27
> **Ubuntiac said:**
> Is anyone getting random coloured borders occasionally popping up around windows with the open ati driver? They mainly happen when switching from one window to another, occasionally when resizing a window, but never when moving a window. From time to time a smaller QT element in the window will get a colour fill like this too:

[IMG]http://img28.imageshack.us/img28/7219/windowborder.jpg[/IMG]

I'm using xorg edgers with 2.6.32-14 on Kubuntu Lucid + KDE 4.4.0

It is an issue in Lucid.  When I started using Ubuntu Lucid in the earlier alphas it had this issue and now I switched over to Kubuntu Lucid and it still has this issue.  However, my Gentoo build does not have this issue with KDE 4.4 and the same goes for my Arch build on my desktop (using the kdemod 4.4 repos).  I lost track of the bug number for this issue, but I think that it is posted in the Lucid threads somewhere.

---

### Post by handy on 2010-02-28
A recent post in the Arch forum thread dedicated to OSS ATi support (by the Perry3D who started the thread & maintains up to date how-to info' in the first post) mentions that Kwin has problems with KMS, no problems with UMS.

---

### Post by handy on 2010-03-01
Major Linux 2.6.34 Kernel GPU DRM Updates:

[http://www.phoronix.com/scan.php?page=news_item&px=ODAyMg](http://www.phoronix.com/scan.php?page=news_item&px=ODAyMg)

---

### Post by nomadewolf on 2010-03-02
> **shane2peru said:**
> I didn't take it as your intention to flame me, lest I would have just ignored it. ;) So no offense taken, just felt I needed to clarify my situation, it wasn't a quick or sloppy decision on my part.  And perhaps in the future after they have been tried and true I may reconsider.  On the other hand I researched Nvidia this time around and bought Nvidia specifically after all my hard-ache with ATI.  Perhaps they are not opensource, but they seem to function well with the proprietary drivers.  Perhaps I'm not a 100% open source fellow, and I certainly do appreciate open source stuff, but don't mind some proprietary stuff. A few years down the road, I'm sure a lot of stuff will be different.

Shane

I understand how you feel. Seriously, i do. But, i think you should take the following into account:
-ATI has OpenSource Drivers now cause of the effort put forth by AMD.
-ATI will have quality OpenSource Drivers in a few months for your card.
-If AMD hasn't bought ATI, we would probably never have OpenSource Drivers for ATI cards.
-AMD allways supported OpenSource Software, even before buying ATI.
-AMD can't realease the source of their drivers due to legal reasons.
-Since AMD's aquisition of ATI, the ATI drivers have seen major speed and stability improvements under Linux.
-By deciding not to buy ATI anymore, you are punishing AMD for ATI's mistake.

And now let me tell you my story:
I have both NVidia and ATI cards. The ATI one works well under Windows and Linux. My NVidia card can't play this old game called Praetorians, which i love, and am forced to play with the ATI.
My NVidia card has a problem of overheating because NVidia is greedy, and decided to use some low quality material to cut the costs, although they sell much more than ATI. My laptop keeps dying, because my NVidia card keeps overheating, and when the warranty is expired, my laptop (which costed me €1500) is going straight to the garbage cause it won't compensate to fix it... All this, NVidia's fault.
So, when you tell me ATI is bad, i tell you, at least they saw their mistake and are trying make up for it big time. As for NVidia, gave lots of trouble costs, and don't even try to solve my problem...

---

### Post by xir_ on 2010-03-02
> **nomadewolf said:**
> I understand how you feel. Seriously, i do. But, i think you should take the following into account:
-ATI has OpenSource Drivers now cause of the effort put forth by AMD.
-ATI will have quality OpenSource Drivers in a few months for your card.
-If AMD hasn't bought ATI, we would probably never have OpenSource Drivers for ATI cards.
-AMD allways supported OpenSource Software, even before buying ATI.
-AMD can't realease the source of their drivers due to legal reasons.
-Since AMD's aquisition of ATI, the ATI drivers have seen major speed and stability improvements under Linux.
-By deciding not to buy ATI anymore, you are punishing AMD for ATI's mistake.

And now let me tell you my story:
I have both NVidia and ATI cards. The ATI one works well under Windows and Linux. My NVidia card can't play this old game called Praetorians, which i love, and am forced to play with the ATI.
My NVidia card has a problem of overheating because NVidia is greedy, and decided to use some low quality material to cut the costs, although they sell much more than ATI. My laptop keeps dying, because my NVidia card keeps overheating, and when the warranty is expired, my laptop (which costed me &#8364;1500) is going straight to the garbage cause it won't compensate to fix it... All this, NVidia's fault.
So, when you tell me ATI is bad, i tell you, at least they saw their mistake and are trying make up for it big time. As for NVidia, gave lots of trouble costs, and don't even try to solve my problem...

I totally agree with everything you said here. I'm in the exact same situation with my £2000 gaming laptop which suffers from poor nvidia workmanship. My most recent laptop has an ATI card and I love it to bits. Until nvidia starts to be more open source friendly i wont be buying another product.

---

### Post by handy on 2010-03-02
I don't know the circumstances with regard to the two posts above, BUT, it may not be all nVidia's fault.  

The manufacturer of the Notebook, or the graphics cards on the market buys the chips from nVidia & gains access to the reference design, beyond that, especially when it comes to cooling, it is up to the manufacturer of the card, or the Notebook, as to how they build the things.

---

### Post by markbuntu on 2010-03-02
> **handy said:**
> I don't know the circumstances with regard to the two posts above, BUT, it may not be all nVidia's fault.  

The manufacturer of the Notebook, or the graphics cards on the market buys the chips from nVidia & gains access to the reference design, beyond that, especially when it comes to cooling, it is up to the manufacturer of the card, or the Notebook, as to how they build the things.

In this case, and it has been much documented and reported on, it was Nvidia that is directly responsible for the failures. Nvidia supplies data sheets that give heat and current and voltage ratings and tolerances for their chips and sometimes also supply a list of approved suppliers for peripheral components like capacitors and resistors etc. 

The widespread failure of the Nvidia chips in notebooks was due to the Nvidia marketing department deliberately mis-rating the thermal tolerance of their gpu chips to notebook manufacturers. The failure of many Nvidia gpu cards was due OEMs using capacitors on the recommended list supplied by Nvidia even though Nvidia knew for years that many of these did not hold up in long term testing but never informed the OEMs.

This evidence has come out in various trials as the OEMs seek to recover warranty costs. Nvidia has blamed variously rouge marketing personnel and other technical snafus when settling these cases but has yet to actually accept or admit anything it did was wrong or offer amends beyond the limited settlements. 

This is a big reason why so many laptops now come with ATI chips. OEMs do not need or want this headache again.

---

### Post by handy on 2010-03-03
**@markbuntu:** Ok, it sounds like in these particular circumstances nVidia is the culprit.

Short term thinking on their behalf obviously.

Marketroids are like that... :(

Hopefully for all concerned in the future at least, they have learned from this big mistake.

---

### Post by xir_ on 2010-03-03
> **handy said:**
> **@markbuntu:** Ok, it sounds like in these particular circumstances nVidia is the culprit.

Short term thinking on their behalf obviously.

Marketroids are like that... :(

Hopefully for all concerned in the future at least, they have learned from this big mistake.

The key problem for my generation of cards is that the cards have a tendency to melt. Likely because of what markbuntu said.

I can already tell my card is degrading. When the system starts to get hot i start to see a lot of artefacts on my screen (this occurred on windows too before i fully ditched it).


Regardless ATI have really been impressing me. They really seem to understand how to engage with the community. They are often on the Phoronix forums offering help and information.

Nvidia should really refocus their business and start to collaborate with the devs of Nouveau. For the moment if any one asks me what graphics to get the answer is now always ATI.

---

### Post by handy on 2010-03-03
:)

Well, you know that I have been saying that at least the Linux GPU world is in huge state of flux for well over 6 months.

It is great to get positive feedback from people that agree.

It won't take long before AMD/ATi are the darlings of the Linux world re. GPUs at least.

In the long run, AMDs actions will most likely speed up the change in attitude in nVidia & other other companies.

FOSS is such an intelligent way to develop, secrecy only slows people down & fosters paranoia.

Which is just plain dumb & dumber.

---

### Post by nomadewolf on 2010-03-06
And NVidia strikes again... When their hardware doesn't fail, their software does the trick...
```
http://www.engadget.com/2010/03/05/nvidia-pulls-196-75-driver-amid-reports-its-frying-graphics-car/
```

---

### Post by shane2peru on 2010-03-06
Ok, I think I finally have it!  This pertains to the proprietary drivers, but perhaps this will help someone. I have the Radeon HD 3100 ati card in my laptop (or perhaps it is integrated?)  At any rate, I have had serious overheating problems for quite some time.  I have tried to sell the laptop deciding it would never work with Linux, and have yet to sell it (seems to work fine with Windows).  I"m not a noob to Linux, that is all I use and have used for several years now.  I have installed about a dozen different distros to see if anyone handled this better.  Honestly OpenSuse did a slightly better job and had newer drivers or something that worked better.  I'm back to Ubuntu because that is my favorite distro.  After over a year of working on this I 'think' I have solved this again.  I added these options to my xorg.conf file:

```

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	Option		"TexturedVideo" "on"
	Option		"UseFastTLS" "1"
	BusID       "PCI:1:5:0"
EndSection

```

I'm not exactly sure why this, worked, I just copied it from someone else's xorg.conf that had reported it working "perfectly".  I opened a flash web game and it didn't overheat!  This was one of the major problems with this, Flash, or any video would often overheat, and has even overheated from just having a few different windows open.  I haven't seen this thing go over a 100C yet, even with flash, a few open windows!  I hope this helps someone, because it has been extremely frustrating for me for a long time.

Shane

---

### Post by Kazade on 2010-03-07
Just thought I'd add to this thread my awesome experience with the open drivers on Lucid...

Until the upgrade I've been using FGLRX (for 3D programming) but without compiz which caused everything to slow up like crazy. I decided to bite the bullet and upgrade to Lucid and use the open drivers. They worked, but were quite slow and a little buggy... for example, my game that I'm writing had really poor texture aliasing and took ages to load each texture into the GPU so startup was slow.

I just upgraded my kernel to 2.6.33 and literally all the bugs have gone away, and glxgears increased from ~700fps to over 2000(!). The drivers are working perfectly fine for everything I've used them for, amazing!!

---

### Post by handy on 2010-03-07
That's good to hear Kazade. :)

I installed the latest *xf86-vide-ati-git* package this morning & it took about 400fps off my glxgears. :(

I'm sure looking forward to the time when we have reached the stable kernel .34 driver packages. Though I know it won't be the end of the road (it never ends :)) but we should mostly be getting into a quite comfortable place by then as far as our 3D gaming & power management is concerned.

Following are my results after the *xf86-vide-ati-git* upgrade:


[I]```
handy ~  $  glxgears
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
6322 frames in 5.0 seconds = 1263.778 FPS
6325 frames in 5.0 seconds = 1264.931 FPS
6320 frames in 5.0 seconds = 1263.902 FPS
6323 frames in 5.0 seconds = 1264.552 FPS
6319 frames in 5.0 seconds = 1263.252 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 104046 requests (104043 known processed) with 0 events remaining.
handy ~  $  glxinfo |grep -i opengl
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL DRI2
OpenGL version string: 2.0 Mesa 7.8-devel
OpenGL shading language version string: 1.10
OpenGL extensions:
handy ~  $ 
```[/I]

---

### Post by handy on 2010-03-08
I just updated the kernel26-git, & libdrm-git, glrptoto-git, dri2proto-git, mesa-git, libgl-git, glut-git, ati-dri-git, (this file xf86-vide-ati-git was upgraded yesterday, see above?) to the latest versions.

It gave me the following results:

[I]```
handy ~  $  glxgears
6342 frames in 5.0 seconds = 1268.252 FPS
6330 frames in 5.0 seconds = 1265.934 FPS
6336 frames in 5.0 seconds = 1267.168 FPS
6331 frames in 5.0 seconds = 1266.144 FPS
6330 frames in 5.0 seconds = 1265.925 FPS
6337 frames in 5.0 seconds = 1267.371 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 121722 requests (121719 known processed) with 0 events remaining.
handy ~  $  glxinfo |grep -i opengl
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL DRI2
OpenGL version string: 2.0 Mesa 7.9-devel
OpenGL shading language version string: 1.10
OpenGL extensions:
handy ~  $ 
```[/I]

It hasn't improved the glxgears, fps, but it HAS taken all of the error messages away.

I'll give this system a shot via the phoronix test suite & post the results.

---

### Post by handy on 2010-03-08
Here are the phoronix test suite results:

[http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-317-26676-10968](http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-317-26676-10968)

As expected, they are a little slower in fps, but really it had next to no effect on the game play as a viewer. 

All games looked fantastic, the rendering was beautiful.  Urban Terror often had as many as 32 players, & it was moving fast.

Open Arena was so fast it was ridiculous.

World of Padman looked amazing & moved along pretty quick too.

Nexuiz was still the only one that at certain resolutions would be unplayable.

[I]**[Edit:]** Out of interest, I just had a look to see if Glest was playable, as it never has been on the open-source drivers.

& surprisingly it is!  

The glxgears fps has dropped by about 400fps since the last time I tested Glest, & it was absolutely *_un_*playable.  The PST has dropped fps on all of the games it tests with. 

This leads me to the conclusion that there are obviously improvements in the latest -git packages that make it work better than it did before even if it isn't showing up as speed in those two tests - glxgears & PST.  

Which is really what everybody would be hoping for.[/I] :)

---

### Post by handy on 2010-03-10
Perry3D, began providing an x86_64 -git repo (for Arch) of compiled packages, including the kernel, that are required for the ATi GPU OSS support.

I only started using it 2 or 3 days ago, & it is so quick to install compared to the time you spend compiling (the kernel especially), so now I have his repo at the top of my list in pacman.conf so that every time I do a system upgrade his repo takes precedence over the [core] repo below it. (I'm pretty sure that that is how it works.)

Anyway, today is my first taste of kernel .34 rc1, & all of the other packages in Perry's repo that are for the job of getting the ATi GPU doing its best.

After installation I have found no improvement in glxgears, I'm not going to bother with phoronix test suite ( I'll just call it "PTS" in future) at this early stage of .34. I'll wait for experiential motivation on that one. :)

I just went through a quick game in Glest, (if you wonder why I mention Glest see above?) & there were no problems, apart from the textures on parts of the ground surface not being quite as good as they can be, (I didn't mention it in the previous post, I guess I was still recovering from the fact that Glest was playable!?) no problem at all as far as the enjoyment of the game is concerned, for me at least.

Anyway, I guess the bottom line is, we are now into the development phase of kernel .34, & it has quite a lot to bring to the ATi GPU table; not the least being power management, & there really should be both some 3D speed increases & the ability for a larger variety of game engine support for us here. 

So I'll keep you informed, as I will be upgrading my Arch system at least once, most days, which also means that I'll be basically keeping up with the -git upgrades day by day.

I am really looking forward to the improvements that should be coming through in this particular development phase as I expect them to start to bring smiles to the frowns that so many poorly supported ATi GPU users are used to having.

Just like you, I sure do hope I'm right on just what kernel .34 has for us.  :)

---

### Post by nomadewolf on 2010-03-12
> **handy said:**
> Perry3D, began providing an x86_64 -git repo (for Arch) of compiled packages, including the kernel, that are required for the ATi GPU OSS support.

I only started using it 2 or 3 days ago, & it is so quick to install compared to the time you spend compiling (the kernel especially), so now I have his repo at the top of my list in pacman.conf so that every time I do a system upgrade his repo takes precedence over the [core] repo below it. (I'm pretty sure that that is how it works.)

Anyway, today is my first taste of kernel .34 rc1, & all of the other packages in Perry's repo that are for the job of getting the ATi GPU doing its best.

After installation I have found no improvement in glxgears, I'm not going to bother with phoronix test suite ( I'll just call it "PTS" in future) at this early stage of .34. I'll wait for experiential motivation on that one. :)

I just went through a quick game in Glest, (if you wonder why I mention Glest see above?) & there were no problems, apart from the textures on parts of the ground surface not being quite as good as they can be, (I didn't mention it in the previous post, I guess I was still recovering from the fact that Glest was playable!?) no problem at all as far as the enjoyment of the game is concerned, for me at least.

Anyway, I guess the bottom line is, we are now into the development phase of kernel .34, & it has quite a lot to bring to the ATi GPU table; not the least being power management, & there really should be both some 3D speed increases & the ability for a larger variety of game engine support for us here. 

So I'll keep you informed, as I will be upgrading my Arch system at least once, most days, which also means that I'll be basically keeping up with the -git upgrades day by day.

I am really looking forward to the improvements that should be coming through in this particular development phase as I expect them to start to bring smiles to the frowns that so many poorly supported ATi GPU users are used to having.

Just like you, I sure do hope I'm right on just what kernel .34 has for us.  :)

Hi!
Did you have to install the OSS drivers in .34RC1?
Or do they come embeded in the kernel?
How did you install the drivers? (the kernel i already know how... but, at least .33, won't correctly compile the proprietary drivers...)
Thanks

---

### Post by handy on 2010-03-12
> **nomadewolf said:**
> Hi!
Did you have to install the OSS drivers in .34RC1?
Or do they come embeded in the kernel?
How did you install the drivers? (the kernel i already know how... but, at least .33, won't correctly compile the proprietary drivers...)
Thanks

I'm using Arch, so my method is different than what you will need to use for Ubuntu.

Yes you do have to install other packages, the kernel is only a part of the OSS driver support solution.

The following link should give you all you need for Ubuntu, I grabbed it off of the first page (of this thread), where there are a LOT of other useful links under various headings, if you are interested?

[url]http://ubuntuforums.org/showpost.php?p=8448508&
postcount=101[/url]

Good luck. :)

---

### Post by handy on 2010-03-15
[I]More ATI Radeon KMS Power Management Fun:

Posted by Michael Larabel on March 14, 2010

Power management support within the Linux kernel for the ATI Radeon DRM driver has been in development for months and gone through several revisions, but with the forthcoming Linux 2.6.34 kernel there is initial ATI KMS power management support. For making the power management situation even better, over the weekend Alex Deucher of AMD has been working on another set of patches. [/I]

For more:

[http://www.phoronix.com/scan.php?page=news_item&px=ODA2Mw](http://www.phoronix.com/scan.php?page=news_item&px=ODA2Mw)

---

### Post by KingBongo on 2010-03-16
Wonderful thread! Maybe there is some hope for ATI/AMD on Linux :) Here is my story:

About 6 months ago the graphics card (AGP) in my P4 blew up. I decided to buy an Nvidia because of compatibility problems with some of the best ATI/AMD cards and Linux. I bought an Nvidia clone (I believe), brand new from eBay, a 7950GT AGP. That is probably the best single-slot card Nvidia ever made for the AGP bus. It worked great for about three months until it suddenly died. I sent it back and got a new one. The new was absolutely dead from the beginning. I am through with these Nvidia clones :p

So now I am looking for a new card. The relatively newly released AMD HD4650/HD4670 AGP is really interesting (HDMI for example)! If only it works I would be happy with it for years. I have a few questions some good guys could maybe answer.

1. Will I be able to make the HD4650 or HD4670 work with Ubuntu 10.04? This is critical. I have some BAD experience with the stronger but older HD3850. I never could make it work. I am scared for the HD3850/HD3870 :p

2. The difference between the HD4650 and the HD4670 seems to be mainly better memory on the later one, and slightly higher clocking frequency. Is it worth it on the P4 (3.06GHz, 2GB RAM)? 

3. How does the HD4650/HD4670 compare performance wise with Nvidia 7950GT? Not a really big issue, since the 7950GT already seems to be overkill for the P4 and for what I used it for. Good to know anyway. 

4. I am using the computer together with an older TV. I really need S-Video, or at least I think so. The HD4650/HD4670 doesn't have S-Video out. Will I be able to use an adapter and convert any of the present outputs to S-Video? Do the hardware and drivers support that?

I really would appreciate some help! Please remember I am talking about AGP cards. And no, I am not buying some other computer :)

---

### Post by handy on 2010-03-16
**@KingBongo:** I think that if you take the time to read/skim through this thread, you will find out how your desired GPU is going compatibility wise with the OSS driver support:

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

There are currently 40 pages in the above linked thread, so you may have to develop a strategy to get the best out of it in the least amount of time. :)

As far as S-Video is concerned; I think you will need to get a card that has the built in support with the socket on the back.

As far as performance is concerned; you could have a look at the Tom's Hardware site, where you should be able to come up with reviews/benchmarks for 7950GT (have one of those myself :)) & whatever ATi GPU driven card, though not necessarily in the same review, not that that should matter much.

I don't expect Ubuntu to have the kernel .34 until the 10.10 release, until that kernel is out power management won't exist for the ATi GPUs, & realistically it will take until the following kernel .35 before we can start to hopefully expect most of the driver support work to have been done to the point of supplying great compatibility & very useful speed re. OpenGL games. At least for all but the Evergreen (current) series of cards.  

Though AMD released the documentation on Evergreen, so who knows just how quickly they will be bought up to speed?

The coding is so much faster when you're not trying to reverse engineer your way to a solution. :)

Good luck.

P.S. I'm using the kernel .34-git in Arch at the moment, & as you will see in the thread I linked to above, people are already getting positive results re. power management, (at last). I don't use a notebook computer, so it is not as important to me.

---

### Post by KingBongo on 2010-03-16
handy:
Thank you!

Well. I actually DID skim through all pages, but I could not find anything about my specific card. There seem to be a lot of smart guys in this thread so I thought I'd better ask :) Also, I do not know exactly which chipset is in the HD4650/HD4670. Can somebody help me with that? Another thing is that sometimes AGP cards seem to cause trouble, although the PCI-E versions work flawlessly. I know one thing for sure, I am not buying any ATI/AMD card ever again before I have it confirmed that it works with Ubuntu, and with relative ease. I am not going through the HD3850 mess again :(

I will be looking into the link you posted.

---

### Post by handy on 2010-03-16
> **KingBongo said:**
> 
handy:
Thank you!

Well. I actually DID skim through all pages, but I could not find anything about my specific card. 

I meant of the thread I posted the link to.

> **KingBongo said:**
> 
 There seem to be a lot of smart guys in this thread so I thought I'd better ask :) Also, I do not know exactly which chipset is in the HD4650/HD4670. Can somebody help me with that? 

It's the R700 series, if that is what you meant?

Which should make you happy when you look down its column on this page:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

> **KingBongo said:**
> 
Another thing is that sometimes AGP cards seem to cause trouble, although the PCI-E versions work flawlessly. 

Ain't that the truth.  

A couple of years & more ago, the only distro that could handle my 7950GT (without any input from me)  was Sabayon. 

The amount of trouble I had getting the 7950GT (AGP) to work when I first setup Arch, was amazing.  I spent about 20 hours before I stumbled upon turning AGP OFF in xorg.conf!!!  

The reason being (I think) is that it is not a native AGP chip, & it has been shoehorned into an AGP card, which confused the hell out of X.org.

These days that card no longer causes a problem, I can run it on Arch, (which I reinstalled on that machine last week) it still needs an xorg.conf on my system at least, but I didn't have to do anything unusual (like turn off AGP) to get it to work.

> **KingBongo said:**
> 
I know one thing for sure, I am not buying any ATI/AMD card ever again before I have it confirmed that it works with Ubuntu, and with relative ease. I am not going through the HD3850 mess again :( 

All I can say to you about that, is don't be in a rush.  When the next release of Ubuntu comes out, ask the question in the appropriate sub-forum here.  Find out about other user's experiences which ATi AGP cards are working the best.

Don't forget that Catalyst should be working ok, because Ubuntu is one of the few Linux distro's that AMD support.  

So if all else fails, if you have an R600 or R700 GPU, it will work with Catalyst.  But again, wait until the 10.4 is released & be sure that you aren't buying into trouble by getting feedback from those who know from *experience*.

If you have to use Catalyst until the Ubuntu 10.10 release before you can go OSS, that's not such a problem is it?  You'll get better 3D out of Catalyst in these early stages of OSS ATi GPU driver development, anyway. 

> **KingBongo said:**
> 
I will be looking into the link you posted.

Hopefully there is some helpful info' there.

I'll post a question asking if anyone is using an AGP version of those two cards you are interested in & see what we get back?  It won't necessarily come back quickly, as the Arch forum is tiny by comparison to this one.  Actually, I think most forums are tiny by comparison to this one. ;)

---

### Post by KingBongo on 2010-03-17
handy:
Thank you for all your help. Really!

---

### Post by Kazade on 2010-03-17
Just thought I'd update everyone on my experience. I've been running Lucid + 2.6.33 + the xorg-edgers driver for about 2-3 weeks now and I haven't found a SINGLE problem. Nothing. Not a graphical glitch or an app that ran too slow, it even seems to run Blender fine (although I have only started the program and manipulated a few objects).

Of course I haven't tried anything crazy, like running Doom 3 on full graphics. Yet. 

I am wondering though, what is holding back the performance of the OSS drivers? Is there some key feature missing that when implemented will jump up the performance?

Luke.

P.S.

< spellingnazi > 
@handy "coming" is spelt with a single "m" :)
< /spellingnazi >

---

### Post by sdowney717 on 2010-03-17
How well does google earth run?

---

### Post by nomadewolf on 2010-03-17
> **KingBongo said:**
> Wonderful thread! Maybe there is some hope for ATI/AMD on Linux :) Here is my story:

About 6 months ago the graphics card (AGP) in my P4 blew up. I decided to buy an Nvidia because of compatibility problems with some of the best ATI/AMD cards and Linux. I bought an Nvidia clone (I believe), brand new from eBay, a 7950GT AGP. That is probably the best single-slot card Nvidia ever made for the AGP bus. It worked great for about three months until it suddenly died. I sent it back and got a new one. The new was absolutely dead from the beginning. I am through with these Nvidia clones :p

So now I am looking for a new card. The relatively newly released AMD HD4650/HD4670 AGP is really interesting (HDMI for example)! If only it works I would be happy with it for years. I have a few questions some good guys could maybe answer.

1. Will I be able to make the HD4650 or HD4670 work with Ubuntu 10.04? This is critical. I have some BAD experience with the stronger but older HD3850. I never could make it work. I am scared for the HD3850/HD3870 :p

2. The difference between the HD4650 and the HD4670 seems to be mainly better memory on the later one, and slightly higher clocking frequency. Is it worth it on the P4 (3.06GHz, 2GB RAM)? 

3. How does the HD4650/HD4670 compare performance wise with Nvidia 7950GT? Not a really big issue, since the 7950GT already seems to be overkill for the P4 and for what I used it for. Good to know anyway. 

4. I am using the computer together with an older TV. I really need S-Video, or at least I think so. The HD4650/HD4670 doesn't have S-Video out. Will I be able to use an adapter and convert any of the present outputs to S-Video? Do the hardware and drivers support that?

I really would appreciate some help! Please remember I am talking about AGP cards. And no, I am not buying some other computer :)

1. The OSS drivers are pretty advanced, so they should be completed already this year. So if you card doesn't work, it WILL work... Also, it's a mid end card, and those have higher chance to work.

2. A more powerful card is always worth it IMO. But, you have to look at the price, and have in mind that it's basically the same card with higher specs, that you can over-clock manually...
Also, what does MOST of the work in games is the card, so, the faster the better. A P4 would hardly be a hog...

3. Basically, Nvidia compare to ATI cards like this:
    You have an ATI card, let's say 4650
    And the NVidia 7950GT
    You want to compare the second digit of the number, in this case 6 for ATI and 9 for the NVidia. So, NVidia is a higher end card and should be better. BUT the 7950 is old, and used to compete with the HD2900 series, so the ATI is 2 generations younger, so it might actually be faster, cause it's built in a better manufacturing process and has a better architecture...
Anyways, i would definitely go with the ATI in this case.
There are other tricks to check out the performance of the cards without testing them, but it's matter of self education...

4. There are numerous adapters, i'm pretty sure you can convert maybe all your outputs to S-Video, but nothing like googling the cables you need.
No specific hardware or software is needed for that. Just plug the cables and you're good to go.

---

### Post by handy on 2010-03-17
> **Kazade said:**
> ...
I am wondering though, what is holding back the performance of the OSS drivers? Is there some key feature missing that when implemented will jump up the performance? 

The coding isn't finished yet.

My understanding is that it is a small team of guys doing all the work, & they have had & do still have lots to do.

The tech' info' for the Evergreen (current) chip sets have only recently been released by AMD, so they have quite some catching up to do.  Though I must say the guys are not hanging around, they are making good progress even on Evergreen.

> **Kazade said:**
> 
@handy "coming" is spelt with a single "m" :) 

Yes I know, I corrected it some time ago on the original post, if I remember correctly; unfortunately doing so doesn't change the spelling of all of the titles that followed. :)

---

### Post by KingBongo on 2010-03-17
nomadewolf:
Thank you! Great reply. I already noted from the Arch forum that the RV7xx seem to be working already, with some tweaks. If you are using the right kernel (and maybe other things as well) that is. I am already using Ubuntu 10.04 (kernel .32) so that one is covered.

I noted one thing though. You say that using an adapter for S-Video should work, but handy says it will probably not work ;) Who is right and who is wrong? Yes, I am trying to start a fight amongst the two of you :D

---

### Post by handy on 2010-03-17
> **KingBongo said:**
> 
I noted one thing though. You say that using an adapter for S-Video should work, but handy says it will probably not work ;) Who is right and who is wrong? Yes, I am trying to start a fight amongst the two of you :D

I'm probably wrong. If you want to verify that you can buy an adapter, then search for one in one of the major online stores, if you can find one then you know that you can probably do it, if you can't find one, then even if it can be done you may have trouble doing it. :)

As far as kernel .32 & the open driver support for ATi GPUs is concerned, it works, & quite nicely, but it is still quite limited with regards to fps & complex 3D games & no power management.  Some games work better than others.

If you want to get the best out of your ATi GPU via the open solution, you will want to move into later versions of the kernel & the other associated packages, which you can do.

I've just added a how-to to the Ubuntu section of the first page of this thread, for anyone that is interested.

---

### Post by KingBongo on 2010-03-18
handy:
Thank you! Maybe I will give the HD4650/HD4670 a shot then. I am only using the computer for movies anyway, that's 2D right? If I understand it correctly 2D already works fine.

As always, Apple is my friend ;) Adapter,
[http://store.apple.com/us/product/M9267G/A](http://store.apple.com/us/product/M9267G/A)

---

### Post by handy on 2010-03-18
> **KingBongo said:**
> handy:
Thank you! Maybe I will give the HD4650/HD4670 a shot then. I am only using the computer for movies anyway, that's 2D right? If I understand it correctly 2D already works fine.

As always, Apple is my friend ;) Adapter,
[http://store.apple.com/us/product/M9267G/A](http://store.apple.com/us/product/M9267G/A)

Yep, the 2D & movie playing is of superior quality to that of Catalyst, so your on a winner. :)

On another note:-

**ATI Kernel Power Management Moves A Bit More:** 

*On Sunday we reported that ATI in-kernel power management was moving along after AMD's Alex Deucher spent some time in recent days building upon Rafa&#322; Mi&#322;ecki's initial power management support. Alex's patches added GUI idle IRQ support, support for changing the GPU clocks when the engine is idle, support for turning down the number of active SIMDS when running in a lower power stage for the ATI R600 ASICs and later, and new ASIC specific callback functions. This morning though he's taken the support a bit further. *

For more:

[http://www.phoronix.com/scan.php?page=news_item&px=ODA3Mw](http://www.phoronix.com/scan.php?page=news_item&px=ODA3Mw)

---

### Post by Kazade on 2010-03-19
OK, I've noticed a couple of issues with the OSS drivers:

1. Flash is damn slow, any slightly complex site drops to around 1 FPS
2. I tried running a game in Wine and started getting GL_INVALID_ENUM from a call to glDrawArrays - My guess is that it's because the driver only supports EXT_framebuffer_object rather than ARB_framebuffer_object. I haven't researched which enum it is attempting to use so I could be wrong, my guess is based on the fact that switching Wine's offscreen rendering from fbos to pbuffer makes the game run (albeit slowly).

---

### Post by handy on 2010-03-19
I've read that people have problems with Wine gaming.  I can't speak from experience as I'm not currently using Wine for games.

Hopefully the problem will get attention before too long. 

Perhaps this problem is down in the priority list for the team working on the drivers.  They may want to get the GPU driver support somewhere near finished before giving attention to bugs like this one?

I'll see if anyone knows what the problem is between Wine & the OS drivers in the Arch forum, I'll post if I get a useful reply.

---

### Post by Ubuntiac on 2010-03-19
> **Kazade said:**
> Flash is damn slow, any slightly complex site drops to around 1 FPS

Really? I haven't noticed that at all...

---

### Post by Kazade on 2010-03-19
> **Ubuntiac said:**
> Really? I haven't noticed that at all...

It might be a problem with flash... I'll try reinstalling it tonight.

---

### Post by handy on 2010-03-19
Flash works ok for me too.

Another phoronix article re. the new Catalyst:

[I]**Ubuntu Gets Another ATI Catalyst Driver Handout:**

Well, to no surprise the trend of Ubuntu receiving unreleased  Catalyst drivers  has continued. Since Ubuntu 8.10, AMD has had to supply Canonical with early Catalyst drivers not otherwise publicly available so that they could ship with support for their binary Catalyst driver within the operating system's package repository.[/I] 

For more:

[http://www.phoronix.com/scan.php?page=news_item&px=ODA4MA](http://www.phoronix.com/scan.php?page=news_item&px=ODA4MA)


For Arch users, ViOLO has extracted the new Ubuntu Catalyst 10.4 packages & installed it on Arch & it works well. :)  

As I write this he is working on creating a 64bit version, so they should both be in AUR today, which is good news for those that would like to upgrade their xorg-server to 1.7, & the other associated packages that you would have had to be blocking in pacman due to the previous two versions of Catalyst only being compatible with xorg-server 1.6. Though the joy will be short lived as xorg-server 1.8 is due out soon. :confused:

***[Edit:]** For Arch users, ViOLOs packages are called catalyst-beta 10.3-333, until the true 10.4 versions are released in April. They are now available via the AUR.*

---

### Post by KingBongo on 2010-03-20
Does anybody know if the ATI HD3850 AGP card will fully (and easily) work with the OSS driver when they are completed? Or maybe with catalyst? Maybe one of them work already, didn't check.

About a year ago I tried to make one of these cards work, but failed. It would be nice for others playing with it right now to know.

---

### Post by handy on 2010-03-20
> **KingBongo said:**
> Does anybody know if the ATI HD3850 AGP card will fully (and easily) work with the OSS driver when they are completed? Or maybe with catalyst? Maybe one of them work already, didn't check.

About a year ago I tried to make one of these cards work, but failed. It would be nice for others playing with it right now to know.

That card is supported by AMD/ATi, so Catalyst will work.

The forthcoming version of Catalyst (as mentioned in previous post) seems to be a good one (made to time with the next release of Ubuntu, as AMD supports Ubuntu).

As far as the open-source support is concerned, it should already be supported.

See if you can find a supplier/shop that will sell you the card on the proviso that if it doesn't work you can bring it back & buy a more expensive model.  You never know such a plan might work, it would in my small country town. :)

Really, the only doubt in my mind is that it is AGP, & I know from experience that, that can cause problems. Hopefully X.org has developed beyond those problems now, I know it has re. my nVidia 7950GT AGP card which was a horror to deal with in the past.

---

### Post by handy on 2010-03-20
Feedback on the Arch forum is making the forthcoming Catalyst sound like the best Linux version ever released for the ATi GPUs. 

So far, all those who have tested this pre-release for Ubuntu version of Catalyst, on Arch, have had nothing but positive things to say.

This is probably the first time such positive feedback has ever happened with an fglrx/Catalyst release.  

Such a dramatic change from the normal disappointment that accompanies the fglrx/Catalyst releases is certainly most welcome by all & quite a surprise to most of us. :)

Thus far the word is all of the following are working well & they apparently were not:

Kwin
Quake4
Neverwinter Nights 1, at highest settings
No Compiz crash on maximise
Eschalon Book I

---

### Post by handy on 2010-03-20
timong, on the Arch forum has managed to get the Ubuntu pre-release version of Catalyst to work with xorg-server 1.8. a bit of a hack, but even so, this is very good news for those people who know who they are. :D

Quote from Timong:

*right now i'm running kde + kwin + catalyst-beta (ubuntu) + xorg 1.8 *

***[Edit:]** He added later that games work fine too. :)*

---

### Post by handy on 2010-03-20
The people over on the Arch forum that are testing the Ubuntu pre-release version of Catalyst are really, really happy with its performance.

It is the first time I have ever seen the people in that thread not bitching about the AMD/ATi poor drivers.

Really fast game speed, great video, Kwin, & on it goes.

AMD has & is going to make a LOT of people happy with this next Catalyst release it would seem. :D

Most of us are thinking that it is about time.

---

### Post by Kenny_Strawn on 2010-03-20
Will the beta version of the Catalyst driver work with the VisionTek ATI Radeon HD 2400 Pro PCI? That's my card for you. It's an RV610-based card.

---

### Post by handy on 2010-03-21
> **Kenny_Strawn said:**
> Will the beta version of the Catalyst driver work with the VisionTek ATI Radeon HD 2400 Pro PCI? That's my card for you. It's an RV610-based card.

My understanding is that Catalyst works with the R600, R700 & the Evergreen series of GPUs, but it no longer supports the earlier series. Your card fits into the R600 category so it should be supported. From what I've read they bought your card out in PCI, AGP & PCIe x16, so I would think it should be good to go.

The full version will be released with the next version of Ubuntu anyway, so if your a Ubuntu user you won't have long to wait.

I'm not sure if kernel .32 is essential, also xorg-server 1.7 & the associated packages?

If you wanted to install this pre-release Catalyst you may have to use the procedure in the how-to in the Ubuntu section of the first page of this thread to be able to upgrade your kernel & other packages.

---

### Post by pirlo89 on 2010-03-21
hi,

Im buying a new laptop (sony vaio e series) that comes with ATI Mobility Radeon™ HD 5470. And i  couldn't  find the driver on their website. Do you know when will it be available for ubuntu? will it work when ubuntu 10.04 is released ?

---

### Post by handy on 2010-03-21
> **pirlo89 said:**
> hi,

Im buying a new laptop (sony vaio e series) that comes with ATI Mobility Radeon&#8482; HD 5470. And i  couldn't  find the driver on their website. Do you know when will it be available for ubuntu? will it work when ubuntu 10.04 is released ?

The AMD/ATi closed source drivers called Catalyst will support it & the open-source solution for the Evergreen series (which yours is a part of) is developing fast, but is a long way behind the open-source drivers for the earlier series of ATi GPUs, as AMD released the tech' info' for Evergreen last of all.

So Catalyst will have to do the job for you until the open-source drivers are good enough. :)

In Ubuntu you will have to enable the *medibuntu* repository that holds the closed source packages so that you can then easily install it. A search for a how-to in Tutorials & Tips sub-forum should give you what you need.

---

### Post by pirlo89 on 2010-03-21
> **handy said:**
> The AMD/ATi closed source drivers called Catalyst will support it & the open-source solution for the Evergreen series (which yours is a part of) is developing fast, but is a long way behind the open-source drivers for the earlier series of ATi GPUs, as AMD released the tech' info' for Evergreen last of all.

So Catalyst will have to do the job for you until the open-source drivers are good enough. :)

In Ubuntu you will have to enable the *medibuntu* repository that holds the closed source packages so that you can then easily install it. A search for a how-to in Tutorials & Tips sub-forum should give you what you need.


Thank you very much :D

---

### Post by handy on 2010-03-21
[I]**Radeon 3D Performance: Gallium3D vs. Classic Mesa:**

Gallium3D, the graphics driver architecture started by Tungsten Graphics to overhaul the hardware driver support in Mesa, has been around for a few years but it is finally getting close to appearing on more desktop systems. Now that the Nouveau DRM code is in the mainline Linux kernel and its main 3D driver is Gallium3D-based, we will hopefully be seeing that adopted by more distributions soon -- it's already being flipped on with Fedora 13. On the ATI side the "r300g" Gallium3D driver that provides Gallium3D support for the R300-R500 (up through the Radeon X1000 series) is also being battered into surprisingly good shape. To see where the Radeon Gallium3D support is at for these older ATI graphics cards we have run a set of tests comparing the OpenGL performance under the latest Mesa 7.9-devel code with the Gallium3D driver to running the classic Mesa DRI driver.[/I]

For more:

[http://www.phoronix.com/scan.php?page=article&item=gallium3d_r300g&num=1](http://www.phoronix.com/scan.php?page=article&item=gallium3d_r300g&num=1)

---

### Post by yodermk on 2010-03-23
Just pulled the trigger and updated to Lucid to get Free 3D on my 3200HD (*finally*). It definitely works. My verdict for my three most important uses of 3D:

* Destop Effects: A bit more jumpy than I would really like to see, but definitely work. Much smoother on my Fedora system at work with an nVidia and its binary blob. Not sure if the jumpiness here is due to the low end card (doubt it) or the newness of these drivers. How much better would it be if I had, say, a 4850? Should Lucid+1 improve it significantly?

* Google Earth. Yep, it works. Fairly well.

* Extreme Tux Racer. Ditto.

EDIT: Reading back a couple weeks I see that Kazade had much more success with 2.6.33. Nice. Will have to look into updating to that, though I feel a bit more comfortable with distro kernels.

---

### Post by Ubuntiac on 2010-03-23
> **yodermk said:**
> * Destop Effects: [..] How much better would it be if I had, say, a 4850?

On my 4850 they look silky smooth, indeed. I'm sure refinements in the drivers though will get this kind of performance on lower and lower end cards over time though. I'm also on Kubuntu, and thus using KDE's desktop effects, not compiz's.

The only thing I've noticed is that some games don't seem to like this driver (like Savage 2). I have a hunch that it may be because they require glsl which hasn't been fully implemented yet...

---

### Post by handy on 2010-03-23
The quakeio engine based games work really well, as it is apparently an easy engine on the GPU.

---

### Post by KingBongo on 2010-03-23
Does anybody know (generally) how the old PCI interface (not PCIe) is supported when it comes to graphics cards? Good or bad?

---

### Post by handy on 2010-03-23
> **KingBongo said:**
> Does anybody know (generally) how the old PCI interface (not PCIe) is supported when it comes to graphics cards? Good or bad?

The drivers are made to support the various series of GPUs. I would think that if the GPU is supported then that's it. 

Though as previously mentioned in this thread, you may have to muck about with the xorg.conf to get it to work.  Though that has not been the case with my nVidia AGP card with a PCIe GPU on it anymore; & that is with the proprietary nVidia drivers.

Really, the only way to know if your card is going to work is to try it.

---

### Post by yodermk on 2010-03-24
Another question -- you've said that the power management is not working yet but will be in 2.6.34. However I'm wondering what you mean by that.  Do you mean the card's ability to put the monitor in suspend mode?  Or some other ability of the card to save power?

I had always assumed the later, but after the upgrade, my monitor no longer goes to sleep. That kind of stinks. Wasn't sure if that's what you meant by power saving issues.

---

### Post by handy on 2010-03-24
> **yodermk said:**
> Another question -- you've said that the power management is not working yet but will be in 2.6.34. However I'm wondering what you mean by that.  Do you mean the card's ability to put the monitor in suspend mode?  Or some other ability of the card to save power?

I had always assumed the later, but after the upgrade, my monitor no longer goes to sleep. That kind of stinks. Wasn't sure if that's what you meant by power saving issues.

All of which you speak is starting to happen in kernel .34, but it won't be finished for a while.

What I mean is the ability to have multi-stage GPU & its dedicated RAM, stages of power usage.  Which equates to quieter systems that use less energy, which is of course most useful for notebook users.

Sleep & what have you is part of the game also.

Kernel .34 is the beginning of PM for the ATi GPUs, the development will go on for a while before we get to the stage where we don't even think about it anymore, because we just take it for granted... ;)

Have a look at the last 5 or so pages of this thread to get an idea of what is going on with kernel .34 & the associated packages relating to ATi GPU support:

[http://bbs.archlinux.org/viewtopic.php?pid=730280#p730280](http://bbs.archlinux.org/viewtopic.php?pid=730280#p730280)

---

### Post by Kazade on 2010-03-24
> **handy said:**
> 
Have a look at the last 5 or so pages of this thread to get an idea of what is going on with kernel .34 & the associated packages relating to ATi GPU support:

[http://bbs.archlinux.org/viewtopic.php?pid=730280#p730280](http://bbs.archlinux.org/viewtopic.php?pid=730280#p730280)


Is it just me that gets this message when I go to that link?

> 
You are banned from this forum. The administrator or moderator that banned you left the following message:

Spam

Please direct any inquiries to the forum administrator at [email]simo@archlinux.org[/email].


I've never been to that forum in my life!

---

### Post by handy on 2010-03-24
Yes it's just you!? 

Perhaps you ISP has given you an IP that was banned from the Arch forums?

Try this link?

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

---

### Post by Untitled_No4 on 2010-03-24
The open source drivers on cause my system to overheat quite badly. Now that 10.04 has the fglrx drivers I've tested and confirmed that the issue is related to the open source drivers. Basically, with fglrx drivers my system runs at around 35c - 40c, but with the open source drivers the coolest it gets is 50c but it often goes even higher.

Does anyone have any information about this? A Google search didn't really return any helpful results.

Edit: my GPU is Mobility Radeon HD 3650

---

### Post by handy on 2010-03-24
Power management for the ATi GPUs has only just started to be implemented with kernel .34, & it is working, though not completely at this stage. So the solution is on the way, I expect Ubuntu will have it by 10.10. hopefully.

---

### Post by handy on 2010-03-25
[I]**Woah, AMD Releases OpenGL 4.0 Linux Support!**

Posted by Michael Larabel on March 25, 2010

Woah, here comes a pleasant surprise from AMD with their Catalyst Linux driver. AMD yesterday released a Catalyst 10.3 Linux driver that really didn't bring anything too exciting (and it still doesn't support X.Org Server 1.7), but today they've delivered a new preview driver that's based on Catalyst 10.3 and it brings OpenGL 3.3/4.0 support! [/I]

For more:

[http://www.phoronix.com/scan.php?page=news_item&px=ODEwMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODEwMQ)

---

### Post by Ubuntiac on 2010-03-26
Sweeeeeeeeeeeeeeeeeeeeeeeeeeeeet! :D

---

### Post by iRiUX on 2010-03-26
I installed ati open-source drivers yesterday on my ATI 4570 on Kubuntu 10.04, Man this thing has improved so much. I didn't consider using the open-source instead of catalyst until now, last time I tried it (several months ago) I found flaws which I didn't like. But this, lol... my desktop is so snappy, I'm not used to this experience even with my catalyst.

I don't know whether its due to the new kernel/kde 4.4.1 or whatever, but this thing is fast. Everything is millisecond responsive. I have tried 1080p flash video, I can't believe its more responsive than Catalyst... wtf, lol.

glxgears shows 730 FPS with composition enabled, that's nearly three times less than catalyst, but this driver is so much more responsive, don't know why. glxinfo:
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV710 9553) 20090101  TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1-DEVEL

I just tried two games (Heroes of Newerth and Savage 2), they don't run. So basically that's the major downside of this driver. So I advice those who don't play such heavy games to install the open-source drivers instead, you wont' regret:
sudo aptitude install xserver-xorg-video-ati

---

### Post by mintochris on 2010-03-26
I can't get any compositing enabled on 10.04 at the moment - ati 9600XT, so you can count yourself lucky!

---

### Post by iRiUX on 2010-03-26
> **mintochris said:**
> I can't get any compositing enabled on 10.04 at the moment - ati 9600XT, so you can count yourself lucky!

First time I installed it (yesterday) I couldn't enable composition either, I thought it didn't support it. It was due to fglrx not being removed properly I think, or due to me install everything in terminal. I went into terminal and erased every trace of fglrx and the open-source drivers, then I installed it again. Now it works perfect. :D

Went to /usr/share/ati and sudo sh fglrx-uninstall.sh

Also sudo aptitude purge fglrx xserver-xorg-video-ati

When removing fglrx, it noted that the directories of ati were not empty, so it won't remove them, I rm -rf'd them all, then

Also sudo aptitude install xserver-xorg-video-ati

---

### Post by Redache on 2010-03-26
I've noticed a vast improvement as well. I have a HD3450 in my Laptop, and that now runs much better with the Open Source Drivers. The HD4870 in my Desktop also appears to be better as well.

Now all I need is a fix for Flash + Compositing and I'd be very happy.

---

### Post by handy on 2010-03-26
I've had a thread running on this topic since last August: :)

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

& I agree the improvements just keep on coming. I'm using kernel .34-git the other required packages are -git also. Power management is being implemented in kernel .34, which is nice.

---

### Post by Mark Phelps on 2010-03-26
> **handy said:**
> [I]**Woah, AMD Releases OpenGL 4.0 Linux Support!**

Just so I understand the announcement ... these changes are NOT to the open source drivers, right?

---

### Post by handy on 2010-03-26
> **Mark Phelps said:**
> Just so I understand the announcement ... these changes are NOT to the open source drivers, right?

No, not at this stage.

This thread is primarily concerned with the open-source drivers but also with Catalyst & any contributors (especially AMD, who are doing a lot, particularly for the open-source stuff) that are helping in the the development of both.

---

### Post by Ubuntiac on 2010-03-26
Hey, does anyone know if there's a way to switch between Catalyst and ATI as easily as easily as between Kernel versions at Grub. I'm loving the ATI driver and would like to be able to help by filing bugs. I'm missing Savage2 though... :(

I know that you can change the string in xorg.conf, but my understanding is that you'd also need to install and uninstall driver stuff every time.

---

### Post by handy on 2010-03-26
> **Ubuntiac said:**
> Hey, does anyone know if there's a way to switch between Catalyst and ATI as easily as easily as between Kernel versions at Grub. I'm loving the ATI driver and would like to be able to help by filing bugs. I'm missing Savage2 though... :(

I know that you can change the string in xorg.conf, but my understanding is that you'd also need to install and uninstall driver stuff every time.

If you have a search, (Ubuntu forums, games I think?) there is a thread where a guy wanted to be able to easily switch xorg.conf , with some suggestions he wrote a script that worked beautifully.

If you can find that thread you are in, as he took care of the incompatible files very nicely.

If you find it could you please post the link here for future reference?

Good luck. :)

---

### Post by Ubuntiac on 2010-03-27
Well, I looked and I looked. I found plenty of people running scripts to swap between a single and a dual monitor setup, but nothing to toggle between fglrx ant ati. :(

---

### Post by handy on 2010-03-28
> **Ubuntiac said:**
> Well, I looked and I looked. I found plenty of people running scripts to swap between a single and a dual monitor setup, but nothing to toggle between fglrx ant ati. :(

Sorry, I should have bookmarked it.

Have you searched for a solution via Scroogle?

---

### Post by Ubuntiac on 2010-03-28
> **handy said:**
> Have you searched for a solution via Scroogle?

Heh heh. Someone after my own thinking. Yes, in fact, I did search with Scroogle (and Cuil). :)

The closest I found was this:
[http://ubuntuforums.org/showthread.php?p=8909615](http://ubuntuforums.org/showthread.php?p=8909615)

Which was for switching between FGLRX and Nvidia. Close, but I have no idea what's different between the ATI / FGLRX / Nvidia drivers... :-/

---

### Post by handy on 2010-03-28
> **Ubuntiac said:**
> Heh heh. Someone after my own thinking. Yes, in fact, I did search with Scroogle (and Cuil). :)

The closest I found was this:
[http://ubuntuforums.org/showthread.php?p=8909615](http://ubuntuforums.org/showthread.php?p=8909615)

Which was for switching between FGLRX and Nvidia. Close, but I have no idea what's different between the ATI / FGLRX / Nvidia drivers... :-/

That link is to the thread I was thinking of. Sorry, my memory let us down.

I think that it is very likely possible to modify the script to do what you want, but I'm not up for it. My scripting & programming peaked in my Amiga days about 15 or so years ago. ;)

[I]**[Edit:]** I was just thinking that it really would be very useful for what I expect to be a growing number of users to be able to choose from the Grub menu, between the open-source & the proprietary drivers.

I hope someone with the knowledge takes this problem up & solves it for the community. It will encourage many more users to try the open-source drivers I think, & many who only use the open-source drivers would be happy to be able to easily switch to Catalyst when the need arises.
[/I]

---

### Post by iRiUX on 2010-03-28
My review of the Open-Source drivers after trying it out for a few days:

Specs and 'benchmark':

Card: ATI 4570
OS: Kubuntu 10.04
Driver info: 1.5 Mesa 7.7.1-DEVEL
GLXGEARS:
780 FPS (Composition Enabled)
1316 FPS (Composition Disabled)

**Desktop Experience:** (Open-Source wins this one)
Excellent, its extremely snappy, its faster than any catalyst I've tried (I've tried them all since verion 9.x until 10.4 beta. Composition is also enabled, all animations work perfectly. In catalyst I experience a slight delay when maximizing or minimizing a window, also changing window size can sometimes not go smoothly, this all goes very smoothly with the open-source drivers.

**Video Experience:** (Open-Source wins this one)
Excellent, extremely snappy again, not what I'm used to even with catalyst. The annoyances I had with catalyst were especially when maximizing/minimizing video, changing size of video, etc. It would always lag with catalyst, but not with the open-source driver. I click and it jumps to full screen the moment I click, same with making it smaller. Also with catalyst I experience tearing in fast moving video, which I find VERY annoying. I've tried 1080p Flash and normal video, very snappy, no lag at all.

**Games Experience:** (Catalyst wins this one)
The open-source drivers will not play your heavy games, at least they don't even start on my computer. I've tried Savage 2 and Heroes of Newerth, all the other games you'd find in the repositories will work.

**Power Management?:** (Catalyst wins this one)
The open-source drivers make my laptop warmer and I hear the ventilator, which I normally don't hear. This must be due to improper or lack of power management, I don't know.

**Distro/latest stuff support:** (Open-Source wins this one)
If you want to upgrade to the latest kernel and I don't know what, your only option to use a driver without hacks and what not, will be the open-source one. Catalyst 10.4 beta didn't work for me in Kubuntu 10.04, according to some it works though... for me, this one is also for open-source.

**Conclusion:** I'm only worried about the power management. If they fix that, I'm going to stay with the open-source drivers permenently. I don't play the heavy games anymore anyway since Im too busy and it takes away too much of my time. :)

If you want to install it, you can install it with the following command: **sudo aptitude install xserver-xorg-video-ati**

Anyone know when the new open-source drivers will be released?

---

### Post by Xbehave on 2010-03-28
> **iRiUX said:**
> **Power Management?:** (Catalyst wins this one)
The open-source drivers make my laptop warmer and I hear the ventilator, which I normally don't hear. This must be due to improper or lack of power management, I don't know.

[2.6.33]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/") had power management improvements, i think they are being improved in .34

---

### Post by handy on 2010-03-28
kernel .34, & the associated packages, as far as the ATi open-source drivers are concerned, seems to be primarily about power management. 

It is happening; from what I read this morning on the Arch forum, there was a great leap forward in the most recent -git packages, in both PM & 3D speed. :D

I don't know, but I expect Ubuntu will use kernel .34 in 10.10?

Though there is a how-to for using development packages in the Ubuntu Stuff section of the first page of this thread.

---

### Post by Xbehave on 2010-03-28
> **handy said:**
> I don't know, but I expect Ubuntu will use kernel .34 in 10.10?
The .34 release cycle just started and while kernel releases are not time based, they tend to be every 3/4 months so .34 should be out well before 10.10 starts freezing stuff at the end of june. Im not sure on which freeze decides on the kernel version and it's possible that .35 will be out before the FeatureFreeze. Hopefully by .35 Power saving will work better than catalyst because i think KMS and processor scheduling can give it a real edge over catalyst which only deal with powersaving on the card.

---

### Post by handy on 2010-03-28
Ubuntu tends to be a little behind with the kernel versions it uses, this must be due to the Ubuntu development schedule. 

I'll be surprised if 10.10 is using kernel .35, we can hope.

I think people are going to be quite impressed with the PM that comes with kernel .34.

---

### Post by handy on 2010-03-29
[I]**S3TC Support For Mesa Brought Up Again**

Posted by Michael Larabel on March 28, 2010

Besides the Mesa 7.8 release announcement hitting the Mesa mailing list over the weekend, also catching our interest is a new discussion concerning S3TC texture compression in this open-source software stack. One of the developers working on Spring RTS, an open-source real-time strategy game engine for Linux and Windows, is wanting the open-source Mesa developers to implement S3TC texture compression/decompression. But this is a rather sticky situation.
[/I]

For more:

[http://www.phoronix.com/scan.php?page=news_item&px=ODEwOQ](http://www.phoronix.com/scan.php?page=news_item&px=ODEwOQ)

---

### Post by iRiUX on 2010-03-29
1) Why is the power management stuff in the kernel rather than in the driver itself?
2) Where do I get the new 7.8 drivers that were released (any deb packages? :D)
3) There are deb packages for kernels that get released and I've upgraded the kernel before, but since you then cannot use catalyst anymore, it must be worth the upgrade. Also, kernel x.34 will be available on ubuntu via backports, so its even easier.

---

### Post by iRiUX on 2010-03-29
> **iRiUX said:**
> 1) Why is the power management stuff in the kernel rather than in the driver itself?
2) Where do I get the new 7.8 drivers that were released (any deb packages? :D)
3) There are deb packages for kernels that get released and I've upgraded the kernel before, but since you then cannot use catalyst anymore, it must be worth the upgrade. Also, kernel x.34 will be available on ubuntu via backports, so its even easier.

Nevermind I found it:
[ftp://freedesktop.org/pub/mesa/7.7.1/](ftp://freedesktop.org/pub/mesa/7.7.1/)
[ftp://freedesktop.org/pub/mesa/7.8/](ftp://freedesktop.org/pub/mesa/7.8/)

---

### Post by iRiUX on 2010-03-29
I need some help compiling this thing. I did **make linux-dri-x86-64** and it went on without any errors, the following files were created in lib64:

```
egl_glx.so       egl_x11_vmwgfx.so  libEGL.so      libGL.so      libGLU.so             libGLw.so        mach64_dri.so  r200_dri.so    savage_dri.so
egl_x11_i915.so  i915_dri.so        libEGL.so.1    libGL.so.1    libGLU.so.1           libGLw.so.1      mga_dri.so     r300_dri.so    tdfx_dri.so
egl_x11_i965.so  i965_dri.so        libEGL.so.1.0  libGL.so.1.2  libGLU.so.1.3.070800  libGLw.so.1.0.0  r128_dri.so    radeon_dri.so  unichrome_dri.so
```

Then I did **sudo make install** and at the end it gives an error:

```
make[2]: Entering directory `/home/iriux/Downloads/Mesa-7.8/src/glu'
/bin/sh ../../bin/minstall -d /usr//lib64
/bin/sh ../../bin/minstall -d /usr//lib64/pkgconfig
/bin/sh ../../bin/minstall ../../lib64/libGLU.so* /usr//lib64
/bin/sh ../../bin/minstall -m 644 glu.pc /usr//lib64/pkgconfig
make[2]: Leaving directory `/home/iriux/Downloads/Mesa-7.8/src/glu'
make[2]: Entering directory `/home/iriux/Downloads/Mesa-7.8/src/glw'
/bin/sh ../../bin/minstall -d /usr//include/GL
/bin/sh ../../bin/minstall -d /usr//lib64
/bin/sh ../../bin/minstall -d /usr//lib64/pkgconfig
/bin/sh ../../bin/minstall -m 644 *.h /usr//include/GL
/bin/sh ../../bin/minstall ../../lib64/libGLw.so* /usr//lib64
/bin/sh ../../bin/minstall -m 644 glw.pc /usr//lib64/pkgconfig
make[2]: Leaving directory `/home/iriux/Downloads/Mesa-7.8/src/glw'
make[1]: Leaving directory `/home/iriux/Downloads/Mesa-7.8/src'
make[1]: Entering directory `/home/iriux/Downloads/Mesa-7.8/progs'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/iriux/Downloads/Mesa-7.8/progs'
```

It seems to be due to nothing being in progs folder? am i right? Does that mean the first make didnt go through well or could it still be something else?

---

### Post by handy on 2010-03-29
@iRiUX: I'm not much good to you here, as I use a system that does it all in a completely different way.

Hopefully someone who uses Ubuntu will see your post & point you in the right direction.

Did you try doing via the how-to on the Ubuntu Stuff section of the first page of this thread?

You will find it easier that way.

---

### Post by Xbehave on 2010-03-29
I can't find the guide I used (it covered radeon/mesa and kernel from git and how to use git) but, try following:
[http://www.phoronix.com/forums/showpost.php?p=77655&postcount=1](http://www.phoronix.com/forums/showpost.php?p=77655&postcount=1)
[http://psung.blogspot.com/2009/02/configuring-radeon-r600r700-devices-on.html](http://psung.blogspot.com/2009/02/configuring-radeon-r600r700-devices-on.html)
[http://dri.freedesktop.org/wiki/Building#head-f566c8a09713eaa70d3ee69a3fd44fbc043f16cc](http://dri.freedesktop.org/wiki/Building#head-f566c8a09713eaa70d3ee69a3fd44fbc043f16cc)

but I found the xorg-edgers ppa to be current enough so i don't both anymore,

---

### Post by handy on 2010-03-29
The how-to in the first post deals with using the xorg-edgers ppa.

---

### Post by ttanev on 2010-03-30
Xorg-edgers ppa is maybe the best way to try current mesa. I was very happy after the tryout yesterday with the edgers modified kernel and lucid, yet I came back to Ubuntu 9.10 and preferred fglrx due to some gaming last couple of days. Can't wait for 2.6.34.xxx kernel, because the only downside in the current "edgers" was the incredible fan noise from my Sapphire 4870 with RadeonHD driver. Really appreciate the info here, the thread saved me from the weird behavior after lucid upgrade, trying to start in "low graphics mode" and not starting X at all :)
:popcorn:

---

### Post by Twisp on 2010-03-30
> **iRiUX said:**
> Then I did **sudo make install** and at the end it gives an error:

```
make[2]: Entering directory `/home/iriux/Downloads/Mesa-7.8/src/glu'
/bin/sh ../../bin/minstall -d /usr//lib64
/bin/sh ../../bin/minstall -d /usr//lib64/pkgconfig
/bin/sh ../../bin/minstall ../../lib64/libGLU.so* /usr//lib64
/bin/sh ../../bin/minstall -m 644 glu.pc /usr//lib64/pkgconfig
make[2]: Leaving directory `/home/iriux/Downloads/Mesa-7.8/src/glu'
make[2]: Entering directory `/home/iriux/Downloads/Mesa-7.8/src/glw'
/bin/sh ../../bin/minstall -d /usr//include/GL
/bin/sh ../../bin/minstall -d /usr//lib64
/bin/sh ../../bin/minstall -d /usr//lib64/pkgconfig
/bin/sh ../../bin/minstall -m 644 *.h /usr//include/GL
/bin/sh ../../bin/minstall ../../lib64/libGLw.so* /usr//lib64
/bin/sh ../../bin/minstall -m 644 glw.pc /usr//lib64/pkgconfig
make[2]: Leaving directory `/home/iriux/Downloads/Mesa-7.8/src/glw'
make[1]: Leaving directory `/home/iriux/Downloads/Mesa-7.8/src'
make[1]: Entering directory `/home/iriux/Downloads/Mesa-7.8/progs'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/iriux/Downloads/Mesa-7.8/progs'
```

It seems to be due to nothing being in progs folder? am i right? Does that mean the first make didnt go through well or could it still be something else?
What you posted looks correct, so what is your problem?

---

### Post by handy on 2010-03-30
**@ttanev:** You can use the kernel .34 & ppa. On Arch I've been using kernel .34 -git since it first became available, it works great & you can see if the PM is functioning on your machine well enough to stick with it (it probably is). :)


On another note:

The following was posted re. Catalyst 10.4 beta in the Arch forum today by ViOLO. Some of you may find it very interesting:-

[I]10.4 beta is not alternative - its the future! smile
xserver 1.8 will arrive in a days, and catalyst 10.4 should work with it. Ofcourse not on clean 1.8 - it need a version change before compiling.

Like i wrote on phoronix forum:
(you actually should read this cuz of incoming new config order)
"I would like to confirm that this catalyst 10.4 beta works fine on xserver 1.8 - at least on yesterday's git build. The final version shall arrive soon, so i dont expect much changes here.
I have succesfuly ran it basing on krionius (aka timong) research posted mostly here: [http://bbs.archlinux.org/viewtopic.php?pid=728571#p728571](http://bbs.archlinux.org/viewtopic.php?pid=728571#p728571)
As you can see you must cheat catalyst by compiling xserver 1.8 as xserver 1.7.5.1, otherwise catalyst wont work with it cuz of xserver version mismatch.
Also with xserver 1.8 comes some changes cuz of switching to udev instead of hal - you need to create /etc/xorg.conf.d directory with additional files in it for every input device you have (otherwise your mouse/keybrd wont start).
More here: [http://forums.gentoo.org/viewtopic-p-6219864.html?sid=6bf3658fee0e9f70b4998cdf57f66731](http://forums.gentoo.org/viewtopic-p-6219864.html?sid=6bf3658fee0e9f70b4998cdf57f66731) and here: [http://who-t.blogspot.com/2010/01/new-configuration-world-order.html](http://who-t.blogspot.com/2010/01/new-configuration-world-order.html) &#8230; order.html
Plus dont add any new xserver Section into your /etc/X11/xorg.conf - this file is still used by catalyst - i mean ie dont add any Section "InputClass" into xorg.conf cuz when you do this both aticonfig and amdcccle wont start cuz of parsing xorg.conf error (just use /etc/xorg.conf.d directory for it)."

Sooo - we all own timong a beer for hes research!
Ofcourse i will prepare repo with needed files (mean patched xserver 1.8 + catalyst) as soon as 1.8 appear on arch repos.
I will repeat this message when time will come...[/I]

---

### Post by iRiUX on 2010-03-30
> **Twisp said:**
> What you posted looks correct, so what is your problem?

I think it all went right... the thing is, I restart and check and its still using the same old drivers. Its supposed to be using the new drivers according to what I read.

---

### Post by handy on 2010-03-30
> **iRiUX said:**
> I think it all went right... the thing is, I restart and check and its still using the same old drivers. Its supposed to be using the new drivers according to what I read.

Try uninstalling the old drivers?

After which you may have to reinstall the new ones.

---

### Post by Ubuntiac on 2010-03-30
I'd love to know exactly what the OSS drivers need to be able to start playing the higher end 3d games like Savage 2 / Heroes of Newerth / Doom 3 / Prey etc...

Personally I'm just hanging out for the day I can play Savage 2 on my laptop with ati foss drivers...

---

### Post by handy on 2010-03-31
> **Ubuntiac said:**
> I'd love to know exactly what the OSS drivers need to be able to start playing the higher end 3d games like Savage 2 / Heroes of Newerth / Doom 3 / Prey etc... 

My understanding is that there is a small team with a lot of coding to do, coding based on the info' released by AMD. These changes have to be integrated with changes happening in the kernel, X.org & other associated packages.

It isn't a simple task, that is for sure.  An enormous amount of time is being donated to the community by the people involved. 

Which is usually the FOSS way.

---

### Post by dabby_yo on 2010-03-31
> **Ubuntiac said:**
> I'd love to know exactly what the OSS drivers need to be able to start playing the higher end 3d games like Savage 2 / Heroes of Newerth / Doom 3 / Prey etc...

Personally I'm just hanging out for the day I can play Savage 2 on my laptop with ati foss drivers...

You can play Doom 3 with the OSS drivers.

---

### Post by handy on 2010-03-31
The quakeio engine works well with the open-source drivers.

This previously quoted link is the results of the phoronix test suite on my machine:

[http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834](http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834)

It was made on the 13-feb, using kernel .32 & the current -git packages of the time, that are required for the oss radeon support.

The first 3 games ran incredibly well, smooth & very fast busy action.

Nexuiz doesn't use the quakeio engine & wasn't running too well, at least at the resolutions tested.

---

### Post by iRiUX on 2010-03-31
I have some very good news. After compiling didn't install the drivers (I think it was due to not uninstalled the previous drivers as handy suggested), I decided to try out the xorg-edgers PPA. It has upgraded the Mesa to 7.9-Devel. Now here is the good news:

Heroes of Newerth actually runs! wtf, lol... i'm going to try it out and let you guys know its performance. I'll also try out Savage 2. If this thing actually can run these heavy games then they've really managed to make some awesome drivers.

---

### Post by iRiUX on 2010-03-31
Okay, So Heroes of Newerth works, but Savage 2 doesn't start. At low settings I can 20-22 FPS. At the settings below I get 12-17 FPS:

Also some artifacts issues, and as you can see the tree is larger than it should be. They've made quite an advancement. Screenshots taken at different resolutions because I was testing.

---

### Post by MisfitI38 on 2010-03-31
> **iRiUX said:**
> Okay, So Heroes of Newerth works, but Savage 2 doesn't start. At low settings I can 20-22 FPS. At the settings below I get 12-17 FPS:

Also some artifacts issues, and as you can see the tree is larger than it should be. They've made quite an advancement. Screenshots taken at different resolutions because I was testing.

Impressive; 12-17 fps would be unthinkable a short while ago.

---

### Post by shane2peru on 2010-04-06
OK, after much time, I finally have installed the latest Open Source drivers for my ATI Radeon HD3100 card.  I must say that the Open Source (newest drivers) are very much ahead of the proprietary ATI drivers.  Way to go Open Source guys!!!!  I'm using Lucid in beta1 right now and added the ppa to get the latest with this:

```
sudo add-apt-repository ppa:xorg-edgers
```
I also got the kernel.  I had some help from the people over at #Radeon irc channel as I wasn't sure exactly how to do that, and they gave me some added instructions to get everything setup correctly.  Works like a charm, no overheating so far!  Thanks guys of this thread!  I had serious overheating problems with normal ATI os drivers and proprietary drivers.  I'm happy to have my laptop working again!

Shane

---

### Post by xir_ on 2010-04-06
> **shane2peru said:**
> OK, after much time, I finally have installed the latest Open Source drivers for my ATI Radeon HD3100 card.  I must say that the Open Source (newest drivers) are very much ahead of the proprietary ATI drivers.  Way to go Open Source guys!!!!  I'm using Lucid in beta1 right now and added the ppa to get the latest with this:

```
sudo add-apt-repository ppa:xorg-edgers
```
I also got the kernel.  I had some help from the people over at #Radeon irc channel as I wasn't sure exactly how to do that, and they gave me some added instructions to get everything setup correctly.  Works like a charm, no overheating so far!  Thanks guys of this thread!  I had serious overheating problems with normal ATI os drivers and proprietary drivers.  I'm happy to have my laptop working again!

Shane


Could you let us know if power-saving has been introduced yet?

---

### Post by shane2peru on 2010-04-06
> **xir_ said:**
> Could you let us know if power-saving has been introduced yet?

I was told that it had.  I'm not exactly sure how to tell if it has been, but if you have instructions I would be happy to let you know.

Shane

---

### Post by xir_ on 2010-04-06
> **shane2peru said:**
> I was told that it had.  I'm not exactly sure how to tell if it has been, but if you have instructions I would be happy to let you know.

Shane

Well the way i generally do it is compare the output from powertop.

For instance with the binary driver i see a wattage of about 9 watts on my laptop.

With the OS driver i used to see about 20 watts.

But this is probably going to be a bit far for you to go just to find out.

---

### Post by handy on 2010-04-06
kernel .34-git, brings power management for ATi.

On the Arch forum I read that there are around 30 patches to add to the kernel .34-git, which Perry3D is calling kernel26.pm in his specialised for ATi open-source & pre-compiled repo.

It would seem that PM is working on some hardware & not others at this point.

Early days.

---

### Post by xir_ on 2010-04-06
> **handy said:**
> kernel .34-git, brings power management for ATi.

On the Arch forum I read that there are around 30 patches to add to the kernel .34-git, which Perry3D is calling kernel26.pm in his specialised for ATi open-source & pre-compiled repo.

It would seem that PM is working on some hardware & not others at this point.

Early days.

I've also read of phronix that the power-management wont really be comprehensive either. That the devs were looking at having about 80% of the power management of the full binary, because that last 20% is all the really complicated parts.

This is the only thing holding me off from dropping the binary right now.

---

### Post by shane2peru on 2010-04-06
> **xir_ said:**
> Well the way i generally do it is compare the output from powertop.

For instance with the binary driver i see a wattage of about 9 watts on my laptop.

With the OS driver i used to see about 20 watts.

But this is probably going to be a bit far for you to go just to find out.

Well, mine is running at 33 Watts.  I installed powertop.  Pretty neat app, never used it before, so I don't know if that is good or bad.

Shane

---

### Post by handy on 2010-04-06
Unfortunately powertop can't use the ACPI on my machine I get the following error:

*no ACPI power usage estimate available*

& I can't make much sense re. the GPU temp out of lm-sensors either.

---

### Post by handy on 2010-04-06
xorg-server 1.8 is on its way:

[http://www.mail-archive.com/arch-dev-public@archlinux.org/msg12804.html](http://www.mail-archive.com/arch-dev-public@archlinux.org/msg12804.html)

[I]**[Edit:]** The following link gives more details re. changes in xorg-server 1.8:

[http://linux.softpedia.com/get/System/Hardware/Xorg-server-30226.shtml](http://linux.softpedia.com/get/System/Hardware/Xorg-server-30226.shtml)[/I]

---

### Post by shane2peru on 2010-04-06
Ok, is power consumption based on the kernel stuff?  How can I get mine lowered?  4 watts is very good, which in turn = long battery life!  Any links?  HowTo's?  

Shane

---

### Post by handy on 2010-04-06
> **shane2peru said:**
> Ok, is power consumption based on the kernel stuff?  How can I get mine lowered?  4 watts is very good, which in turn = long battery life!  Any links?  HowTo's?  

Shane

Yes, as I have mentioned once or twice here & there, ;) kernel .34 is bringing PM to the ATi GPUs. I have read that it could be 80% effective as the other 20% is the hard stuff that will have to wait.

If you have a look a long way down [**_the OP of this thread_**]("http://ubuntuforums.org/showthread.php?t=1238129") you will find a section called Ubuntu Stuff, there is a how-to there, including links, where you can choose a kernel & install it (I'm running kernel .34-git & it works beautifully for me. There is xorg-edgers ppa repo, where you can upgrade your system beyond where Ubuntu sits.

What I don't know is whether there is a Ubuntu kernel available that has the 30 or so PM patches applied?

Following the how-to is really quite easy.

---

### Post by xir_ on 2010-04-07
> **shane2peru said:**
> Ok, is power consumption based on the kernel stuff?  How can I get mine lowered?  4 watts is very good, which in turn = long battery life!  Any links?  HowTo's?  

Shane

Well you said that it was 33 watts with the opensource ati driver. What about with the binary (it should be lower).

Also there is a ppa with some new tweaks to lower power consumption (it was proposed for lucid).

Powertop will advise you on tweaks whilst its running and can even implement them for you.



@handy
The big news with X-server 1.8 has to be the switcheroo patch set being able to switch drivers without having to restart X. This could allow Linux to have an optimums (nvidia) style power savings if you have dual graphics.

I really am excited in the way this stuff is progressing.

---

### Post by shane2peru on 2010-04-07
> **handy said:**
> Yes, as I have mentioned once or twice here & there, ;) kernel .34 is bringing PM to the ATi GPUs. I have read that it could be 80% effective as the other 20% is the hard stuff that will have to wait.

If you have a look a long way down [**_the OP of this thread_**]("http://ubuntuforums.org/showthread.php?t=1238129") you will find a section called Ubuntu Stuff, there is a how-to there, including links, where you can choose a kernel & install it (I'm running kernel .34-git & it works beautifully for me. There is xorg-edgers ppa repo, where you can upgrade your system beyond where Ubuntu sits.

What I don't know is whether there is a Ubuntu kernel available that has the 30 or so PM patches applied?

Following the how-to is really quite easy.

I meant specifically for the power management stuff, I guess I wasn't real clear on that.  Yes, I did follow that guide and am using the .33 kernel with the edgers ppa stuff also it really helped out my laptop a lot!  

> **xir_ said:**
> Well you said that it was 33 watts with the opensource ati driver. What about with the binary (it should be lower).

Also there is a ppa with some new tweaks to lower power consumption (it was proposed for lucid).

Powertop will advise you on tweaks whilst its running and can even implement them for you.



binary?  I'm not sure what you mean by that.  Do you mean the latest drivers for ati?  I'm using them and have the edgers ppa enabled.  If you mean something else, by all means do share. :)

Shane

---

### Post by ceelo on 2010-04-07
Major kudos to the open source community for their work on the open source ATI drivers. The proprietary ATI drivers no longer support my video card, but the open source driver still works flawlessly. =)

Keep up the great work!

---

### Post by Ubuntiac on 2010-04-07
> **xir_ said:**
> The big news with X-server 1.8 has to be the switcheroo patch set being able to switch drivers without having to restart X. This could allow Linux to have an optimums (nvidia) style power savings if you have dual graphics.

Are you saying that we might be able to switch between FGLRX and ATI easily soon... and that we wouldn't even need to restart X?!

That would be AWESOME! :popcorn:

---

### Post by shane2peru on 2010-04-07
DRM or not to DRM?  Here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)  I'm not sure if DRM is better or not?  I used it because someone over at the #radeon irc channel recommended it, but I don't really know what the difference is.  Any simplified explanations would be appreciated.  Thanks!

Shane

---

### Post by handy on 2010-04-07
**@shane2peru:** You will need to use kernel .34-git to have any chance of accessing power management (PM). As there is basically none for the ATi GPUs before that kernel.


*The following is not about PM, it is just for information purposes.*

I'm running kernel (2.6.34-rc2-dirty) on Arch with the other ATi GPU associated packages mostly coming from -git, here is my results when using the following command:

```
[I]handy ~  $  glxinfo |grep -i opengl
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL DRI2
OpenGL version string: 2.0 Mesa 7.9-devel
OpenGL shading language version string: 1.10
OpenGL extensions:[/I]
```

---

### Post by xir_ on 2010-04-08
> **Ubuntiac said:**
> Are you saying that we might be able to switch between FGLRX and ATI easily soon... and that we wouldn't even need to restart X?!

That would be AWESOME! :popcorn:

Well so far the patch-set worked on intel and ati (open source drivers). It was very much so a proof on concept patch.

But i cant see why if ati ever get their binary driver up to scratch why you couldn't do that.

some links
[URL="http://airlied.livejournal.com/70480.html"]http://airlied.livejournal.com/70480.html
[/URL]
[URL="http://www.phoronix.com/forums/showthread.php?t=21979"]http://www.phoronix.com/forums/showthread.php?t=21979
[/URL]

---

### Post by liedan on 2010-04-08
Hi guys.

I have Ubuntu Karmic 64bit and Ati mobility radeon HD3450 which belongs to the R600 series. I followed handy's instructions from the first post (those entitled "Ubuntu staff" ) in order to get open source 3D support. 

I downloaded and installed stable kernel 2.6.33, added and upgraded from Xorg edgers.
However, no 3D support:(

```
hollas@hollas-laptop:~$  glxinfo |grep -i opengl
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
hollas@hollas-laptop:~$ uname -a
Linux hollas-laptop 2.6.33-020633-generic #020633 SMP Thu Feb 25 10:10:03 UTC 2010 x86_64 GNU/Linux

```glxgears gives the same shitty results as before.

One thing is weird and probably related to my problem. Shortly before splash screen, i get some weird statements..something about firmware problems...i noticed similar lines about possible missing firmware when I was installing kernel...
W: Possible missing firmware /lib/firmware/2.6.33-020633-generic/radeon/R700_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/2.6.33-020633-generic/radeon/R600_rlc.bin for module radeon

Any ideas??

---

### Post by Ubuntiac on 2010-04-08
Yeah, for some reason, the packages don't seem to come with a firmware file (I'm guessing it's legals....) Anyway, you can download that one file and copy it into the path listed in your post and that should fix it. I believe there's a link earlier in this thread, so just do a search (in this thread) for the filename, download, move and you should be fine.

Weird, I know!

---

### Post by handy on 2010-04-08
> **liedan said:**
> Hi guys.

I have Ubuntu Karmic 64bit and Ati mobility radeon HD3450 which belongs to the R600 series. I followed handy's instructions from the first post (those entitled "Ubuntu staff" ) in order to get open source 3D support. 

I downloaded and installed stable kernel 2.6.33, added and upgraded from Xorg edgers.
However, no 3D support:(

...
Any ideas??

In Arch we have to use radeon_ucode, I think that is the package that covers that problem.

I'm surprised that xorg-edgers hasn't got that one covered.

Perhaps some searching & reading on the topic will solve the problem.  

If you do solve it please post how here?

I'll ask someone who might know in another forum & report back if he can help.

Also, you might like to try kernel .34, as the -git kernel is working really well currently.

---

### Post by shane2peru on 2010-04-08
> **handy said:**
> **@shane2peru:** You will need to use kernel .34-git to have any chance of accessing power management (PM). As there is basically none for the ATi GPUs before that kernel.


*The following is not about PM, it is just for information purposes.*

I'm running kernel (2.6.34-rc2-dirty) on Arch with the other ATi GPU associated packages mostly coming from -git, here is my results when using the following command:

```
[I]handy ~  $  glxinfo |grep -i opengl
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL DRI2
OpenGL version string: 2.0 Mesa 7.9-devel
OpenGL shading language version string: 1.10
OpenGL extensions:[/I]
```

hmm, when I run the .34 kernel, it runs hot, and uses less power.  When I run the .33 kernel out of the drm-next folder it runs much cooler and doesn't overheat.  So I hope they get a .34 kernel in the drm folder soon.  I don't know enough about that stuff, that is just what I have found, I have a radeon HD3100 ATI card in this laptop, so I need the dmr radeon stuff in the kernel, that seems to be the problem.

Shane

---

### Post by handy on 2010-04-09
Keep checking that Ubuntu kernel page. Hopefully they will put together a kernel .34-git, with the 30 or so PM patches for you.

---

### Post by liedan on 2010-04-09
Hi,
thanks for suggestions. I tried Ubuntiacs solution. I downloaded the file R600_rlc.bin from here: [HTML]http://sourceforge.net/mailarchive/forum.php?thread_name=a728f9f90911301058j180e66eaofc60d3166cef5b0%40mail.gmail.com&forum_name=dri-devel  [/HTML]I copied it to a folder  /lib/firmware/2.6.33-020633-generic/radeon/  ,rebooted and...nothing. no change. Reinstalling xorg did not help either. Now i really dont know what to do.

Before splash screen, i get following errors:

[ .000000] [FirmwareWarn ]: MTTR : CPU 0: SYSCFG[MtrrFixDramModEn]  not cleared by BIOS.clearing this bit
[0. 310171]  [FirmwareWarn ]: MTTR : CPU 1: SYSCFG[MtrrFixDramModEn]  not cleared by BIOS.clearing this bit
[]  ata3 : softreset failed (device not ready)
[]  ata1: softreset failed (device not ready)
[    2.213064] r600_cp: Failed to load firmware "radeon/R600_rlc.bin"
[    2.213133] [drm:r600_startup] *ERROR* Failed to load firmware!
[    2.213178] radeon 0000:01:05.0: disabling GPU acceleration

I' fairly sure i'm suffering from this bug: [http://www.linuxquestions.org/questions/linux-newbie-8/r600_cp-failed-to-load-firmware-radeon-r600_rlc-bin-791940/](http://www.linuxquestions.org/questions/linux-newbie-8/r600_cp-failed-to-load-firmware-radeon-r600_rlc-bin-791940/)
However, the solution inclludes recompiling the kernel, which i really don't want to do as a newbie.


> I'll ask someone who might know in another forum & report back if he can help.

Also, you might like to try kernel .34, as the -git kernel is working really well currently.     I originally wanted to install v2.6.34-rc3 version from here: [HTML]http://kernel.ubuntu.com/~kernel-ppa/mainline/     [/HTML]. However, there is only source code for Karmic and because i am a newbie, i don't know how to build a kernel from it. However, I noticed, that there is also a folder "daily" [HTML]http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/[/HTML]Do I want to install the kernel from here? If so, which version is safe to use? (from which date) 

Thank you for your help.

---

### Post by handy on 2010-04-09
I'm using kernel .34-rc2. It has no problems for me.

I'm not using the patched kernel with PM at this stage. (My machine is quiet, cool & not a Notebook)

If you go through & compile a kernel you will learn a lot. It takes quite a while to make all of the settings, but it is kinda fun, somewhat of an adventure the first time in particular.

You won't loose the kernel you are using now, you will add the new one to your /boot/grub/menu.lst file. So if you make a mistake you can choose the kernel you are using now & boot with that, which should give you some courage. :)

I'm sure that there is a compiling the kernel how-to or two on the net.  When I do it, (which isn't often) I go through & look at all of the choices, some things I know I don't need (it will be obvious to you) others I'm not sure about, so I leave them in the kernel.

Some people are somewhat obsessive compulsive about the kernel & trim it down to having only what they need & nothing more. 

These days the way the kernel is written & using relatively modern hardware there is next to no speed increase for spending all of that time organising a kernel's compilation for just your system. 

Good luck & have fun. :)

P.S. The person on the other forum didn't have an answer, he hadn't struck the problem.

---

### Post by handy on 2010-04-09
Read on the Arch forum that ViOLO & co. have got Catalyst-10.4-beta working with xorg-server 1.8. :)

---

### Post by Ubuntiac on 2010-04-09
Only someone who runs Arch (or Gentoo) could call compiling one's own kernel "fun"! ;-P

---

### Post by handy on 2010-04-09
> **Ubuntiac said:**
> Only someone who runs Arch (or Gentoo) could call compiling one's own kernel "fun"! ;-P

I didn't think Gentoo was much fun. 

Thankfully Arch uses binary packages, with the exception of the packages that come out of AUR (Arch User Repository). :)

Perry3D maintains a repo containing the latest worthwhile pre-compiled packages (including the kernel-git) for getting the best out of the ATi GPUs. For which all who use it are very grateful. :D

Compiling a kernel is an adventure for those of us that do it seldom. Though I'm certainly glad I don't have to do it every time I want to upgrade my kernel...

---

### Post by Ubuntiac on 2010-04-09
> **handy said:**
> Perry3D maintains a repo containing the latest worthwhile pre-compiled packages (including the kernel-git) for getting the best out of the ATi GPUs. For which all who use it are very grateful. :D

Interesting... I'm actually experimenting with dual booting arch+kdeMOD at the moment myself. It's the first non-*buntu distro I ever tried that I actually liked! Still learning lots though, especially with the dark art of PKGBUILD's (why do people always seem to write that in CAPS?)

---

### Post by handy on 2010-04-09
> **Ubuntiac said:**
> Interesting... I'm actually experimenting with dual booting arch+kdeMOD at the moment myself. It's the first non-*buntu distro I ever tried that I actually liked! Still learning lots though, especially with the dark art of PKGBUILD's (why do people always seem to write that in CAPS?)

PKGBUILD is its name in this case sensitive distro world we live in.

Here is the link to Perry3D's very useful/informative thread. It is my prime source of info' that I bring back here to offer to anyone that might be interested. The first post is a continually updated as needed how-to re. getting the most out of the ATi GPUs on Arch:

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

---

### Post by Ubuntiac on 2010-04-09
Thanks! That looks very, er... well, handy! :roll:

---

### Post by handy on 2010-04-10
> **Ubuntiac said:**
> Thanks! That looks very, er... well, handy! :roll:

:lolflag: As you spend time with Arch, it becomes more familiar. You'll get used the different ways of doing things & as you learn it more you are continually modifying your install, so it keeps on becoming more & more just the way you like it.  Without the interruptions/destructions that come with total rebuilds every so often. (My install is over 2 years old & very comfy ;))

On a side note, I just had a look at the first page of Perry3D's thread & thought I'll implement the PM with KMS as per the simple how-to at the bottom of the thread. (don't know why I hadn't done it ages ago really?)

It worked. :)

Now I'll have to go back into the thread & find out how to configure it...

---

### Post by Untitled_No4 on 2010-04-10
> **handy said:**
> On a side note, I just had a look at the first page of Perry3D's thread & thought I'll implement the PM with KMS as per the simple how-to at the bottom of the thread. (don't know why I hadn't done it ages ago really?)

It worked. :)

Now I'll have to go back into the thread & find out how to configure it...

Huh, that was what was missing to keep the temperature down. Before enabling dynamic power management my computer temp around 55-65 C with kernel .34 and xorg edgers compared to 45 - 50C with fglrx. After enabling dynamic pm my current temperature is 43c with open source drivers.

This is how I set it up in Kubuntu (10.04 with kernel 34 and xorg edgers as per your instructions in first post):
```

sudo kate /etc/modprobe.d/radeon-kms.conf

```
(use gedit instead of kate if you're not running KDE)

That file should already be there, add dynpm=1 at the end of it. Mine now looks like that:
```
options radeon modeset=1 dynpm=1
```

reboot and run 
```
dmesg | grep drm
```

and somewhere along the output you should find:
[drm] radeon: dynamic power management enabled
[drm] radeon: power management initialized

Thanks Handy, and (though I guess he doesn't read this) thanks Perry3D.

---

### Post by handy on 2010-04-10
> **Untitled_No4 said:**
> 
Thanks Handy, and (though I guess he doesn't read this) thanks Perry3D.

Thanks heaps for your post Untitled_No4. :D

It will surely help the Ubuntu users who are adventurous. ;)

I'll pass on your thanks to Perry3D, in the Arch thread.

---

### Post by handy on 2010-04-11
**@Untitled_No4:** I have added the key elements from your post under the xorg-edgers how-to in the OP. I'm sure you won't mind. ;)


Re power management, I use lm-sensors & powertop, to get readings on my machine, though others get more information than I do on the iMac. 

It seems like ACPI is inaccessible for powertop at least, so I don't get the readings that I would like to see. I get the following error:

*no ACPI power usage estimate available*

Does anyone know of any other software for reading temp sensors & fan speeds?

---

### Post by Untitled_No4 on 2010-04-11
Of course I don't mind. I hope it helps someone else. It was so easy to set it and after a day of using my laptop with the changes to modprobe I can tell you it makes a huge difference. I have a thinkpad and therefore sometimes it's on my lap and my lap feels the difference. Previously it would go so hot it would be very uncomfortable, and since the hinges on thinkpads are metallic, the left one, which is just above the the CPU, would get too hot to touch. Not anymore.

RE: lm-sensors and powertop. I _think_ I don't get wattage readings on Karmic, but I've just installed it on Lucid and my reading is 29.6W, but I don't have fglrx readings to compare it to. I have found a review of my laptop which says that the power consumption under load in Windows using ATI is around 46W. I'm not sure if it says a lot, but it says to me that my ~30W is not something I should worry about.

Lm-sensors I have actually compared my temp in Karmic (with fglrx) and my temp in Lucid (with open source + pm) and I have found out that most sensors show the same temp and those who fluctuate have a 1 - 2c difference, some higher in Lucid, some lower. My fan speed is around the same numbers as well, 3000rpm.

---

### Post by Untitled_No4 on 2010-04-11
There's something I forgot to add. I'm very happy this works since I was itching to move to the open source drivers and the high temperature was the only thing stopping me. It's great being able to resize windows in KDE without a lag and the open source drivers use less memory as well which is nice. I'm slightly worried about using mainline kernel and xorg version unsupported by Ubuntu, but so far there were no problems whatsoever. I intend to keep using it until Lucid is officially released and then make a final decision when I upgrade to Lucid. For the meantime I have Karmic as backup in case things go wrong. 
I do have a slight problem which is unrelated to the changes made for PM as I had it before when using open source drivers. I can awkwardly work around it so it's not a big issue but I probably need some time to research a solution for the problem.

---

### Post by handy on 2010-04-11
Power Management seems to install ok on my iMac, but it isn't functioning properly yet:

As can be seen in the following:

[I]handy ~  $  dmesg | grep drm
[drm] Initialized drm 1.1.0 20060810
[drm] radeon kernel modesetting enabled.
[drm] radeon: Initializing kernel modesetting.
[drm] register mmio base: 0x50620000
[drm] register mmio size: 65536
[drm] Clocks initialized !
[drm] Internal thermal controller without fan control
[drm] 2 Power State(s)
[drm] State 0 Default (default)
[drm] 	16 PCIE Lanes
[drm] 	3 Clock Mode(s)
[drm] 		0 engine/memory: 600000/650000
[drm] 		1 engine/memory: 600000/650000
[drm] 		2 engine/memory: 600000/650000
[drm] State 1 Performance 
[drm] 	16 PCIE Lanes
[drm] 	3 Clock Mode(s)
[drm] 		0 engine/memory: 600000/650000
[drm] 		1 engine/memory: 600000/650000
[drm] 		2 engine/memory: 600000/650000
[drm] radeon: dynamic power management enabled
[drm] radeon: power management initialized
[drm] Detected VRAM RAM=256M, BAR=256M
[drm] RAM width 128bits DDR
[drm] radeon: 256M of VRAM memory ready
[drm] radeon: 512M of GTT memory ready.
[drm] radeon: using MSI.
[drm] radeon: irq initialized.
[drm] GART: num cpu pages 131072, num gpu pages 131072
[drm] Loading RV630 Microcode
[drm] ring test succeeded in 1 usecs
[drm] radeon: ib pool ready.
[drm] ib test succeeded in 0 usecs
[drm] Enabling audio support
[drm] Default TV standard: NTSC
[drm] Default TV standard: NTSC
[drm] Default TV standard: NTSC
[drm] Radeon Display Connectors
[drm] Connector 0:
[drm]   DVI-I
[drm]   HPD1
[drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[drm]   Encoders:
[drm]     CRT1: INTERNAL_KLDSCP_DAC1
[drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[drm] Connector 1:
[drm]   LVDS
[drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[drm]   Encoders:
[drm]     LCD1: INTERNAL_LVTM1
[drm] Connector 2:
[drm]   DIN
[drm]   Encoders:
[drm]     TV1: INTERNAL_KLDSCP_DAC2
[drm] Requested: e: 60000 m: 65000 p: 16
[drm] Setting: e: 60000 m: 65000 p: 16
[drm] fb mappable at 0x40141000
[drm] vram apper at 0x40000000
[drm] size 9216000
[drm] fb depth is 24
[drm]    pitch is 7680
fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[drm] Requested: e: 60000 m: 65000 p: 16
[drm] Setting: e: 60000 m: 65000 p: 16
fb0: radeondrmfb frame buffer device
[drm] Initialized radeon 2.2.0 20080528 for 0000:01:00.0 on minor 0
[drm] Requested: e: 60000 m: 65000 p: 16
[drm] Setting: e: 60000 m: 65000 p: 16
[drm] not in vbl for pm change 00020002 00000000 at entry
[drm] Requested: e: 60000 m: 65000 p: 16
[drm] Setting: e: 60000 m: 65000 p: 16
[drm] not in vbl for pm change 00020002 00000000 at entry[/I]

I expect that the problem will be solved before kernel .34 is released. I hope so anyway. Though my machine doesn't have a temperature problem, but it would be good if it used less electricity.

---

### Post by Untitled_No4 on 2010-04-11
My output is slightly longer but I guess it's because my thinkpad has more outputs, but the only difference I notice is in this line:
fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
where mine says:
fb0: radeondrmfb frame buffer device

Apart from that I think mine is much the same.

---

### Post by handy on 2010-04-11
Mine went on longer too, I just cut it off as it was just basically repeating itself.

I think there is a little more work required upstream before PM will work on my GPU in an iMac at least. 

As previously stated it isn't really a problem, as the machine is neither hot or noisy.

---

### Post by liedan on 2010-04-11
Hi,
i' ve found the solution to my problem with missing firmware. All i had to do was reinstalling the kernel:) 

To some up my journey for 3D open source support:
1)install 2.6.33 kernel
2)add and upgrade from  xorg edgers
3) download missing firware file (R600_rlc.bin) from 
[HTML]http://sourceforge.net/mailarchive/forum.php?thread_name=a728f9f90911301058j180e66eaofc60d3166cef5b0%40mail.gmail.com&forum_name=dri-devel  [/HTML] and copy it to /lib/firmware/2.6.3xxx/radeon
4) reinstall the kernel 

I have also tried to install 2.6.34-rc2 . The bug with missing firmware was also there.
Another weird thing I noticed is that glxgears shows less fps (~half) in this kernel in compare with the kernel 2.6.33.  Any ideas why?

Anyway,i did some testing in graphical software and  even when using kernel 2.6.33,the performance of open source driver is far from fglrx. Kinda dissapointing after all the trouble i had. :( At least i have the compiz working.

---

### Post by handy on 2010-04-11
@liedan: Good you got it working. The speed will keep on improving as the dev' work progresses. If you have KMS running, turning it off will usually increase your speed. 

I just installed kernel26-drm-radeon-testing David Airlie (the developer from Red Hat): [http://airlied.livejournal.com/71261.html](http://airlied.livejournal.com/71261.html) & it has improved my PM removing an error or two, but it is still not functioning properly (it is doing nothing) fortunately my machine is cool/quiet by nature.

Here is the output for anyone interested:

[I]handy ~  $  dmesg | grep drm
[drm] Initialized drm 1.1.0 20060810
[drm] radeon kernel modesetting enabled.
[drm] radeon: Initializing kernel modesetting.
[drm] register mmio base: 0x50620000
[drm] register mmio size: 65536
[drm] Clocks initialized !
[drm] Internal thermal controller without fan control
[drm] 2 Power State(s)
[drm] State 0 Default (default)
[drm] 	16 PCIE Lanes
[drm] 	3 Clock Mode(s)
[drm] 		0 engine/memory: 600000/650000
[drm] 		1 engine/memory: 600000/650000
[drm] 		2 engine/memory: 600000/650000
[drm] State 1 Performance 
[drm] 	16 PCIE Lanes
[drm] 	3 Clock Mode(s)
[drm] 		0 engine/memory: 600000/650000
[drm] 		1 engine/memory: 600000/650000
[drm] 		2 engine/memory: 600000/650000
[drm] radeon: dynamic power management enabled
[drm] radeon: power management initialized
[drm] Detected VRAM RAM=256M, BAR=256M
[drm] RAM width 128bits DDR
[drm] radeon: 256M of VRAM memory ready
[drm] radeon: 512M of GTT memory ready.
[drm] radeon: using MSI.
[drm] radeon: irq initialized.
[drm] GART: num cpu pages 131072, num gpu pages 131072
[drm] Loading RV630 Microcode
[drm] ring test succeeded in 1 usecs
[drm] radeon: ib pool ready.
[drm] ib test succeeded in 0 usecs
[drm] Enabling audio support
[drm] Default TV standard: NTSC
[drm] Default TV standard: NTSC
[drm] Default TV standard: NTSC
[drm] Radeon Display Connectors
[drm] Connector 0:
[drm]   DVI-I
[drm]   HPD1
[drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[drm]   Encoders:
[drm]     CRT1: INTERNAL_KLDSCP_DAC1
[drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[drm] Connector 1:
[drm]   LVDS
[drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[drm]   Encoders:
[drm]     LCD1: INTERNAL_LVTM1
[drm] Connector 2:
[drm]   DIN
[drm]   Encoders:
[drm]     TV1: INTERNAL_KLDSCP_DAC2
[drm] Requested: e: 60000 m: 65000 p: 16
[drm] Setting: e: 60000 m: 65000 p: 16
[drm] fb mappable at 0x40141000
[drm] vram apper at 0x40000000
[drm] size 9216000
[drm] fb depth is 24
[drm]    pitch is 7680
[drm] Requested: e: 60000 m: 65000 p: 16
[drm] Setting: e: 60000 m: 65000 p: 16
fb0: radeondrmfb frame buffer device
[drm] Initialized radeon 2.2.0 20080528 for 0000:01:00.0 on minor 0
[drm] Requested: e: 60000 m: 65000 p: 16
[drm] Setting: e: 60000 m: 65000 p: 16
[drm] not in vbl for pm change 00020002 00000000 at entry
[/I]

---

### Post by phredbull on 2010-04-11
> **Untitled_No4 said:**
> Huh, that was what was missing to keep the temperature down. Before enabling dynamic power management my computer temp around 55-65 C with kernel .34 and xorg edgers compared to 45 - 50C with fglrx. After enabling dynamic pm my current temperature is 43c with open source drivers.
...
snip
...
My laptop also runs very hot.
I tried this procedure, but when I do
```
dmesg | grep drm
```there is no mention of dynamic PM. Perhaps it isn't supported for my old card, (rv200)?
:confused:

EDIT: After updating to kernel 2.6.34, dynamic PM seems to be working. Glxgears seems the same, but now Open Arena is playable, (and sound seems to work properly now), and Alien Arena is playable, at least w/minimal settings.

BUT:
Update Manager is asking me to update Linux firmware, but after downloading, it fails to complete the process. I couldn't find the firmware files in the link posted above...

---

### Post by handy on 2010-04-11
[I]Ubuntu 10.04 Gets A New Catalyst** Pre-Release**

Posted by Michael Larabel on April 11, 2010

A month ago the Canonical crew working on Ubuntu 10.04 LTS received an unreleased Catalyst 10.4 driver from AMD for inclusion with the Lucid Lynx since the publicly available ATI Catalyst drivers had not -- and to this day still do not -- support the X.Org Server 1.7 used by this next Ubuntu release. Similar pre-releases for Ubuntu have happened in the past when AMD hasn't been quick to the game in supporting new Linux kernels and X Servers. This driver was made available in Ubuntu 10.04 even before Catalyst 10.3 was released. Catalyst 10.4 still has not been publicly released, but another updated 10.4 driver has made its way into the Lucid repository.[/I]

For more read on:

[http://www.phoronix.com/scan.php?page=news_item&px=ODE0MQ](http://www.phoronix.com/scan.php?page=news_item&px=ODE0MQ)

---

### Post by handy on 2010-04-11
> **phredbull said:**
> 
EDIT: After updating to kernel 2.6.34, dynamic PM seems to be working. Glxgears seems the same, but now Open Arena is playable, (and sound seems to work properly now), and Alien Arena is playable, at least w/minimal settings. 

kernel .34, is where ATi GPU PM begins. :) Not available before that in the open-source drivers.

> **phredbull said:**
> 
BUT:
Update Manager is asking me to update Linux firmware, but after downloading, it fails to complete the process. I couldn't find the firmware files in the link posted above...

Does this site help you?:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by shane2peru on 2010-04-11
YEAHHH!  .34 with drm is in there now!  Downloading now.  34 without drm is tolerable, but there is a telp diff with the drm stuff for my computer.  That is great.  I can testify that the OS drivers are great.  Kudos to the devs on this, for my Radeon HD3100 card in my toshiba laptop, the OS drivers are better than the proprietary ones.  My laptop always overheated with the others!

Shane

---

### Post by handy on 2010-04-12
> **shane2peru said:**
> YEAHHH!  .34 with drm is in there now!  Downloading now.  34 without drm is tolerable, but there is a telp diff with the drm stuff for my computer.  That is great.  I can testify that the OS drivers are great.  Kudos to the devs on this, for my Radeon HD3100 card in my toshiba laptop, the OS drivers are better than the proprietary ones.  My laptop always overheated with the others!

Shane

For the sake of those who don't know:

I'll have to temper your enthusiasm with the statement that for most people, the use of the kernel .34-rc3 & related -git packages that make up the latest releases of the open-source drivers; is currently (when running KMS which is slower than UMS = the old way) in 3D somewhere around half as fast as if they were using Catalyst. 2D is brilliant. 

On my HD2600Pro, I get 1265 fps out of glxgears when using KMS, with UMS I get up near 1700 fps, on Catalyst I was better than double 1700 fps. 

Though glxgears does not truly represent positive changes in the software. I could not play Glest (much too slow) then there was an update, my glxgears did not improve, but I can now play Glest with no problems...

There are variations on the speed difference, depending on your hardware & just which game engine you are using. 

As stated previously in this thread, the quakeio engined games work quite well as they very efficiently use GPUs.

---

### Post by shane2peru on 2010-04-12
Yes, for those of you who are looking at the frame rates, I'm sure there were advantages, however, my computer didn't even work (over heated within 5 min of opening only firefox), so frame rate at that point was irrelevant.  I started looking into this and trying experimental stuff because my computer was literally a paper weight and that was all it was good for.  So I have grown to hate ATI, and right now am really appreciating the open drivers.  So, yeah, the frame rates may not quite be there yet, but I'm just very glad to use my computer again.

Shane

---

### Post by handy on 2010-04-12
> **shane2peru said:**
> Yes, for those of you who are looking at the frame rates, I'm sure there were advantages, however, my computer didn't even work (over heated within 5 min of opening only firefox), so frame rate at that point was irrelevant.  I started looking into this and trying experimental stuff because my computer was literally a paper weight and that was all it was good for.  So I have grown to hate ATI, and right now am really appreciating the open drivers.  So, yeah, the frame rates may not quite be there yet, but I'm just very glad to use my computer again.

Shane

Cool, thanks for adding that.

No wonder you are so happy with PM functioning, you have been involved in a long & probably tedious battle, & you won. :D

---

### Post by phredbull on 2010-04-12
.34 kernel w/Karmic Koala is running better than ever! I played Quake Live for a while, good times!
I'm in no hurry to update to Lucid at this point.
\\:D/

---

### Post by xir_ on 2010-04-13
a new rc has been released for the kernel. Now at rc4

[http://www.phoronix.com/scan.php?page=news_item&px=ODE0Nw]("http://www.phoronix.com/scan.php?page=news_item&px=ODE0Nw")

apparently there have been some improvements including HDMI audio output for r700 cards

---

### Post by handy on 2010-04-13
> **xir_ said:**
> a new rc has been released for the kernel. Now at rc4

[http://www.phoronix.com/scan.php?page=news_item&px=ODE0Nw]("http://www.phoronix.com/scan.php?page=news_item&px=ODE0Nw")

apparently there have been some improvements including HDMI audio output for r700 cards

Thanks for telling us.

I expect Perry3D will incorporate it into his pre-compiled (Arch) repo shortly.

---

### Post by handy on 2010-04-15
A new branch in git.kernel has been created, it incorporates a reworking of the power management that makes PM more effective & work more the way it was meant to:

Here is the kernel:

[http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing-pm2](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing-pm2)

Here is the patch:

[http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=commitdiff;h=f8efa536373135f1896c794ecdbb3ccb12eebbb6](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=commitdiff;h=f8efa536373135f1896c794ecdbb3ccb12eebbb6)

I have been using a kernel from Dave Airlied's site for some days, it works better than the main branch does re. PM.

---

### Post by handy on 2010-04-21
The guys on the Arch forum who are using the new PM kernel branch (previous post) are really happy.

Pull the power plug from your notebook & it goes into the appropriate power mode, for example.

I'm sure that there are exceptions as not all hardware has been tested by the dev's. But it is certainly looking great for the many at the moment.

---

### Post by Untitled_No4 on 2010-04-22
> **handy said:**
> Pull the power plug from your notebook & it goes into the appropriate power mode, for example.
How can you check what is your current power mode?

---

### Post by handy on 2010-04-22
> **Untitled_No4 said:**
> How can you check what is your current power mode?

I'm using Arch, so I can't give you a step by step for Ubuntu. You need to have kernel .34, as that is where the PM is happening for the ATi GPUs. There is a better kernel branch re. PM, as mentioned in a previous post not too far back in this thread.

This is what we are using in Arch:

```
[I]    endlessroad1991 wrote:

    **_Without_ KMS** (It won't work if KMS is enabled!!):
        In your xorg.conf file, add 2 lines to "Device" Section:
                Option      "DynamicPM"                   "on"
                Option      "ClockGating"                  "on"
        --------
        If the two options are enabled successfully, you will see following lines in /var/log/Xorg.0.log:
                (**) RADEON(0): Option "ClockGating" "on"
                (**) RADEON(0): Option "DynamicPM" "on"
                ......
                Static power management enable success
                (II) RADEON(0): Dynamic Clock Gating Enabled
                (II) RADEON(0): Dynamic Power Management Enabled
        --------
        If you desire low power cost, you can add an extra line to "Device" Section of xorg.conf:
                Option      "ForceLowPowerMode"   "on"

    **_With_ KMS** (It won't work if KMS is disabled!!). Kernel 2.6.34 required:
        Add
                radeon.dynpm=1
        to grub commandline,
        or add
                options radeon dynpm=1
        to /etc/modprobe.conf
        --------
        If it's enabled successfully, you will see following lines in output of "dmesg | grep drm":
                [drm] radeon: dynamic power management enabled
                [drm] radeon: power management initialized[/I]
```

Here is someone's "dmesg | grep drm" it shows the that notebook's GPU's four state PM:

```
[I]$ dmesg | grep drm
[drm] Initialized drm 1.1.0 20060810
[drm] radeon defaulting to kernel modesetting.
[drm] radeon kernel modesetting enabled.
[drm] radeon: Initializing kernel modesetting.
[drm] register mmio base: 0x94300000
[drm] register mmio size: 65536
[drm] Clocks initialized !
[drm] 4 Power State(s)
[drm] State 0  (default)
[drm]   1 Clock Mode(s)
[drm]           0 engine: 500000
[drm] State 1 Performance 
[drm]   1 Clock Mode(s)
[drm]           0 engine: 500000
[drm] State 2 Battery 
[drm]   1 Clock Mode(s)
[drm]           0 engine: 200000
[drm] State 3  
[drm]   1 Clock Mode(s)
[drm]           0 engine: 500000
[drm] radeon: power management initialized
[drm] Detected VRAM RAM=256M, BAR=256M
[drm] RAM width 32bits DDR
[drm] radeon: 256M of VRAM memory ready
[drm] radeon: 512M of GTT memory ready.
[drm] radeon: irq initialized.
[drm] GART: num cpu pages 131072, num gpu pages 131072
[drm] Loading RS780 Microcode
[drm] ring test succeeded in 1 usecs
[drm] radeon: ib pool ready.
[drm] ib test succeeded in 0 usecs
[drm] Enabling audio support
[drm] Default TV standard: NTSC
[drm] Radeon Display Connectors
[drm] Connector 0:
[drm]   VGA
[drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[drm]   Encoders:
[drm]     CRT1: INTERNAL_KLDSCP_DAC1
[drm] Connector 1:
[drm]   LVDS
[drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[drm]   Encoders:
[drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[drm] fb mappable at 0x80141000
[drm] vram apper at 0x80000000
[drm] size 4096000
[drm] fb depth is 24
[drm]    pitch is 5120
fb0: radeondrmfb frame buffer device
[drm] Initialized radeon 2.2.0 20080528 for 0000:01:05.0 on minor 0[/I]
```

I have seen a seven state PM output. :)

---

### Post by Untitled_No4 on 2010-04-22
Sorry, I think I didn't quite make myself understood.
I have kernel 34 and all that set up. I get 6 states in my "dmesg | grep drm" output, but my question was with regards to that paritcular sentence:
> Pull the power plug from your notebook & it goes into the appropriate power mode, for example.
When I unplug my cable my screen dims itself and my battery widget (KDE user here) pops and says that the the current Power Profile is Powersave. Does that mean that the GPU also goes into powersave mode? Or is there a command that outputs the currently active power mode?

I also checked the Arch forum thread about ATI and I saw that some people there run "echo 2 > /sys/class/drm/card0/device/power_state" to change the power mode, but I don't have a power_state file or folder in that location or anywhere on my computer. Is it something that relates to the patches made for Arch?

I also need to find out where to post issues with the open source driver. Using kernel .34 and xorg edgers has made a huge difference on my ThinkPad T500 when it's not docked, but when docked it becomes very hot again.

---

### Post by handy on 2010-04-22
> **Untitled_No4 said:**
> 
Sorry, I think I didn't quite make myself understood.
I have kernel 34 and all that set up. I get 6 states in my "dmesg | grep drm" output, but my question was with regards to that paritcular sentence:

When I unplug my cable my screen dims itself and my battery widget (KDE user here) pops and says that the the current Power Profile is Powersave. Does that mean that the GPU also goes into powersave mode? Or is there a command that outputs the currently active power mode? 

From what I've read in the Arch forum, the GPU *should* go into power-save too.

Have you tried using the kernel from Dave Airlied's site (linked above)? It is much better for PM than the Linus branch is currently.

> **Untitled_No4 said:**
> 
I also checked the Arch forum thread about ATI and I saw that some people there run "echo 2 > /sys/class/drm/card0/device/power_state" to change the power mode, but I don't have a power_state file or folder in that location or anywhere on my computer. Is it something that relates to the patches made for Arch? 

The kernel is basically vanilla with some extra PM development from a Red Hat guy & associated people. That command is kernel specific by the look of it.

> **Untitled_No4 said:**
> 
I also need to find out where to post issues with the open source driver. Using kernel .34 and xorg edgers has made a huge difference on my ThinkPad T500 when it's not docked, but when docked it becomes very hot again.

Perry3D has this link at the top of the OP of the ATi open-source driver thread on the Arch forum, where he requests people to report bugs to help the dev's making this software work for us all:

[https://bugs.freedesktop.org/query.cgi](https://bugs.freedesktop.org/query.cgi)

---

### Post by handy on 2010-04-26
I just upgraded kernel .34, the other associated -git packages & also thought it was time I gave xorg-server 1.8 a try.

It works fine, I had no need to add or edit anything in the new /etc/X11/xorg.conf.d 

Xorg-server 1.8 works fine with the open-source ATi drivers, but the closed ATi drivers require a little simple hacking & I'm not sure whether nVidia have released their new driver yet that will work with the forthcoming release of xorg-server. [Edit:] They have. /edit

One of the new things that 1.8 does is remove the requirement of running HAL. I'll remove the daemon from my rc.conf on Arch & hopefully will still be able to use my keyboard & mouse. As previously I discovered that if I started using HAL again, I could dump the xorg.conf altogether.

If I have any problem with HAL gone I'll add an edit to below.

**[Edit:]** I just rebooted without the HAL daemon running & the machine is functioning fine so far.  I just thought I'd delete HAL from the system but I found that at this stage there are too many packages that still require HAL, which is understandable I suppose seeing as xorg-server 1.8 hasn't been released yet.

This is the result of trying to delete HAL from my system:

[I]handy ~  $  pdelete hal
checking dependencies...
error: failed to prepare transaction (could not satisfy dependencies)
:: exo: requires hal>=0.5.13-2
:: gnome-vfs: requires hal>=0.5.13
:: gstreamer0.10-good-plugins: requires hal>=0.5.13
:: handbrake: requires hal
:: ogmrip: requires hal
:: vlc: requires hal[/I]

**[Edit2:]** nVidia's pre-release drivers support xorg-server 1.8:

[http://ubuntuforums.org/showpost.php?p=9168346&postcount=1271](http://ubuntuforums.org/showpost.php?p=9168346&postcount=1271)

---

### Post by handy on 2010-04-28
[I]**More Radeon Power Management Improvements**

Posted by Michael Larabel on April 27, 2010

The last time we talked about the open-source ATI power management support was a month ago when we shared that the in-kernel Radeon support started to utilize the I2C support and provided GUI idle IRQ support, support for changing the GPU clocks when the engine is idle, and support for turning down the number of active SIMDS when running in a lower power stage for the ATI R600 ASICs and later. Days later the initial thermal monitoring support came about along with other Radeon DRM changes. This month we now have more reliable memory re-clocking support. [/I]

Read more:

[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Mg)

---

### Post by ttanev on 2010-04-29
Better PM than binary driver maybe ? :)
I tried to use the overclock utility from here:
[http://www.overclock.net/linux-unix/517861-how-overclocking-ati-cards-linux.html](http://www.overclock.net/linux-unix/517861-how-overclocking-ati-cards-linux.html) 
...but even trying to set the voltage and frequencies at the supported minimum the card is still noisy /I got Sapphire HD4870/. If the mentioned above Open Source driver PM support is better than the binary, then there will be only one disadvantage in 3D... :) I'll try it after I upgrade /to Lucid/, last time didn't succeed to enable it on karmic.

---

### Post by handy on 2010-04-29
You are using kernel .34 I take it?

The one from Dave Airlied's site is the best for PM at the moment.

---

### Post by Untitled_No4 on 2010-04-29
I'm still not sure which driver I will use when I install Lucid as my main system (which won't be today). I like the open source drivers since they take less memory and work better with KDE, but I have two issues with the open source drivers.

1. PM is disabled when using dual screens. I was told on xorg's bugzilla that this is the intended functionality to avoid graphical glitches. 
2. I have Thinkpad T500 with a dock and two external dual monitors (one DVI one VGA). According to Lenovo specifications the laptop's LCD is disabled when using dual external monitors which is how it works with fglrx. With the open source drivers the LCD is magically enabled and the DVI monitor is using the settings of the LCD, which corrupts the display on the DVI. The workaround is either to start the computer with one external monitor disconnected or enable DVI and disable LCD in xrandr until they get it right, but it doesn't always happen on the first try and it sometimes creates some funky visual effects. It should affect anyone with a laptop and external dual monitors. I think that having external monitors with the same resolution as the LCD might also be a workaround (since it will only appear to be working, while it isn't). I guess there are not many people with my setup out there since my bug report seems to be going nowhere. 

I still really want to use the open source drivers but there are patches around which should fix my issues with fglrx, so I might still opt for the proprietary option.

---

### Post by handy on 2010-04-29
The only positive thing I can say is that at least there is a choice. ;)

---

### Post by Untitled_No4 on 2010-04-29
Don't get me wrong, I don't think that open source drivers suck or anything, it's just that my particular situation sucks. On my office Lenovo Desktop, with dual screens, I have seen in the last year or so since ATI stopped supporting its card how the open source drivers improved dramatically and even if I don't use them in 10.04 I will revisit the open source driver in time for 10.10.

---

### Post by handy on 2010-04-29
Hopefully kernel .35 will have the PM advancements mentioned in the phoronix article linked to further up the page. The kernel & associated packages will have expanded support for the ATi GPU stuff, just how the tasks to be worked on are prioritised though we just have to wait & see. Hopefully your multi-monitor problem gets solved soon.

---

### Post by georgi.dunchev on 2010-05-01
Hi, I went through the whole thread and found a lot of food for thought.

However I could not answer one question:
This Power Management stuff that is being implemented the recent months usually mentions R600.
However I'm using thinkpad t60 with ATI X1400 (R500) that is idling at 65C and causing my whole laptop to be quite hot and noise because of the constant need to run the fan at above 3000RPM.
Does anybody know if there is something in the works for the PM of R500 cards? Or even if these cards support such PM.


BTW:
> Re power management, I use lm-sensors & powertop, to get readings on  my machine, though others get more information than I do on the iMac. 

It seems like ACPI is inaccessible for powertop at least, so I don't get  the readings that I would like to see. I get the following error:

*no ACPI power usage estimate available*

Does anyone know of any other software for reading temp sensors &  fan speeds?PowerTOP can read and estimate power usage based on the power drawn from a laptop's battery. So even on a laptop you should be on battery power and off AC to have ACPI readings.

---

### Post by handy on 2010-05-01
> **georgi.dunchev said:**
> 
Hi, I went through the whole thread and found a lot of food for thought.

However I could not answer one question:
This Power Management stuff that is being implemented the recent months usually mentions R600.
However I'm using thinkpad t60 with ATI X1400 (R500) that is idling at 65C and causing my whole laptop to be quite hot and noise because of the constant need to run the fan at above 3000RPM.
Does anybody know if there is something in the works for the PM of R500 cards? Or even if these cards support such PM. 

It says that the PM for the R500 is mostly done here:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

> **georgi.dunchev said:**
> 
BTW:
PowerTOP can read and estimate power usage based on the power drawn from a laptop's battery. So even on a laptop you should be on battery power and off AC to have ACPI readings.

Yes I know, others do quite well out of PowerTop, but my alu' iMac seems to be just a little too Applyfied for all of PowerTop to work properly.

As I say, it doesn't run hot & it's not noisy at all so I'm not really too concerned.  I would like to see the numbers though. :)

---

### Post by gohanssjn on 2010-05-01
If someone could help me with selection...

Just installed 10.04, so 2.6.32-21 generic is what my kernel is I think.

What should I download?  New to trying this...

---

### Post by handy on 2010-05-01
If you want power management you need kernel .34, so get the latest  version of that available?

The info' you need (for both the kernel, other packages & setting up power management) is in a how-to under *"Ubuntu stuff:"* way down the first post of this thread.

---

### Post by screaminj3sus on 2010-05-02
> **handy said:**
> If you want power management you need kernel .34, so get the latest  version of that available?

The info' you need (for both the kernel, other packages & setting up power management) is in a how-to under *"Ubuntu stuff:"* way down the first post of this thread.

just updated my kernel on my laptop and I Can finally use the OSS drivers (without an insanely hot vid card)! Compiz with no tearing and no video tearing FTW.

---

### Post by Primefalcon on 2010-05-02
you know.... Nvidia have been ceasing to cooperate with the OSS community and ATI are cooperating as much as possible.... the decision on which to buy right there is a no brainer atm. At least between those 2.

---

### Post by screaminj3sus on 2010-05-02
Yeah I regretted getting a laptop with an ati vid card for ages ebcause the linux drivers are so bad, but these OSS drivers are maturing so fast I am glad now. OSS drivers are awesome. Can always keep my kernel and xorg up to date and they are still compatible, and they work out of the box.

---

### Post by Primefalcon on 2010-05-02
I got an ATI  1300 XT pro myself and 3 days after buying it....,. ATI ceased support of it..... needless to say I was really peeved and cussing badly.........

you know what though with how the card is handling since even karmic, I've had a lot better performance from it.... and with nvidia now.... I am very happy I did go ATI.... so I went from happy to cussing to super happy :-)

---

### Post by ttanev on 2010-05-02
Just upgraded to Lucid, with the proprietary driver it comes with and I'm very disappointed as my HD4870 got 3.5 degrees hotter /~42.5/ in idle and  of course the fan went faster. Last time when I tried to install the .34 rc3 and then rc4 I got dependencies issues, maybe it's better to wait for some of the next releases. 
Can this be the root of the problem:
[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng) 
I mean the kernel difference, not the GRUB bug.

Edit: Just saw the rc5 and 6 here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 
I'll try later with them too :)

---

### Post by Primefalcon on 2010-05-02
> **ttanev said:**
> Just upgraded to Lucid, with the proprietary driver it comes with and I'm very disappointed as my HD4870 got 3.5 degrees hotter /~42.5/ in idle and  of course the fan went faster. Last time when I tried to install the .34 rc3 and then rc4 I got dependencies issues, maybe it's better to wait for some of the next releases. 
Can this be the root of the problem:
[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng) 
I mean the kernel difference, not the GRUB bug.

Edit: Just saw the rc5 and 6 here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 
I'll try later with them too :)
naww, that's was just for grub not detecting multi boot systems (it wouldn't add windows to the grub boot menu) it was fixed before release though...

---

### Post by handy on 2010-05-02
@ttanev: Try the latest kernel .34 version & use xorg-edgers ppa, see the first post *"Ubuntu stuff:"* for how-to, if you need it?

---

### Post by georgi.dunchev on 2010-05-02
> **handy said:**
> It says that the PM for the R500 is mostly done here:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

Thanks, and I also found this: [http://www.phoronix.com/forums/showpost.php?p=124600&postcount=7](http://www.phoronix.com/forums/showpost.php?p=124600&postcount=7)
> 04-27-2010 by agd5f 
voltage drop support is already implemented for most r1xx-r5xx chips  that support it, but it's commented out until I have a chance to  test/debug it more thoroughly.So for r100-r500 laptop users, things could turn up soon (fingers crossed)

---

### Post by screaminj3sus on 2010-05-02
What is my mobility hd2600? r600?

And question, what kernel is better for ati power management, the rc6, or the drm-next?

---

### Post by handy on 2010-05-02
> **screaminj3sus said:**
> 
What is my mobility hd2600? r600? 

Yes it is an R600.

> **screaminj3sus said:**
> 
And question, what kernel is better for ati power management, the rc6, or the drm-next?

I'd go with drm-next. You can install them both in parallel & choose which one you want to use at boot.

I sometimes have 4 of the things in my grub menu. :)

---

### Post by screaminj3sus on 2010-05-03
Alright I am downloading the drm-next now and Ill see if there is any improvement, the power management right now is pretty bad compared to fglrx still. (using rc6 and radeon drivers from xorg-edgers driver only repo)

---

### Post by BigLouis87 on 2010-05-04
Hello! I am on Ubuntu Lucid with an ATI Mobility X1600, so it should be an r520. I tried following the instruction for Ubuntu, installing the new kernel .34 and the xorg-edgers, but even if I can read "powersaving enabled" in dmesg I cannot see any improvements about temperature and power (my laptop consume now on idle ~30W, when with the old fglrx only ~20W).

I've read the last posts and I have understood that I have to compile myself a "special" version of the kernel, the "drm-next"... is it right?:confused:
But I haven't understood how to do that and where to get it! Can someone explain me?:)

Thank you!

---

### Post by Untitled_No4 on 2010-05-04
You probably don't need to compile a kernel since the drm-next kernel is already packaged for you and you can download it from [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/)

I don't know why you haven't seen an improvement with the open source drivers and the .34 kernel since I have seen a huge improvement compared to the drivers/xorg that comes with Lucid even with the .34 kernel, but maybe the drm-next kernel will help.

---

### Post by xir_ on 2010-05-04
I just tried the .34 kernel and xorg edgers and i saw no real power improvement. Oddly using the mainline ppa my cpu wouldn't dynamically downclock anymore.

This probably was the cause of my lack of power savings.

---

### Post by BigLouis87 on 2010-05-04
Thank you! Now using the drm-next the pc temperature is finally 3-4 degrees under... it's far from old fglrx but it's a big step for OSS driver!
Only one question: is it possible to manually manage power step, as in the closed driver? I noticed (by dmesg) that it often step from one frequency to another, about every 20 sec, and more often if desktop effects are enabled (even on idle), about every 6 sec. It's a waste of power and on every stepping the display start flickering!  I would like to put it always on the lowest frequency and boost it only few times when I turn on my UrbanTerror :)
is it possible?

thank you:)

---

### Post by handy on 2010-05-04
**BigLouis87:** try "su" and then "*echo **X** > /sys/class/drm/card0/device/power_state*"
    make sure **X** is a valid status id!
    
My card has only status 0 and 1, so **X** can only be 0 or 1. (see below?)

You will see how many **Power State(s)** your card has when you run: "*dmesg | grep drm*"

Not that this works for my card at this stage, though it does for similar GPUs. My PM has very likely been bastardised by Apple. :-|

[I][drm] 2 Power State(s)
[drm] State 0  (default)
[drm] 	16 PCIE Lanes
[drm] 	3 Clock Mode(s)
[drm] 		0 engine/memory: 600000/650000
[drm] 		1 engine/memory: 600000/650000
[drm] 		2 engine/memory: 600000/650000
[drm] State 1 Performance 
[drm] 	16 PCIE Lanes
[drm] 	3 Clock Mode(s)
[drm] 		0 engine/memory: 600000/650000
[drm] 		1 engine/memory: 600000/650000
[drm] 		2 engine/memory: 600000/650000[/I]

---

### Post by screaminj3sus on 2010-05-04
eh drm-next sucks for me because it pc freaks out whenever it wakes up from suspend with it (screen keeps flickering on and off with artifacts over and over :/

---

### Post by screaminj3sus on 2010-05-04
I tried drm-next but when my machine comes back from suspend it freaks out and the screen flickers on and off with artifacts, and temps were still pretty high (54-63 degrees C, laptop warm-hot to touch)

Here's my power states: (and question, why does it say 256 mb vram? I know for a fact my card has 512mb gddr3 dedicated vram)
> 4 Power State(s)
[   17.251253] [drm] State 0 Default (default)
[   17.251255] [drm] 	16 PCIE Lanes
[   17.251257] [drm] 	3 Clock Mode(s)
[   17.251259] [drm] 		0 engine/memory: 500000/600000
[   17.251261] [drm] 		1 engine/memory: 500000/600000
[   17.251263] [drm] 		2 engine/memory: 500000/600000
[   17.251265] [drm] State 1 Performance 
[   17.251267] [drm] 	16 PCIE Lanes
[   17.251269] [drm] 	3 Clock Mode(s)
[   17.251270] [drm] 		0 engine/memory: 300000/405000
[   17.251273] [drm] 		1 engine/memory: 300000/405000
[   17.251275] [drm] 		2 engine/memory: 500000/600000
[   17.251276] [drm] State 2 Battery 
[   17.251278] [drm] 	16 PCIE Lanes
[   17.251280] [drm] 	3 Clock Mode(s)
[   17.251282] [drm] 		0 engine/memory: 300000/405000
[   17.251284] [drm] 		1 engine/memory: 300000/405000
[   17.251286] [drm] 		2 engine/memory: 300000/405000
[   17.251288] [drm] State 3 Performance 
[   17.251289] [drm] 	16 PCIE Lanes
[   17.251291] [drm] 	3 Clock Mode(s)
[   17.251293] [drm] 		0 engine/memory: 500000/600000
[   17.251295] [drm] 		1 engine/memory: 500000/600000
[   17.251297] [drm] 		2 engine/memory: 500000/600000
[   17.251302] [drm] radeon: dynamic power management enabled
[   17.251304] [drm] radeon: power management initialized
[   17.251350] [drm] Detected VRAM RAM=256M, BAR=256M
[   17.251351] [drm] RAM width 128bits DDR
[   17.253473] [drm] radeon: 256M of VRAM memory ready
[   17.253475] [drm] radeon: 512M of GTT memory ready.


And heres my temp with the laptop only on for 10 minutes:

> brandon@brandon-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +57.0°C  (crit = +100.0°C)   

---

### Post by handy on 2010-05-04
> **screaminj3sus said:**
> eh drm-next sucks for me because it pc freaks out whenever it wakes up from suspend with it (screen keeps flickering on and off with artifacts over and over :/

All part of the fun & games of playing on the bleeding edge. :)

My machine freezes every couple of days due to all the dev' packages & kernel I'm running to satisfy my desire to play this game with the ATi OSS drivers. (It has only happened 3 times) I can live with that until I get an upgrade that will fix it, though I expect you'll be dumping that kernel pretty quick.

---

### Post by screaminj3sus on 2010-05-04
> **handy said:**
> All part of the fun & games of playing on the bleeding edge. :)

My machine freezes every couple of days due to all the dev' packages & kernel I'm running to satisfy my desire to play this game with the ATi OSS drivers. (It has only happened 3 times) I can live with that until I get an upgrade that will fix it, though I expect you'll be dumping that kernel pretty quick.

Yeah I am back to rc6 for now and am anticipating 2.6.35. My main problem with linux is vid drivers so the main reason I am running ubuntu right now it to see the oss driver progress so I can know when itll actually be able to run properly on my laptop someday lol.

---

### Post by handy on 2010-05-04
> **screaminj3sus said:**
> Yeah I am back to rc6 for now and am anticipating 2.6.35. My main problem with linux is vid drivers so the main reason I am running ubuntu right now it to see the oss driver progress so I can know when itll actually be able to run properly on my laptop someday lol.

Ubuntu is not necessarily the ideal distro for your purpose, I would suggest Arch if it meets your other requirements as it is bleeding edge to start with & there is a great bunch of guys that have been on the ATi GPU OSS case for quite some time. 

There are pre-compiled repo's (specifically for this ATi GPU situation) with the most current packages & kernels (tested first before inclusion) & continual feedback in the specific topic thread, the first post of the thread is kept up to date on the situation in a how-to kind of way:

[http://bbs.archlinux.org/viewtopic.php?id=79509&p=1](http://bbs.archlinux.org/viewtopic.php?id=79509&p=1)

Arch is different though, generally people either love it or get out of there pretty quick. The steepest part of the learning curve is the installation & setup of your system, after that the more you do it the better & easier it gets. :)

---

### Post by BigLouis87 on 2010-05-04
> **handy said:**
> **BigLouis87:** try "su" and then "*echo **X** > /sys/class/drm/card0/device/power_state*"
    make sure **X** is a valid status id!
    
My card has only status 0 and 1, so **X** can only be 0 or 1. (see below?)


mmmh... I don't have "power_state"!:
```
cat /sys/class/drm/card0/device/
boot_vga                  drm/                      msi_bus                   resource1
broken_parity_status      enable                    power/                    resource2
class                     firmware_node/            remove                    rom
config                    graphics/                 rescan                    subsystem/
consistent_dma_mask_bits  irq                       reset                     subsystem_device
device                    local_cpulist             resource                  subsystem_vendor
dma_mask_bits             local_cpus                resource0                 uevent
driver/                   modalias                  resource0_wc              vendor

```
and under "power" there is only "control" (set "on") and "wakeup". Can you tell me why??:lolflag:
However dmesg say that I have 4 powersteps (with fglrx I had only 3... wow!)
Do I have to disable dynpm in the option of the module?
Thank you;)

PS: When I'll have some time I'll retry to reinstall Arch... it will be the third time! :D

---

### Post by handy on 2010-05-04
**@BigLouis87:** Sorry, I'm out of my depth. As previously mentioned the card in my iMac is not responding to the PM as other GPUs of the same model, so I haven't had any first hand experience of being able to fiddle with the settings.

See what you can scroogle up on the subject on the web.

Good luck & let us know what you find out please?

Re. Arch installation, follow the Beginners' Guide to the letter & check the Arch forum for any problems post there if you need to. 

These days beyond a very obscure wireless network situation there isn't much in the way of obstructions that are insurmountable re. the install.

---

### Post by prions on 2010-05-04
This is awesome. :p

Any chance older cards (my x200m) will get support?

---

### Post by handy on 2010-05-04
> **prions said:**
> This is awesome. :p

Any chance older cards (my x200m) will get support?

This is posted in the first post:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

:D

---

### Post by prions on 2010-05-04
Thats awesome! Lets hope they turn out to be great. :popcorn:

---

### Post by screaminj3sus on 2010-05-04
> **handy said:**
> Ubuntu is not necessarily the ideal distro for your purpose, I would suggest Arch if it meets your other requirements as it is bleeding edge to start with & there is a great bunch of guys that have been on the ATi GPU OSS case for quite some time. 

There are pre-compiled repo's (specifically for this ATi GPU situation) with the most current packages & kernels (tested first before inclusion) & continual feedback in the specific topic thread, the first post of the thread is kept up to date on the situation in a how-to kind of way:

[http://bbs.archlinux.org/viewtopic.php?id=79509&p=1](http://bbs.archlinux.org/viewtopic.php?id=79509&p=1)

Arch is different though, generally people either love it or get out of there pretty quick. The steepest part of the learning curve is the installation & setup of your system, after that the more you do it the better & easier it gets. :)

I tried arch and got it all installed fine but I thought simple things like getting wireless to work are just too much of a hassle and couldn't getting it to work the way i wanted (didnt find any of the arch documentation in this area very helpful).. I like bleeding edge but I also hate having to every single little tiny thing manually.

I really like the idea of its rolling update model, but I cant stand not having such basic things having to be configured manually.

---

### Post by prions on 2010-05-04
> **handy said:**
> This is posted in the first post:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

:D

While I think my card is supported, is there any way to check? I'm not familiar with their naming system (r200, r300, etc). Its a legacy card so I'm not sure. 

Thanks.

---

### Post by handy on 2010-05-05
> **prions said:**
> While I think my card is supported, is there any way to check? I'm not familiar with their naming system (r200, r300, etc). Its a legacy card so I'm not sure. 

Thanks.

It looks like it is an R300, from what I gather it is a bit different, it is not listed on any of the pages where I go to check on this kind of stuff, but I see that it may be similar to an X300 chip.

Sorry I can't be of more help on that one.

---

### Post by screaminj3sus on 2010-05-05
The x200m is basically an integrated X300 card which is r400 I think. Even the older radeon 9xxx cards were r300, youd have to have an absolutely ancient card to have r200.

R200 cards = radeon 8xxx cards
R300 = 9xxx
R400 = x300 (200m is an integrated x300) - X800

---

### Post by Ubuntiac on 2010-05-05
> **handy said:**
> Arch is different though, generally people either love it or get out of there pretty quick. The steepest part of the learning curve is the installation & setup of your system

Really? I just ran the Chakra graphical installer and had it installed my first time in 15  minutes. The process was near identical to Kubuntu's...

I haven't had to tweak / configure anything yet barring installing the wireless driver (download 1 text file, makepkg, tell Arch to install the package...)

Being able to make an up to date package for most apps straight from the most up to date git / svn code is as simple as typing makepkg. Amazing.

Right now I'm *loving* my dual boot Kubuntu / Arch setup. I still love Kubuntu, but I wish all the stories of how "hard" Arch is hadn't put me off for so long. I have a feeling that in many cases, they're outdated.

---

### Post by prions on 2010-05-05
> **screaminj3sus said:**
> The x200m is basically an integrated X300 card which is r400 I think. Even the older radeon 9xxx cards were r300, youd have to have an absolutely ancient card to have r200.

R200 cards = radeon 8xxx cards
R300 = 9xxx
R400 = x300 (200m is an integrated x300) - X800

Thank you so much. :p

@Handy; thanks also.

---

### Post by handy on 2010-05-05
> **screaminj3sus said:**
> The x200m is basically an integrated X300 card which is r400 I think. Even the older radeon 9xxx cards were r300, youd have to have an absolutely ancient card to have r200.

R200 cards = radeon 8xxx cards
R300 = 9xxx
R400 = x300 (200m is an integrated x300) - X800

It says that the X300 is in the R300 series here:

[http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7](http://dri.freedesktop.org/wiki/ATIRadeon#head-42a0993a30370e48f1bec676a025da9c5903b9d7)

---

### Post by handy on 2010-05-05
> **Ubuntiac said:**
> Really? I just ran the Chakra graphical installer and had it installed my first time in 15  minutes. The process was near identical to Kubuntu's...

I haven't had to tweak / configure anything yet barring installing the wireless driver (download 1 text file, makepkg, tell Arch to install the package...)

Being able to make an up to date package for most apps straight from the most up to date git / svn code is as simple as typing makepkg. Amazing.

Right now I'm *loving* my dual boot Kubuntu / Arch setup. I still love Kubuntu, but I wish all the stories of how "hard" Arch is hadn't put me off for so long. I have a feeling that in many cases, they're outdated.

Using a graphical method is really best for people that are already familiar with Arch.

The problems with using a graphical installation come later. When you use such a method you don't get the hands on education of how Arch does things, which is at least quite different to most other distros & in some instances totally unique. 

Anyway, I'm glad you are enjoying it. :)

I think you had better do a whole lot of reading, as you could be missing out on a lot of fundamental knowledge required to use Arch properly. Properly in this instance means in a fashion that will save you from getting yourself into trouble that others will have difficulty getting you out of because you aren't doing things in the way that Arch was designed to be used.

Be very careful. PKGBUILDs are the way to configure an Arch install. Packages that aren't in the Arch repo's are usually available in the Arch User Repository (AUR), so you set up an account there & use a suitable package manager to install from there.

I suggest you read the Beginners' Guide as though you were using it to install, it will teach you a great deal.

Anyway, no more Arch talk here.

---

### Post by screaminj3sus on 2010-05-05
> **Ubuntiac said:**
> Really? I just ran the Chakra graphical installer and had it installed my first time in 15  minutes. The process was near identical to Kubuntu's...

I haven't had to tweak / configure anything yet barring installing the wireless driver (download 1 text file, makepkg, tell Arch to install the package...)

Being able to make an up to date package for most apps straight from the most up to date git / svn code is as simple as typing makepkg. Amazing.

Right now I'm *loving* my dual boot Kubuntu / Arch setup. I still love Kubuntu, but I wish all the stories of how "hard" Arch is hadn't put me off for so long. I have a feeling that in many cases, they're outdated.

hm ive never heard of chakra, i may have to give arch another try.

Thinking about it though I really had no issue with archs text install using the guide, my issues came after installing gnome and such trying to get wireless and other things working as good as in ubuntu.

---

### Post by handy on 2010-05-05
**@screaminj3sus:** At least you have done text mode installs; that gives you a LOT of knowledge that Ubuntiac is yet to find out about. Apart from all of the other things you learn with time/experience about optimising your setup & recovering from trouble, (all of which requires an understanding of the config files) particularly trouble that you have upgraded into.

---

### Post by Untitled_No4 on 2010-05-05
> **screaminj3sus said:**
> eh drm-next sucks for me because it pc freaks out whenever it wakes up from suspend with it (screen keeps flickering on and off with artifacts over and over :/

Happens to me too, but with the boot time of Lucid it's actually quicker to shut down and restart than to suspend.

Edit: 
Sorry, didn't realise there were two more pages of replies. This thread isn't usually so busy.

---

### Post by prions on 2010-05-05
Hey I have another question, are these changes implemented yet? Or do I need to do some upgrading for it to work?

---

### Post by handy on 2010-05-05
> **prions said:**
> Hey I have another question, are these changes implemented yet? Or do I need to do some upgrading for it to work?

Spend some time & read page one of this thread & the links, you will then have a rough understanding of what is going on?

---

### Post by screaminj3sus on 2010-05-06
Im givin arch another shot now, those newer kernels are too tempting :) Ill report back if I can get power management working more effieciently than ubuntu with rc6 or not.

---

### Post by handy on 2010-05-08
Just to say that the games in the "Humble Indie Bundle" all work fine with the kernel .34 & the other dev' packages I'm using for the ATi GPU & the open drivers, except for the Penumbra games. 

I went on & bought the Penumbra Collection, even though I already knew that the first part of the three - Overture - didn't work. The price was too good & soon enough the OSS drivers will do the job.

I've tested the three Penumbra games, they all work at the introduction, & the sound is brilliant, but it would seem that they crash when the game engine is loaded. Though I did get to use the engine a for a few minutes before it crashed in Overture & probably in the tutorial for Black Plague, though there were hardly any textures use at all in the tutorial.

---

### Post by del_diablo on 2010-05-08
A short question: Can you run blender with the latest drivers?
I mean that it can actually refocus the rendering window after rendering, actually use the menus, and no popup delay?

---

### Post by handy on 2010-05-08
[I]**DRI2 Sync & Swap For ATI Finally Comes About**
Posted by Michael Larabel on May 07, 2010

Last year a new set of DRI2 extensions came about for sync and swap support of display buffers to better reduce potential "tearing" that may appear on displays in some composited environments. This work that's exposed to the client through OpenGL/GLX extensions also can lead to improved performance, video memory savings, and other benefits as talked about extensively on the Composite Swap Wiki page. A new GLX swap event extension also came about out of expressed needs by the Clutter/Mutter developers. [/I]

Read on:

[http://www.phoronix.com/scan.php?page=news_item&px=ODIyNA](http://www.phoronix.com/scan.php?page=news_item&px=ODIyNA)

[i]
**ATI Gets Dynamic Power Management & Profiles Too**
Posted by Michael Larabel on May 08, 2010

For years we have been talking about open-source ATI Radeon power management for their Linux driver and it's finally all coming to fruition. Back in April of 2008 we talked about dynamic clocks coming to R500+ ASICs and various other initiatives to improve the Radeon power management in their DDX driver, but everything got shook up with the migration to their ATI kernel mode-setting driver, which finally now allows for real power management capabilities. [/i]

Read on:

[http://www.phoronix.com/scan.php?page=news_item&px=ODIyOA](http://www.phoronix.com/scan.php?page=news_item&px=ODIyOA)

---

### Post by ttanev on 2010-05-08
Tried drm-next with xorg-edgers on Asus m51tr and it worked beautifully well. Had a lot of issues with the standard lucid kernel and with brightness controls, then with .34rc6 and suspend/hibernate functions, but now with latest kernel/xorg-edgers the only thing that can distinguish the binary driver is the 3D gaming performance. And it's not too much better with it, as it is a HD3450 dedicated controller. Got to try it on my HD4870 next week. 
Can't wait to try steam based game /left4dead2 ?/ on it :)

---

### Post by handy on 2010-05-08
> **del_diablo said:**
> A short question: Can you run blender with the latest drivers?
I mean that it can actually refocus the rendering window after rendering, actually use the menus, and no popup delay?

I can't help you with that one as I don't use Blender. Hopfully someone else here can, though perhaps a Scroogle will get you an answer?

> **ttanev said:**
> Tried drm-next with xorg-edgers on Asus m51tr and it worked beautifully well. Had a lot of issues with the standard lucid kernel and with brightness controls, then with .34rc6 and suspend/hibernate functions, but now with latest kernel/xorg-edgers the only thing that can distinguish the binary driver is the 3D gaming performance. And it's not too much better with it, as it is a HD3450 dedicated controller. Got to try it on my HD4870 next week. 
Can't wait to try steam based game /left4dead2 ?/ on it :)

Good news. :)

Please let us know how it goes with the HD4870 & Steam?

---

### Post by del_diablo on 2010-05-08
> **handy said:**
> I can't help you with that one as I don't use Blender. Hopfully someone else here can, though perhaps a Scroogle will get you an answer?

No can find on scroogle.
On Fedora the ages old drivers are really a mess, the GUI on blender lags and it crashes all the time. Which makes it completely unbearable.... :(

Start blender, hit tab to go to edit mode, hit W and click "Bevel" and move your mouse(then leftclick to apply it), repeat the beveling for 2 or 3 times, render by clicking F12, change active window by alt tabbing and then alt tab back.
And to be sure attempt to hit any of the GUI. And attempt to scale the windows.
If there was no hickups, everything worked, you could get the render windows back in focus, then it works.

Under pure VESA blender runs...... except for that the GUI is not responding.
Under Fedora 12's test of the radeon drivers(ages old) it is 1 more tad responsive than under VESA, but still completely useless.

---

### Post by shane2peru on 2010-05-09
wow, some new kernels in the [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/)     repo.  Downloading them now.  

Let me get this straight, it seems to be more the kernel that has made the difference for me than anything else.  I mean, as for overheating and making my laptop usable.  I'm not into gaming and framerates so much as I just don't want my laptop overheating every time I run it.  And it is all linked to my ATI drivers, or ATI something, and the kernel seems to have made a huge difference in my laptop.  I have the Radeon HD3100.  I'm really pleased by the work that is going on.

Shane

---

### Post by handy on 2010-05-09
Before kernel .34, there was no power management for the ATi GPU with OSS.

As far as the OSS support for the ATi GPU, the prime thing has been PM in this kernel, & hopefully the very recent improvements mentioned in the 2 phoronix articles above will be incorporated in kernel .35.

Other development is ongoing in the other packages as well.

I look forward to the day that I can play the Penumbra Collection on the OSS drivers, hopefully it happens in kernel .35 or .36. :)

I am using the Arch [core] packages with KMS enabled; kernel .33, & all, at the moment. The frame rate in glxgears is identical to what I had with kernel .34 & the other relevant dev' packages, but NO PM. This is ok for me as I'm not on a Notebook & the PM didn't function on my iMac anyway.

---

### Post by DougieFresh4U on 2010-05-09
> **shane2peru said:**
> wow, some new kernels in the [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/)     repo.  Downloading them now.  
Shane
Is that kernel more recent than [this one]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/") as it was put lower in the 'pecking' order in grub?

---

### Post by shane2peru on 2010-05-10
> **DougieFresh4U said:**
> Is that kernel more recent than [this one]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/") as it was put lower in the 'pecking' order in grub?

I'm really not sure how all that works.  I have to stick with the drm stuff because my laptop seems to overheat with anything other than that.  So I'm not really sure what the kernel pecking order is, though that would be something nice to know.  

Shane

**EDIT:**  - Re-looking at that it seems to have the date of April 30th, where mine has May 8 right in the title name, so I'm going to guess newer would be more recent.  My guess.

---

### Post by xir_ on 2010-05-10
theres been some development on updating the gallium drivers for the R600 series chips (this is the 2000/3000/4000 radeons).


They slowly seem to be getting towards the point of mainlining their gallium driver. This would be awesome if it becomes default.


[http://www.phoronix.com/scan.php?page=news_item&px=ODIzMw]("http://www.phoronix.com/scan.php?page=news_item&px=ODIzMw")

If only intel will get onto the gallium bandwagon.

---

### Post by madjr on 2010-05-10
hey guys i got penumbra to work better with the ATi open drivers in ... Wine

check here:
[http://ubuntuforums.org/showthread.php?t=1479237](http://ubuntuforums.org/showthread.php?t=1479237)


can we get the driver devs to support penumbra better ?

---

### Post by handy on 2010-05-10
I expect that they have quite a few other priorities that are a lot higher than fixing how Penumbra runs at the moment.

The dev's would be trying to meet deadlines for the release of kernel .34 for starters.

---

### Post by madjr on 2010-05-11
> **handy said:**
> I expect that they have quite a few other priorities that are a lot higher than fixing how Penumbra runs at the moment.

The dev's would be trying to meet deadlines for the release of kernel .34 for starters.

now that penumbra will go open source , should be easier yay

---

### Post by handy on 2010-05-11
> **madjr said:**
> now that penumbra will go open source , should be easier yay

Yes it really has been a great week for the Linux community in particular. :)

---

### Post by Ubuntiac on 2010-05-11
> **madjr said:**
> now that penumbra will go open source , should be easier yay

Woah, really?! Hadn't heard that one yet! I also just bought it today as part of the Humble Indie Bundle. Still, not going to complain, I was mainly buying to support indie dev anyway. If they're going to release stuff as open source, well, bonus! :D

---

### Post by handy on 2010-05-11
> **Ubuntiac said:**
> Woah, really?! Hadn't heard that one yet! I also just bought it today as part of the Humble Indie Bundle. Still, not going to complain, I was mainly buying to support indie dev anyway. If they're going to release stuff as open source, well, bonus! :D

It will be the code that is opened up, the graphics & other content will still be closed. So the game will still have a price on its head. ;)

---

### Post by handy on 2010-05-12
[I]**X.Org Server 1.8.1 Released To The Wild**
Posted by Michael Larabel on May 11, 2010

X Server 1.8 was released in early April, but the first point release to this major X.Org update has now been pushed out by Peter Hutterer.

X.Org Server 1.8.1 boasts a variety of fixes and minor improvements while all major work is already focused on delivering X Server 1.9 that should make its debut in August. [/I]

Read on:

[http://www.phoronix.com/scan.php?page=news_item&px=ODI0Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODI0Mg)

---

### Post by screaminj3sus on 2010-05-12
I am currently running xorg 1.8 on arch and have been able to disable hal from starting up :) Seems to be very nice so far.

I am kinda gettin annoyed with the latest drm-radeon kernel. when I enable dynpm with it my screen flickers everytime it changes clocks (probabloy cause they indroduced early mem clock/voltage changing support I imagine) and my gui gets laggy, and profile pm just sucks and doesnt do anything to help temps unless i set it to run low all the time which makes scrolling in my web browsers laggy.

---

### Post by xir_ on 2010-05-12
> **Ubuntiac said:**
> Woah, really?! Hadn't heard that one yet! I also just bought it today as part of the Humble Indie Bundle. Still, not going to complain, I was mainly buying to support indie dev anyway. If they're going to release stuff as open source, well, bonus! :D

The released it because people donated over 1 million. Its great to have some games that will be open source and work on an open source driver stack on an open source kernel.

---

### Post by Ubuntiac on 2010-05-12
Just did some quick experimentation with Penumbra. Basically everything works fine except:

* Post processing (slow and turns the camera upside down)
* Motion blur (as above)
* Bloom
* Antialiasing (Penumbra won't even load with this on)

Everything else you can crank as high as is enjoyable on your card. Enjoy!

---

### Post by handy on 2010-05-12
> **screaminj3sus said:**
> I am currently running xorg 1.8 on arch and have been able to disable hal from starting up :) Seems to be very nice so far.

I am kinda gettin annoyed with the latest drm-radeon kernel. when I enable dynpm with it my screen flickers everytime it changes clocks (probabloy cause they indroduced early mem clock/voltage changing support I imagine) and my gui gets laggy, and profile pm just sucks and doesnt do anything to help temps unless i set it to run low all the time which makes scrolling in my web browsers laggy.

Yes, I'm using the packages & kernel from the Arch stable repo's currently. I'll go onto the dev' packages again when they start on kernel .35.

---

### Post by Old Marcus on 2010-05-13
For average use, office work, web browsing and watching the occasional movie, what driver would you recommend? For an ATI Radeon HD 4350. I want the least amount of potential hassle, basically.

---

### Post by madjr on 2010-05-13
> **Old Marcus said:**
> For average use, office work, web browsing and watching the occasional movie, what driver would you recommend? For an ATI Radeon HD 4350. I want the least amount of potential hassle, basically.

well the open driver is not bad for what you want and already preinstalled, so is less hassle

the binary is more for 3d gaming, etc.

anyway you can try them both.

the open driver is getting better and better each release

---

### Post by cTn on 2010-05-13
> **handy said:**
> **BigLouis87:** try "su" and then "*echo **X** > /sys/class/drm/card0/device/power_state*"
    make sure **X** is a valid status id!
    
My card has only status 0 and 1, so **X** can only be 0 or 1. (see below?)

You will see how many **Power State(s)** your card has when you run: "*dmesg | grep drm*"

Not that this works for my card at this stage, though it does for similar GPUs. My PM has very likely been bastardised by Apple. :-|

[I][drm] 2 Power State(s)
[drm] State 0  (default)
[drm] 	16 PCIE Lanes
[drm] 	3 Clock Mode(s)
[drm] 		0 engine/memory: 600000/650000
[drm] 		1 engine/memory: 600000/650000
[drm] 		2 engine/memory: 600000/650000
[drm] State 1 Performance 
[drm] 	16 PCIE Lanes
[drm] 	3 Clock Mode(s)
[drm] 		0 engine/memory: 600000/650000
[drm] 		1 engine/memory: 600000/650000
[drm] 		2 engine/memory: 600000/650000[/I]


this command isn't working anymore, do you know what happened? :(

---

### Post by murderslastcrow on 2010-05-13
Lol, I'm still interested in the progress here, but I totally sold my open-source-only ATi card (X1400) lappy to buy one with more official support. :3 Things really did get a lot better as time went on- I'm sure that, in a few years, we won't have to compromise, anymore. Things just keep getting more open, more supported, more functionality as time goes on. We've come so very far, but now we can show how far we really can go.

When we're done fighting against compatibility issues and hardware issues, just think what we could achieve! :D

---

### Post by handy on 2010-05-13
> **cTn said:**
> this command isn't working anymore, do you know what happened? :(

The kernel has been changing, have a read of the last 5 pages of so of this thread & see if that helps you out:

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

---

### Post by handy on 2010-05-13
> **Old Marcus said:**
> For average use, office work, web browsing and watching the occasional movie, what driver would you recommend? For an ATI Radeon HD 4350. I want the least amount of potential hassle, basically.

The OS solution should really be the best fit for you.

---

### Post by madjr on 2010-05-14
well i got penumbra working for me and is almost as good as when i was testing it in windows (i've also experienced glitches in windows a few times!...), so i decided that if am going to experience glitches it would be on linux :)

penumbra settings that i changed:

800x600 (yeap old lappy :/)
texture quality: medium
shadows: off
post effects: off
vsync: on
depth of field: off


with those settings is actually playable now for me (less glitchy)

so my half baked drivers are not so bad after all

---

### Post by cTn on 2010-05-14
> **handy said:**
> The kernel has been changing, have a read of the last 5 pages of so of this thread & see if that helps you out:

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

Problem is that they are all talking about the vanilla kernel etc, which have the power_state sysfs option but drm-next in our ubuntu doesn't have it or they replaced it so command is different :(

---

### Post by screaminj3sus on 2010-05-15
Yeah I can confirm the command I use for arch's drm-radeon-testing kernel:

> echo dynpm > /sys/class/drm/card0/device/power_method

Does not work with ubuntu's drm-next kernel

---

### Post by Confused Computer User on 2010-05-15
> **madjr said:**
> well the open driver is not bad for what you want and already preinstalled, so is less hassle

the binary is more for 3d gaming, etc.

anyway you can try them both.

the open driver is getting better and better each release

I disagree... I find the opposite to be true on my ATI Radeon X1600. 9.10 worked better than 10.04 which might I add required me to remove the card in order for it to function at usable speed. I mean why should I remove the card.... Now I can put it back in and see if it works better but I'm afraid of ruining the system. I'm not an expert on computing so I'd rather wait till 10.10 and try it then.

---

### Post by handy on 2010-05-17
**Kernel release: 2.6.34**

[http://www.linux.org/news/2010/05/16/0001.html](http://www.linux.org/news/2010/05/16/0001.html)

Now let's see what PM goodies (amongst other OpenGL associated speed improvements) get incorporated into kernel .35. :)

---

### Post by Old Marcus on 2010-05-18
> **handy said:**
> The OS solution should really be the best fit for you.

Ok, I'll go for the Open Source option then. How do I know if the ATI OS drivers are running, and not just a generic gfx driver?

---

### Post by handy on 2010-05-18
> **Old Marcus said:**
> Ok, I'll go for the Open Source option then. How do I know if the ATI OS drivers are running, and not just a generic gfx driver?

To check your installation run:

**glxinfo | grep -i opengl**

I get the following when I do that:

```
[I]OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:[/I]
```


There should be no string like this: 

*OpenGL renderer string: Software Rasterizer*

---

### Post by Old Marcus on 2010-05-18
Ok, thanks. :)

---

### Post by Navario on 2010-05-23
I just want to mention this important note from the xorg-edgers ppa. 

> libdrm's epoch was accidentally bumped in this PPA, if you updated  between 05-12 and 05-16 please run this command to fix it or it will no  longer update! Sorry for the inconvenience.
 Lucid:
sudo apt-get update && sudo apt-get install libdrm-dev/lucid  libdrm2/lucid libdrm-nouveau1/lucid libdrm-radeon1/lucid  libdrm-intel1/lucid
Maverick:
sudo apt-get update && sudo apt-get install libdrm-dev/maverick  libdrm2/maverick libdrm-nouveau1/maverick libdrm-radeon1/maverick  libdrm-intel1/maverick

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")


---

### Post by Xbehave on 2010-05-23
thanks, Navario. I don't have time to track development anymore so i would probably have missed that if you hadn't reposted it here :D

---

### Post by handy on 2010-05-23
Very interesting article, showing that AMD are starting to get the Catalyst driver sorted out:

[I]**The Cost Of Running Compiz**
Published on May 21, 2010
Written by Michael Larabel
Page 1 of 5
Discuss This Article

Earlier this week we published benchmarks comparing Arch Linux and Ubuntu. There were only a few areas where the two Linux distributions actually performed differently with many of their core packages being similar, but one of the areas where the results were vastly different was with the OpenGL performance as Ubuntu uses Compiz by default (when a supported GPU driver is detected) where as Arch does not. This had surprised many within our forums so we decided to carry out a number of tests with different hardware and drivers to show off what the real performance cost is of running Compiz as a desktop compositing manager in different configurations.

Read on:[/I]

[http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=1](http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=1)

---

### Post by DavidJohn212 on 2010-05-26
thanks handy ! thanks for this information & the list.....

---

### Post by DavidJohn212 on 2010-05-26
thanks handy! thanks for information & the list..........:KS

---

### Post by xir_ on 2010-05-26
> **handy said:**
> Very interesting article, showing that AMD are starting to get the Catalyst driver sorted out:

[I]**The Cost Of Running Compiz**
Published on May 21, 2010
Written by Michael Larabel
Page 1 of 5
Discuss This Article

Earlier this week we published benchmarks comparing Arch Linux and Ubuntu. There were only a few areas where the two Linux distributions actually performed differently with many of their core packages being similar, but one of the areas where the results were vastly different was with the OpenGL performance as Ubuntu uses Compiz by default (when a supported GPU driver is detected) where as Arch does not. This had surprised many within our forums so we decided to carry out a number of tests with different hardware and drivers to show off what the real performance cost is of running Compiz as a desktop compositing manager in different configurations.

Read on:[/I]

[http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=1](http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=1)

 i think that the reason the nvidia drivers are doing so well with compiz is that it make the drivers maintain a higher clock speed so the game performance increases.

Id like to see some clocking information to go with those benchmarks.

---

### Post by handy on 2010-05-26
[I]**Catalyst 10.5 For Linux Is Out: Nothing Exciting**

Posted by Michael Larabel on May 26, 2010

AMD has just put out their Catalyst 10.5 Linux driver update. Unfortunately, there isn't anything too exciting in this release.

Officially, the only new feature in Catalyst 10.5 for Linux is "early look" support for SUSE Linux Enterprise Desktop / SUSE Linux Enterprise Server 11 Service Pack 1. There are, however, resolved issues pertaining to Hybrid CrossFire, kernel panics on hibernation, and suspend-and-resume fixes. [/I]

Read on:

[http://www.phoronix.com/scan.php?page=news_item&px=ODI5Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODI5Mg)

---

### Post by babyhuey on 2010-05-28
I can't for the life of me get KMS running on my 10.04 installation. 
I have installed the lastest mainline drm-next from [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/)
And I have xorg-edgers ppa.

After booting into gnome there is no sign of "drm" in dmesg. 

The only error I get in Xorg.0.log is:
```
(EE) open /dev/fb0: No such file or directory
```

And the only warnings I get are:
```
[    28.262] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.292] (WW) Falling back to old probe method for vesa
[    28.292] (WW) Falling back to old probe method for fbdev
[    28.640] (WW) RADEON(0): Direct rendering disabled

```

One line I don't recall seeing the last time I used kms is the following
```
[KMS] drm report modesetting isn't supported.
```

This is with an Evergreen card(Desktop 5850) so I am of course not expected to get acceleration.

Thanks for the help!

---

### Post by handy on 2010-05-28
**@babyhuey:** Post your output from:

*glxinfo |grep -i opengl*

---

### Post by DoktorSeven on 2010-05-28
10.5 oddly broke 3d in Wine.  Yeah, Wine ONLY.  3d native apps, both 32 AND 64 bit worked great. 

Console kept complaining about GLXUnsupportedPrivateRequest any time I ran any 3d app in Wine.  Everything else ran just fine.

Reverted to 10.4 and everything is great.  No idea what the deal there is.

---

### Post by handy on 2010-05-28
I guess the Wine guys will have to work with it & present a Wine update that fixes the problem, if indeed it is their problem to fix.

---

### Post by DoktorSeven on 2010-05-29
Not sure if it's an ATi or Wine issue.  I have talked to some people that haven't had this problem at all, though, so it's all a bit strange.

---

### Post by del_diablo on 2010-05-29
Well, I updated from 10.4 to 10.5 on Archlinux. It solved quite a bit on of problems.
There is still a few rendering bugs here and there, but it works quite well.
Got to try the open drivers later.

---

### Post by KingBongo on 2010-05-30
Hi again. Thanks to this excellent thread and with the help from some clever guys I decided to buy an ATI Radeon HD4670 AGP graphics card since my Nvidia 7950GT AGP (combined with P4 3.06GHz Hyper Threading) does not seem to cut it when it comes to 1080p movies. The P4 is working at or close to 100% much of the time (both the real and the "ghost" processor) resulting in major stuttering. As I understand it the 7950GT does not support hardware encoding of H264 movies. That's probably the cause why vdpau (hardware encoding) isn't implemented by NVidia for this card anyway. Using coolbits I also tried to overclock the GPU and the memory, no worky. No surprise since the card isn't the bottleneck it seems. Because of these problems I probably need an AGP graphics card that supports hardware encoding, the best one being the HD4670. 

Before I buy the HD4670 card I have a few questions:

1. Can the situation be improved so that the 7950GT works with 1080p? I am tolking about a) better drivers, b) shutting down some processes, c) only running X without the desktop, c) overclocking the P4, c) a.s.o.

2. Is hardware encoding for the HD4670 supported by either the open source driver or Catalyst? Which movie players support hardware encoding in Linux? Without both of these components it would be useless to buy the card.

Please help!

---

### Post by handy on 2010-05-30
Someone may have answers for you, we'll see?

If I was in your situation I would be searching sites like VLC & mplayer to find out what they can & can't do for you.

I'd also be looking to see what the output is of the ATi GPU you are interested in, in comparison to the nVidia card you already own.

As far as drivers are concerned you always run the latest version, you could give the cutting edge ATi OSS drivers a go as well, as they are great with movies. See the how-to in the Ubuntu Stuff: section way down in the OP of this thread.

Check out this page: 

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature) 

& chase down more specifics if required from the x.org site.

Rather than running without a desktop you could try a light weight WM like Openbox.

I would have thought that the P4 was capable of running a hi-res movie?

You could have a bit of a browse through this thread, as there are people there using the 4570 GPU:

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

A reply from someone using an AGP 4570 GPU on a P4 system would probably be just what the Dr. ordered for you. ;)

---

### Post by KingBongo on 2010-05-30
handy:
Thank you! If I remember it correctly you are the guy who have been helping me the most with my questions. Thank you.

Yeah, I also thought that a maxed out P4 (second latest generation) would be enough, but no. The way I understand it the second latest generation is also a bit faster than the latest one, frequency-wise. What I have read is that the 3.06GHz processor is comparable to the 3.4GHz version of the latter in most cases. My problems must either come from some strange issue, or encoding 1080p is crazy intense. The movie just stutters or more correctly freezes for a few seconds all the time. So far I have tried (from the repositories) Miro, VLC and Movie Player, no luck.  

Whatever the reason, I am not giving up on this computer! Crazy fun ;) If I have to buy a new card I will do so.

I will read the links you posted.

EDIT:
I think you mean this link to RadeonHD, [http://www.x.org/wiki/radeonhd%3Afeature](http://www.x.org/wiki/radeonhd%3Afeature). I don't understand where it can be seen if hardware encoding of 1080p is supported or not. Can somebody help me?

---

### Post by MarcusW on 2010-05-30
This is not an answer to your question but still: If you buy a newer nvidia card you get VDPAU. Doesn't need to be an expensive one, as long as it is 8XXX or newer, why not buy a cheap nvidia card with passive cooling? :)

I never found a working solution for 1080p while I was using ATI (HD4850), and I always had screen tearing while playing videos. I think decoding 1080p is under "Video Decode (XvMC/VDPAU/VA-API)" on the page [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature), and it's either "N/A" or "TODO" so I wouldn't count on it right now.

---

### Post by handy on 2010-05-30
> **KingBongo said:**
> ... 
EDIT:
I think you mean this link to RadeonHD, [http://www.x.org/wiki/radeonhd%3Afeature](http://www.x.org/wiki/radeonhd%3Afeature). I don't understand where it can be seen if hardware encoding of 1080p is supported or not. Can somebody help me?

No, using radeonhd is not advised. Use the radeon = xf86-video-ati & associated packages.

Also, I run an AGP 7950GT card in an Athlon64 3500+, 2GB RAM, machine. It has no trouble at all playing videos at 1920x1200. Also I use VLC for all my video playback.

---

### Post by handy on 2010-05-30
[I]**Voltage Tweaking Comes To R600+ GPUs On Linux**
Posted by Michael Larabel on May 27, 2010

Earlier this month we reported on vastly improved ATI power management support within the open-source Radeon graphics driver stack for Linux that now supports dynamic power management along with different power management profiles. Following that we provided a detailed look at the ATI Linux power management support with plenty of charts showing how the power management is working out with this latest open-source code. [/I]

Read on:

[http://www.phoronix.com/scan.php?page=news_item&px=ODI5NA](http://www.phoronix.com/scan.php?page=news_item&px=ODI5NA)

---

### Post by handy on 2010-05-30
I had a spell from the radeon development packages for a couple of weeks or so because there was a bug effecting the display on my HD2600Pro. It wasn't much of a problem but it had been there for some weeks.

Anyway I just reinstalled the latest packages that Perry's put together into a repo (for Arch users) & the bug is now gone. Also the output of the **dmesg | grep drm** command now looks much less like work in progress.

I'm using the drm-radeon-testing kernel:

[http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing)

With all PM patches applied to it (by Perry).

Kernel .34 has been released (its in [testing] repo on Arch) so the changes happening in the kernel I'm using will be mostly about the GPU & PM, I would think.

---

### Post by KingBongo on 2010-05-30
Thanks for the answers!

MarcusW:
Problem is that I am using the AGP bus. 7950GT is (probably) the strongest Nvidia AGP card ever made. I think that there was one or more overclocked versions of it as well for sale, but since the P4 seems to be the bottleneck that wouldn't help much, if any. I believe I need hardware decoding to solve my issues, which the HD4670 provides. By the way, the HD4670 has the R700 chipset if I remember it correctly so hardware decoding it still to be implemented :(

handy:
Thank you for the advice on which driver to use, :) I believe the Athlon64 3500+ kills most any P4, doesn't it? Well, except for maybe the P4 Extreme which was very expensive back in the day and therefore is very rare. That might be the explanation if the videos were H264. Do you use VLC from the repos?

---

### Post by handy on 2010-05-30
> **KingBongo said:**
> ...
handy:
Thank you for the advice on which driver to use, :) I believe the Athlon64 3500+ kills most any P4, doesn't it? Well, except for maybe the P4 Extreme which was very expensive back in the day and therefore is very rare. That might be the explanation if the videos were H264. Do you use VLC from the repos?

Yes I think the Athlon I'm using is far more powerful than the P4s. I use VLC out of the Arch repo, so it is a later version than what's in the Ubuntu repo's.

I think your problem must be the CPU. My AGP 7950GT has never even looked like having trouble with videos, & it has played a lot of DVDs & various other formats all at 1920x1200 res'.

---

### Post by handy on 2010-05-30
> **MarcusW said:**
> ...
I never found a working solution for 1080p while I was using ATI (HD4850), and I always had screen tearing while playing videos. I think decoding 1080p is under "Video Decode (XvMC/VDPAU/VA-API)" on the page [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature), and it's either "N/A" or "TODO" so I wouldn't count on it right now.

I haven't had video tearing on my HD2600Pro for nearly 2 years. 

& since I've been using the Radeon OSS packages (10 months) I haven't experienced it all, though I know others have in the past.

---

### Post by del_diablo on 2010-05-30
> **MarcusW said:**
> I never found a working solution for 1080p while I was using ATI (HD4850), and I always had screen tearing while playing videos. I think decoding 1080p is under "Video Decode (XvMC/VDPAU/VA-API)" on the page [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature), and it's either "N/A" or "TODO" so I wouldn't count on it right now.

Running 3460 mobile I can testify that i have never experienced video tearing on my laptop.

---

### Post by screaminj3sus on 2010-05-30
I've never had tearing using the oss drivers either. (although I only started using them somewhat recently.)

fglrx however I have never NOT had tearing :p

---

### Post by purelinuxuser on 2010-05-30
Never noticed tearing with my ATI cards either.

As for the driver in general- the problem I see is performance/bugs being unevenly distributed among cards.  For instance, I have an X800XT with an EXTREMELY FAST bootup/shutdown time and fair 3d performance (10 or so FPS on FlightGear, on Google Earth I guess around 15).  However, my Xpress 200M on my old laptop has poor performance (4 FPS on FlightGear, probably 4 or 6 on Google Earth- not that Google Earth frame rates matter anyway, a perspective bug makes it unusable) and is LOADED with bugs. :( KMS/modesetting is broken, so there's a 1 in 8 chance it will actually start up properly (i.e. WITHOUT random stipple patterns on the boot splash and X).  At least suspend works properly :P

---

### Post by handy on 2010-06-02
[I]**Thermal Monitoring Comes To Newer Radeon DRM**
Posted by Michael Larabel on June 01, 2010

Over the past few days we have had a number of new open-source ATI Radeon support upbringings to report on including the ATI R600/700 Gallium3D driver being merged, voltage control for managing the power on newer ATI GPUs, and the ATI Radeon HD 5000 series Mesa code coming soon, but the slew of open-source ATI news is not over yet. [/I]

Read on:

[http://www.phoronix.com/scan.php?page=news_item&px=ODMxMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODMxMQ)

---

### Post by handy on 2010-06-09
Some people are finding that the most recent Catalyst release has a memory leak?

Check it out?

***[Edit:]** htop is good for observing such problems.*

---

### Post by KingBongo on 2010-06-14
Hi again. Can someone help me with this please. As previously mentioned and discussed, I bought this AGP card [http://www.hisdigital.com/un/product2-448.shtml](http://www.hisdigital.com/un/product2-448.shtml) and this adapter (DVI to S-video) [http://store.apple.com/us/product/M9267G/A?fnode=MTY1NDA3Ng&mco=MTA4NDU1Mjc](http://store.apple.com/us/product/M9267G/A?fnode=MTY1NDA3Ng&mco=MTA4NDU1Mjc) . 

People told me that if I were able to find an adapter from DVI to S-Video it would probably work. However, I get no picture on my old CRT TV. The TV detects some signal because it changes mode, but no real picture is to be seen. In the Monitor Preferences the Adapter+TV combo is detected as "Monitor: Apple Computer Inc 10" ". I have tried playing around with the resolution and the frequency (56Hz and 60Hz) in all possible configurations (only a few) but no luck. What can I do? 

My setup is the following:

Lucid Lynx
Kernel 2.6.35rc3-maverick
PPA-xorg-edgers repos added
updated and upgraded

---

### Post by handy on 2010-06-15
[I]**r300g performance**

Lately Marek Olšák has been focusing on r300g performance. He did a bunch of commits the last days that remove useless code and duplicated security checks. While doing so he also wrapped some debugging code to be enabled/disabled at compile time.

When a developer is focusing on performance this is generally a good sign, because it basically means that the groundwork is done.

On his way he also rewrote occlusion queries. The following commit line shows his intention:

This fixes flickering in Enemy Territory: Quake Wars. The driver now renders everything correctly in this game and the graphics is awesome.

I'll most likely grab myself a copy of the Enemy Territory: Quake Wars demo and test his latest achievements.[/I]

[http://tirdc.livejournal.com/27350.html](http://tirdc.livejournal.com/27350.html)

---

### Post by KingBongo on 2010-06-15
Man. I definitely agree that in 2D the open-source drivers are incredible! It is subtle, but everything seems smoother than ever. Nice.

Now, if somebody would only help me to get my S-Video going....

---

### Post by JDShu on 2010-06-15
> **handy said:**
> [I]**r300g performance**

Lately Marek Olšák has been focusing on r300g performance. He did a bunch of commits the last days that remove useless code and duplicated security checks. While doing so he also wrapped some debugging code to be enabled/disabled at compile time.

When a developer is focusing on performance this is generally a good sign, because it basically means that the groundwork is done.

On his way he also rewrote occlusion queries. The following commit line shows his intention:

This fixes flickering in Enemy Territory: Quake Wars. The driver now renders everything correctly in this game and the graphics is awesome.

I'll most likely grab myself a copy of the Enemy Territory: Quake Wars demo and test his latest achievements.[/I]

[http://tirdc.livejournal.com/27350.html](http://tirdc.livejournal.com/27350.html)

Yeah I've noticed that he's been committing a whole lot lately. I think I'm going to get a radeon card soon once I muster up the funds.

---

### Post by ttanev on 2010-06-15
> **JDShu said:**
> Yeah I've noticed that he's been committing a whole lot lately. I think I'm going to get a radeon card soon once I muster up the funds.

Just curious - what GPU do you use now ?

I am trying to adapt the switcheroo functionality [in here]("http://asusm51ta-with-linux.blogspot.com/2010/05/07052010-fedora-13-beta-kernel-2.html") on Ubuntu Lucid with Asus M51TR notebook with hd3200/hd3470 adapters and am following a guide to compile the kernel from gid:
[http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/)
When I checkout 2.6.35rc3-maverick and /as there is switcheroo support since 2.6.34/ and when I change the configuration with "debian/rules editconfigs" on the top of the window is 2.6.32... and there is no option "Device Drivers -> Graphics support -> Laptop Hybrid Graphics - VGA Switcheroo". Any ideas ? Is there shorter way to recompile the 2.6.35 kernel with such functionality and is there a how-to or guide how to do it. Thanks in advance.

---

### Post by handy on 2010-06-16
Good news for Catalyst users.

There are some very good reports coming in on Catalyst 10.6 on the Arch forum. It is using much less RAM & CPU time & the 2D acceleration is really working.

---

### Post by handy on 2010-06-17
Some more news on Catalyst 10.6:

[http://www.phoronix.com/forums/showthread.php?t=24296](http://www.phoronix.com/forums/showthread.php?t=24296)

---

### Post by ttanev on 2010-06-17
The so called Direct2D is now enabled by default and have huge improvement over last time I've tried it. Was ~2x.xx seconds, now it's:
[[IMG]http://img411.imageshack.us/img411/2350/screenshotgtkperf.th.png[/IMG]]("http://img411.imageshack.us/img411/2350/screenshotgtkperf.png")

There was a bug before and I wasn't able to refresh trough VNC with compiz enabled /with metacity everything was ok/, have to check if it's fixed already.

---

### Post by del_diablo on 2010-06-19
[http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_xv&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_xv&num=1)

And finally the opensource driver beats catalyst in anything besides 2D accel, which is sort of good news. 1080 decoding woho

---

### Post by handy on 2010-06-19
> **del_diablo said:**
> [http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_xv&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_xv&num=1)

And finally the opensource driver beats catalyst in anything besides 2D accel, which is sort of good news. 1080 decoding woho

The guys on the Arch forum aren't too impressed with the phoronix article, they find it to be incorrect in more than area.

See posts 1416 & beyond in this thread if you are interested:

[http://bbs.archlinux.org/viewtopic.php?pid=777616#p777616](http://bbs.archlinux.org/viewtopic.php?pid=777616#p777616)

---

### Post by handy on 2010-06-19
Apparently there are problems being found with Catalyst 10.6. One such has to do with the "black box" which is the kind of thing that if you experience it you will know what the description means.

The only solution found thus far is the following courtesy of balihb a Debian user on the Arch forum:

**aticonfig --set-pcs-str=DDX,ForceXAA,TRUE**

This way the 2D accel is set back to the old (slow) 10.5 way. I think that there won't be any real solution till 10.7.

Some doubt a solution will arrive that quickly...

---

### Post by Untitled_No4 on 2010-06-21
I've tried 10.6 on a test install, and although I was impressed the maximising/minimising bug is fixed and that it uses less RAM (but not as low as open source driver), there was a new bug I encountered: when dragging a window around it takes a split of a second before the window starts moving and then it moves too fast and slows as it reaches the current location of the mouse pointer.

---

### Post by KingBongo on 2010-06-26
Ok. Since I have been tricked to buy an Apple DVI-to-Video converter (don't worry about that) that doesn't work, maybe somebody can at least explain why it doesn't? ;) I have spent hours trying to understand it myself. I have been reading a ton in forums, reading about hardware, playing around with xrandr and other stuff. 

The way I understand it DVI-I (is on my card since it looks like one) has already VGA output built in as specified by standard, or more exactly analog output. So a DVI to VGA converter should always work as long as the operating system and the drivers are able to send out VGA via the DVI port. In fact, so far I haven't seen anything not working that way.

Here is what I am thinking; Apples DVI to (S-)Video converter takes that VGA (analog) signal and converts it to likewise analog (S-)Video signal by using only analog electric circuitry. I cannot see any reason how it could be any more complicated than that in that little thing. So after the conversion you should have an (S-)Video signal sent out which the CRT TV should be able to handle. So why isn't it working then? WTF? What am I missing here? If you have any ideas, please explain!

I an a little bit suspicious that the drivers are not working for that device, so the wrong signals are sent out in the first place. As I previously told you the converter is recognized as an "Apple 10" Monitor", which maybe there are no drivers for. Could that be it?

---

### Post by rajeev1204 on 2010-06-26
I dont know why you are comparing articles from phoronix or the arch forums when there are ATI users right here on this forum.

Iam using the 10.6 catalyst and its phenomenal .Like you already read , the only problem i had was with max and min and its fixed, with or without compiz.

Compiz is also smooth now .

And right now iam typing this while my quake 4 window is minimised ,well gaming has always been good with the drivers.

---

### Post by Martje_001 on 2010-07-02
> **KingBongo said:**
> Ok. Since I have been tricked to buy an Apple DVI-to-Video converter (don't worry about that) that doesn't work, maybe somebody can at least explain why it doesn't? ;) I have spent hours trying to understand it myself. I have been

[snip]

d that be it?
Have you tried lowering the refresh rate? My TV can only handle 100 Hz and its halves (so 50 Hz, 25 Hz).

---

### Post by KingBongo on 2010-07-02
Martje_001:
Please tell me HOW! I would like to try different refresh rates, interlaced vs. non-interlaced modes and also different resolutions, but I don't know how!

---

### Post by rihad on 2010-07-04
I have a ATI video card identified as 
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
on Kubuntu 10.04. After a recent "aptitude safe-upgrade" about a month ago the box started to freeze when I try to shut it down or reboot (either in KDE, or by means of the poweroff/halt/shutdown command) with the monitor being turned off, and cannot continue to shut down properly, necessitating pressing the PC power button. Also, when I switch to 1-st VT using Ctrl+Alt+F1, the screen turns off instead of showing the login prompt. Ctrl+Alt+F7 brings me back to X. I've found a workaround: Log out from KDE first, and only after that choose "turn off" in the menu. I've opened a [thread](http://kubuntuforums.net/forums/index.php?topic=3112509.15), some folks suggested that ATi dropped support for my card (RV370) about a year ago, and I should switch to the open-source driver. How can I install it then?
> rihad@rihad:~$ dpkg -l|fgrep radeon
ii  libdrm-radeon1                       2.4.18-1ubuntu3                                 Userspace interface to radeon-specific kerne
ii  radeontool                           1.6.1-0ubuntu1                                  utility to control ATI Radeon backlight func
ii  xserver-xorg-video-radeon            1:6.13.0-1ubuntu5                               X.Org X server -- AMD/ATI Radeon display dri
rihad@rihad:~$
> rihad@rihad:~$ dpkg -l|fgrep fgl
ii  fglrx                                2:8.723.1-0ubuntu4                              Video driver for the ATI graphics accelerato
ii  fglrx-amdcccle                       2:8.723.1-0ubuntu4                              Catalyst Control Center for the ATI graphics
ii  fglrx-modaliases                     2:8.723.1-0ubuntu4                              Identifiers supported by the ATI graphics dr
ii  xorg-driver-fglrx                    2:8.723.1-0ubuntu4                              Transitional package for xorg-driver-fglrx
rihad@rihad:~$

Thanks.

---

### Post by shane2peru on 2010-07-14
> **handy said:**
> *Added Power Management how-to on 14-April-10 - link update 3-June-10*



**Power Management:**

This is how I set it up in Kubuntu (10.04 with kernel 34 and xorg edgers as per your instructions in first post)= steps 1 -> 7 just above:

```
sudo kate /etc/modprobe.d/radeon-kms.conf
```

(use gedit instead of kate if you're not running KDE)

That file should already be there, add dynpm=1 at the end of it. Mine now looks like that:

```
options radeon modeset=1 dynpm=1
```

reboot and run

```
dmesg | grep drm
```

and somewhere along the output you should find:
[drm] radeon: dynamic power management enabled
[drm] radeon: power management initialized


Thanks for this PM info.  If we add that there, does that mean we don't need to add it in the command line part of the kernel line? I have that in this file:  /etc/default/grub this line: GRUB_CMDLINE_LINUX_DEFAULT=dynpm=1  with some other options, does that cause it to load twice?

Also something interesting that I ran into and seemed to help was configuring the k10temp module to work with the kernel you can see the how to here:

[http://ubuntuforums.org/showthread.php?t=1287819](http://ubuntuforums.org/showthread.php?t=1287819)


Shane

---

### Post by handy on 2010-07-17
**@shane2peru:** I'd just try removing the command from Grub to see if you still need it. ;)

I run the commands from both my (old) Grub kernel line & from modprobe.d/radeon.conf on my Arch/Openbox setup.

Not that it does me any good as thus far the PM features of provided by the open drivers don't work on the HD2600Pro in my iMac, (& due to its bastardisation by Apple it may never be supported) not that it really matters as it always runs quiet & cool anyway, though I would like to be able to regulate power usage to some degree if possible.

I am in the process of upgrading my Arch system as I type this (very large upgrade as I have been away for a month) so who knows what changes I will find in the current development packages?

If there is anything interesting I'll post it here (as usual ;)).

---

### Post by handy on 2010-07-17
I've just upgraded & am using the most current [stable] kernel.34 in Arch, with the appropriate dev' packages that Perry3D tests & puts together in a repo for Arch users that want to use them.

I've found that I don't need to add any parameters to the menu.lst kernel line to have both KMS & PM functioning.

(It may be worth noting that Arch doesn't use the new version of Grub, & does a few other things differently than the *buntu variants do.)

When I upgraded I also upgraded the *kernel26-drm-radeon-testing* (which I have been using for sometime) but found my networking was broken? So I'll use the current stable kernel.34 kernel (which I run in parallel) until the bug wherever it lies is fixed.

---

### Post by handy on 2010-07-17
For anyone using the kernel26-drm-radeon-testing 20100712-1 , if your network does not start. Try entering the following in the terminal:

**sudo dhcpcd eth0**

Fix courtesy of *roughL* on the Arch forum.

---

### Post by handy on 2010-07-21
I just upgraded to kernel26-drm-radeon-testing 20100721-1, & I'm still experiencing the same network bug.

Fortunately the easy fix of just entering:

**sudo dhcpcd eth0**

Still works.

On another note, the OpenGL speed of this testing kernel is dreadful on my machine:

[i]OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL DRI2
OpenGL version string: 2.0 Mesa 7.9-devel
OpenGL shading language version string: 1.10
OpenGL extensions:
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.

304 frames in 5.0 seconds = 60.778 FPS
302 frames in 5.0 seconds = 60.324 FPS
302 frames in 5.0 seconds = 60.324 FPS
302 frames in 5.0 seconds = 60.324 FPS
302 frames in 5.0 seconds = 60.324 FPS
302 frames in 5.0 seconds = 60.324 FPS[/i]

I expect that there will be a new release with a fix for this pretty quickly. :)

---

### Post by Kazade on 2010-07-22
> **handy said:**
> 
On another note, the OpenGL speed of this testing kernel is dreadful on my machine:

[i]OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL DRI2
OpenGL version string: 2.0 Mesa 7.9-devel
OpenGL shading language version string: 1.10
OpenGL extensions:
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.

304 frames in 5.0 seconds = 60.778 FPS
302 frames in 5.0 seconds = 60.324 FPS
302 frames in 5.0 seconds = 60.324 FPS
302 frames in 5.0 seconds = 60.324 FPS
302 frames in 5.0 seconds = 60.324 FPS
302 frames in 5.0 seconds = 60.324 FPS[/i]

I expect that there will be a new release with a fix for this pretty quickly. :)

Erm... glxgears is not a benchmark :) 

"Running synchronized to the vertical refresh. The framerate should be approximately the same as the monitor refresh rate."

The refresh rate of your monitor is 60hz, when vsync is enabled you'll never get a framerate higher than the refresh rate. The drivers are working fine :)

EDIT: Apparently there is a bug where vsync is always on, but when vsync is enabled the behaviour you are seeing is correct. See: [https://bugs.freedesktop.org/show_bug.cgi?id=28771](https://bugs.freedesktop.org/show_bug.cgi?id=28771)

---

### Post by handy on 2010-07-22
Yes, you are right Kazade, I was just coming back to post about that & read your post. :)

I am no expert on this stuff, I just keep following it & reporting what I think is interesting in the hope that someone finds it helpful or interesting at least. ;)

I do what I do to the best of my understanding, beyond that, I'm always happy to have my understanding increased...

On another branch, we mostly all know that glxgears is NOT a benchmark, but we mostly ALL use it as a general indication of OpenGL performance. Which kind of makes it a pain in the ****.

I don't feel like doing a phoronix test suite run every time I install a new kernel or mesa development set, which can be daily at times. 

So what do you do?

---

### Post by Kazade on 2010-07-22
> **handy said:**
> 
So what do you do?

True. It's a shame there's not an actual mini benchmark tool. Perhaps I should write one ;)

Luke.

---

### Post by handy on 2010-07-22
> **Kazade said:**
> True. It's a shame there's not an actual mini benchmark tool. Perhaps I should write one ;)

Luke.

Please, please do?

You will become an open source legend if you do. :)

Tough job though, if it wasn't someone would have already got around to doing it already.

Could the glxgears code be used as a base to start from?

---

### Post by handy on 2010-07-25
The previously mentioned problem with *vsync vblank* in the kernel26-radeon-testing can be fixed a variety of ways, this shows a quick & easy way:
[B]
vblank_mode=0 glxgears[/B]

---

### Post by pinguy on 2010-07-25
> **handy said:**
> Please, please do?

You will become an open source legend if you do. :)

Tough job though, if it wasn't someone would have already got around to doing it already.

Could the glxgears code be used as a base to start from?

[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)
Already been done.

---

### Post by handy on 2010-07-25
> **pinguy said:**
> [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)
Already been done.

I know about that, if you look back aways in this thread you will see posts of my results using it. :)

What we want is a simple, reliable tool that gives us a means of gaining a 3D benchmark quickly.

The phoronix test suite is, as it states, a test suite.

---

### Post by pinguy on 2010-07-25
> **handy said:**
> I know about that, if you look back aways in this thread you will see posts of my results using it. :)

What we want is a simple, reliable tool that gives us a means of gaining a 3D benchmark quickly.

The phoronix test suite is, as it states, a test suite.

Sorry my bad :) should of read the earlier posts before hijacking the thread.

---

### Post by handy on 2010-07-25
> **pinguy said:**
> Sorry my bad :) should of read the earlier posts before hijacking the thread.

No worries mate. :)

I don't think too many people are ever going to bother reading 630~ posts of out of date info' to see what they have been missing. ;)

---

### Post by handy on 2010-07-28
I would post something in regard to the ATi OSS situation if I knew of it. It seems that right now is about as slow for development as I have seen it over the last 12 months. I'm sure that this situation like all others will change soon enough.

---

### Post by gloken on 2010-08-05
Hey, I have to apologize for not reading the thread, but it's a monster.
Is there 3D support for the open ATI drivers yet?

I've got an ati radeon hd 3600 sitting in my box, previously I'd been running the proprietary drivers, but as part of a house cleaning attempt I've upgraded to Karmic and need to set the video card up again. 

Should I go crawling woefully back to the proprietary drivers, or can I (somehow) get some kind of 3d support from the open driver?

---

### Post by xir_ on 2010-08-05
> **gloken said:**
> Hey, I have to apologize for not reading the thread, but it's a monster.
Is there 3D support for the open ATI drivers yet?

I've got an ati radeon hd 3600 sitting in my box, previously I'd been running the proprietary drivers, but as part of a house cleaning attempt I've upgraded to Karmic and need to set the video card up again. 

Should I go crawling woefully back to the proprietary drivers, or can I (somehow) get some kind of 3d support from the open driver?

ATI drivers are now very good, yours comes under the r600 core I believe. It is very well supported and as of maverick will have some good power management.
Here is a link to the current feature set [link ]("http://www.x.org/wiki/RadeonFeature")



On a more handy note (ha) there is some info on the 36 kernel that just came out on [phrononix]("http://www.phoronix.com/scan.php?page=news_item&px=ODQ3NQ"). (id read the comments too).

---

### Post by Kazade on 2010-08-05
> **gloken said:**
> Hey, I have to apologize for not reading the thread, but it's a monster.
Is there 3D support for the open ATI drivers yet?

I've got an ati radeon hd 3600 sitting in my box, previously I'd been running the proprietary drivers, but as part of a house cleaning attempt I've upgraded to Karmic and need to set the video card up again. 

Should I go crawling woefully back to the proprietary drivers, or can I (somehow) get some kind of 3d support from the open driver?

If you fancy being a bit risky, installing the 2.6.35 kernel from mainline packages along with the xorg-edgers PPA can give you pretty good 3D support. Once 2.6.36 hits mainline we'll also get a large speed increase from the colour tiling support which is to be introduced.

If you wanna be less risky, install the xorg-edgers PPA and leave the kernel alone.. it's still quite risky though :)

---

### Post by gloken on 2010-08-05
> **Kazade said:**
> If you fancy being a bit risky, installing the 2.6.35 kernel from mainline packages along with the xorg-edgers PPA can give you pretty good 3D support. Once 2.6.36 hits mainline we'll also get a large speed increase from the colour tiling support which is to be introduced.

If you wanna be less risky, install the xorg-edgers PPA and leave the kernel alone.. it's still quite risky though :)

My learning process with ubuntu involves tanking my system and swearing for six days.

With that said though... how concerned should I be about doing this? If I'm doing kernel upgrades, I'm tempted to move ahead to 10.04 while I'm at it, since it's LTS. Not that I'd imagine that would help me much in this case.

---

### Post by Kazade on 2010-08-05
> **gloken said:**
> My learning process with ubuntu involves tanking my system and swearing for six days.

With that said though... how concerned should I be about doing this? If I'm doing kernel upgrades, I'm tempted to move ahead to 10.04 while I'm at it, since it's LTS. Not that I'd imagine that would help me much in this case.

Well, 10.04 only comes with the 2.6.32 kernel - so I was jumping you even further than that :)

I'd recommend that you install 10.04, and then the stable updates xswat ppa. That's really safe. 

If that doesn't give you OSS 3D acceleration, then you'll need to add xorg-edgers to get it which is pretty experimental and can break. Only do it if you have backups and aren't worried about dealing with breakage. 

If that works and you still wanna push it further, you can download a pre-packaged 2.6.35 kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-maverick/)

So, it depends how risky you wanna be really. Xswat is safe, xorg-edgers is less safe, xorg-edgers plus 2.6.35 has the potential to break more (like Wifi or something).

---

### Post by handy on 2010-08-05
I've mostly been using the development kernels for many months now. I've not had any real problems they have been perfectly stable.

There is a how-to for xorg-edgers & such low down in the OP of this thread for anyone interested.

---

### Post by handy on 2010-08-20
The following should make the owners & potential owners of the ATI Radeon HD 5000 "Evergreen" family happy: :D

[http://www.phoronix.com/scan.php?page=news_item&px=ODUzMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODUzMQ)

[http://www.phoronix.com/scan.php?page=article&item=amd_evergreen_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_evergreen_3d&num=1)

---

### Post by chris200x9 on 2010-08-20
> **handy said:**
> The following should make the owners & potential owners of the ATI Radeon HD 5000 "Evergreen" family happy: :D

[http://www.phoronix.com/scan.php?page=news_item&px=ODUzMQ](http://www.phoronix.com/scan.php?page=news_item&px=ODUzMQ)

[http://www.phoronix.com/scan.php?page=article&item=amd_evergreen_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_evergreen_3d&num=1)

any news of an aur package?

---

### Post by handy on 2010-08-20
No news at this early stage.

I'll post here when Perry has put together a package for Arch.

---

### Post by Untitled_No4 on 2010-08-22
This is for future reference for 10.10 since the ATI power management works differently than it did on 10.04.

Firstly, there is no need to install a mainline Kernel or use the xorg edgers repository in Maverick to get dynamic power management.

To enable dynamic power management one has to use the root user since sudo will not work here. Since Ubuntu by default doesn't set a root password, if you haven't already set up a root password you will have to do it now by running:
```
sudo passwd root
```
then enter your password, your new root password and repeat root password. 

Now switch to root by running:
```
su
```
and entering your password.

By default the system enables power management profiling. You can enable dynamic power management by running:
```
echo dynpm > /sys/class/drm/card0/device/power_method
```
(your card might not be card0, so double check it first). You can enable the power management profiling again by running
```
echo profile > /sys/class/drm/card0/device/power_method
```

When using power management profiles you can switch profiles by running
```
echo $PROFILE > /sys/class/drm/card0/device/power_profile
``` (again, assuming your card is card0), with $PROFILE being either one of these options: default, auto, high, low.

These settings are not permanent and will revert to default when rebooting the system. 

Despite this my system still runs hotter using the open source drivers than it is using the proprietary drivers (although not as hot as it used to get in Lucid). Two other problems push me personally back to the proprietary driver:
1. There is no power management for the open source drivers when used with dual monitors.
2. A bug that affects my particular setup (laptop + two external monitors).

I really hope that one day I will be able to use the open source drivers since I think they run better, and in my experience they use much less RAM. Unfortunately I think that to ever be able to use the open source drivers I will have to get a new machine altogether, but hopefully this information will help someone else when using/testing Maverick.

---

### Post by handy on 2010-08-24
People are starting to make use of the following Gallium packages:

mesa-git-gallium 
ati-dri-git-gallium  
libgl-git-gallium

Perry is looking into the possibility of organising pre-compiled packages for Arch users. I don't expect they are too far off. :)

[quote=Perry3D on Arch forum:]
*But there seems to be a way to have classic mesa and gallium installed parallel. You just have to change an environment variable to switch to gallium (LIBGL_DRIVERS_PATH). That works for different applications separately. For example "LIBGL_DRIVERS_PATH=/usr/lib/radeon-gallium glxgears". A mesa-full package with classic mesa and gallium (r300 - r700) would be really cool.*[/quote]

---

### Post by MooPi on 2010-08-28
Not certain what I'm using other than the name on lsmod (radeon). But I don't see a need to go any further then that in regard to tweaking my system drivers. The 3d acceleration is great with the standard xorg.server. Bravo open ATI. 
  Curious if this would be good enough for compiz features. I only ask because I currently don't use it. Also would the standard radeon driver work for gnome-shell which I'm not using either. My install is Lucid 10.04 testing on a budget build computer.

---

### Post by handy on 2010-08-28
> **MooPi said:**
> Not certain what I'm using other than the name on lsmod (radeon). But I don't see a need to go any further then that in regard to tweaking my system drivers. The 3d acceleration is great with the standard xorg.server. Bravo open ATI. 
  Curious if this would be good enough for compiz features. I only ask because I currently don't use it. Also would the standard radeon driver work for gnome-shell which I'm not using either. My install is Lucid 10.04 testing on a budget build computer.

I've got the current development packages that Perry has put together installed on my machine but I haven't tested them yet (still commented out in menu.lst) as I've got the machine busy doing other things currently.

Gallium will eventually supersede the classic Mesa packages, so eventually at least all the open driver users will be using it. But it will take a while for that to happen.

I never use compiz. I don't even use icons & windows, so it wouldn't do much for me anyway. lol

I think it works fine with the radeon packages.

As far as the Gnome shell is concerned (I hear about here & there) I don't even know what it is. Not interested, I'm a happy Openbox user. Anyway I expect that it will work fine with the open radeon drivers too.

People are getting fantastic frame rates out of 3D games running the quake engines, online with people speeding around everywhere trying to kill each other.

Sometimes I think that there really is no hope for humanity... hmm.

---

### Post by xir_ on 2010-08-29
someone told me that the Xorg Edgers includes the latest kernel DRM, can anyone confirm this. I always assumed that it update xorg and mesa.

---

### Post by handy on 2010-08-30
> **xir_ said:**
> someone told me that the Xorg Edgers includes the latest kernel DRM, can anyone confirm this. I always assumed that it update xorg and mesa.

Go & have a look at their site, you will see what they have listed?

There is a link in the OP of this thread I believe, the link above edgers is the kernel-ppa, you will find your answers in those two links.

---

### Post by meborc on 2010-09-09
> **Untitled_No4 said:**
> ...
To enable dynamic power management one has to use the root user since sudo will not work here. Since Ubuntu by default doesn't set a root password, if you haven't already set up a root password you will have to do it now by running:
```
sudo passwd root
```
then enter your password, your new root password and repeat root password. 

Now switch to root by running:
```
su
```
and entering your password.
...

don't do that... there is no reason to come up with root password... :)

use "sudo -i" instead to gain temporary root

---

### Post by Ubuntiac on 2010-09-10
Gah. Lucid +ATI worked fine for desktop effects on my laptop, but now Maverick + ATI I get told that "Desktop effects cannot be enabled for the following technical reason" (with no reason listed).

Time to go bug hunting methinks....

---

### Post by Ayuthia on 2010-09-10
> **Ubuntiac said:**
> Gah. Lucid +ATI worked fine for desktop effects on my laptop, but now Maverick + ATI I get told that "Desktop effects cannot be enabled for the following technical reason" (with no reason listed).

Time to go bug hunting methinks....

I am not for sure about the cause if it, but I ran into that with my laptop a while back also.  I found somewhere that if you go into ~/.kde4/share/config/kwinrc and look for:
```

[Compositing]
CheckIsSafe=false

```
and change it to true, it should work.  At least that is what I ended up doing.

---

### Post by SeePU on 2010-09-14
ATI open drivers don't work on Evergreen cards, right?   I mean, not for 3D... right?   That was my impression.   Can anyone confirm?  If you have a HD 5xxx card and use open drivers, can you try a 3D application?

I think the ATI drivers, both binary and open source leave a lot to be desired.  How is your HD 5xxx card for you in Lucid or Maverick?

It seems that the 'play catch-up' path is very frustrating as I read way more posts of ATI drivers not working or delivering function of the card than any Nvidia problems.   The Nvidia open source drivers obviously suck more but Nvidia is not asserting to have much of an open source driver.

---

### Post by del_diablo on 2010-09-23
5xxx is.... gaining support in the FLOSS driver.
Check phoronix on it.
*sigh* I am sort of annoyed at the development, its still ages until I can run anything I assume.

---

### Post by del_diablo on 2010-09-25
If anybody is running the latest and bleeding drivers: Does performance exists under 3D yet for 2xxx, 3xxx or 4xxx series?

---

### Post by CarpKing on 2010-09-25
> **del_diablo said:**
> If anybody is running the latest and bleeding drivers: Does performance exists under 3D yet for 2xxx, 3xxx or 4xxx series?

What do you mean by "performance?"  I have a 4xxx series, and Compiz and glxgears work fine with the drivers that came with Lucid.  I don't have any 3d games at the moment, though, so I can't test how they work.

---

### Post by Ric_NYC on 2010-09-25
Something good happened!!! What's changed? :confused:
I have an "old" ATI Radeon™ Xpress 1200 Graphics.
Now I can watch Youtube videos in full screen. No more choppy videos.



Maverick Meerkat, Acer Aspire 5515.

---

### Post by iarenoob on 2010-09-29
Hi, my kernel is 2.6.32-24 (lucid) which isn't listed in the index that is linked to on the first post.  While file am i supposed to download?  Also, the packages are kernel-specific, but not card-specific? does each package include drivers that work for every card? O_O

Im using an "evergreen" car (HD 5000) and I think the driver can only be compiled from source, any1 know where i can get the source code for it?

---

### Post by Lucradia on 2010-09-29
Also know that it won't be called ATi after this year. It'll just be AMD from now on.

---

### Post by the_jlx on 2010-09-29
ubuntu 10.04 = death for my radeon 9800 AIW
makes me want to QQ that i have to go back to windows on this machine.:(:(:(
oh well my main machine uses nvidia 250gts damm all i wanted to do is to have a extra ubuntu machine running
Edit: rebooting back into shame

---

### Post by iarenoob on 2010-09-29
The .deb's linked to in the first post don't work for evergreen right?  I'm pretty sure the evergreen drivers exist but i can't find them anywhere, can someone point me to where the source code is?

---

### Post by Dustin2128 on 2010-09-29
> **Lucradia said:**
> Also know that it won't be called ATi after this year. It'll just be AMD from now on.
been calling it AMD since june to get myself ready.

---

### Post by del_diablo on 2010-09-30
> **iarenoob said:**
> Hi, my kernel is 2.6.32-24 (lucid) which isn't listed in the index that is linked to on the first post.  While file am i supposed to download?  Also, the packages are kernel-specific, but not card-specific? does each package include drivers that work for every card? O_O

They are suppose to be partially "series" spesific.
The ATI driver is suppose to be for 9800 and before, but it seems they recently broke it in the update frenzy(source: the_jlx). Sort of a shame?
The radeon driver is suppose to be for the KMS and everything after 2xxx series(and some of the 1xxx series i heard).
I recommend testing the drivers, and report how they work.

---

### Post by Slug71 on 2010-09-30
Is both the ATI Open drivers and Nouveau using Gallium for 3D?

---

### Post by iarenoob on 2010-09-30
> **del_diablo said:**
> They are suppose to be partially "series" spesific.
The ATI driver is suppose to be for 9800 and before, but it seems they recently broke it in the update frenzy(source: the_jlx). Sort of a shame?
The radeon driver is suppose to be for the KMS and everything after 2xxx series(and some of the 1xxx series i heard).
I recommend testing the drivers, and report how they work.

umm, does that mean they don't work for evergreen? and if I used those drivers which package should i download, my kernel doesn't seem to be listed there

---

### Post by JDShu on 2010-09-30
> **Slug71 said:**
> Is both the ATI Open drivers and Nouveau using Gallium for 3D?

AMD has two open drivers, the Gallium drivers and the "Classic" drivers which don't use Gallium. Right now for the newer cards, the Classic drivers are better, but the majority of the progress is being made in their Gallium drivers. For the older cards, the Gallium Drivers are on par with the Classic ones.

---

### Post by Slug71 on 2010-09-30
> **JDShu said:**
> AMD has two open drivers, the Gallium drivers and the "Classic" drivers which don't use Gallium. Right now for the newer cards, the Classic drivers are better, but the majority of the progress is being made in their Gallium drivers. For the older cards, the Gallium Drivers are on par with the Classic ones.

Thanks.

---

### Post by sandyd on 2010-10-02
Im noticing a huge difference as well in OSS Radeon over the last while as well.

I can now easily play 1080p (blu-ray) on a 3650 mobility card (through HDMI) without any lag at all....
Ive totally switched over.

---

### Post by Dustin2128 on 2010-10-02
> **sandyd said:**
> Im noticing a huge difference as well in OSS Radeon over the last while as well.

I can now easily play 1080p (blu-ray) on a 3650 card without any lag at all....
I should hope so, especially seeing as I can do the *exact same thing *on my laptop with an integrated chip. The point is moot though, since I don't own a display capable of 1920x1080 :(. I have to hookup a second monitor just to see the whole thing... I think I know what I'm going to be getting after the dual geforce gt 240s.

---

### Post by sandyd on 2010-10-03
> **JDShu said:**
> AMD has two open drivers, the Gallium drivers and the "Classic" drivers which don't use Gallium. Right now for the newer cards, the Classic drivers are better, but the majority of the progress is being made in their Gallium drivers. For the older cards, the Gallium Drivers are on par with the Classic ones.
How can I tell which ones im using?
according to emerge....
```

sandy@sandyd-laptop /etc/kde/startup $ sudo emerge -pv xf86-video-ati
Password: 

These are the packages that would be merged, in order:

Calculating dependencies... done!
[ebuild   R   ] x11-drivers/xf86-video-ati-6.13.1  0 kB

Total: 1 package (1 reinstall), Size of downloads: 0 kB

 * IMPORTANT: 4 news items need reading for repository 'gentoo'.
 * Use eselect news to read news items.

sandy@sandyd-laptop /etc/kde/startup $ 


```
im using 6.13.1

---

### Post by del_diablo on 2010-10-03
> **iarenoob said:**
> umm, does that mean they don't work for evergreen? and if I used those drivers which package should i download, my kernel doesn't seem to be listed there

I said "parts of 1xxx, and 2xxx and higher".
Evergreen is the 4xxx series was it? It works, but I got no idea how good.
Frankly, thread needs somebody posting "how well it works" on the different series, because there are not enough information about it.
The radeon feature page is a bit useless since it too dated, and not everything is tested(IT SHOULD be tested).

---

### Post by JDShu on 2010-10-03
> **sandyd said:**
> How can I tell which ones im using?


Being that all I do is lurk the Phoronix forums, I couldn't tell you 100%. If you are using an r600 card though (HD 2000 or greater I think) then I'm pretty sure it defaults to the classic drivers. On Gentoo, it looks like the "gallium" USE flag is masked. I haven't used Gentoo in years though, so I can't tell you any more than that, sorry :(

---

### Post by Ayuthia on 2010-10-03
> **sandyd said:**
> How can I tell which ones im using?
according to emerge....
```

sandy@sandyd-laptop /etc/kde/startup $ sudo emerge -pv xf86-video-ati
Password: 

These are the packages that would be merged, in order:

Calculating dependencies... done!
[ebuild   R   ] x11-drivers/xf86-video-ati-6.13.1  0 kB

Total: 1 package (1 reinstall), Size of downloads: 0 kB

 * IMPORTANT: 4 news items need reading for repository 'gentoo'.
 * Use eselect news to read news items.

sandy@sandyd-laptop /etc/kde/startup $ 


```
im using 6.13.1

If I remember correctly, you need to check what mesa is using.  You should be able to see it if you do:
```
eslect mesa list
```
In order to get the gallium portion enabled, you will need to pull it from x11-overlay.  At least that is what I recall doing when I was using it.

I am still using the fglrx drivers for now with my laptop (It has the HD3200).  Mainly because it still runs 10-20C hotter with the open source version but I do feel that the open source version performs better than the fglrx driver.

---

### Post by sandyd on 2010-10-04
> **Ayuthia said:**
> If I remember correctly, you need to check what mesa is using.  You should be able to see it if you do:
```
eslect mesa list
```In order to get the gallium portion enabled, you will need to pull it from x11-overlay.  At least that is what I recall doing when I was using it.

I am still using the fglrx drivers for now with my laptop (It has the HD3200).  Mainly because it still runs 10-20C hotter with the open source version but I do feel that the open source version performs better than the fglrx driver.
ah. So I need mesa from the x11 overlay in order to get gallium.

EDIT: great! I see it now.
thanks!

Now to see if KDE 4.5 is going to be fuzzy about which opengl driver I use...

---

### Post by avengerxp on 2010-10-06
having an ATI x1950... as at today my experience with ubuntu 10.04 has been bitter (being a hardcore multimedia n gamer in XP)

switchin back to old humble XP is the only solution i see

---

### Post by yodermk on 2010-10-24
Ok so I upgraded from Lucid to Maverick, and my Radeon 3200 HD continued to work with desktop effects, I think a bit better than before.

Was working fine for a week (with no shutdown), then all of a sudden things started wacking out -- all black tooltip windows, crazy wide window borders, and grey translucent menus with no text.  Rebooted, then desktop effects became so slow that KDE disabled them.  (Those problems were still visible before KDE disabled them.)

Just tried a live CD, that worked fine.

No matter what I do I can't get it back on my installed system.  When I tried to enable effects in Gnome it said no driver could be found.  I suppose a re-install would fix it but I really want to avoid that if at all possible.

In xorg.conf it was set to the 'ati' driver (I'm not sure how it was set when it worked).  I changed it to 'radeon' with no difference.

Any help would be appreciated.  I didn't want to spend my weekend debugging X failure - I kind of thought Linux was past that. :(

---

### Post by handy on 2010-10-24
Sorry *yodermk*, I can't help you with Ubuntu upgrade problems. :(
___________

I've been away in Europe for a month, so I'm a bit out of touch. 

I upgraded my Arch system & everything is running fine here on my HD2600Pro. 

As JDShu has already stated, *Gallium* is where the prime development action is currently heading.

I'll post these links *which are all(?) on the OP* again, as the first link gives you an idea of where the current development is up to, & the 2nd link helps people work out just what series of GPU they are actually running:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

The next one is linked on the above page but I'll add it here anyway:

[http://www.x.org/wiki/GalliumStatus](http://www.x.org/wiki/GalliumStatus)


[http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units](http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units)

& this fourth link, may help intermediate users get more of an understanding re. gallium & some, (You can install both the classic & gallium AMD support & do a little fiddle to switch between them:

[https://bbs.archlinux.org/viewtopic.php?id=79509&p=1](https://bbs.archlinux.org/viewtopic.php?id=79509&p=1)


[I]**[Edit:]** The following command should give you feedback on your GPU's driver installation;- helpful if you have installed both classic-mesa & gallium:

```
LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri_g/ glxinfo |grep -i opengl
``` [/I]

I'm NOT using gallium & get the following output:

[I]handy ~  $  LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri_g/ glxinfo |grep -i opengl
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583) 20090101  TCL DRI2
OpenGL version string: 1.4 (2.1 Mesa 7.9-devel)
OpenGL extensions:[/I]

If you were using gallium you would get something like the following:

[I]# LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri_g/ glxinfo |grep -i opengl
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on R700 (HD4XXX)
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:[/I]

---

### Post by KingBongo on 2010-10-24
handy:
Hi. Do you know if current Gallium development is geared towards GPU encoding or not? I am not informed enough to know if that is the only thing needed for us with less than the fastest machines to watch 1080p movies, but without that my P4 surely isn't powerful enough. Right now I am forced to use the fglrx drivers, which are less than perfect and probably will remain so.

My dream is that desktop Linux one day will get were Linux for smart phones is today. It seems to be a never ending story where it is very very hard to penetrate into Microsoft's domain.

---

### Post by handy on 2010-10-25
**@KingBongo:** So the open AMD drivers aren't good enough at this stage?

Have you tried using the latest kernel & other associated packages from *edgers* & such (links in OP)?

I have been having NO problems at all displaying movies on my 1920x1280 monitor with a lowly HD2600Pro, for some time.

---

### Post by KingBongo on 2010-10-25
handy:
I haven't tried the xorg-edgers stuff (all of it I believe) for a while. I did previously, a couple of times, and every time the graphics died :p Do you have to do something extra to get the kernel?

I have also been using the drivers only from xorg-edgers. It works, but I couldn't notice any difference. Maybe there is a difference now?

The reason I am using fglrx now is not to get GPU encoding, but to get a picture at all :p When I installed Ubuntu 10.10 everything was black. Installing fglrx was the easiest solution then.

---

### Post by handy on 2010-10-26
**@KingBongo:** If you have a look at the [**_Ubuntu Stuff section of the OP_**]("http://ubuntuforums.org/showpost.php?p=7773102&postcount=1") (which is greatly simplified these days ;)), in that section you will find a how-to & info' regarding getting latter versions of kernels than the standard Ubuntu version.

Using Arch I'm always using a later version than Ubuntu does, & very often I'm using development versions. They have (from memory; I've been doing it on & off for about 2 years) very rarely ever given me any trouble. 

You can install these later kernel versions in parallel; editing menu.lst so you can choose which is default &/or using the grub menu to choose which one you want to boot with.

I must say that Arch still uses the old Grub. So I don't know how easy or hard it is to edit the Grub2 config'.

---

### Post by Ubuntiac on 2010-10-26
> **handy said:**
> I don't know how easy or hard it is to edit the Grub2 config'.

It's about the same, just in a different file (and you need to do grub-update afterwards)

On a side note, I just upgraded Lucid -> Maverick and all of a sudden my favourite Linux game "Savage 2" now runs! Woo Hoo! Further more absolutely everything, except shadows works great, even turned up to maximum settings and I still get a great framerate on an ATI HD4850.

Call me impressed! It's now gone from being where I couldn't get anything more than basic 2D on FOSS ATI, to the point where I haven't actually managed to find a Linux game I want to play that I can't. Awesome! (I don't care what they say, I'm still going to try it with "Oil Rush" when it comes out :))

---

### Post by handy on 2010-10-26
> **Ubuntiac said:**
> 
It's about the same, just in a different file (and you need to do grub-update afterwards) 

That's cool. 8)

> **Ubuntiac said:**
> 
On a side note, I just upgraded Lucid -> Maverick and all of a sudden my favourite Linux game "Savage 2" now runs! Woo Hoo! Further more absolutely everything, except shadows works great, even turned up to maximum settings and I still get a great framerate on an ATI HD4850.

Call me impressed! It's now gone from being where I couldn't get anything more than basic 2D on FOSS ATI, to the point where I haven't actually managed to find a Linux game I want to play that I can't. Awesome! (I don't care what they say, I'm still going to try it with "Oil Rush" when it comes out :))

This thread is currently about 14 months old. I agree with you, the improvements that have happened re. the FOSS support side, for the AMD GPUs in this short period of time is absolutely awesome. & we still have the Gallium development (which is steaming along) to look forward to becoming mainstream.

It's all good. :D

---

### Post by KingBongo on 2010-10-26
handy
I forgot to tell you. I am actually running the 2.6.36 kernel from the kernel.ubuntu site. Maybe its time to switch to open-source once more :)

---

### Post by Dsky on 2010-10-26
hi guys i've a problem

i've a toshiba m40-282 with an ati radeon x700.

i tried installing ubuntu 10.10 but the black screen at the start remained black... i could only start in recovery mode...

i tried then installing 10.04... the x starts but all the pc was so slow... (with open source driver) i tried taking off the video effects... and now its faster but if i try to see a movie the pc return so slow and i cant see the movie...

what have i to do?  change distro? try with another older one?

Thanks!

---

### Post by alexan on 2010-10-26
ATI is working hard to make linux driver usable... saddly, they to make such job they did drop the support of older cards (which include yours)
The last usable thing from ATI laboratories for your video card.. are usable only an older Xorg than 1.60

I do suggest you to take a quick look over puppylinux (little download for distro+easy patch)

on puppylinux forum: [http://www.murga-linux.com/puppy/](http://www.murga-linux.com/puppy/)


go and ask which is the latest puppy to support ati driver for x700 (better if it's Puppy Arcade.. so you can check directly with 3d emulators/games)

---

### Post by Dsky on 2010-10-26
the notebook has 1gb ram... the puppy isnt a little too small?

basiccly with ubuntu 8.04 there are drivers for my card but is the 8.04 too old?

what about salix or other?

---

### Post by blueturtl on 2010-10-26
I went on my HTPC from Ubuntu 9.10 to 10.10.

I no longer need to use fglrx as the open source drivers now provide better day-to-day functionality. With fglrx I just couldn't get video playback and Compiz to play together. Now I'm a really happy guy. :)

I wonder how the features and support are for 3D games? Can I run anything more complex than World of Goo?

I'm using a HD 4650.

---

### Post by handy on 2010-10-27
> **Dsky said:**
> hi guys i've a problem

i've a toshiba m40-282 with an ati radeon x700.

i tried installing ubuntu 10.10 but the black screen at the start remained black... i could only start in recovery mode...

i tried then installing 10.04... the x starts but all the pc was so slow... (with open source driver) i tried taking off the video effects... and now its faster but if i try to see a movie the pc return so slow and i cant see the movie...

what have i to do?  change distro? try with another older one?

Thanks!

The FOSS, AMD drivers support your hardware, you should look into trying that solution. 

Your card is in the R400 series, have a look here:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)


> **blueturtl said:**
> ...

I wonder how the features and support are for 3D games? Can I run anything more complex than World of Goo?

I'm using a HD 4650.

Anything using a Quake engine works really well, as that engine is really well GPU optimised. Apart from that there certainly are other games that are far more 3D intensive than WoG that work great.

Personally, I bought a PS3 when they took $200 off the price, so I took the easy way out when it comes to games. Not that I play many; Oblivion (yeh, I know I ran it on Linux) & Gran Tourismo 5 Prologue, are all I need these days (PS3 wise). 

Though I do have a few native Linux games that I paid for (that special bundle a while back) installed because I wanted to support the dev's. I don't even worry about playing them at this point, I couldn't be bothered mucking about with them yet (they probably work fine though) I'll give them a go later when the FOSS support for my GPU is that much further down the road.

I'm a patient man. :) (usually)

---

### Post by Dsky on 2010-10-27
> **handy said:**
> The FOSS, AMD drivers support your hardware, you should look into trying that solution. 

Your card is in the R400 series, have a look here:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)





sorry im a newby, can u explain what have i to do?

ps. in the meanwhile i tried ubuntu 9.10 and the notebook is stable with normal video aspect but seeing a movie it's not so fluid

---

### Post by handy on 2010-10-27
> **Dsky said:**
> sorry im a newby, can u explain what have i to do?

ps. in the meanwhile i tried ubuntu 9.10 and the notebook is stable with normal video aspect but seeing a movie it's not so fluid

I'd love to be the one to help you with the process. BUT, I've been about 2.5 years away from Ubuntu, so we really need someone with their finger on the pulse of your system to help you through this one.

Hold on, I expect that someone will come along soon & give you either the step by step, or give you a link where it is all laid out for you.

Sorry, that's the best I can do for you. :)

---

### Post by alexan on 2010-10-27
> **Dsky said:**
> the notebook has 1gb ram... the puppy isnt a little too small?

basiccly with ubuntu 8.04 there are drivers for my card but is the 8.04 too old?

what about salix or other?

It should consider only for testing propouse: see what's your videocard able to do.. and which is the latest functional version of Xorg you need (which is an old one.. since ATI didn't updated their close driver to new XORG version): that's the problem with closed driver.. once the original developer cut the work, no more update, no more fixing.
Next time try to opt to an nvidia (probably the best proprietary closed driver for ubuntu) or Intel (open source: lower gaming performance, but virtually unlimited updates)

Ubuntu 8.04 use Xorg 7.1; it could work.. you can always test; but it's a 700MB download

There's a puppy linux that seem work with your hardware:
[http://www.murga-linux.com/puppy/viewtopic.php?t=36567](http://www.murga-linux.com/puppy/viewtopic.php?t=36567)
additionally (on puppylinux) you can test its real perfomance with a native linux game (based upon doom3's engine) to test with puppy (well, the demo at the last):
[http://www.murga-linux.com/puppy/viewtopic.php?t=36489](http://www.murga-linux.com/puppy/viewtopic.php?t=36489)


> **handy said:**
> The FOSS, AMD drivers support your hardware, you should look into trying that solution. 

Your card is in the R400 series, have a look here:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

He's already using; the problem were the performance: these opensource driver come from reverse engineering.. which is double work rather the original one made for the video board maker (thus, require more time to be usable with performances: software engineer to dig out the *hidden little secret* which make run the cards in the proprietary drivers)

---

### Post by handy on 2010-10-27
> **alexan said:**
> ...
He's already using; the problem were the performance: these opensource driver come from reverse engineering.. which is double work rather the original one made for the video board maker (thus, require more time to be usable with performances: software engineer to dig out the *hidden little secret* which make run the cards in the proprietary drivers)

Sorry old mate, but you don't know what you are talking about. :)

AMD have been providing both technical information & code to the FOSS people for well over a year now.

Nothing personal; but do a tiny bit of research & you'll understand what I'm talking about. :D

---

### Post by alexan on 2010-10-27
> **handy said:**
> Sorry old mate, but you don't know what you are talking about. :)

AMD have been providing both technical information & code to the FOSS people for well over a year now.

Nothing personal; but do a tiny bit of research & you'll understand what I'm talking about. :D

My bad.. then enjoy your opensource tessellation with HD2000+ :confused:


Anyway, AMD Radeon now?
Well, AMD had chance to bring a new "clean" name in the Linux Game Industry; but I don't have too many hopes in it.
AMD+Xbox360+Microsoft= still not good for Linux

The astonishing Highlights that did come from AMD/ATi with the latest 10.10

Support for new Linux operating systems

This release of AMD Catalyst driver for Linux introduces support for the  following new operating systems: *MS's tada sound*
[I]openSUSE 11.3 support (production)
Ubuntu 10.10 support (early look)[/I]

---

### Post by 3Miro on 2010-10-27
The FOSS ATI driver definitely worked better for me than Catalyst, however, the only way I could the performance that I needed was to switch the Nvidia driver. I don't like that Nvidia is closed source, so I am really want the FOSS ATI to work.

---

### Post by Dsky on 2010-10-27
so? :D i'm confused...

now with ubuntu 9.10 it seems working

---

### Post by handy on 2010-10-27
> **Dsky said:**
> so? :D i'm confused...

now with ubuntu 9.10 it seems working

I don't blame you for being confused!

The last two posts were of no use to you (or anyone else for that matter) at all.

Don't give up on this thread due to those posts. If you need help, try here, as you just might get it. :)

Help, as opposed to opinion that is. :|

Though you never can tell just what you'll get. :D

---

### Post by del_diablo on 2010-10-27
> **alexan said:**
> My bad.. then enjoy your opensource tessellation with HD2000+ :confused:

If you are wondering: There are 2-3 people working mainly on the driver, and then you got 20-30 people doing random bits around it.
I just wish somebody had hired in a few more people to work fulltime on it, the driver would have been ages faster these days.

---

### Post by handy on 2010-10-28
> **del_diablo said:**
> If you are wondering: There are 2-3 people working mainly on the driver, and then you got 20-30 people doing random bits around it.
I just wish somebody had hired in a few more people to work fulltime on it, the driver would have been ages faster these days.

I expect that I'm a whole lot older than you, for better or worse. :) So I'm a whole lot more patient...

As I see it, the crux of the biscuit (as Frank Zappa would say) is that AMD have both opened up the code to the AMD/ATi GPUs & have been contributing code to the Linux open source support for these GPUs.

This has been the reason why the AMD/ATi GPU FOSS code has been developing so incredibly fast over the last year or so. The improvements that have occurred in this time have been astounding. As my understanding is that the FOSS dev's have been given so much help by AMD. Which is SO incredibly cool.

If you compared the FOSS ATi/GPU drivers from a year ago with what we have now, it is mind boggling that so much improvement has happened in such a short time.

I'll go back to my first statement; as you get older, the years get so much shorter. Which I think is unfortunate, as I'm addicted to just about everything on this glorious planet. :D

---

### Post by JDShu on 2010-10-28
Phoronix finally has a new article regarding r300 performance:

[http://www.phoronix.com/scan.php?page=article&item=mesa_r300g_oct10&num=1]("http://www.phoronix.com/scan.php?page=article&item=mesa_r300g_oct10&num=1")

r600 article pending.

I am definitely getting an AMD card when I scratch up the funds :D

---

### Post by handy on 2010-10-28
> **JDShu said:**
> Phoronix finally has a new article regarding r300 performance:

[http://www.phoronix.com/scan.php?page=article&item=mesa_r300g_oct10&num=1]("http://www.phoronix.com/scan.php?page=article&item=mesa_r300g_oct10&num=1")

r600 article pending.

I am definitely getting an AMD card when I scratch up the funds :D

When I was in the computer business I used to use Cyrix CPUs, instead of Pentiums, then when AMD bought out the Athlon CPUs they were all I ever used except in one case when a customer specifically wanted a P4.

If it wasn't for AMD, we would be paying a great deal more for a whole lot less CPU power. I'll support them for as long as both they & I exist (barring the unexpected of course). I do have an iMac running an Intel CPU, but there was no way around that one at the time.

Due to AMD's FOSS support for their GPUs, I will only use their GPUs in the future, until something unexpected happens in the computer world.

---

### Post by CarpKing on 2010-10-28
> **Dsky said:**
> so? :D i'm confused...

now with ubuntu 9.10 it seems working

Is there any reason you're using 9.10 instead of 10.10?  The open-source ATI drivers have been improving rather quickly, so the driver there will likely be better.  Also, other programs will be in newer versions and the OS will be supported longer.  You could get an even newer version of the driver than comes with 10.10, but if the included one is suitable for your purposes you probably shouldn't mess with that.

---

### Post by CarpKing on 2010-10-28
> **handy said:**
> As I see it, the crux of the biscuit (as Frank Zappa would say) is that AMD have both opened up the code to the AMD/ATi GPUs & have been contributing code to the Linux open source support for these GPUs.

This has been the reason why the AMD/ATi GPU FOSS code has been developing so incredibly fast over the last year or so. The improvements that have occurred in this time have been astounding. As my understanding is that the FOSS dev's have been given so much help by AMD. Which is SO incredibly cool.

As an indication, Bridgeman, AMD's de facto open source liasan (I'm not sure what his official duties are) recently beat the news bot as the user with the highest number of posts on the Phoronix (Linux graphics news site) forums.

---

### Post by handy on 2010-10-28
> **CarpKing said:**
> Is there any reason you're using 9.10 instead of 10.10?  The open-source ATI drivers have been improving rather quickly, so the driver there will likely be better.  Also, other programs will be in newer versions and the OS will be supported longer.  You could get an even newer version of the driver than comes with 10.10, but if the included one is suitable for your purposes you probably shouldn't mess with that.

Also **Dsky**, you can use the guide in the OP of this thread under **Ubuntu Stuff:**, to get access to later versions of files than those provided in the Ubuntu repositories via using the xorg-edgers repo, & you can also install a later version of the kernel (in parallel if you like, so you can choose via the Grub menu which kernel you want to boot into).

---

### Post by Ubuntiac on 2010-10-29
Just wondering if any of you ATI geniuses might have any idea why my laptop gets opengl, desktop effects etc on the live CD, but only software rasteriser after installing. Details over at [this thread]("http://ubuntuforums.org/showthread.php?t=1607663"). All ideas appreciated!

---

### Post by jrusso2 on 2010-10-29
Looks like another year of coming of age for ATI

---

### Post by handy on 2010-10-29
> **jrusso2 said:**
> Looks like another year of coming of age for ATI

It seems to me that with the perpetual dynamic development that goes hand in hand with the FOSS & Linux kernel based distros, (& hardware too for that matter) that everything to do with Linux seems to be in a perpetual state of coming of age.

---

### Post by phredbull on 2010-10-29
> **Ubuntiac said:**
> Just wondering if any of you ATI geniuses might have any idea why my laptop gets opengl, desktop effects etc on the live CD, but only software rasteriser after installing. Details over at [this thread]("http://ubuntuforums.org/showthread.php?t=1607663"). All ideas appreciated!
If I have KMS on, it uses software rasterizer. If I turn KMS off, it uses my Radeon card. Either way, desktop effects work, but it seems better w/KMS on.

---

### Post by handy on 2010-10-29
> **Ubuntiac said:**
> Just wondering if any of you ATI geniuses might have any idea why my laptop gets opengl, desktop effects etc on the live CD, but only software rasteriser after installing. Details over at [this thread]("http://ubuntuforums.org/showthread.php?t=1607663"). All ideas appreciated!

Perhaps enabling the xorg-edgers repo might give you an easy fix when it installs updated file versions?

Sorry I can't be of more help, I've been away from the Ubuntu way of doing things for years now.

---

### Post by del_diablo on 2010-10-31
Hmmmm, running debian sid combined with xorg edgers, which was a lot less messier than expected.
Blender runs fine as far as I have tested(2.55 beta), running on 3470 card.

---

### Post by the rent is too damn high on 2010-11-11
Handy sent me to this thread with:

> if you have trouble installing the Radeon FOSS stuff, if you post in the above thread you are more likely to get some helpWell, I'm using an ATI Radeon X300, and I installed fglrx successfully (or so I think).  However, whenever I try to run:

```
wine "c:/program files/world of warcraft/wow.exe" -opengl
```I get the message:

```
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program files\\world of warcraft\\wow.exe" failed, status c0000005
```:confused:

---

### Post by dh04000 on 2010-11-11
> **Ubuntiac said:**
> Just wondering if any of you ATI geniuses might have any idea why my laptop gets opengl, desktop effects etc on the live CD, but only software rasteriser after installing. Details over at [this thread]("http://ubuntuforums.org/showthread.php?t=1607663"). All ideas appreciated!

I've seen this way too many times. Usually its not the video card that stops working after install but the wireless card for me.

---

### Post by del_diablo on 2010-11-11
> **the rent is too damn high said:**
> Handy sent me to this thread with:

Well, I'm using an ATI Radeon X300, and I installed fglrx successfully (or so I think).  However, whenever I try to run:

X300, that is the famed 1xxx series right?
Son, unless you are on Hardy Heron(8.04 was it?), it won't work. The last driver was 9.3.....
To quote:
> AMD has moved a number of DX9 ATI Radeon™ graphics accelerators products to a legacy driver support structure.  This change impacts Windows XP, Windows Vista, and Linux distributions.  AMD has moved to a legacy software support structure for these graphics accelerator products in an effort to better focus development resources on future products.

The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
***_ATI Radeon X300 Series_***
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series

I think your GPU uses the same architecture as 9800, which means that the ati driver is suppose to work. Uninstall fgrlx, and open up synaptics and find xorg-driver-ati or what its called.

---

### Post by handy on 2010-11-11
I also told *the rent is too damn high* that the card was no longer supported by Catalyst (fglrx), posting the Radeon Feature link to show him what was going on, on the FOSS side of things, & told him to remove Catalyst & install the Radeon FOSS drivers.

?

**@the rent is too damn high:** The bottom line is that you can not get Catalyst (fglrx) to work with your card on current systems. You either have to install an old version of Ubuntu (as has been previously stated) or go with the FOSS Radeon (xf86-video-ati) driver files, which are working nicely, but the 3D is still slower than Catalyst.

---

### Post by the rent is too damn high on 2010-11-14
> remove Catalyst & install the Radeon FOSS drivers.

I installed everything I could find regarding [xf86-video-ati]("http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/tag/?id=xf86-video-ati-6.13.2"), but now I'm getting the error,
```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  198
  Current serial number in output stream:  198
```

What do I do?:confused:  (Also, now my cursor is flailing wildly about the screen and not responding to my mouse-movement)

---

### Post by handy on 2010-11-14
Did you remove Catalyst before you installed the Radeon packages?

---

### Post by the rent is too damn high on 2010-11-15
I removed everything synaptics gave me when I searched "fglrx" except for the jockey files.  I read somewhere not to remove those.  Should I?  And sorry for being so dense.

---

### Post by del_diablo on 2010-11-15
Just run sudo rm /etc/X11/xorg.conf
that should purge it.

---

### Post by the rent is too damn high on 2010-11-15
I ran sudo rm /etc/X11/xorg.conf, and it told me there was no directory to delete.  Oddly enough, after running a command stopped by an error, now the program wow.exe runs!

Unfortunately, my sense of ecstasy was short-lived, for the game will only run for about 7-10 minutes, then freeze up my entire computer.  Two attempts, same freezing, wont unlock, cursor wont move, forced to do a hard-restart.

Oh by the way my crazy-moving cursor got solved with a can of compressed air and a nozzle blowing out the gunk under my ****-mouse. :D

---

### Post by handy on 2010-11-16
There is a wonderful new patch that whilst not directly involved with our GPU driver stack, it will certainly have an effect on our desktop & video performance, for some more than others:

[http://www.phoronix.com/scan.php?page=article&item=linux_2637_video](http://www.phoronix.com/scan.php?page=article&item=linux_2637_video)

I certainly look forward to this patch being incorporated into our kernel26-drm-radeon-testing kernel, for starters. 

It looks like it won't come into mainstream until Linux 2.6.38 kernel as the kernel freeze is in place for 2.6.37.

---

### Post by Largaroth on 2010-11-17
HI All, I just tried out the .33 kernel, with drivers (but there was a problem retrieving software apparently) so I proceeded to try le .34 (having not noticed any difference with the .33) and then...

My whole system crashed XD.
One of the risks I guess, it started acting really weird, not recognising some devices, and then completely losing important folders and so stopped booting completely. Anyway, I just installed the latest Ubuntu (oh and also, my install disk was scratched and wouldn't complete an installation, it was rather frustrating ^^), but I don't know that I'll be trying these kernels again ^^".

I just thought I might say this, so that anyone installing these (and who doesn't really have enough knowledge to do a system restoration from the command line) knows what he/she is risking ^^. However, they do seem to work for some or most people ? So I think it is worth a shot, just be aware ^^

---

### Post by handy on 2010-11-17
> **Largaroth said:**
> 
HI All, I just tried out the .33 kernel, with drivers (but there was a problem retrieving software apparently) so I proceeded to try le .34 (having not noticed any difference with the .33) and then... 

I've been using .37 kernel for some time. So if you are trying out .33 you are a long way away from the cutting edge.

> **Largaroth said:**
> 
...
Anyway, I just installed the latest Ubuntu (oh and also, my install disk was scratched and wouldn't complete an installation, it was rather frustrating ^^), but I don't know that I'll be trying these kernels again ^^". 

You say that you just installed the latest Ubuntu but the install disk was scratched & wouldn't complete an installation???

You are wasting our time with this post.

> **Largaroth said:**
> 
I just thought I might say this, so that anyone installing these (and who doesn't really have enough knowledge to do a system restoration from the command line) knows what he/she is risking ^^. However, they do seem to work for some or most people ? So I think it is worth a shot, just be aware ^^

I'm not being personally derogatory when I say this, but your advice is technically useless.

---

### Post by Ayuthia on 2010-11-17
> **Largaroth said:**
> HI All, I just tried out the .33 kernel, with drivers (but there was a problem retrieving software apparently) so I proceeded to try le .34 (having not noticed any difference with the .33) and then...

My whole system crashed XD.
One of the risks I guess, it started acting really weird, not recognising some devices, and then completely losing important folders and so stopped booting completely. Anyway, I just installed the latest Ubuntu (oh and also, my install disk was scratched and wouldn't complete an installation, it was rather frustrating ^^), but I don't know that I'll be trying these kernels again ^^".

I just thought I might say this, so that anyone installing these (and who doesn't really have enough knowledge to do a system restoration from the command line) knows what he/she is risking ^^. However, they do seem to work for some or most people ? So I think it is worth a shot, just be aware ^^

I think that the issues that you are running into are related to the incomplete installation rather than the instructions from this post.  As of this post, .37 is the only kernel that is not considered stable.  There are other distributions that are using .36 so I am fairly confident that they are fine.

As for the open source graphics driver, they are tied to the graphics card.  The worst things that you will run into is a possibility that X might not start, you have a computer that might run hotter (because of the current work on the power management), or you run into some differences in performance.

As for me, I have been using various versions in Gentoo without any issues and recently updated Maverick to use this.  The main things that I have found is that the temps between the proprietary version and open source have gotten pretty close.  The fglrx version used to be better up until 10.10 was released.  That version does not seem to perform as well.  The other nice feature with the open source is that suspend works.

Of course, things will vary from computer to computer but you should not have any issues with losing any data based on these code changes unless you try out release candidate kernels (like .37).

---

### Post by handy on 2010-11-17
I've been using the kernel release candidate .37 since it first came out, & I have had no problems with it.

Actually, for most of the last 15 or so months I have been using the development versions of the kernel & all of the FOSS driver stack for the AMD GPU's. 

There has rarely ever been a problem. Though once or twice I have had to briefly go back to the stable kernel - driver stack.

---

### Post by xiongnu on 2010-11-18
the video card i have is an ATI rage pro 128, and it's using the default video driver came with ubuntu.  is it possible to take advantage of this ATI open driver to improve the performance?

---

### Post by handy on 2010-11-19
> **xiongnu said:**
> the video card i have is an ATI rage pro 128, and it's using the default video driver came with ubuntu.  is it possible to take advantage of this ATI open driver to improve the performance?

Your are already using the AMD/ATi open driver. You may possibly improve performance by using a later kernel & the xorg.edgers PPA repo. If you are interested in doing that, there is a how-to in the OP of this thread, under the "Ubuntu Stuff" heading.

---

### Post by the rent is too damn high on 2010-11-19
O mighty ones of ATI Open Drivers... help?

I still haven't been able to get this WoW-Game working on my machine.  I found a troubleshooting article which addressed the problem of starting the game, and it freezing about 8-10 minutes in.  It advised I edit the etc/x11/xorg.conf.  That'd be fine and dandy, but I sudo-removed it to put in the new driver!

So, the fglrx driver keeps the game from starting, and my new one keeps it from running.  On a side note, I searched for a xorg.conf, and found one in /usr/share/doc/xserver-xorg-video-nouveau/examples .

---

### Post by handy on 2010-11-22
> **rituparnakashyap said:**
> To begin with i have a Sony Vaio VPCEB24EN Laptop with configuration

Intel core i3 Processor 
3 GB RAM
ATI Radeon HD 5145, 512 MB 

Installation of Ubuntu 10.10 Notbook edition make my lappy extremly hot in comparison to Windows 7, which includes degrading my battery performance from 3 hours to 45 min. As my CPU uses is normal, i deduce that my Graphics might be the cause of the heat and power consumption. Tried installing proprietory drivers from Get Software -> System -> Additional Drivers, which maximized the problem. My screen keep freezing now and then. So i uninstalled the driver and downloaded ati-driver-installer-10-11-x86.x86_64.run from ati site. While install it has issue of its own. The text written in the installer is invisible. [A print screen is attached]. This is to mention that the core fonts are installed in the system.

I shall be glad if anyone have the solution for my problems
1. Over heating and battery backup issue. 
2. ATI catalyst font issue.

Thanks in advance

[edit:] Here is your linked image:

[http://ubuntu-ky.ubuntuforums.org/attachment.php?attachmentid=176242&d=1290416211](http://ubuntu-ky.ubuntuforums.org/attachment.php?attachmentid=176242&d=1290416211)


I quoted your post & moved it here as you will hopefully get more help in this thread.

The Evergreen GPU's (the series that you are using) are incomplete, but they are running reasonably:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

The Ubuntu 10.10 installs the FOSS Radeon driver stack by default.

If you want to try a later version of the kernel, (I'm using Arch & the -git packages driver stack plus kernel (2.6.37-rc1-31697-gb2298fd-dirty) you should have a look at the OP of this thread & scroll down to "Ubuntu Stuff:" where there is a how-to on getting later versions of the kernel than that which Ubuntu comes with & how-to enable the xorg-edgers PPA repo.

None of which is as hard as it sounds as you will see if you read it in the first post.

There is also a procedure that may help you cool your GPU, but it will very likely use more battery power.

Some people are reporting as good or better results using the FOSS Gallium driver stack:

[http://www.x.org/wiki/GalliumStatus](http://www.x.org/wiki/GalliumStatus)

I haven't as yet spent the time to configure my machine & try it out, as I'm quite happy with the Radeon stack.

I just put back the Power Management section in the OP, it may give you a start on being able to control the PM on you system, I can't remember whether it needs to be modified for Ubuntu or not at the moment. Perhaps someone who knows will verify that & offer changes if they are required?

Hopefully you will find a solution to your problem soon.

---

### Post by abelundercity on 2010-11-23
Is there a utility I can use to tweak the xorg-edgers drivers without breaking them? Since the last update I've been crashing out of Second Life with alarming frequency.  Or is it just better to wait for the next update and hope?

---

### Post by madjr on 2010-11-23
booooooooo, supertux cart, still is not playable with the open ati drivers. I thought that would had been solved by now in 10.10 :/

---

### Post by ParadoxBlue on 2010-11-24
> **Kazade said:**
> Well, 10.04 only comes with the 2.6.32 kernel - so I was jumping you even further than that :)

I'd recommend that you install 10.04, and then the stable updates xswat ppa. That's really safe. 

If that doesn't give you OSS 3D acceleration, then you'll need to add xorg-edgers to get it which is pretty experimental and can break. Only do it if you have backups and aren't worried about dealing with breakage. 

If that works and you still wanna push it further, you can download a pre-packaged 2.6.35 kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-maverick/")

So, it depends how risky you wanna be really. Xswat is safe, xorg-edgers is less safe, xorg-edgers plus 2.6.35 has the potential to break more (like Wifi or something).

Ok after reading through this voluminous thread I believe this post comes closest to addressing my problem. I'm running an ATI x1650 graphics card and upon upgrading from Karmic to Lucid I seem to have lost Compiz support. I have to disable all effects to make my system usable under Lucid. Karmic worked just fine with effects fully enabled. I have found the xswat page [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") . I'm not really sure how to proceed from here. Any help is greatly appreciated and I give thanks for any advice in advance.

---

### Post by sandyd on 2010-11-26
Currently using 
-Gallium from SVN (only gallium, I did not compile classic support)
-xf86-video-ati from svn
-libdrm from svn
-XOrg 1.8.2

For once, I can play openarena without lag.:D

---

### Post by madjr on 2010-11-26
> **ParadoxBlue said:**
> Ok after reading through this voluminous thread I believe this post comes closest to addressing my problem. I'm running an ATI x1650 graphics card and upon upgrading from Karmic to Lucid I seem to have lost Compiz support. I have to disable all effects to make my system usable under Lucid. Karmic worked just fine with effects fully enabled. I have found the xswat page [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") . I'm not really sure how to proceed from here. Any help is greatly appreciated and I give thanks for any advice in advance.

have you tested compiz with a live-cd?

i have a crappy ati x1250 and compiz works very well (on both 10.04 and 1010)

this is why i dont do upgrades, i fresh install to a new partition

---

### Post by handy on 2010-11-27
On a loosely connected side note; it would seem that the kernel patch that I was using this easy shortcut:

[http://lkml.org/lkml/2010/11/16/413](http://lkml.org/lkml/2010/11/16/413)

to bring about the same (initial) results has been incorporated into this kernel that I use:

[http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing)

Files are still being generated in */cgroup/cpu/* after I edited /etc/rc.local in a fashion that would disable their creation.

I must say that on my system, YouTube vid's are definitely working better than before I implemented either of these two ways of bringing about the same result.

---

### Post by handy on 2010-12-03
I thought it is about time I gave Gallium a try on my HD2600Pro GPU. On Arch all I had to do was install the mesa-full-gallium package & change an environment variable. This gives you the ability to switch the environment variable on/off to move from Gallium to Classic mode if need be (on Arch).

Apparently for Ubuntu if you use the xorg-edgers PPA, you don't have to configure anything the Gallium driver stack will just work.

My system looks the same & functions the same with Gallium, but my (not a benchmark) glxgears was about 60fps slower. Which I can live with as it makes no difference to my day to day use of the machine. 

So it looks like I've been got by Gallium too.

I look forward to the increased 3D speed which will eventually come via the Gallium stack. My fps have been the same for months using the Classic stack.

---

### Post by Starlight on 2010-12-04
Hello *waves*

I'm having strange problems with the official radeon driver on my laptop (it has radeon hd 5650), so I've tried switching to the open source one. The strange problems disappeared, but OpenGL stuff is totally unusable, so I can't play games, and I can't even use stuff like google earth.

I've read something about Gallium, but I have no idea what it is and how to use it. Do I just need to add the xorg-edgers repository and update the system? Or do I also need to manually install a new kernel, like in the "Ubuntu stuff" section of the OP? Is there a chance that it would make OpenGL usable with the open source radeon driver on my computer?

---

### Post by handy on 2010-12-04
Hi, yes installing the xorg-edgers repo will most likely make a difference (apparently in Ubuntu you have no other configuration to do for Gallium). Using a later kernel & (the dev' packages from xorg-edgers) will bring improvements though we need to try them to find out just how much improvement & in which areas, this is due to all of the different GPUs, their various capabilities & the level of the development currently available for each.

I've been using the kernel .37, since it first became available & have had no problems with it. So you should also have no problems with it.

Now as far as whether the improvements will be enough for you, that is a question that you will only be able to answer with experience.

You can install the other kernel & run it in parallel, so if you don't like it you can use a different one, & continue upgrading the development kernel which gives you the opportunity to test it out & see how it is coming along, & stick with it when you like it.

As far as Google Earth is concerned, you may find the following that I lifted from the Arch forum helpful, if not at least interesting:


[I][quote=ijanos]Guys, is google earth working for you with the open drivers? [/quote]

For me with my custom kernel 2.6.36-rc7, xorg-server-1.9.2-1, dri2proto-git-20101030-1, glproto-git-20101030-1, libdrm-git-20101107-1, mesa-full-gallium-20101107-1, xf86-video-ati-git-20101107-1:

And the aur package bin32-google-earth-5.2.1.1547-1.

With this packages the google earth work using the r600g (LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri_g/). Is usable without "anisotropic filter".

With preempt-rt kernel, the performance is better, no much, but better.

The fusion-icon work with some effects with r600g(LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri_g/).
[/I]
____________

So from the above, I'd go with the latest kernel & the latest packages that you can get from xorg-edgers, you will have the best chance of success.

Good luck.

---

### Post by del_diablo on 2010-12-05
Running 2.6.36 of Debian now, using pinning.
A thing I found recently: Driconf, more or less gfx controlpanel for our beloved FLOSS driver. You need it to enable the propitary texture compression, and glorious vsync options.
I am running a dated driver, whenever the next update to testing comes in, I guess there will be a massive speedup.
Running mobility 3470 BTW.
Good for desktop resolution, and blender runs quite well(opengl render works gloriously too). Gliderwrapper for D2 does not work at all, it lacks extensions. The troughput is roughly 1/20 of what the Windows binary driver is capable of(15 MB/sek vs 340 MB/sek), but that might be due incompatiblity with wine.
I don't think I have any native 3D games to benchmark it on, except perhaps alien arena or cube?
I guess the updated driver will be quite a bit better for running Wine, going from the phoronix benchmarks(2-3 weeks ago?).

---

### Post by handy on 2010-12-05
**@del_diablo:** So you are not using Gallium?

---

### Post by sandyd on 2010-12-05
> **handy said:**
> Hi, yes installing the xorg-edgers repo will most likely make a difference (apparently in Ubuntu you have no other configuration to do for Gallium). Using a later kernel & (the dev' packages from xorg-edgers) will bring improvements though we need to try them to find out just how much improvement & in which areas, this is due to all of the different GPUs, their various capabilities & the level of the development currently available for each.

I've been using the kernel .37, since it first became available & have had no problems with it. So you should also have no problems with it.

Now as far as whether the improvements will be enough for you, that is a question that you will only be able to answer with experience.

You can install the other kernel & run it in parallel, so if you don't like it you can use a different one, & continue upgrading the development kernel which gives you the opportunity to test it out & see how it is coming along, & stick with it when you like it.

As far as Google Earth is concerned, you may find the following that I lifted from the Arch forum helpful, if not at least interesting:


[I]

For me with my custom kernel 2.6.36-rc7, xorg-server-1.9.2-1, dri2proto-git-20101030-1, glproto-git-20101030-1, libdrm-git-20101107-1, mesa-full-gallium-20101107-1, xf86-video-ati-git-20101107-1:

And the aur package bin32-google-earth-5.2.1.1547-1.

With this packages the google earth work using the r600g (LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri_g/). Is usable without "anisotropic filter".

With preempt-rt kernel, the performance is better, no much, but better.

The fusion-icon work with some effects with r600g(LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri_g/).
[/I]
____________

So from the above, I'd go with the latest kernel & the latest packages that you can get from xorg-edgers, you will have the best chance of success.

Good luck.

What?
Google Earth r600 (svn) is usable with anisotropic filter set on. And all the effects work with r600, not some.

---

### Post by handy on 2010-12-05
> **sandyd said:**
> What?
Google Earth r600 (svn) is usable with anisotropic filter set on. And all the effects work with r600, not some.

If you read the quote again you will see that it is "without anisotropic". As far as all the effects working or not, that comes down to your interpretation of what was written...

---

### Post by madjr on 2010-12-06
anyone else have problems with unity and the ati open drivers?

the old one didnt even render

and the new one has improved a little but has graphical glitches that still make it unusable (specially glitchy on the panel, indicator text/icons and squares/tooltips on the side bar)

the classic gnome 2d desktop with compiz works well tho

just want to know if new kernels / drivers fix the issue, if not then going to report it.

---

### Post by del_diablo on 2010-12-06
> **handy said:**
> **@del_diablo:** So you are not using Gallium?

Nah, I am not.
Unless there is a repo somewhere dedicated to the radeon driver fresh of the latest git for Debian, I don't think manually compiling down is worth it. It works for my main addition(blender), and it gets down proper smooth desktop resolution. I can wait around until experimental and unstable is updated, most of the changes are sort of trivial since I am on weak hardware anyhow.

---

### Post by Starlight on 2010-12-06
Thanks handy! :) I've updated the kernel to version 2.6.37 rc2 and updated all the xorg-edgers stuff, and now the open source driver seems to be working really well, I can even use desktop effects on KDE and use OpenGL programs at the same time! (the official ATI driver had a problem with that)

---

### Post by handy on 2010-12-06
> **Starlight said:**
> Thanks handy! :) I've updated the kernel to version 2.6.37 rc2 and updated all the xorg-edgers stuff, and now the open source driver seems to be working really well, I can even use desktop effects on KDE and use OpenGL programs at the same time! (the official ATI driver had a problem with that)

Thanks for your feedback. :) (It looks like Gallium is good for you on your Evergreen series which is great.)

It really helps those of us that don't know what the dev' packages have achieved, especially as far as the various desktops & their 3D effects are concerned.

---

### Post by sandyd on 2010-12-06
I swear that the X11 developers are playing tricks on me :D
I re-emerged everything for my new system, and AIGLX apparently did not like the new symbols in the r600 dri....

which led me to xorg 1.9.2 ;)

---

### Post by handy on 2010-12-07
> **sandyd said:**
> I swear that the X11 developers are playing tricks on me :D
I re-emerged everything for my new system, and AIGLX apparently did not like the new symbols in the r600 dri....

which led me to xorg 1.9.2 ;)

So is Google Earth doing its thing for you now?

---

### Post by sandyd on 2010-12-07
> **handy said:**
> So is Google Earth doing its thing for you now?

yup. working perfectly after all the compiling.

---

### Post by screaminj3sus on 2010-12-10
How do I make echo low > /sys/class/drm/card0/device/power_profile permanent??

---

### Post by handy on 2010-12-10
> **screaminj3sus said:**
> How do I make echo low > /sys/class/drm/card0/device/power_profile permanent??

In Arch you add it to /etc/rc.local ***[edit:]** or /etc/profile.d/radeon.sh . /edit* 

I don't remember what you do with it on Ubuntu, I think it has been covered in this thread previously though, you might want to scan back to where the PM came on the scene & read on from there?

---

### Post by screaminj3sus on 2010-12-10
> **handy said:**
> In Arch you add it to /etc/rc.local .
I don't remember what you do with it on Ubuntu, I think it has been covered in this thread previously though, you might want to scan back to where the PM came on the scene & read on from there?
All I have been able to find is how to do it with dynpm in ubuntu with modprobe.d, haven't been able to find anything about how to enable profile permanently.

---

### Post by I_can_see_the_light on 2010-12-11
When I browse to [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") I see that the latest kernel .37 (release candidates) is only available for Maverick and Natty, will they work on Lucid as well? The xorg-edgers ppa included a kernel update as well, 2.6.35, what is the recommendation here?

The reason I'm asking is because Kwin is running unacceptably slow with desktop effects enabled, things are a little bit better with Compiz so that's what I'm using right now but any sort of 3d stuff seem to slow the system down to a crawl.

```
glxinfo | grep -i opengl
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV380 3150) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
```

With PCLinuxOS the performance is really good and I noticed that they are using an older version of Mesa, 7.5.x I think, and an older version of xorg-server as well.

Any thoughts?

---

### Post by handy on 2010-12-11
> **I_can_see_the_light said:**
> 
When I browse to [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") I see that the latest kernel .37 (release candidates) is only available for Maverick and Natty, will they work on Lucid as well? The xorg-edgers ppa included a kernel update as well, 2.6.35, what is the recommendation here? 

I think that the reason the later kernels may be difficult to use with Lucid, is due to the incorporation of kernel mode switching (in particular) in the more recent kernels. I think that due to this, there would be a need to upgrade X.org to be compatible with such kernels. This may cause dependency hell?

> **I_can_see_the_light said:**
> 
The reason I'm asking is because Kwin is running unacceptably slow with desktop effects enabled, things are a little bit better with Compiz so that's what I'm using right now but any sort of 3d stuff seem to slow the system down to a crawl.

```
glxinfo | grep -i opengl
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV380 3150) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
```

With PCLinuxOS the performance is really good and I noticed that they are using an older version of Mesa, 7.5.x I think, and an older version of xorg-server as well.

Any thoughts?

I don't know if the latest kernel available for Lucid, in combination with the files available for from the xorg-edgers ppa, this will automatically set Lucid up to be using the Gallium drivers? This is what happens with the current release of Ubuntu, but you may be caught out by the latest kernel version available for Lucid? 

Many find that they get better performance from Gallium. (I don't, but the glxgears drop of 60fps is negligible so I use Gallium, with my Arch install.) 

Sorry I can't be of more help, I've probably created more questions than answers. Hopefully someone with more specific Ubuntu knowledge will post some firm answers for you.

---

### Post by JDShu on 2010-12-11
> **I_can_see_the_light said:**
> When I browse to [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") I see that the latest kernel .37 (release candidates) is only available for Maverick and Natty, will they work on Lucid as well? The xorg-edgers ppa included a kernel update as well, 2.6.35, what is the recommendation here?

The reason I'm asking is because Kwin is running unacceptably slow with desktop effects enabled, things are a little bit better with Compiz so that's what I'm using right now but any sort of 3d stuff seem to slow the system down to a crawl.

```
glxinfo | grep -i opengl
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV380 3150) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
```

With PCLinuxOS the performance is really good and I noticed that they are using an older version of Mesa, 7.5.x I think, and an older version of xorg-server as well.

Any thoughts?

I'm running Lucid with the 2.6.37-7-generic-pae kernel and xorg-edgers. Working fine for me. Just a matter of choosing the right packages from PPA for Ubuntu Kernel PPA in the Software Center. I use an HD4550.

The difference is huge, mainly because it supports OpenGL 2.1 now.

---

### Post by I_can_see_the_light on 2010-12-12
Ok, thanks to both of you.

Guess I'm going to try the Ubuntu kernel ppa then, didn't know it existed before. The funny thing is that the performance in Gnome is almost OK (generic desktop use, minimising, maximising and moving windows) whereas in KDE it's sub par.

---

### Post by screaminj3sus on 2010-12-12
> **I_can_see_the_light said:**
> Ok, thanks to both of you.

Guess I'm going to try the Ubuntu kernel ppa then, didn't know it existed before. The funny thing is that the performance in Gnome is almost OK (generic desktop use, minimising, maximising and moving windows) whereas in KDE it's sub par.

From my experience, KDE simply does not work well with ati cards. With my mobility hd2600 I have tried KDE versions 4-4.5 and performance has always been absolutely abysmal with both the open source drivers and fglx. Gnome has always been fine.

---

### Post by I_can_see_the_light on 2010-12-12
[QUOTE=screaminj3sus]From my experience, KDE simply does not work well with ati cards. With my mobility hd2600 I have tried KDE versions 4-4.5 and performance has always been absolutely abysmal with both the open source drivers and fglx. Gnome has always been fine.[/QUOTE]
I see, my previous problems with KDE (or more specifically Kwin+ATI combo) have been hard computer lock ups. The card in my laptop (Mobility radeon X600) have been the most troubled while my desktop with a radeon 9600 have played a little nicer. Note that this is only basic desktop work, I haven't used any graphics intensive applications for a couple of years.

---

### Post by JDShu on 2010-12-13
I have a question of my own. With my HD4550, can I plug in both a vga monitor and an hdmi monitor for dual display?

---

### Post by blueturtl on 2010-12-13
I can do that with my HD 4650, so my guess is: yes.

---

### Post by JDShu on 2010-12-13
Awesome :D I will look to buy an HDMI Monitor sometime in the near future.

---

### Post by handy on 2010-12-14
> **JDShu said:**
> Awesome :D I will look to buy an HDMI Monitor sometime in the near future.

Let us know how you go with it, please?

---

### Post by sandyd on 2010-12-17
Anisotropic Filtering on Google Earth 6 (gallium)
[http://img202.imageshack.us/img202/1138/snapshot8m.png](http://img202.imageshack.us/img202/1138/snapshot8m.png)

Works fine, even with 3D buildings!

and please ignore the disgusting fonts, I need to compile oxygen-gtk in a 32bit chroot.

---

### Post by JDShu on 2010-12-18
> **handy said:**
> Let us know how you go with it, please?

Seems like other obligations have dried up my wallet :( I will definitely get one when I get the funds though :D

I wanted to mention that the Gallium driver and the Classic driver are really far apart now in terms of functionality. With Gallium I am able to run Braid, Steel Storm, and use WebGL (Google Bodybrowser works) which the Classic driver is not able to do.

---

### Post by handy on 2010-12-19
> **JDShu said:**
> Seems like other obligations have dried up my wallet :( I will definitely get one when I get the funds though :D

I wanted to mention that the Gallium driver and the Classic driver are really far apart now in terms of functionality. With Gallium I am able to run Braid, Steel Storm, and use WebGL (Google Bodybrowser works) which the Classic driver is not able to do.

I think the difference between Gallium & Classic is somewhat variable & depends on the GPU you are using.

I know that Gallium is where we will eventually get our 3D fps speed increases. Over the last couple of dev' kernel & rest of the driver stack releases I've picked up the 60fps I'd lost when I changed to Gallium recently, plus a slight gain in speed. 

So it is happening. :)

---

### Post by sandyd on 2010-12-19
> **handy said:**
> I think the difference between Gallium & Classic is somewhat variable & depends on the GPU you are using.

I know that Gallium is where we will eventually get our 3D fps speed increases. Over the last couple of dev' kernel & rest of the driver stack releases I've picked up the 60fps I'd lost when I changed to Gallium recently, plus a slight gain in speed. 

So it is happening. :)
+1 to what GPU your using.

I started to have some form of stuttering on r600 after I pulled from git this morning. Maybe I need to compile with the latest radeon-ucode.....

EDIT: no problem after changing version of radeon-ucode.

Theirs something weird ive been noticing.

Occasionally, after a compile, theirs weird performance issues. However, after changing (upgrade/downgrading) radeon-ucode, and recompiling the kernel, the problem vanishes.

---

### Post by sandyd on 2010-12-20
Wow. Just noticed while building Google ChromeOS
```

[binary  N    ] media-libs/mesa-7.7.1-r1 to /build/x86-generic/ USE="gallium nptl xcb -debug -motif -pic (-selinux)" VIDEO_CARDS="intel -mach64 -mga -msm -none -nouveau -r128 -radeon -radeonhd -savage -sis (-sunffb) -svga -tdfx -via" 

```
for non-portage users, this shows that mesa is being compiled with gallium ;)

---

### Post by handy on 2010-12-20
> **sandyd said:**
> Wow. Just noticed while building Google ChromeOS
```

[binary  N    ] media-libs/mesa-7.7.1-r1 to /build/x86-generic/ USE="gallium nptl xcb -debug -motif -pic (-selinux)" VIDEO_CARDS="intel -mach64 -mga -msm -none -nouveau -r128 -radeon -radeonhd -savage -sis (-sunffb) -svga -tdfx -via" 

```
for non-portage users, this shows that mesa is being compiled with gallium ;)

Perry mentioned sometime in the last couple of weeks that he thought there was no need to install both the classic & Gallium mesa packages if you wanted to change the environment variable & switch between the two manually the Gallium package should do both.

Which is nice.

It looks like Gallium is now the Boss in this field.

---

### Post by Starlight on 2010-12-26
I've noticed that Java seems to crash everything, after switching to the xorg-edgers repository and using the open source radeon driver :( Suddenly after a few minutes of using Java, everything crashes and the xorg log says there was a segmentation fault in the radeon driver :(

---

### Post by handy on 2010-12-26
> **Starlight said:**
> I've noticed that Java seems to crash everything, after switching to the xorg-edgers repository and using the open source radeon driver :( Suddenly after a few minutes of using Java, everything crashes and the xorg log says there was a segmentation fault in the radeon driver :(

I've not & I haven't read of anyone else having this problem?

It would be good to hear from others on this topic?

---

### Post by sandyd on 2010-12-26
> **handy said:**
> I've not & I haven't read of anyone else having this problem?

It would be good to hear from others on this topic?
a) what card are you using?
b) [s]what SVN commit are you at (the latest does not crash, at least for me...)[/s]
It was 2010 12 21. I checked out commits from that day and compiled it. Not detecting any issue.

Current configuration
```

X.Org X Server 1.9.2
Release Date: 2010-10-30
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.36-sandyd x86_64 Gentoo
Current Operating System: Linux sandyd-laptop 2.6.36-sandyd #5 SMP Wed Dec 22 12:02:40 EST 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-sandyd root=/dev/sda1 ro
Build Date: 19 December 2010  09:59:03PM
 
Current version of pixman: 0.20.0
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.

```
Using libdrm svn + xf86-video-ati svn.

---

### Post by handy on 2010-12-26
I'm rarely ever not using the cutting edge FOSS driver stack (xf86-video-ati based) & kernel files located in Perry3D's repo built specifically for Arch; which we happen to host at spiralinear.org.

Arch 64bit
X.Org version: 1.9.2
Kernel: 2.6.37-rc3-32326-g1040cc0-dirty
Video: Radeon HD 2600 Pro/256MB RAM
OpenGL renderer string: Gallium 0.4 on AMD RV630
OpenGL version string: 2.1 Mesa 7.10-devel
OpenGL shading language version string: 1.20

---

### Post by sandyd on 2010-12-26
> **handy said:**
> I'm rarely ever not using the cutting edge FOSS driver stack (xf86-video-ati based) & kernel files located in Perry3D's repo built specifically for Arch; which we happen to host at spiralinear.org.

Arch 64bit
X.Org version: 1.9.2
Kernel: 2.6.37-rc3-32326-g1040cc0-dirty
Video: Radeon HD 2600 Pro/256MB RAM
OpenGL renderer string: Gallium 0.4 on AMD RV630
OpenGL version string: 2.1 Mesa 7.10-devel
OpenGL shading language version string: 1.20
bit offtopic, but ive been meaning to ask this for some time.
how stable is kernel 2.6.37 currently?

---

### Post by handy on 2010-12-26
> **sandyd said:**
> bit offtopic, but ive been meaning to ask this for some time.
how stable is kernel 2.6.37 currently?

Faultless from day one of public access from my experience.

We have been using this one for a while now, as it has been the best thing available for the AMD/ATi GPU's; it has caused no trouble:

[http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing)

---

### Post by sandyd on 2010-12-26
> **handy said:**
> Faultless from day one of public access from my experience.

We have been using this one for a while now, as it has been the best thing available for the AMD/ATi GPU's; it has caused no trouble:

[http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing)
ooh. works nicely.
no more KDE sliding menu lag. :)

---

### Post by handy on 2010-12-27
> **sandyd said:**
> ooh. works nicely.
no more KDE sliding menu lag. :)

I think it may pay you to keep an eye on the first post of this thread (& likely the last page too), as Perry3D, researches, compiles, tests & only passes on to his Arch repo users what has shown itself to be good stuff.

Occasionally a fault gets past him, if so it is fixed (inside of his repo) inside of 24 hours anyway. 

We all use parallel kernels anyway so if you do happen to upgrade into trouble you can reboot into a safe house. :)

[https://bbs.archlinux.org/viewtopic.php?pid=613720#p613720](https://bbs.archlinux.org/viewtopic.php?pid=613720#p613720)

---

### Post by handy on 2010-12-27
I just called a system upgrade on Arch & these are the newest packages that I just installed from Perry3D's repo:

kernel26-drm-radeon-testing-20101225-1
mesa-full-20101225-1  
mesa-demos-git-20101225-1
mesa-full-gallium-20101225-1

Which obviously mean they were the latest builds on the 25-12-2010, Oz time... ;)

I appreciate that they aren't much good for someone looking for accurate version/revision numbers, but what the hell! :)

---

### Post by andytech on 2010-12-27
I've never had hearing using the oss drivers. i think this drivers work good in new technology..

---

### Post by sandyd on 2010-12-27
> **handy said:**
> I think it may pay you to keep an eye on the first post of this thread (& likely the last page too), as Perry3D, researches, compiles, tests & only passes on to his Arch repo users what has shown itself to be good stuff.

Occasionally a fault gets past him, if so it is fixed (inside of his repo) inside of 24 hours anyway. 

We all use parallel kernels anyway so if you do happen to upgrade into trouble you can reboot into a safe house. :)

[https://bbs.archlinux.org/viewtopic.php?pid=613720#p613720](https://bbs.archlinux.org/viewtopic.php?pid=613720#p613720)
i actually keep multiple mesa installations on my computer through a specialized chroot/mount environment. If theirs an issue with the mesa/xf86-video-ati/libdrm drivers, I can pull back to the last working one by using mount --bind :).

However, mesa itself doesn't seem to have many regressions, even though im pulling from svn.

But still, i have to say that gallium is making a lot of headway compared to the junk i had when using ubuntu 9.10. Even though it isn't up to par with win7, its well enough for daily usage :). The only thing I find lacking (this is actually gentoo's fault) is that due to lazy binding (-z), I cant use it on hardened configs.

---

### Post by sandyd on 2011-01-08
Just did another svn pull this morning.
Seems that the KDE transparent menu stopped lagging when theirs an application under it :D.

Now if they could finish the antialiasing for r600 and full vaapi/vdpau support... :D .

---

### Post by JDShu on 2011-01-08
Did you guys notice that they're starting to work on optimizations? Last night a developer committed some code to r300g claiming up to 10% speed increase in TORCs. They'll probably apply it to r600g too :D

Btw, I got a dvi to vga cord to hook up an unused monitor for a dual monitor setup. It works great! I just wish there was an easy way to calibrate the colors.

---

### Post by sandyd on 2011-01-08
> **JDShu said:**
> Did you guys notice that they're starting to work on optimizations? Last night a developer committed some code to r300g claiming up to 10% speed increase in TORCs. They'll probably apply it to r600g too :D

Btw, I got a dvi to vga cord to hook up an unused monitor for a dual monitor setup. It works great! I just wish there was an easy way to calibrate the colors.
ya, i saw some new code additions to r300 during the svn pull :D

and Vaapi actually works, I think it just needs some more testing thats all.

EDIT: I just decided to fiddle a bit with the xorg.conf options, and after
```

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        Option     "BusType" "PCIE"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        Option     "GARTSize" "64"              # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        Option     "EnableDepthMoves" "on"       # [<bool>]
        Option     "EnablePageFlip" "1"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        Option     "AccelDFS" "1"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        Option     "ColorTiling" "1"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        Option     "RenderAccel" "true"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        Option     "AccelMethod" "EXA"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>

```
Desktop performance is FLYING. even with the notorious KDE Blur on. Im not noticing any performance difference with switching blur on or off.
oh yay!

---

### Post by handy on 2011-01-08
I'm getting better performance than I've ever had on my R600, using Gallium.

For my usage, I have no problems running with this driver stack, except that I can't play much more than WoG with it due to the 3D being too slow.

If they have gotten most of the other priorities out of the way, & can start focussing on optimisation it is going to get pretty exciting for us who have been using, watching & waiting for this time to come for so long. (That is not derogatory re. the dev's, they have really done an awesome job over the last year or so.)

Fingers crossed it starts to happen for us real soon now.

---

### Post by del_diablo on 2011-01-09
[Phoronix: A more ATI comparision]("http://www.phoronix.com/scan.php?page=article&item=amd_driver_q111&num=1")
Lets see: 2 week old gitpull with 2.6.37 VS Catalyst 10.12
The 2 weeks is not going to make a difference, the drivers are **** except for the oldest of the showcased cards here. On the oldest the performance is reaching "acceptable" levels, so long you are running a 60 Hz monitor.
I wonder how long it will be until proper performance, 2-3 years?
And by that I mean Gallium 3D performing at the least 95% of catalysts performance.

---

### Post by mjhouska on 2011-01-09
Well i  updated to Ubuntu 10.10 on my Lenovo T60p (ATI firegl 5250) An gcompris is now working! so i guess 3d is now working finally. But still celestia refuses to load(i can only use the nonGL version of celestia in XP) so i will be going back to NVidia ASAP anyway. In XP GL Celestia loads but text is mangled up.

---

### Post by mjhouska on 2011-01-09
BTW Kstars works fine

---

### Post by JDShu on 2011-01-09
> **del_diablo said:**
> [Phoronix: A more ATI comparision]("http://www.phoronix.com/scan.php?page=article&item=amd_driver_q111&num=1")
Lets see: 2 week old gitpull with 2.6.37 VS Catalyst 10.12
The 2 weeks is not going to make a difference, the drivers are **** except for the oldest of the showcased cards here. On the oldest the performance is reaching "acceptable" levels, so long you are running a 60 Hz monitor.
I wonder how long it will be until proper performance, 2-3 years?
And by that I mean Gallium 3D performing at the least 95% of catalysts performance.

Hmm, do you use a CRT monitor? As far as I know, *all* LCDs are 60 Hz.

---

### Post by handy on 2011-01-09
I have found over the last year that this driver stack including the associated parts of the kernel have from time to time made dramatic leaps & bounds in their progress.

So as I said previously I expect that when the other things are done & 3D performance becomes the priority, that performance will improve incredibly quickly. :)

When you look at where things are at here:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

It is easy to see that 3D performance is getting very close to becoming the main focus for the dev's.


Something that is easy to forget is that AMD have been & are being a truly great help in the development of the open driver stack.

---

### Post by cascade9 on 2011-01-09
> **JDShu said:**
> Hmm, do you use a CRT monitor? As far as I know, *all* LCDs are 60 Hz.

Nope, there are 120Hz models (TVs and monitors). There are 75Hz moels as well, but they display at 60Hz so dont count. ;)

---

### Post by JDShu on 2011-01-09
> **cascade9 said:**
> Nope, there are 120Hz models (TVs and monitors). There are 75Hz moels as well, but they display at 60Hz so dont count. ;)

Ah ok, fair enough. Are these widespread? I haven't heard of them until now.

---

### Post by sandyd on 2011-01-09
> **JDShu said:**
> Ah ok, fair enough. Are these widespread? I haven't heard of them until now.

I have a 120.
Their not quite widespread, the one my cousin has is a 60, as with the former LG 1080p monitor I had. Also, my TV is 60hz.

---

### Post by JDShu on 2011-01-09
> **sandyd said:**
> I have a 120.
Their not quite widespread, the one my cousin has is a 60, as with the former LG 1080p monitor I had. Also, my TV is 60hz.

Heeh, learn something every day. How's the performance? 

Also:

[http://www.phoronix.com/scan.php?page=news_item&px=ODk5OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODk5OQ)

Covers the optimizations that are being started :)

---

### Post by I_can_see_the_light on 2011-01-10
> **I_can_see_the_light said:**
> The reason I'm asking is because Kwin is running unacceptably slow with desktop effects enabled, things are a little bit better with Compiz so that's what I'm using right now but any sort of 3d stuff seem to slow the system down to a crawl.

```
glxinfo | grep -i opengl
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV380 3150) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
```

With PCLinuxOS the performance is really good and I noticed that they are using an older version of Mesa, 7.5.x I think, and an older version of xorg-server as well.

An update on this. I haven't got around to test the xorg-edgers ppa yet but last week I gave Chakra a test run from a live CD and guess what, 3D performance was fine! Chakra 0.3.0 runs on Mesa 7.7.1, Linux kernel 2.6.35 and xorg-server 1.7.7. 

My Kubuntu install runs on Mesa 7.7.1, Linux kernel 2.6.32 and xorg-server 1.7.6. I tried using a backported kernel from Maverick (2.6.35) but that didn't make any difference. Then I thought it could be because of KMS, because in PCLOS KMS isn't active, but I then found out that Chakra has KMS activated so now it's back to square one. 

Could it be a problem with the packaging (in either Ubuntu or Debian) of the R300 driver? Can't see what else it could be?

---

### Post by handy on 2011-01-10
There are more files involved than just mesa.

I think that if you use the xorg-edgers ppa, & use a late kernel you will get past this problem.

(I've been using kernel .37 since the day it became available with not a problem - its currently up to rc8.)

---

### Post by I_can_see_the_light on 2011-01-10
> **handy said:**
> There are more files involved than just mesa.

I think that if you use the xorg-edgers ppa, & use a late kernel you will get past this problem.

(I've been using kernel .37 since the day it became available with not a problem - its currently up to rc8.)

You're probably right, though I find it a little peculiar that things are working so much better in the two distros I mentioned earlier. I will try the xorg-edgers ppa when I have the time.

As a side note, I disabled KMS at boot time and the speed increase in glxgears was tenfold, however I got a hard freeze after a little while so I didn't get to try it for long.

---

### Post by handy on 2011-01-10
> **I_can_see_the_light said:**
> You're probably right, though I find it a little peculiar that things are working so much better in the two distros I mentioned earlier. I will try the xorg-edgers ppa when I have the time. 

I'm running Arch 64bit; haven't been a true Ubuntu user since Dapper as Edgy was buggy on my system so I moved on. The bugs are not a problem now, but I'm more at home using a different distro. 

The community here is great, & Ubuntu is a terrific distro for all kinds of uses. So I still hang around some. :)

---

### Post by del_diablo on 2011-01-10
> **JDShu said:**
> Also:

[http://www.phoronix.com/scan.php?page=news_item&px=ODk5OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODk5OQ)

Covers the optimizations that are being started :)

Wait am I reading correctly: MESA which is suppose to be a backend for CPU to do 3D rendering if only it was fast enough, is getting optimizations for a GPU?
Why is this not done on the Gallium stack instead?

---

### Post by JDShu on 2011-01-10
> **del_diablo said:**
> Wait am I reading correctly: MESA which is suppose to be a backend for CPU to do 3D rendering if only it was fast enough, is getting optimizations for a GPU?
Why is this not done on the Gallium stack instead?

Gallium is part of mesa.

---

### Post by handy on 2011-01-10
> **del_diablo said:**
> Wait am I reading correctly: MESA which is suppose to be a backend for CPU to do 3D rendering if only it was fast enough, is getting optimizations for a GPU?
Why is this not done on the Gallium stack instead?

I have both the mesa-classic & the mesa-gallium installed on my Arch system, which gives me the ability if I so desire to manually switch between the two of them if I so desire by changing environment variables.

Before long there will be only one... ;)

---

### Post by sandyd on 2011-01-11
> **I_can_see_the_light said:**
> An update on this. I haven't got around to test the xorg-edgers ppa yet but last week I gave Chakra a test run from a live CD and guess what, 3D performance was fine! Chakra 0.3.0 runs on Mesa 7.7.1, Linux kernel 2.6.35 and xorg-server 1.7.7. 

My Kubuntu install runs on Mesa 7.7.1, Linux kernel 2.6.32 and xorg-server 1.7.6. I tried using a backported kernel from Maverick (2.6.35) but that didn't make any difference. Then I thought it could be because of KMS, because in PCLOS KMS isn't active, but I then found out that Chakra has KMS activated so now it's back to square one. 

Could it be a problem with the packaging (in either Ubuntu or Debian) of the R300 driver? Can't see what else it could be?

> **handy said:**
> There are more files involved than just mesa.

I think that if you use the xorg-edgers ppa, & use a late kernel you will get past this problem.

(I've been using kernel .37 since the day it became available with not a problem - its currently up to rc8.)
Unfortunatey, it isn't a problem with the packaging.
This bug has existed for some time already (ill post links later, my system is currently really slow), because xorg pointed at KDE, and KDE pointed at xorg for the issue. Im having the same problem with KDE with gallium SVN. Which means gallium is a POS for anyone using KDE for the time (and yes, I have everything new, including kde 4.6rc2)

---

### Post by handy on 2011-01-11
> **sandyd said:**
> Unfortunatey, it isn't a problem with the packaging.
This bug has existed for some time already (ill post links later, my system is currently really slow), because xorg pointed at KDE, and KDE pointed at xorg for the issue. Im having the same problem with KDE with gallium SVN. Which means gallium is a POS for anyone using KDE for the time (and yes, I have everything new, including kde 4.6rc2)

I've not been seeing complaints from KDE users on the Arch forum regarding this. How old is this particular bug?

I use Openbox so I have no personal experience on this subject.

---

### Post by sandyd on 2011-01-11
> **handy said:**
> I've not been seeing complaints from KDE users on the Arch forum regarding this. How old is this particular bug?

I use Openbox so I have no personal experience on this subject.
[http://forums.gentoo.org/viewtopic-t-826409-start-0.html](http://forums.gentoo.org/viewtopic-t-826409-start-0.html) (this has the same issue with r600), except that I can enable the drivers, it just makes the desktop unusable


[https://bugs.kde.org/show_bug.cgi?id=246047](https://bugs.kde.org/show_bug.cgi?id=246047)

---

### Post by handy on 2011-01-12
I have heard talk of this from time to time on the Arch forum. I don't really pay any attention to desktop effects as I barely have a desktop.  I don't use icons apart from a small xfce4-panel, beyond that I automatically open Worker, Firefox, Sakura & Cream on their own respective desktops when I boot into Openbox. I use the OB menu for the less commonly used app's, or ones that I don't access from Worker.

So I'm kind of on an island away from desktop stuff that's floating in a black desktop...

I shouldn't have started this post...  ;)

---

### Post by I_can_see_the_light on 2011-01-12
> **sandyd said:**
> Unfortunatey, it isn't a problem with the packaging.
This bug has existed for some time already (ill post links later, my system is currently really slow), because xorg pointed at KDE, and KDE pointed at xorg for the issue. Im having the same problem with KDE with gallium SVN. Which means gallium is a POS for anyone using KDE for the time (and yes, I have everything new, including kde 4.6rc2)
But the question still remains, why is it affecting Ubuntu and not Chakra and PCLOS?

---

### Post by psusi on 2011-01-12
So what exactly is gallium?

---

### Post by del_diablo on 2011-01-12
> **psusi said:**
> So what exactly is gallium?

A driver architecture.
A "normal" driver is written against API's, like Direct X or OpenGL or stuff.
The thing about Gallium 3D is that they make a layer to write the driver against instead of the normal API groups, and that layer further enables plugins for the drivers. The plugins are stuff like OpenGL, extensions, etc...
So benefit is that once the driver architecture is done, and a driver is fully written, the driver will automatically get access to all the plugins, instead of bootstrapping the driver to each individual API.
The advantage is more or less that you get access to OpenGL, and tons of plugins instead of waiting for the driver to intigrate them.
Of course, that is my understanding of it, if I am wrong on some of it, please correct me.

> **JDShu said:**
> Gallium is part of mesa.
But the plan is then that the "finished" Gallium3D drivers will use MESA for opengl lib?
I don't think it is like that, but if it is, I am crying.

---

### Post by psusi on 2011-01-12
As I understand it, the normal mesa drivers implement OpenGL, and if you want to run a windows directx app, WINE has to emulate directx by translating to OpenGL.  Native Linux apps use OpenGL already.

It sounds like you are saying the purpose of gallium is to natively implement the directx calls to speed up wine?

---

### Post by medic2000 on 2011-01-12
> **handy said:**
> I have heard talk of this from time to time on the Arch forum. I don't really pay any attention to desktop effects as I barely have a desktop.  I don't use icons apart from a small xfce4-panel, beyond that I automatically open Worker, Firefox, Sakura & Cream on their own respective desktops when I boot into Openbox. I use the OB menu for the less commonly used app's, or ones that I don't access from Worker.

So I'm kind of on an island away from desktop stuff that's floating in a black desktop...

I shouldn't have started this post...  ;)
+1 for Arch, Openbox and shortcuts for starting apps. This is the ultimate desktop experience! :)

---

### Post by del_diablo on 2011-01-12
No, that has nothing to do with anything.
Lets say we write 4-5 drivers.
Then a new version of OpenGL comes out.
Instead of writing ANOTHER +3-4 drivers, the OpenGL driver is a plugin.
The purpose of Gallium is to speed up driver development, and reduce mantainance time.
While you ironically can do what you said(DX plugin for Wine), stuff like video codecs acceleration and a lot of other fun stuff will land instead :P
Write once, deploy everywhere.

---

### Post by psusi on 2011-01-12
When they add things to OpenGL, you don't rewrite all the drivers, you just update them... or not since the new stuff probably isn't supported on the older hardware.

It sounds more like mesa is the framework in which OpenGL compliant hardware drivers are written ( as well as the reference software implementation ), and Gallium is is attempting to extend that framework to include more apis to get the video card to perform other tasks like GP-GPU, and acceleration of transcoding.

---

### Post by handy on 2011-01-12
> **medic2000 said:**
> +1 for Arch, Openbox and shortcuts for starting apps. This is the ultimate desktop experience! :)

Only for some. For most users it is not at all the way they prefer to interface with their computer.

---

### Post by handy on 2011-01-12
**Gallium3D Technical Overview**

Gallium3D is a new architecture for building 3D graphics drivers. Initially supporting Mesa and Linux graphics drivers, Gallium3D is designed to allow portability to all major operating systems and graphics interfaces. 

[http://wiki.freedesktop.org/wiki/Software/gallium](http://wiki.freedesktop.org/wiki/Software/gallium)

---

### Post by sandyd on 2011-01-12
> **I_can_see_the_light said:**
> But the question still remains, why is it affecting Ubuntu and not Chakra and PCLOS?
I have no idea. Unless they applied extra patches, or are using KDE 4.5 (gallium works kinda fine in there)

---

### Post by I_can_see_the_light on 2011-01-13
> **sandyd said:**
> I have no idea. Unless they applied extra patches, or are using KDE 4.5 (gallium works kinda fine in there)

I'm using KDE 4.5 in Kubuntu Lucid, are you saying it's worth a shot trying out gallium? By the way, neither Chakra 0.3.0 nor PCLOS 2010 use gallium.

---

### Post by medic2000 on 2011-01-13
> **handy said:**
> Only for some. For most users it is not at all the way they prefer to interface with their computer.

I know. I only spoke for myself.

 I came to this type of "usage" level by level. I've used Windows, KDE, Gnome, Xfce... And now i can not think another way. Because everytime you need to start "Firefox" you dont need to leave keyboard, grab the mouse and take the cursor to the firefox shortcut and click. Just "Super + F" and you are done! And it launchs in my 5th destop named "Internet". Just a "Super + 5" and i am there. There are only a handful applications installed on my computer and they do "every" job! So less applications, less libraries, less bugs!

Very easy. Very fast. 

But i know everybody has their way. And its great for them too. I can only suggest them to try. It takes time but gives great fruits. Like the great "Vim" editor.

Oh i am drifting from the topic. Sorry for that. Just couldnt resist when i saw another posted about the refined desktop.

---

### Post by JDShu on 2011-02-25
So I've been keenly interested in the drivers and wanted to share what I've learned about recent developments. 

It seems fair to say that at least technically, the oss ATI drivers are continuously getting better, and support for the newest hardware is coming out earlier and earlier after initial launch. [The recent page flipping support]("http://www.phoronix.com/scan.php?page=news_item&px=OTAwNA") makes a [HUGE]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_expanded") impact and should be generally available by the distros later in the year. The devs are now looking for bottlenecks in order to optimize the driver efficiently. I have complete faith in them succeeding and making the drivers even better.

Critically, [s3tc support]("http://www.phoronix.com/scan.php?page=news_item&px=OTEwNg") has been implemented into the newer drivers, so that should make a lot of previously unplayable games, well, playable. Unfortunately, since its a patented tech, I don't think it will be included in the major distros. Maybe non corporation repos like medibuntu or linux mint will make it available.

On a similar note, it won't be possible to fully implement OpenGL 3 and 4 on the oss drivers (this includes the intel drivers and nouveau) again due to patented technologies. This means, among other things, that certain new games (I think this includes the upcoming [Oil Rush]("http://www.youtube.com/watch?v=q4dPuQ4pw70")) may never be runnable, or even if they are, performance will be terrible. Perhaps they'll be able to do something similar to s3tc, but there are no plans on the horizon.

All in all, the oss drivers are becoming seriously awesome, but there are some unfortunate show stoppers that may or may not get resolved.

Note: Most of the links are from Phoronix, I guess because they are the only ones who do regular reporting about hardware on Linux. Phoronix has its issues, but their forums are frequented by the oss driver devs.

---

### Post by CarpKing on 2011-02-25
The most informative part of Phoronix is the forum thread for each article, where everyone jumps in to point out all the mistakes the article author makes.  It's like an accidental wiki!  

It's pretty cool that both several OSS driver devs and an ATI representative post there regularly.  Makes for very interesting discussions.

---

### Post by del_diablo on 2011-02-25
> **JDShu said:**
> Unfortunately, since its a patented tech, I don't think it will be included in the major distros. Maybe non corporation repos like medibuntu or linux mint will make it available.

Nobody cares.
All Ubuntu has to do to get around it is to setup the initial mirror somewhere in EU that is not GB nor France.
Problem solved, and then the userbase was happy again.

> On a similar note, it won't be possible to fully implement OpenGL 3 and 4 on the oss drivers (this includes the intel drivers and nouveau) again due to patented technologies.

What part of the full OGL3 or OGL4 spec is patentented? By who?
And why is a free spec patented?
Just curious.


And as CarpKing said, phoronix itself is a horrible source, using the forums as supplement makes it a good source.

---

### Post by JDShu on 2011-02-25
> **del_diablo said:**
> Nobody cares.
All Ubuntu has to do to get around it is to setup the initial mirror somewhere in EU that is not GB nor France.
Problem solved, and then the userbase was happy again.

What part of the full OGL3 or OGL4 spec is patentented? By who?
And why is a free spec patented?
Just curious.

And as CarpKing said, phoronix itself is a horrible source, using the forums as supplement makes it a good source.

Well, Ubuntu can't officially ship it without infringing on a patent. They would be knowingly distributing patented tech.

The patented technology in OGL3/4 is floating point textures. It's arguably something that shouldn't even be patented, but it is what it is, and its in the spec because we really really need it. It was filed by SGI, who sold it to MS, who apparently sold it to some patent holding company. I think thats how it went anyway.

And yes, the Phoronix forums are an awesome place to lurk and get insight. Not only the devs, but some of the members are very knowledgeable too.

EDIT: [This may help illuminate]("http://www.x.org/wiki/Events/XDC2009/Notes")
> idr: OpenGL 3 and Mesa

Several patented technologies in OpenGL that we want in Mesa
Floating point textures and render targets (in core GL3), certain compressed texture formats
external libraries solve some of it (for S3TC), could kinda do that with fp textures... but not targets
could act like freetype (configure switch for patented technologies)
could try to get OIN to help on the patent license front
plan: yes, do both of those


---

### Post by CarpKing on 2011-02-26
Phoronix is pretty good for letting you know when there's something worth finding out.  You just have to do a bit of extra work to actually find the truth of that something.  

I don't recommend doing shots every time the articles use the word "though" without a comma on either side unless you can hold your liquor.

---

### Post by handy on 2011-02-26
I tend to find out the truth via Perry3D's thread on the Arch forum.

People there mostly are using the cutting edge kernel & driver stack so they tend to pull out the problems, exposing them & bringing about investigation from other regulars of that thread.

Phoronix topics do get bought up, but the practicalities of such are what people are truly interested in there.

---

### Post by handy on 2011-03-13
Good news for the AMD/ATi users, Ubuntu 11.4 will be using the .38 kernel & the Gallium graphics driver stack for all supported GPUs.

The 69000 series GPU's will be best served by using the kernel upgrade & xorg-edgers ppa how-to under the Ubuntu Stuff: heading found in the OP of this thread, to get into the .39 kernel & the advantages that it will have for them.

Read lots of details here:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1)

---

### Post by phredbull on 2011-05-08
What is the best way to get the xorg-edgers packages for Debian? Get source and compile?:confused:

---

### Post by ddimit on 2011-05-17
i have installed these debians 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc8-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-rc8-natty/")
because my kernel is 2.6.38-8-generic
im sudo apt-get update
then sudo apt-get upgrade
and tells me one file kept back and  the final error message ```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
please help me because i have serious problem with 1080p movies

---

### Post by murderslastcrow on 2011-05-17
I'm currently using an R600 card and, while it was performing quite well before, the new Gallium drivers in 2.6.38 are rocking my world! I can use the new Blender and all of my artwork stuff without any issues, now- hopefully it just keeps getting better. :3 *satisfied customer*

---

### Post by el_koraco on 2011-05-17
The OSS ATI drivers in Ubuntu 11.04 rock the hell out of the system with any kind of video rendering. I just hope that in a year's time they will get close to supporting fan management as fglrx does, because that's the only thing that keeps me installing the horrible fglrx on my laptop.

---

### Post by meborc on 2011-05-17
> **el_koraco said:**
> The OSS ATI drivers in Ubuntu 11.04 rock the hell out of the system with any kind of video rendering. I just hope that in a year's time they will get close to supporting fan management as fglrx does, because that's the only thing that keeps me installing the horrible fglrx on my laptop.

+1 

the fan noise from my 4850HD is too much for my co-worker. I have to use use ```
aticonfig --pplib-cmd "set fanspeed 0 24"
``` with fglrx to get a normal working environment.

24 is the lowest I can set it and it is not too noisy, temperatures are below 40 C as I only use the card to have 2 monitors.

---

### Post by el_koraco on 2011-05-17
The noise itself wouldn't bother me, it's the heat. fglrx has better fine grain control, so you get less noise and temps you can tolerate. I think the problems regarding heat started with KMS, at least that's what I found out reading older bug reports. But ATI has put out a call for two more developers for the open source driver stack, so I'm hoping this will get handled soon. BTW, the 11.5 Catalyst is in line with KMS and Plymouth in Natty on my machine. I get the same results as when I employed the Plymouth fixes in 10.04 and 10.10. So things are obviously moving in the right direction there as well, but the desktop is like three times more responsive with radeon.

---

### Post by handy on 2011-05-31
Today (as there was yesterday) there was an upgrade of the -git AMD/ATi driver stack (on Arch), I just did the superficial check & got the following results, which give me ~200 fps, speed increase. Which is the first one I've had for months. :) 

This using the classic stack & the following command:

**glxinfo | grep -i opengl && glxgears**
> 
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV630 9583)  TCL DRI2
OpenGL version string: 2.1 Mesa 7.11-devel (git-29ceeeb)
OpenGL shading language version string: 1.20
OpenGL extensions:

7219 frames in 5.0 seconds = 1443.752 FPS
7215 frames in 5.0 seconds = 1441.940 FPS
7221 frames in 5.0 seconds = 1444.175 FPS
7211 frames in 5.0 seconds = 1442.198 FPS
7220 frames in 5.0 seconds = 1443.959 FPS
7211 frames in 5.0 seconds = 1442.159 FPS
7211 frames in 5.0 seconds = 1442.179 FPS 

This is using the Gallium stack & the following command:

**LIBGL_DRIVERS_PATH=/usr/lib/xorg/modules/dri_g/ glxinfo |grep -i opengl && glxgears**
> 
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV630
OpenGL version string: 2.1 Mesa 7.11-devel (git-29ceeeb)
OpenGL shading language version string: 1.20
OpenGL extensions:

7190 frames in 5.0 seconds = 1437.857 FPS
7219 frames in 5.0 seconds = 1443.778 FPS
7179 frames in 5.0 seconds = 1435.756 FPS
7184 frames in 5.0 seconds = 1436.640 FPS
7183 frames in 5.0 seconds = 1436.583 FPS
7179 frames in 5.0 seconds = 1435.776 FPS
7183 frames in 5.0 seconds = 1435.516 FPS 

---

### Post by handy on 2011-06-09
This is a worthwhile read from the Phoronix site:

**May 2011: Gallium3D vs. Classic Mesa vs. Catalyst**

[http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011](http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011)

---

### Post by handy on 2011-06-11
This is more interesting than the previously posted test results.


[B]A Fresh Look At The AMD Radeon Gallium3D Performance
Published on June 10, 2011[/B]:

[http://www.phoronix.com/scan.php?page=article&item=amd_r600g_june10&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600g_june10&num=1)

---

### Post by JDShu on 2011-06-11
> **handy said:**
> This is more interesting than the previously posted test results.


[B]A Fresh Look At The AMD Radeon Gallium3D Performance
Published on June 10, 2011[/B]:

[http://www.phoronix.com/scan.php?page=article&item=amd_r600g_june10&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600g_june10&num=1)

Indeed this was really interesting. Unfortunately since Phoronix never benchmarked those tweaks earlier we have no idea how performance has improved with them over time. At least it seems that there is continual steady improvement with the default options.

---

### Post by handy on 2011-06-11
> **JDShu said:**
> Indeed this was really interesting. Unfortunately since Phoronix never benchmarked those tweaks earlier we have no idea how performance has improved with them over time. At least it seems that there is continual steady improvement with the default options.

There is improvement. Currently the dev' work seems to have started to work on optimising the 3D performance. 

I know it is not a benchmark, but my glxgears speed has risen on each of the last two upgrades (within the last 5 days) by ~250 fps. Prior to that my R600 series GPU hadn't had any 3D speed improvements for months.

Hopefully in future Phoronix will continue with tests that incorporate the tweaks as well.

---

### Post by Jaksis on 2011-06-15
Hi all,

maybe any can explain where to get and how to install open source drivers for radeon's?

Thanks.

---

### Post by I_can_see_the_light on 2011-06-15
> **Jaksis said:**
> Hi all,

maybe any can explain where to get and how to install open source drivers for radeon's?

Thanks.

You should normally not have to do anything, they will be loaded at boot. Have you previously used the proprietary drivers released by AMD? If so you must uninstall those and possibly do some tweaking.

---

### Post by Jaksis on 2011-06-15
> **I_can_see_the_light said:**
> You should normally not have to do anything, they will be loaded at boot. Have you previously used the proprietary drivers released by AMD? If so you must uninstall those and possibly do some tweaking.

No, I just install ubuntu 11.04, and see, that my x1600 with unity works not so smoothly that i expect. Now I see, that is released Catalyst 11.4 drivers, i try install it, but have error, that they can't find my adapter...

*Ahh... catalyst 11.4 dont support x1600 :(*

---

### Post by del_diablo on 2011-06-15
> **I_can_see_the_light said:**
> You should normally not have to do anything, they will be loaded at boot. Have you previously used the proprietary drivers released by AMD? If so you must uninstall those and possibly do some tweaking.

That is.... WRONG! The default activiated is quite.... and more than dated :(
This is a good start: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by handy on 2011-06-15
> **del_diablo said:**
> That is.... WRONG! The default activiated is quite.... and more than dated :(
This is a good start: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

I think that you are being a little harsh del_diablo...

Jalsis is obviously a new user (just like we all were once) & is asked the question about installing the open-source drivers, not knowing that, that driver stack is what is the default when Ubuntu is installed.

I_can_see_the_light, has replied appropriately to the questions asked.

Then from Jaksis response we find that he(?) is (at least now) using the Catalyst (closed source stack).

From the discourse it is not hare to appreciate that a new user is trying to get the best results that they can out of the (very likely) two available options for the GPU that they are using. 

Try this, then that, & carry on...

I do that all the time.

Lets be kind.

---

### Post by el_koraco on 2011-06-15
> **handy said:**
> 
I_can_see_the_light, has replied appropriately to the questions asked.

Then from Jaksis response we find that he(?) is (at least now) using the Catalyst (closed source stack).



From what I see, he's using the radeon driver on natty, for an older card which isn't supported by the recent releases of Catalyst, and isn't getting the best results. So I would advise that he read up on the xorg edgers ppa and try to find out if he can get it to work better.

---

### Post by el_koraco on 2011-06-15
Jaksis, I suggest you start by reading these two documents, which are ubuntu specific. 

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Jaksis on 2011-06-15
Yes, I read that documentations before. 
I put in source list [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) and make upgrade. Can't say, that is better now, but tnx anyway.

---

### Post by Hman242 on 2011-06-15
Speaking of ATI drivers, how well do you think a Radeon 6870 would work in Ubuntu?

---

### Post by handy on 2011-06-15
> **el_koraco said:**
> From what I see, he's using the radeon driver on natty, for an older card which isn't supported by the recent releases of Catalyst, and isn't getting the best results. So I would advise that he read up on the xorg edgers ppa and try to find out if he can get it to work better.

He has obviously tried successfully or not to install the Catalyst stack.

He may need to know that he must uninstall the open-source stack before he installs Catalyst?

**@Jaksis:** Have a look at the first post of this thread & scroll down to the *Ubuntu Stuff:* section & follow those instructions in the order that they are written.

With any luck your GPU & your machine's favoured resolution won't cause you too many more headaches. :)

---

### Post by handy on 2011-06-15
> **Hman242 said:**
> Speaking of ATI drivers, how well do you think a Radeon 6870 would work in Ubuntu?

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

[http://www.x.org/wiki/GalliumStatus](http://www.x.org/wiki/GalliumStatus)

Gallium is what we (the open-source users, including Ubuntu) are all using now.

---

### Post by del_diablo on 2011-06-15
Can we please set a rule here about linking to the radeon future program should be banned? While it should be linked, there is currently no way of telling how many months it has been since somebody actually updated it.
Or how much of that tecnical non-sense a user can figure out and make sense off.

---

### Post by handy on 2011-06-15
> **del_diablo said:**
> Can we please set a rule here about linking to the radeon future program should be banned? While it should be linked, there is currently no way of telling how many months it has been since somebody actually updated it.
Or how much of that tecnical non-sense a user can figure out and make sense off.

No, we can't set that rule. & it is NOT the future program it is an indication of where development is currently at.

From my experience, those sites are updated VERY often.

If you have a problem with this I think that you should take it up with the X.org people & not here.

If you can't understand what the sites are saying that is not our fault.

---

### Post by del_diablo on 2011-06-15
If I remember a few months ago those matrixes where not updated for several months.
Nor where they really telling anything useful.
If I want to know "does this work?", they are not useful either.

Another note: He asked HOW WELL THEY WORKED.........
That requires a proper benchmark, and some video capture of it. Or some roughe estimations. The feature matrix does not contain any of those.

And lets go into a fallancy: If something is broken, should one tell other people, or just shut up and let it pass? You are suggesting that anything broken must NEVER be fixed, and it is the same fallancy as "you have no right to get help", because the argument one is really stating is "we are allowed to be assholes intead of helping".

---

### Post by handy on 2011-06-15
Good. 

I agree with everything you said.

---

### Post by I_can_see_the_light on 2011-06-15
> **del_diablo said:**
> That is.... WRONG! The default activiated is quite.... and more than dated :(
This is a good start: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Wrong? Wow, like **handy** said, that's harsh.

Neither you nor me knew at the time what GPU he had or what his requirements were. To many people the default setup is more than fine, it all depends on what you do with your computer.

But lets not get into an argument over this, it's a beautiful sunny day (at least where I'm at :) )

---

### Post by handy on 2011-06-15
> **I_can_see_the_light said:**
> ...

But lets not get into an argument over this, it's a beautiful sunny day (at least where I'm at :) )

Lucky you. 

It has been raining very heavily for some days here (& more to come), the pump I use to get water from the river to our 5,000 imperial gallon tank, got drowned today. First time in 20 years, so I can't really complain. The trees are enjoying it. They should make the most of it as a drought is predicted to start in January next year (again).

---

### Post by handy on 2011-06-15
> **el_koraco said:**
> From what I see, he's using the radeon driver on natty, for an older card which isn't supported by the recent releases of Catalyst, and isn't getting the best results. So I would advise that he read up on the xorg edgers ppa and try to find out if he can get it to work better.

Yes, you are correct.

Only the open-source driver stack supports that card these days. He will get the best performance by following the how-to situated in the "Ubuntu Stuff" section of the first post of this thread.

I'm currently using the 2.6.39-rc6-ARCH-54949-g2a9e586-dirty kernel, (& expecting to move to the new git 3.0 version any day now). The dev' kernels & other associated packages involved in the AMD/ATi driver stack have given me next to no trouble over the last 1.70 years. (for all that's worth. :))

---

### Post by mips on 2011-06-15
handy I think you should become the official spokesperson for this project the way you keep track of things ;)

---

### Post by handy on 2011-06-15
> **mips said:**
> handy I think you should become the official spokesperson for this project the way you keep track of things ;)

What, the weather? :lolflag:

(I probably am in the Cafe, though there are many that contribute that know so much more than I ever will. In the end I'm just a talking head.)

---

### Post by I_can_see_the_light on 2011-06-15
> **handy said:**
> Lucky you. 

It has been raining very heavily for some days here (& more to come), the pump I use to get water from the river to our 5,000 imperial gallon tank, got drowned today. First time in 20 years, so I can't really complain. The trees are enjoying it. They should make the most of it as a drought is predicted to start in January next year (again).

Wow! I guess things are evening out when looking at a broader perspective though, we could really do with some rain here since everything is getting yellow from all the pollen.

---

### Post by handy on 2011-06-15
> **I_can_see_the_light said:**
> Wow! I guess things are evening out when looking at a broader perspective though, we could really do with some rain here since everything is getting yellow from all the pollen.

Tough for those that suffer from hay fever I'd reckon.

---

### Post by I_can_see_the_light on 2011-06-15
> **handy said:**
> Tough for those that suffer from hay fever I'd reckon.

Yes, my wife thought she had an eye infection but it turned out to be hay fever related.

---

### Post by henrique_rauen on 2011-06-17
Guys,
I installed Ubuntu 11.04 and the default open source drivers are working great for my HD 5750, the only problem is that I connect my PC to the TV via the HDMI output in order to watch some HD videos, and although the image is great, i can't get to send audio over. Looking at [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature) it says its not supported for my card (Evergreen), but the discussion between del_diablo and Handy about that page being updated kind of give me hopes,  :P (the last one to die, right?). Anyone knows for sure if it is possible to send audio over HDMI with the open source drivers and my card?

I also tried with the prop drivers from AMD, and I DID**** get the sound over HDMI, the problem is that I can't get the playback to be as smooth as it should (comparing to the open source drivers and win7-64. Managed to remove tearing, Vsync etc, which helped, but still not smooth as it should).

---

### Post by JDShu on 2011-06-17
> **henrique_rauen said:**
> Guys,
I installed Ubuntu 11.04 and the default open source drivers are working great for my HD 5750, the only problem is that I connect my PC to the TV via the HDMI output in order to watch some HD videos, and although the image is great, i can't get to send audio over. Looking at [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature) it says its not supported for my card (Evergreen), but the discussion between del_diablo and Handy about that page being updated kind of give me hopes,  :P (the last one to die, right?). Anyone knows for sure if it is possible to send audio over HDMI with the open source drivers and my card?

I also tried with the prop drivers from AMD, and I DID get the sound over HDMI, the problem is that I can't get the playback to be as smooth as it should (comparing to the open source drivers and win7-64. Managed to remove tearing, Vsync etc, which helped, but still not smooth as it should).

The feature matrix is very up to date. In fact if you look at the recent changed link, you'll see that it was updated today (date of this post).

---

### Post by handy on 2011-06-18
Some people are getting choppy video playback using the Catalyst driver. This may help you:

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by handy on 2011-07-12
Here's some good news:

[http://www.phoronix.com/scan.php?page=news_item&px=OTY1OQ](http://www.phoronix.com/scan.php?page=news_item&px=OTY1OQ)

---

### Post by el_koraco on 2011-07-20
I've had some luck pimping the Galium/radeon driver with regard to power management in Fedora. 

Added 

```
Section "Device"
        Identifier  "Videocard0"
        Driver      "radeon"
        Option "ClockGating"       "true"
        Option "DynamicPM"         "true"
EndSection

```

to /etc/X11/xorg.conf. Brought down the temp by about 10 degrees C. Not as good as fglrx, but it's nice to see radeon getting some good PM. Although, I can't for the life of me figure out why this is not the default.

---

### Post by kaldor on 2011-07-20
From my experience with AMD over the last short while, I am likely not buying NVIDIA again. AMD actually puts effort into supporting Linux these days, and their open source drivers are really good apart from gaming.

---

### Post by handy on 2011-07-21
I've had the same attitude as yours for some time kaldor. AMD are giving so much to the open-source community I couldn't possibly support anyone else no-matter how much better their drivers were.

It is only a matter of time & the open-source drivers will give sufficient support to the gamers. I expect that eventually AMD will only support open-source drivers.

---

### Post by GSF1200S on 2011-07-21
> **kaldor said:**
> From my experience with AMD over the last short while, I am likely not buying NVIDIA again. AMD actually puts effort into supporting Linux these days, and their open source drivers are really good apart from gaming.

Please dont take this the wrong way as I am all for the recent developments in relation to ATI video cards (really, kudos to them), but I dont think thats fair to Nvidia.

Yes, Nvidia isnt doing as ATI does (with open source), but they do offer good drivers and great products. I have fantastic 2d performance, 3d performance, power management and an extremely powerful control interface (though Nvidia could always make things better), while many ATI users still suffer in at least one area.

Again, ATI has done the right thing and their linux support is much better than it used to be, but to somehow imply Nvidia is evil or worse off performance-wise is not true to what I believe having experience with both brands.

---

### Post by handy on 2011-07-21
> **GSF1200S said:**
> 
Please dont take this the wrong way as I am all for the recent developments in relation to ATI video cards (really, kudos to them), but I dont think thats fair to Nvidia. 

Why isn't it fair to nVidia, to give AMD praise for the huge amount of work that they have done re. their multifaceted contributions to the open-source AMD/ATi driver stack? When nVidia basically do nothing in that regard?


> **GSF1200S said:**
> 
Yes, Nvidia isnt doing as ATI does (with open source), but they do offer good drivers and great products. I have fantastic 2d performance, 3d performance, power management and an extremely powerful control interface (though Nvidia could always make things better), while many ATI users still suffer in at least one area. 

None of that has anything to do with nVidia's lack of support for the nVidia open-source driver stack.
You could just as well be praising MS for their Office Suite against OpenOffice or LibreOffice.

> **GSF1200S said:**
> 
Again, ATI has done the right thing and their linux support is much better than it used to be, but to somehow imply Nvidia is evil or worse off performance-wise is not true to what I believe having experience with both brands.

It has never been implied in this entire mega-thread that nVidia has inferior performance to the open-source AMD/ATi driver stack.

I use both brands also, as many of us do. The bottom line here is that over the last couple of years due to AMD's choice to give so much support to the development of the open-source driver stack for their GPUs, we have been able to benefit from a huge increase in the performance & reliability of that stack.

I know that you weren't really making a post to hit the AMD open-source support GSF1200S, but you kind of did anyway. :)

---

### Post by el_koraco on 2011-07-21
Not to mention that AMD has better support for hybrid graphics than Nvidia. The binary drivers suck, but I'm happy to endure that if it means that the open source stack will catch up in a year or two. Imagine buying a machine with an ATI GPU, regular or hybrid, and not have to fiddle with proprietary drivers.

---

### Post by GSF1200S on 2011-07-21
> **handy said:**
> Why isn't it fair to nVidia, to give AMD praise for the huge amount of work that they have done re. their multifaceted contributions to the open-source AMD/ATi driver stack? When nVidia basically do nothing in that regard?
I was referring to the implicit suggestion that one should move away from Nvidia, and in a tone that is almost condescending to their product. I explicitly stated that I support AMD for their contributions to open-source regarding this issue, but I dont think its right to condemn a hardware company who chooses to not contribute in open-source endeavors WHEN THEY RELEASE a driver that is fantastic for the product itself. However, one COULD cite their reluctance to provide an official solution to Optimus on Linux, and I would agree that it is very poor they fail to do so. In terms of performance graphically, Nvidia is stellar in the Linux world (read: the best), but if Bumblebee or Nvidia doesnt resolve the Optimus issue, its all for naught.

> **handy said:**
> None of that has anything to do with nVidia's lack of support for the nVidia open-source driver stack.
You could just as well be praising MS for their Office Suite against OpenOffice or LibreOffice.
Well, many people serious in corporate/business environments will hold Office in a much higher regard in terms of performance than LibreOffice; while LibreOffice is fine for me, I can see the equivalent in that Nvidia hardware performs much better on my chosen OS relative to ATI hardware. Also, I dont hold the fact that Office is "better" to many others against Linux- MS could release Office for Linux (just as Nvidia could aid the open source drivers). And while I have MANY problems with Microsoft due to their monopolistic business policies, they have a right to compete in the market as they choose- unlike Windows which people are forced to use from the moment they purchase a computer, Office is USUALLY a choice. Again, one could cite how they use closed document formats instead of open ones pushed by Ooo and LibreOffice, and THAT is a problem I have with MS in regards to Office.

> **handy said:**
> It has never been implied in this entire mega-thread that nVidia has inferior performance to the open-source AMD/ATi driver stack.
I know- I simply reiterated that fact in response to the quote I quoted- Im not trolling or an Nvidia fanboy (I have ATI products too).

> **handy said:**
> I use both brands also, as many of us do. The bottom line here is that over the last couple of years due to AMD's choice to give so much support to the development of the open-source driver stack for their GPUs, we have been able to benefit from a huge increase in the performance & reliability of that stack.
We have for sure, and thats great- I wasnt contesting that in the slightest.

> **handy said:**
> I know that you weren't really making a post to hit the AMD open-source support GSF1200S, but you kind of did anyway. :)
Perhaps, if showing any support to a product not open source is considered "hitting the AMD open-source support." In principle however, I do not see supporting Nvidia on account of their driver support as anti open source- in terms of hardware, Nvidia is competing against ATI, and have a vested interest in hiding components from them as a competitor; in a socialist sense I agree even the drivers should be open (causing progress to be at a much faster pace), but as a realist in a capitalist world, I understand their motivation to keep "trade secrets" for at least a little while. Nvidia sells hardware; their drivers are software in the literal sense, but are so in a fashion that opening them would threaten their ability to compete with an ATI which is backed by AMD. I reiterate that I fully support AMD/ATI's actions, but I dont hate Nvidia in this case.

In short, in a Utopian view, I fully support all software (including drivers) being open, but I must be realistic to the burdens placed on a hardware company trying to have a competitive edge in a capitalist society.

**EDIT** I really think we are going off topic, and I also think we are on the same side in terms of ATI; I just sensed a tone I didnt feel was warranted and sought to address it with perspective :)

---

### Post by GSF1200S on 2011-07-21
> **el_koraco said:**
> Not to mention that AMD has better support for hybrid graphics than Nvidia. The binary drivers suck, but I'm happy to endure that if it means that the open source stack will catch up in a year or two. Imagine buying a machine with an ATI GPU, regular or hybrid, and not have to fiddle with proprietary drivers.

I agree about hybrid graphics...

---

### Post by handy on 2011-07-21
**@GSF1200S:** This is a thread dedicated to the AMD/ATi GPU open-source driver stack. If you come here & wave the nVidia flag, (even if you do have a little white flag waving at the same time) expect to get shot down.

If you like to get shot down, keep coming here & waving the flag, there are plenty of us who will enjoy the target practice... :lolflag:

---

### Post by GSF1200S on 2011-07-21
> **handy said:**
> **@GSF1200S:** This is a thread dedicated to the AMD/ATi GPU open-source driver stack. If you come here & wave the nVidia flag, (even if you do have a little white flag waving at the same time) expect to get shot down.
I find this fact ironic considering I own ATI products, but ok. All ive said is the truth, and if you wish to defame my character as an ad hominem attack to discredit my argument, go right ahead ;)
> **handy said:**
> If you like to get shot down, keep coming here & waving the flag, there are plenty of us who will enjoy the target practice... :lolflag:
All I did was said what I believe to be true. Call me a flag waving lemming if you will..

---

### Post by handy on 2011-07-21
Now you've gone & taken it personal. There is no need to do that. You aren't being personally attacked in anyway shape or form. It is only some of your ideas about something that some others don't agree with. So what? That's life, if we all agreed on everything then we may as well be Lemmings & go over the cliff in our case out of boredom.

(By the way, Lemmings got a bad rap there, they don't actually do that.) :)

---

### Post by GSF1200S on 2011-07-21
> **handy said:**
> Now you've gone & taken it personal. There is no need to do that. You aren't being personally attacked in anyway shape or form. It is only some of your ideas about something that some others don't agree with. So what? That's life, if we all agreed on everything then we may as well be Lemmings & go over the cliff in our case out of boredom.

(By the way, Lemmings got a bad rap there, they don't actually do that.) :)

Take what personal? ;) Even if you were to straight out attack me, I wouldnt really care; obviously we both have opinions we are entitled to have and they differ from one another (though really, I never attacked ATI and you never degraded Nvidia yourself- what the hell are we even arguing for?). Again, I stated my case pertaining to Nvidia, defended when you mentioned me flag waving, and qualified the reasons why I felt it was necessary for me to say what I did. Were both are in the same boat ideologically- we just differ in terms of how we reason a company in a capitalistic society should operate (to survive) without being looked down upon.

Really, the basis of my message was simply that we comprise a very very small portion of Nvidia's business (same with ATI), and we shouldnt be quick to condemn their business practices when they have supported Linux quite well. Notice how Linux users didnt contribute a lot of development to Songbird (according to the devs of Songbird- they could be lying I suppose), and yet Linux users straight up flamed them when they dropped Linux support; I guess im trying to avoid that same attitude with a company who in this case has supported Linux very well. We need all the help we can get with so many things in this world working against the Linux software ecosystem. Most people would not complain if Adobe released Photoshop for Linux, and there is certainly nothing free about that ;)

I didnt get my "feelings" hurt, but I am not going to lie down and be labeled without defending myself- I just reproached when personal statements, such as me being a flag waiver, were levied in my direction.

I used lemmings as term to attach some emotion to my inferred implication, but yeah, they dont really do that..

At least you like XFCE and we dont have to fight in that thread ;)

---

### Post by handy on 2011-07-21
Good.

---

### Post by GSF1200S on 2011-07-21
> **handy said:**
> Good.

Haha.. :)

---

### Post by handy on 2011-08-17
I fairly recently upgraded (on Arch) to the 3.0 kernel, & the associated AMD/ATi git packages.

I'm most impressed, as I picked up ~200fps on the (not a benchmark) glxgears. So that makes roughly 400fps over the last 6 weeks or so for my HD2600 Pro. :)

---

### Post by bcschmerker on 2011-08-17
> **handy said:**
> **@GSF1200S:** This is a thread dedicated to the AMD/ATi GPU open-source driver stack. If you come here & wave the nVidia flag, (even if you do have a little white flag waving at the same time) expect to get shot down.

If you like to get shot down, keep coming here & waving the flag, there are plenty of us who will enjoy the target practice... :lolflag:Nyuk, nyuk, nyuk, nyuk, nyuk!  I'm still awaiting word on a [backport of Kernel 3.0 to Lucid](http://ubuntuforums.org/showthread.php?t=1816419), as improved drivers for the Advance Micro Devices® Radeon HD series at least through the 5000's will improve my current HD 3200's handling of GPU code a fair amount. \\:D/ My hybrid Everex® packs a Gigabyte MA78GM-S2HP mobo (in for an all-VIA® stock mobo using a 1.6 GHz C7-D) with and AMD® Athlon 64® X2 5600+ with 4 GB RAM; the 780G north bridge and Radeon HD 3200 GPU handle things pretty well for an OEM-type rig.  *And*, if it drives the relatively anemic 3200 to good speeds, I can reckon how it would fly an HD 5830, provided that I send an Antec® TPN-750B (which packs 25A capacity on each of four +12VDC busses, plus 180W combined power output for +5VDC and +3.3VDC) in for the Everex'® current 500W Athena® PSU (which has insufficient PCIe auxiliary wattage available). 8-)

Of course, I was *not* expecting nVIDIA® to do likewise for older GeForce® GPU's---my rebuild of an eMachines®/Acer® EL1210 still requires drivers without the kernel to run a planar 8200 and PCIe-expansion 210, as the kernel alone only drives the 8200, leaving the 210 high and dry. :twisted:

---

### Post by Kromgol on 2011-08-17
Does the open-source driver work with more than two monitors? I use three, that's why i'm wondering.

---

### Post by Lucradia on 2011-08-17
glad to see the topic title FINALLY got a spell check. Hated that "comming"

---

### Post by handy on 2011-08-17
> **Lucradia said:**
> glad to see the topic title FINALLY got a spell check. Hated that "comming"

For my pleasure, I added some more m's for you. :)

By the way, I edited that ages ago, so you are falling down on your self appointed job of being a nit picking critic.

---

### Post by handy on 2011-08-23
My (not a benchmark) glxgears speeds keep on creeping up with each upgrade of the git driver stack. :)

---

### Post by JDShu on 2011-08-23
> **handy said:**
> My (not a benchmark) glxgears speeds keep on creeping up with each upgrade of the git driver stack. :)

I've been doing infrequent benchmarks and FWIW, the PTS Urban Terror benchmark improved from 43 fps (default fedora 15) to 47 fps (git snapshot on August 8th) which is something like a 9% gain over the last few months.

---

### Post by handy on 2011-08-23
> **JDShu said:**
> I've been doing infrequent benchmarks and FWIW, the PTS Urban Terror benchmark improved from 43 fps (default fedora 15) to 47 fps (git snapshot on August 8th) which is something like a 9% gain over the last few months.

I should run the PTS again & see what it has to say. I've picked up around 420fps on glxgears in less than 2 months. I don't really play games on this box, though I tried to play Sacred Gold, & have problems due to the 3D demands, so I used to use (motherboard finally died) box2. with an AGP nVidia 7950GT/256, which does/did the job with all settings maxed out.

---

### Post by lpwaqas on 2011-08-28
I had Radeon Mobility HD 3670 in my Dell XPS 1640 I installed FGLRX driver from HardWare > Additional Drivers and it worked like a charm.

I did check it MeerKat.

                description: VGA compatible controller
                product: Radeon Mobility HD 3670
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0

---

### Post by Linuxisfast on 2011-08-29
The biggest issue I see with ATI curently is hardware acceleration with movie players. Currently my 1015B ASUS EeePC can't use h/w acceleration due to this issue, OTOH, its far easier to set nvidia up for h/w acceleration in Ubuntu. The AMD Ontario does represent the best value in netbooks compared to usual Intel offerings. I am sincerely hoping that this issue will be sorted out in near future. I have no desire to run the slow Win7 that my netbook came with, have been a Linux user all my life.

---

### Post by lpwaqas on 2011-09-16
my ati 3670 and 4670 are working just fine :) with propriety drivers activated :) with meerkat.

---

### Post by timuckun on 2011-09-17
11.04 with ATI Radeon HD 5740.

The open source drivers with unity cook the CPU and the fans are on high all the time. The proprietary drivers run much cooler but compiz + the "classic" desktop is unusable.

The proprietary drivers have numerous problems with unity including weird artifacts on the screen. The config applet requires a reboot every time you plug in a monitor or take one away and requires you to run them as root for most cases. Utterly ridiculous in this day and age. When you launch apps the screen flickers and shows lines in both unity and classic with or without compiz.

The open source drivers work well except for cooking the laptop which is terrible for both battery life and longevity.

---

### Post by wolfen69 on 2011-09-17
I stick with Intel video for laptops, and Nvidia for desktops. Much better support, and never had a problem.

---

### Post by bcschmerker on 2011-09-25
> **lpwaqas said:**
> my ati 3670 and 4670 are working just fine :) with propriety drivers activated :) with meerkat.Good show; as of September 2011, 10.10 Maverick's Kernel 2.6.35 is available as a backport to 10.04.3-LTS Lucid.  Due to an anticipated need for 256-bit VRAM (but not necessarily the fastest clocks), I have decided to fish up the recently-discontinued Gigabyte® GV-R485 series (ATi® Radeon HD 4850 family/R770 GPU) on eBay® to see what models can fit one slot (leaving one slot open betwixt the PCI-Express x16, where the card will attach to the system, and the #2 "legacy" PCI 2.0 slot, where a Creative Laboratories® SB0350 audio card resides, to allow airflow to the R485's fan and GPU heat sink), and at what cost range(s).

Although Advance Micro Devices® supports the Radeon HD 6000 Series in Catalyst Control Center (package: fglrx-amdcccle) as of September 2011, the GA-MA78GM-S2HP in my hybrid Everex®, due to BIOS limitations, cannot, so I'm limited to types already supported with X.org open-source drivers anyway.

---

### Post by beew on 2011-10-11
It seems that xorg-edgers no longer works with the ati radeon x1270 card. I have this in a hp netbook, it used to work great with xorg-edgers but at some point it stops working with Natty, Unity (Compiz) refuses to start and I boot into a blank desktop, removing xorg-edgers and it works again but graphics performance is set back by quite a bit. Wonder if that is a bug or if the card is no longer supported.

---

### Post by JDShu on 2011-10-11
I suggest compiling mesa from git for people who want to try the latest  and greatest. It's very easy and not as invasive as PPAs.

---

