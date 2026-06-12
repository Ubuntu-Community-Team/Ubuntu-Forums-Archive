---
title: "[Graphics card] Best driver support: AMD or NVidia?"
date: 2015-07-22
forum: Ubuntu, Linux and OS Chat
---

### Post by pubalapoub on 2015-07-22
Hi all,

I've just spent 2-3 hours browsing several forums to fix an issue (no loss of time since I finally managed to fix it ^^) so I feel a bit lazy now for this new question and I doubt I can find the answer quickly, I hope you will forgive me (don't hesitate to route me to another thread if an existing one answers my question).

I'm running Kubuntu 14.04 and I plan to buy a new graphics card. Among criterion that will help me choose between an AMD or NVidia model is how "good" AMD and NVidia Linux drivers are generally speaking (no matter the card model I will opt for in the end).

I know the focus of these two companies is put on the Windows version of their driver. But when it comes to Linux, which company seems to work harder to produce quality Linux drivers (i.e. taking best advantage of the hardware)?

Thanks in advance for your opinion!

---

### Post by QIII on 2015-07-22
Prepare for fanboy deluge from both sides.

---

### Post by finny388 on 2015-07-22
Indeed QIII

my opinion is that since nvidia has more users and is a bigger company odds are at any given time they will have better support.
i would rather support amd but as I linux user I use intel cpu/nvidia gpu combos b/c of this.

queue the deluge...

---

### Post by efflandt on 2015-07-23
If you are going to get into gaming, Linux Steam seems to work best with Nvidia graphics at this time.

