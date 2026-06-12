---
title: "How low can you go? Linux with beginner interface in 256Mb"
date: 2011-06-28
forum: The Cafe
---

### Post by keithpeter on 2011-06-28
Hello All

I know about [http://ubuntuforums.org/showthread.php?t=478237](http://ubuntuforums.org/showthread.php?t=478237)

Suppose someone had a P3 with 256Mb of ram. Suppose it was a desktop PC or a laptop being used as a desktop so that wifi wasn't so important and power saving didn't matter so much. Suppose there is a wired Internet connection.

The use case is Web browsing, some light word-processing and printing, and a little use of a usb connectible camera and music player.

Has anyone come across a distro that will 'just work' with these specs and allow a reasonable performance? That could be used by someone who is not a computer ace and who has used XP at work?

Has anyone cracked flash (my standard test Youtube video is [http://www.youtube.com/watch?v=c08i_9gumJs)?](http://www.youtube.com/watch?v=c08i_9gumJs)?)

I personally would be installing minimal iso with IceWM, thunar, feh and abiword/gnumeric/cups/chrome and then restricted-extras. I'd be trying to avoid network manager.

Have I just reinvented Lubuntu?

---

### Post by NightwishFan on 2011-06-28
Try Anti-x
> antiX is a fast, lightweight and easy to install linux live CD distribution based on Debian Testing and MEPIS for Intel-AMD x86 compatible systems. antiX offers users the "Magic of Mepis" in an environment suitable for old computers. So don't throw away that old computer yet! The goal of antiX is to provide a light, but fully functional and flexible free operating system for both newcomers and experienced users of Linux. It should run on most computers, ranging from 64MB old PII 266 systems with pre-configured 128MB swap to the latest powerful boxes. 128MB RAM is recommended minimum for antiX. The installer needs minimum 2.2GB hard disk size.

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by keithpeter on 2011-06-28
> **NightwishFan said:**
> Try Anti-x


[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

Hello NightwishFan

Yup, that was my first idea. Then I remembered the upgrade process complete with mysterious 'accept default (N or Y) dialogs, and picking the wrong alternative and ending up with a box that booted to a command line...

What I'm getting at here is that good performance on low hardware is achievable if you have some skills, but many people in the economic position of having low end hardware don't have that much in the way of skills.

AM I making sense? Have I just re-invented Lubuntu and should I just shut up and put Lubuntu on a spare partition and find some bugs?

---

### Post by Dustin2128 on 2011-06-28
256MB? Ha! I laugh at thee! I can have a running GUI system on a system with 64Mb. Swaps a good bit and it's horrible for web browsing, but it can do the basics- email, IM, IRC, programming. Custom compilation of gentoo. It's actually great with twm or just the console.

---

### Post by keithpeter on 2011-06-28
> **Dustin2128 said:**
> It's actually great with twm or just the console.

Hello Dustin2128

And I laugh with you Sir. 

If it was *me* that had to cope with really low end hardware, given a reliable wired internet connection, I'd be looking at something like Arch. 

But what about 'ordinary' folk whose main use case is web surfing and then a bit of light word processing and maybe getting photos off a digital camera and putting mp3s on a phone or player (assume they identify as a mass storage device for now)? 

And low skills? They just want access not geekery?

---

### Post by Dustin2128 on 2011-06-28
> **keithpeter said:**
> Hello Dustin2128

And I laugh with you Sir. 

If it was *me* that had to cope with really low end hardware, given a reliable wired internet connection, I'd be looking at something like Arch. 

But what about 'ordinary' folk whose main use case is web surfing and then a bit of light word processing and maybe getting photos off a digital camera and putting mp3s on a phone or player (assume they identify as a mass storage device for now)? 

And low skills? They just want access not geekery?
I use arch on my higher-end desktop- wouldn't guess it scales down to hardware from the pentium pro era too well, but I haven't tried. IMO though, all most people need is a P4 with 1024MB RAM and xfce. Banshee can sync to ipods and it's not the bloated mess itunes is, chromium and later versions of firefox are pretty light, etc. I'm actually looking for some 386/486 era hardware right now to see what exactly I could do with it.

---

### Post by keithpeter on 2011-06-28
> **Dustin2128 said:**
>  I'm actually looking for some 386/486 era hardware right now to see what exactly I could do with it.


Hello Dustin2128

I can remember seeing RedHat on a 486 many years ago... it ran slowly on a GUI but ran a small intranet server well and reliably for no money, which we thought was amazing at the time. Your quest is obviously a hobby or challenge for you!

My target is a functional system for non-geeks that could save old hardware (say P3/500MHz upwards with 256Mb RAM) from the scrap heap. I think I'll be trying some of the distributions mentioned already...

Cheers

---

### Post by cchhrriiss121212 on 2011-06-28
Try crunchbang, it will do all you need out of the box, uses less than 100MB RAM and is very reliable. 

Not sure about flash performance on a P3 but you could always make use of flash video replacer:
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

Nice video up there BTW.

---

### Post by Dustin2128 on 2011-06-28
> **keithpeter said:**
> Hello Dustin2128

I can remember seeing RedHat on a 486 many years ago... it ran slowly on a GUI but ran a small intranet server well and reliably for no money, which we thought was amazing at the time. Your quest is obviously a hobby or challenge for you!

My target is a functional system for non-geeks that could save old hardware (say P3/500MHz upwards with 256Mb RAM) from the scrap heap. I think I'll be trying some of the distributions mentioned already...

Cheers
SliTaz is a great low resource distribution. Really though, throwing away any old computers is waste, no questions about it. I'd say the line for something becoming unsuitable for day to day use by the majority people is somewhere around a pentium 2.

---

### Post by NightwishFan on 2011-06-28
Puppy Linux as well:
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by keithpeter on 2011-06-28
Hello All

Crunchbang is ace but imagine you know little about computers. I'll certainly look at flash replacer.

Slitaz was the last time I used it ace on a live CD but I had problems with a hard drive install. I'll look again though.

Arvo Part's music keeps me sane... You can learn to play Fur Alina in half an hour, but you can play it differently each week for five years...

---

### Post by cchhrriiss121212 on 2011-06-28
I think crunchbang would be fine for any non-savvy computer user. I mean the simpler something is, the easier it will be to understand, and openbox is beautifully simple. No complicated displays or widgets or update managers or pop ups, just a single right click menu and a simple task bar. What is there to go wrong?

Obviously you will have to set up the menu and such so that it covers all the user's wants, maybe change the theme to something less monochrome. But once it is all set up, you should be able to leave the user to their own devices.

---

### Post by snowpine on 2011-06-28
256mb is plenty; I'm typing this from my 600mhz Pentium 3, used to have 256mb but I recently upgraded to 384, hooray! :)

It is currently running CrunchBang but I've also had excellent luck with AntiX and SliTaz. The first distro I ever tried on it was Ubuntu 7.10 (using the Alternate CD), that worked OK but then I migrated to Xubuntu 7.10 and then Fluxbuntu 7.10, which is the root of my interest in "lightweight" distros.

The important thing to remember is that Flash is not "open source" software. Flash has its own system requirements, and there is nothing any distro designer can do to "improve" Flash since it is a proprietary, closed source app. You can read the Flash hardware requirements here:

[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

When you are comparing open-source software, however, the amount of thought and effort that goes into today's "lightweight" distros is amazing! I've seen a huge improvement across the board just in the last 3 years (anyone who used to use Fluxbuntu will know what I'm talking about). It used to be that going "lightweight" meant giving up a lot of user-friendliness, but I honestly don't think that's the case any more (in fact recently I've been hearing more complaints about the "heavy" desktop environments).

---

### Post by Zerocool Djx on 2011-06-28
prolly the only thing that work with any amount of speed on that level in linux terms would be an early version of slackware. Lubuntu might work, but unless you need a word processor I wouldn't plan on it doing much more. As far as internet connection goes it might be able to process text pages, but something with flash, forget it. one other thing to consider with older computers is the network card speeds, they just sucked back then compared to today's standards.

---

### Post by keithpeter on 2011-06-28
Hello cchhrriiss121212 and snowpine

OK, I was trying to be clever and reply to this forum from the SlitaZ live cd, but Midori crashed and I lost the writing. It was *fast* though on this AMD / nvidia box with the vesa drivers.

How do you download crunchbang without using a torrent these days? IE a direct download?

> **Zerocool Djx said:**
> prolly the only thing that work with any amount of speed on that level in linux terms would be an early version of slackware.

Thanks very much Zerocool Djx but the 'rules' I have set here are currect kernel and security updates available for the packages. I understand where you are coming from here though.

---

### Post by snowpine on 2011-06-28
Yeah, Midori's terrible (IMHO) but you can easily install Firefox in SliTaz if you like. I think they left it out to keep the ISO around their historical 30mb mark...

---

### Post by Zerocool Djx on 2011-06-28
> **keithpeter said:**
> Hello cchhrriiss121212 and snowpine

Thanks very much Zerocool Djx but the 'rules' I have set here are currect kernel and security updates available for the packages. I understand where you are coming from here though.

The biggest problem is the GUI interface and the power to get it moving with the current Kernel. Just having that open would clean most, if not all, your 256MB of ram out, even more so if it's shared memory. Hell I remember when I had a 286 computer with 2-4MB of ram, NOT GB, MB. I ran Dos on it. Then when I got a 386 and 486 I had windows 3.1. If you want performance for something that old you got to think what was going on back then. The internet isn't exactly optimized for low res graphics these days. Hell, one PHP page on today's standards would prolly make that processor melt, lol. You want performance. Go load DOS on it and play hours of the original DOOM! That was fun and you could play that on 16-32mb of ram. I barely got a 800Mhz 634Mb laptop working this past weekend. The processor in that could barily hold the gui and flash? lol, forget it. 

Anyway, Performance is relative to what you want with what you got. It will perform very superior as a paper weight! :)

---

### Post by CraigPaleo on 2011-06-28
How about [Bodhi Linux]("http://www.bodhilinux.com/")? 

> 
System Requirements:

    300mhz i386 Processor
    128megs of RAM
    1.5g HD space

Yes we are sure. Because of the use of Enlightenment and the cut down Ubuntu base we can get you up and running on very low spec boxes. We have also taken the time to ensure when you boot you can let the system know what type of machine you are running. This is done via Enlightenment Profiles, each profile can be customized to use a variety of devices such as Tablets, Laptops and Desktops.

---

### Post by swiftlinuxcreator on 2011-06-28
I am the founder and lead developer of Swift Linux, the first distro based on antiX Linux.  Unlike Puppy Linux, antiX Linux and Swift Linux are fully compatible with the Debian repository of over 30,000 packages.

I consider antiX Linux to be the Ubuntu of lightweight distros and Swift Linux to be the Mint of lightweight distros.  I'm surprised antiX Linux is so obscure given that it's been around for several years.  I'll be doing my part to promote antiX Linux by promoting Swift Linux, and I'm hoping there will be additional antiX Linux derivatives.

The Linux distro market is top-heavy.  The top 10 distros on Distrowatch consist of 7 heavyweight distros, Debian, Arch, and Puppy.  Of these 10, only Puppy Linux is lightweight AND user-friendly.  I think the end of support for Windows XP represents the biggest opportunity for Linux since the introduction of Windows Vista.

---

### Post by Dustin2128 on 2011-06-28
> **swiftlinuxcreator said:**
>  I think the end of support for Windows XP represents the biggest opportunity for Linux since the introduction of Windows Vista.
I disagree, most people are "upgrading" to vista/7 through hardware upgrades. But there's a thread for that.

---

### Post by Lucradia on 2011-06-28
My CPU can't even handle LXDE very well:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
stepping	: 10
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
bogomips	: 3332.78
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
stepping	: 10
cpu MHz		: 1667.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
bogomips	: 3332.83
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

```

And memory:
```
MemTotal:        1016636 kB
MemFree:          270020 kB
Buffers:           37200 kB
Cached:           240572 kB
SwapCached:            0 kB
Active:           468624 kB
Inactive:         218388 kB
Active(anon):     413008 kB
Inactive(anon):    24488 kB
Active(file):      55616 kB
Inactive(file):   193900 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        137736 kB
HighFree:           1836 kB
LowTotal:         878900 kB
LowFree:          268184 kB
SwapTotal:       2064380 kB
SwapFree:        2064380 kB
Dirty:                32 kB
Writeback:             0 kB
AnonPages:        409164 kB
Mapped:            67400 kB
Shmem:             28268 kB
Slab:              35200 kB
SReclaimable:      11504 kB
SUnreclaim:        23696 kB
KernelStack:        1912 kB
PageTables:         3712 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2572696 kB
Committed_AS:    1024564 kB
VmallocTotal:     122880 kB
VmallocUsed:       21940 kB
VmallocChunk:      86396 kB
HardwareCorrupted:     0 kB
AnonHugePages:    184320 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       20472 kB
DirectMap4M:      880640 kB

```

ASUS 1015PE (BestBuy Exclusive) Please note, it has no second core/thread, the 1 processor is non-existant, and the processor only has one core, no threads.

---

### Post by Dustin2128 on 2011-06-28
> **Lucradia said:**
> My CPU can't even handle LXDE very well:
ASUS 1015PE (BestBuy Exclusive) Please note, it has no second core/thread, the 1 processor is non-existant, and the processor only has one core, no threads.
Maybe intel found a way for hyperthreading to compensate for not having a CPU at all.... ;). Actually, it should run great on a system with those specs- lxde runs snappily on a pentium 3 with a third that clock rate and ram size.

---

### Post by Lucradia on 2011-06-29
> **Dustin2128 said:**
> Maybe intel found a way for hyperthreading to compensate for not having a CPU at all.... ;). Actually, it should run great on a system with those specs- lxde runs snappily on a pentium 3 with a third that clock rate and ram size.

Firefox doesn't work very well, and dragging windows is pretty horrible sometimes, waiting for it to update the screen now and then. (Rarely ever drag anyway.)

As for your assumption on HT. Linux can view cores+threads as cores. It's a downfall of Intel.

---

### Post by keithpeter on 2011-06-29
> **swiftlinuxcreator said:**
> I am the founder and lead developer of Swift Linux, the first distro based on antiX Linux. 

Hello swiftlinuxcreator

I shall go and have a look. Always had problems when updating AntiX, so I'll see if I get those 'accept new configuration file' type messages with your version.

Hello CraigPaleo

Bodhi is great, but Enlightenment was just playing up on my test hardware (an Asus netbook oddly enough) and kept filling the display with crash error type windows. I had problems with wpa2 encrypted wifi as well, but wifi is NOT in my 'use case' for this thread. I'll see if there is an update.

Hello Lucradia

I use an atom based netbook most days with Xubuntu and it works ok, there is some tearing when dragging Firefox windows over OpenOffice. XFCE has a setting to use wireframe windows, and on a 1024 by 600 screen I tend to maximise windows and use virtual desktops for different apps.

Everyone

I think what I'm trying to find is something as good as ubuntu at hardware detection but with much lighter applications and memory footprint. I think I may just be reinventing Lubuntu there....

---

### Post by nothingspecial on 2011-06-29
> **Dustin2128 said:**
> 256MB? Ha! I laugh at thee! I can have a running GUI system on a system with 64Mb.

I await kmandla's appearance to laugh at thee all.

---

### Post by keithpeter on 2011-06-29
> **nothingspecial said:**
> I await kmandla's appearance to laugh at thee all.

Alas, kmandla appears to be having a busy time at work!

Certainly, a cli only installation with mocp and links and vi would probably increase my focus...

---

### Post by snowpine on 2011-06-29
> **keithpeter said:**
> Everyone

I think what I'm trying to find is something as good as ubuntu at hardware detection...

Just my opinion...

If you say "this distro has good hardware detection" what you're actually saying is that it includes dozens or hundreds of mb's of drivers for hardware you don't even have. 

Since "hardware detection" is typically a one-time thing, the "lightweight" way to do it is to download and install only the hardware support that you actually need for *your* hardware. :)

So when people say things like "Arch/Debian/SliTaz/etc. has poor hardware detection" in fact I'd argue that's a design decision and not a flaw.

I hope that comes off as conversational and not argumentative, just sharing my 2 cents. ;)

> **keithpeter said:**
> ...but with much lighter applications and memory footprint. I think I may just be reinventing Lubuntu there....

I agree with you here; I think the typical user on typical hardware can get great results sticking with their current favorite distro and simply installing a lightweight windows manager and some alternative lightweight applications. As an absurd (but true!) example, a lot of people use Gnome System Monitor to figure out what's cycling the CPU or clogging their RAM; well guess what, System Monitor itself is a fairly "heavy" application and can make the system even more sluggish! If you learn how to read top (or htop, it's a little prettier) you can save yourself that overhead.

Not that I would ever criticize anyone for trying a new distro, of course... I do it at least once a month. ;)

---

### Post by koleoptero on 2011-06-29
I installed crunchbang xfce on a p3 @ 733mhz laptop with 256mbytes of ram, and gave it to a friend that is completely new to linux and a novice user in any case, and he has been using it for a year with absolutely 0 complaints or questions. Another friend of mine that has some experience with linux and uses it 100% of the time has been running regular ubuntu (without compiz) on a p3 @ 1ghz with 386mbyte ram till 10.10 came out when he switched to debian+xfce.

P3 computers might not be able to play hd video or flash games but they can operate modern lighweight environments just fine.

---

### Post by snowpine on 2011-06-29
> **koleoptero said:**
> P3 computers might not be able to play hd video or flash games but they can operate modern lighweight environments just fine.

+1

I'm typing this from my 600mhz pentium 3 with 384mb ram running CrunchBang Statler with the Ratpoison WM. It is my "sunny day work outside" laptop. Sure, it is a little slower than my desktop, but it runs Chromium browser and LibreOffice just fine. And if it rains or a bird poops on it, I won't be that sad, because it's 10 years old, has a busted keyboard, and I got it for free. :)

ps This old thing actually plays streaming video quite well--I often use it to watch baseball games using mlbviewer and mplayer--but chokes when using the proprietary Adobe Flash player. Fullscreen Youtube is a slideshow! Get it together Adobe!!!

---

### Post by keithpeter on 2011-07-01
Hello All

Just surfaced from three 12 hour days of work, the joys of adult/community teaching at the end of an academic year.

> **snowpine said:**
> +1

I'm typing this from my 600mhz pentium 3 with 384mb ram running CrunchBang Statler with the Ratpoison WM.

Good for you

How do I get #! Statler these days? I don't do torrents. Is there an http or ftp download server?

> **koleoptero said:**
> I installed crunchbang xfce on a p3 @ 733mhz laptop with 256mbytes of ram, and gave it to a friend that is completely new to linux and a novice user in any case, and he has been using it for a year with absolutely 0 complaints or questions. 

Great stuff. How does he find the updates? I used to get those 'accept default' error messages and I never knew which one to choose, then I got errors from apt-get, and when I accepted the suggested solution, it used to uninstall most of the operating system.

> **snowpine said:**
> Just my opinion...

If you say "this distro has good hardware detection" what you're actually saying is that it includes dozens or hundreds of mb's of drivers for hardware you don't even have. 

Since "hardware detection" is typically a one-time thing, the "lightweight" way to do it is to download and install only the hardware support that you actually need for *your* hardware. :)

So when people say things like "Arch/Debian/SliTaz/etc. has poor hardware detection" in fact I'd argue that's a design decision and not a flaw.

I think this is the central issue. How about a low weight distro but with shed loads of drivers so that it will work on most hardware that is compatible with current secure and up-datable kernels? Like a CD-ROM that you shove in the drive and you know it will work?

Have I reinvented Lubuntu for the fourth time on this thread?

PS: this is being typed on a Samsung NC10 netbook bought for seventy quid off the well known auction site. Works fine with Xubuntu.

---

### Post by snowpine on 2011-07-01
> **keithpeter said:**
> I think this is the central issue. How about a low weight distro but with shed loads of drivers so that it will work on most hardware that is compatible with current secure and up-datable kernels? Like a CD-ROM that you shove in the drive and you know it will work?

I'd wager the list is longer than you think and includes Lubuntu, Xubuntu, CrunchBang, Antix, Knoppix, Puppy, and dozens more! :)

---

### Post by Dustin2128 on 2011-07-01
> **Lucradia said:**
> Firefox doesn't work very well, and dragging windows is pretty horrible sometimes, waiting for it to update the screen now and then. (Rarely ever drag anyway.)

As for your assumption on HT. Linux can view cores+threads as cores. It's a downfall of Intel.
Somewhat lame joke criticizing hyperthreading, move along. Give some lighter distro a shot, crunchbang or SliTaz.

---

### Post by keithpeter on 2011-07-02
> **snowpine said:**
> I'd wager the list is longer than you think and includes Lubuntu, Xubuntu, CrunchBang, Antix, Knoppix, Puppy, and dozens more! :)

Hello Snowpine

How do we download CrunchBang without using torrent?

---

### Post by koleoptero on 2011-07-02
> **keithpeter said:**
> Great stuff. How does he find the updates? I used to get those 'accept default' error messages and I never knew which one to choose, then I got errors from apt-get, and when I accepted the suggested solution, it used to uninstall most of the operating system.

He doesn't. Who needs updates if it works? ;)

---

### Post by keithpeter on 2011-07-02
> **koleoptero said:**
> He doesn't. Who needs updates if it works? ;)

Hello koleoptero

I'll have to think about that one. The same logic could be applied to XP :twisted:

---

### Post by weasel fierce on 2011-07-02
How much fuss is installing proprietary Nvidia drivers under swiftlinux ?

Is swiftlinux completely debian compatible?

---

### Post by snowpine on 2011-07-02
> **keithpeter said:**
> Hello Snowpine

How do we download CrunchBang without using torrent?

I don't know the answer, I'm sorry. I used the torrent.

---

### Post by cchhrriiss121212 on 2011-07-03
> **keithpeter said:**
> 
How do we download CrunchBang without using torrent?
Crunchbang has moved to torrent only a few months ago. I could post you one if you like?

---

### Post by CraigPaleo on 2011-07-03
I don't know too much about Crunchbang but there are direct links here: [http://distrowatch.com/?newsid=06504](http://distrowatch.com/?newsid=06504)

It's from February but better than nothing, I suppose.

---

### Post by keithpeter on 2011-07-03
> **cchhrriiss121212 said:**
> Crunchbang has moved to torrent only a few months ago. I could post you one if you like?

Hello cchhrriiss121212

Thanks very much for that kind offer, but I'm suprised that CrunchBang can't get a little bit of 'mirror' space somewhere like Kent (mirrors.org) or HEAnet as its all over the Web and very well linked!

I've put AntiX on a spare partition and will 'live' in that for the summer period (albeit with LibreOffice as drawings and formulas are essential for me). 

In the autumn I'll find a way of getting a current copy of #! and try that as well. Perhaps popping an iso into a dropbox public folder for an hour or so one day by arrangement would be less onerous than posting a physical cd-rom?

My desktop PC hardware is a bit over the top for low footprint distros (its only four years old) but at least I can check out the interfaces.

---

### Post by keithpeter on 2011-07-03
> **weasel fierce said:**
> How much fuss is installing proprietary Nvidia drivers under swiftlinux ?

Is swiftlinux completely debian compatible?

I've just installed AntiX, which is swiftlinux's 'parent', on a spare partition and installing the NVIDIA drivers took a few minutes using the sgfxi script. 

My AntiX sources.list has entries for Mepis, Debian, debian-multimedia, and Liquorix for the kernel that AntiX runs. 

The Swiftlinux publisher posts here, so perhaps a personal message or contact via the web site?

Cheers

---

### Post by anticapitalista on 2011-07-03
The MEPIS repos should be commented out. (that is if you are using latest antiX-M11).

In fact only the Debian repos need/should be enabled. The liquorix one is if you want a newer kernel. The multimedia if you need to play commercial dvds and install libdvdcss.

---

### Post by keithpeter on 2011-07-03
> **anticapitalista said:**
> The MEPIS repos should be commented out. (that is if you are using latest antiX-M11).

In fact only the Debian repos need/should be enabled. The liquorix one is if you want a newer kernel. The multimedia if you need to play commercial dvds and install libdvdcss.

Hello anticapitalista

Below is /etc/apt/sources.list after installing nvidia drivers. The debian-multimedia and mepis repositories are commented out and so I guess its only debian-testing and liquorix that are active.

Should I be commenting out the 'testing' and uncommenting the 'squeeze' lines if I want a quiet life? Should I also be commenting out the liquorix lines? uname -a gives Linux quiet 2.6.36-1-mepis-smp #1 SMP Thu Mar 31 17:07:18 CDT 2011 i686 GNU/Linux


If this is all in the AntiX FAQ just reply with RTFM!

```
# See sources.list(5) for more information

# Note:If you want maximum stability, only use the stable/squeeze repos.

# MEPIS 11 series. 
# Uncomment all MEPIS repos shown here to install headers and linux-kbuild
# from MEPIS repo for latest MEPIS kernel (2.6.36). Then comment back once installed.
#deb ftp://ftp.mepis.com/mepis/ mepis-11.0 main
#deb http://fr1.mepis-deb.org/mepis/ mepis-11.0 main
#deb http://www.mirrorservice.org/sites/ftp.mepis.org/mepis/ mepis-11.0 main 

# Mepis Community Main, Restricted, and Test Repos
# Use these repos ONLY if you enable Debian STABLE (squeeze) repo.
#deb http://main.mepis-deb.org/mepiscr/repo/ mepis11cr main non-free
#deb http://restricted.mepis-deb.org/mepiscr/repo/ mepis11cr restricted restricted-non-free
#deb http://main.mepis-deb.org/mepiscr/testrepo/ mepis11cr test
#deb http://restricted.mepis-deb.org/mepiscr/testrepo/ mepis11cr test-restricted

# Debian Testing. Default for antiX.
# Testing enabled for 'rolling' release.
deb http://ftp.uk.debian.org/debian/ testing main contrib non-free
deb http://security.debian.org/ testing/updates main contrib non-free 
#deb-src http://ftp.uk.debian.org/debian/ testing main contrib non-free

# Debian Stable.
# Since 06-Feb-2011 this is known as "Squeeze". Use for maximum stability INSTEAD of
# the 'rolling' TESTING release concept.
# So, for max stability, UNCOMMENT the next two 'deb' lines and
# COMMENT-OUT the corresponding 'deb' lines in TESTING above.
#deb http://ftp.uk.debian.org/debian/ squeeze main contrib non-free 
#deb http://security.debian.org/ squeeze/updates main contrib non-free
#deb-src http://ftp.uk.debian.org/debian/ squeeze main contrib non-free 

# Multimedia Stable and Testing
# Use to install libdvdcss2 and codecs.
#deb http://www.debian-multimedia.org testing main non-free
#deb http://www.debian-multimedia.org stable main non-free

# goggles music manager
#deb http://apt.progchild.de stable main
#deb-src http://apt.progchild.de stable main

# opera
#deb http://deb.opera.com/opera/ squeeze non-free

# virtualbox
#deb http://download.virtualbox.org/virtualbox/debian squeeze contrib

# liquorix kernels
deb http://liquorix.net/debian/ sid main
deb http://ftp.belnet.be/mirror/liquorix.net/debian sid main

# Libre-kernel
#deb http://linux-libre.fsfla.org/pub/linux-libre/planet planet main

###### Debian Unstable/Sid##########
###### Use at your own risk! ########
#deb http://ftp.uk.debian.org/debian/ unstable main contrib non-free
#deb http://www.debian-multimedia.org unstable main non-free

```

---