I have heard of various issues with proprietary AMD graphics drivers in Steam. But one suggestion was to install Steam first, then the proprietary AMD drivers. Otherwise in 64-bit Ubuntu it might not automatically end up with some 32-bit libs it needs. And there was a post on the Steam Linux forum that said "AMD Catalyst Linux Driver Performs Wildly Different Based On Program's Name" [http://steamcommunity.com/app/221410/discussions/0/541906989390598709/](http://steamcommunity.com/app/221410/discussions/0/541906989390598709/)

I only had the several missing 32-bit libs issue with Nvidia in 64-bit Ubuntu 13.10 on my laptop before everything was sorted out for hybrid Intel/Nvidia graphics. That was not an issue in 14.04 which uses nvidia-prime instead of bumblebee. And that was never an issue on my desktop PC in 64-bit 12.04 or 14.04.

---

### Post by pubalapoub on 2015-07-24
Thanks for your answers! When I started this thread, I was also fearing a bit a battle of fans, which is really _not_ what I want. Rather real facts, based on personal experiences. Then I can make my own opinion.

So apparently, no _significant_ difference between the 2 brands in terms of hardware support. My limited experience showed that both brands bring their Linux proprietary driver that does the job pretty well (if not perfectly well, there's no ideal world). Which means that I'd probably only have to focus on cards specifications, taking into account my current mother board, power unit, these kind of typical criterion... Good!

@efflandt: I'm running the 64bit edition of Kubuntu (14.04) but I don't intend to use Steam (although I installed it some time ago and could test TF2 successfully - with my current AMD card). Actually I'm  a Minecraft player. My intention is to boost FPS, as I'm now  using the Shaders Mod. I can get decent ones in windowed mode (1280x800) but as soon as I switch to full sized window or full screen (1920x1200), FPS drop under 10, which is simply unplayable. That said, the thread you shared about renaming programs' name makes me realize that I never thought about searching possible ways to improve Minecraft performance, I should obviously start with this ;)

Last point: with today's cards being PCIe 3.0 ones, I was also concerned with limitations my PCIe 2.0 slot would cause, but I found a thread yesterday discussing this very topic (~ 3 years old) and the conclusion was clear at the time: no significant limitation due to a PCIe 2.0 slot, which is very good news if still true nowadays. Said differently, I may loose some performance due to the slot of course, but compared to what I get with my current gfx card, I'll still benefit from a huge increase of performance with a new generation card.

---

### Post by mastablasta on 2015-07-24
AMD drops proprietary driver support faster than NVidia, however on the other hand they do work with OS driver team and often features from proprietary driver are then moved to opensource.  i think strategy is to move it all completely to OS. but who could know.

i went with nVidia for the firts time ever this year and it simply didn't work. it worked well on Windows PC so i know card was good. but i couldn't resolve the Linux issue. nVidia couldn't help me either. eventhough card is supported and others said it worked well. in my case it worked using opensource drivers, but the resolution was horrible on that monitor. after installing nVidia drivers even opensource ones didn't work. anyway all other PC's have old AMD cards and they work well. so hard to say. it seems to also really depend on other components in desktop PC as well.

---

### Post by pubalapoub on 2015-07-24
> **mastablasta said:**
> i went with nVidia for the firts time ever this year and it simply didn't work. it worked well on Windows PC so i know card was good. but i couldn't resolve the Linux issue. nVidia couldn't help me either. eventhough card is supported and others said it worked well. in my case it worked using opensource drivers, but the resolution was horrible on that monitor. after installing nVidia drivers even opensource ones didn't work.
Ouch... Could you tell me what your Ubuntu version is and the exact model of that problematic NVidia card please?

From what I read, switching from an AMD card to an NVidia one (or vice-versa) should be done like this:
- uninstall the proprietary driver (which I understand as "revert back to the opensource driver" and then execute "sudo apt-get remove [package(s)]").
- shut down the PC and install the new card.
Had you proceeded that way (provided you had an AMD card installed before)?

---

### Post by sgian on 2015-07-24
What I would do is research whether the specific card you are looking at is supported, regardless of brand.

---

### Post by QIII on 2015-07-24
^^This

---

### Post by pubalapoub on 2015-07-24
> **sgian said:**
> What I would do is research whether the specific card you are looking at is supported, regardless of brand.
Not that simple unfortunately... Beyond theoretical card support, it looks like recent NVidia drivers cause recurrent issues with Ubuntu (see [https://devtalk.nvidia.com/default/topic/858608/linux/driver-for-ubuntu-cannot-start-x-window/](https://devtalk.nvidia.com/default/topic/858608/linux/driver-for-ubuntu-cannot-start-x-window/) for example - that's not the only one I passed by).

As a matter of fact, I have an old spare GeForce 8800 GT card (512 MB), also announced as supported by NVidia driver 340.76. It's indeed supported, but the tests I've conducted today with Minecraft + Shaders Mod revealed terribly poor performance - at least caused by the small amount of memory that equips this old card. While I manage to get 20~25 fps with my Radeon HD 6770 (1 GB), fps drop to 2 (yes, two) with my GeForce 8800 GT, using the exact same Minecraft installation / shaders / saved game.

You know what? I won't spend something like 200 &#8364; on a recent NVidia card, that is *supposed* to provide good performance  with Minecraft, but that could also lead to issues with X.org.

Since I've been able to get acceptable performance from my old Radeon HD 6770, I'm more or less forced to continue with AMD, it will be less risky for me. And despite of Catalyst Center not offering as much options as NVidia's "X Server Settings" utility, the goal I'm pursuing seems truly reachable with an AMD card, for roughly the same price. I just regret the higher power consumption of AMD cards, but as I said earlier, there's no ideal world :)

Thanks to all of you who took the time to answer my questions!

---

### Post by pubalapoub on 2015-07-25
VICTORY!!!

(sorry, I shouldn't shout like this)

Ok. My final choice was the AMD R7 370 (4GB) by Sapphire - actually I had no choice regarding the manufacturer, it was the only "acceptable" one available locally today.

Conclusion: while I was getting ~ 23 fps previously in window mode (1280x800), I now get between 20 and 30 fps... in full screen mode (1920x1200), having raised all graphical details I possibly could :) As well as the render distance (from 8 to 12 for those familiar with Minecraft).

I can even switch from Chocapic's "Medium" shaders to the "Extreme" version (bypassing "High" and "Ultra"), losing 1/3 fps, but still playable at 20 fps - still in full screen.

For Minecraft lovers out there, here is my config, if it can help you estimate if  upgrading one of your hardware components is worthwhile or not:

Gigabyte GA-870A-USB3 rev. 3.0 AM3 motherboard
8 GB RAM (DDR3)
500W power supply unit
1 TB HDD (Western Digital Caviar)
Sapphire Nitro R7 370 4GB (UEFI) graphics card

OS: Kubuntu 14.04 64bit

As to Minecraft (1.7.10 - as there is no Forge for 1.8.7 yet):
Launcher: MultiMC 5 v0.4.7 for Linux 64bit
OptiFine 1.7.10 HD U C1
Forge 10.13.4.1448
Shaders Mod 2.3.28

All that said, and to come back to my initial question ^^, I read many performance tests on [https://www.phoronix.com/](https://www.phoronix.com/) yesterday, read comments, followed links... The conclusions seem to be that:
- the NVidia Linux driver outperforms the AMD one when it comes to OpenGL support.
- the AMD Linux driver does better than the NVidia one when it comes to OpenCL support.

OpenGL was what interested me as Minecraft is using it. But issues faced by several people with the NVidia driver on Ubuntu discouraged me to move to NVidia. I think I made the right choice to meet my personal needs.

---

### Post by Yellow Pasque on 2015-07-25
When I see people reporting problems with the nvidia driver, it often comes down to 1 of 2 things:
1. Trying to download the driver directly from nvidia and build it oneself, i.e. the "Windows" mentality
2. Using a very recent Nvidia GPU on a version of Ubuntu that doesn't yet have a new enough driver (like trying to use a GTX960 on Ubuntu 14.04)

#1 is never a good idea, unless you're experienced with building software on Linux and know how to make packages. [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
The solution to #2 is to use the most recent version of Ubuntu or find a good PPA, like [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

There are also a lot of users who struggle with hybrid Intel/Nvidia laptops (aka "Optimus"), though that doesn't apply to desktop cards like those discussed in this thread.

>  While I manage to get 20~25 fps with my Radeon HD 6770 (1 GB), fps drop to 2 (yes, two) with my GeForce 8800 GT,
Apples and oranges. The 8800GT is equivalent to something older like a RadeonHD 3850 or 2900. Also, Minecraft can be bottlenecked by amount of video RAM (probably much moreso with fancy shader mods), so comparing two cards with different RAM sizes and trying to draw a conclusion about what brand card you're going to buy next seems misguided/pointless.

---

### Post by pubalapoub on 2015-07-26
Thanks for your answer Temüjin.
> **Temüjin said:**
> When I see people reporting problems with the nvidia driver, it often comes down to 1 of 2 things:
1. Trying to download the driver directly from nvidia and build it oneself, i.e. the "Windows" mentality
I wasn't ready to spend a lot of time installing the very latest NV driver manually - with uncertain results.
> **Temüjin said:**
>  2. Using a very recent Nvidia GPU on a version of Ubuntu that doesn't yet have a new enough driver (like trying to use a GTX960 on Ubuntu 14.04)
Perfect example you chose, as I'm running Ubuntu 14.04 (with no intention to move to a more recent release, otherwise I'd loose the benefits of a stable LTS release) and I was precisely intending to purchase a GTX 960 if I had gone for an NV one :)
> **Temüjin said:**
> The solution to #2 is to use the most recent version of Ubuntu or find a good PPA, like [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia ]("https://launchpad.net/~mamarley/+archive/ubuntu/nvidia")
Does a compatibility matrix exist for Ubuntu? Although I spent hours and hours browsing the Net for different kind of information, I don't remember finding a simple table telling which NV cards are supported for a given Ubuntu release. I'd be surprised such matrix doesn't exist, but the fact is I didn't find such (or when I did, information was really not up-to-date, listed cards were so old...).
> **Temüjin said:**
> Apples and oranges. The 8800GT is equivalent to something older like a RadeonHD 3850 or 2900. Also, Minecraft can be bottlenecked by amount of video RAM (probably much moreso with fancy shader mods), so comparing two cards with different RAM sizes and trying to draw a conclusion about what brand card you're going to buy next seems misguided/pointless.
Sorry if the way I presented this information was misleading. My intention was not to compare both cards in terms of performance but to check if/how well my old 8800 GT was supported by Ubuntu 14.04 with the recommended NV driver (331.113). Providing info about fps was just informational, not a comparison criteria. The terrible fps I had experienced with MC + shaders was undoubtedly caused by the lack of memory of this card (the NV "X Server  Settings" utility was clearly showing that the video RAM was used at  100% within a few seconds).

Another info relating to 8800 GT is that the Ubuntu logo (blue and glowing) that normally displays at boot was replaced with a dirty _text_ ("Ubuntu 14.04") as long as I was using any of the NV drivers (331, 304, 173), while - if I remember well - it was displaying normally with the open source driver. I don't know the reason for this.

PS: was it your intention to share the same URL twice?... (I guess not as the one for solution #1 doesn't seem relevant)

---

### Post by pubalapoub on 2015-07-26
Ok guys, I have a few additional remarks/topics to discuss, still relating to the AMD driver, so I hope it's still fine discussing them in this thread.


[LIST]
[*]**TOPIC 1** 
[/LIST]
I experienced a strange behaviour with the X.org process (both with my HD 6770 and R7 370 cards). When first installing the fglrx driver and playing Minecraft for a while (while not sure MC has anything to do with this), I noticed after a long time playing that X.org had allocated **a lot** of memory over the time. It could end up reaching 1.5 GB for example. Taking a closer look at this surprisingly high memory consumption (using KSysGuard), I noticed that allocated memory was increasing constantly, even when not playing, which made me think of a possible memory leak issue.

The thing is: reinstalling the AMD open source driver, then reinstalling the fglrx driver again apparently fixed the issue! Now X.org stays stable, at a decent memory usage (~ 32 MB). May I play MC or not, X.org stays nicely stable. **[COLOR=#ff0000]EDIT:[/COLOR]** the reason for this is that when changing from one driver to another, KDE resets option "Composite display mode" to value "XRender" (read 2nd "EDIT" below).

Anyone having faced the same issue? *And is there a known explanation to it?*

**[COLOR=#ff0000]EDIT:[/COLOR]**I finally understood that this memory issue is present when any of the "[COLOR=#ff0000]OpenGL x.x[/COLOR]" options is selected in **KDE Desktop effects**' "Advanced Options" tab (see the "Composite display mode" drop-down list). The issue is NOT present when "[COLOR=#008000]XRender[/COLOR]" option is selected. One can find several references to similar bugs on [https://bugs.launchpad.net/ubuntu/]("https://bugs.launchpad.net/ubuntu/?field.searchtext=xorg+memory+leak&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=").


[LIST]
[*]**TOPIC 2** 
[/LIST]
I must admit I still don't clearly understand the difference between the fglrx and fglrx-updates sources for the AMD proprietary driver... :confused:

I would assume fglrx-updates would possibly bring newer versions of the driver over the time, while fglrx would stick to the version that was available at the time Ubuntu 14.04 was officially released. Is my understanding correct?

And generally speaking, is there a recommendation regarding which source should be used? Considering I've managed to fix again the "memory leak" issue I mentioned in TOPIC 1 (sorry if this is not truly a memory leak), I plan to stick to the fglrx version of the driver. However, your feedbacks may make me change my mind :)


[LIST]
[*]**TOPIC 3** 
[/LIST]
I'm also wondering what the **amdnotifyui** tool - which gets installed along with the fglrx driver - was for? I searched the Net but couldn't find any explanation (note that I'm not googling but duckduckgoing ^^), sadly not even on AMD's Web site. This tool apparently has no man pages associated with it (AMD to blame here) nor a --help parameter.


Thanks again for your opinions.

---

