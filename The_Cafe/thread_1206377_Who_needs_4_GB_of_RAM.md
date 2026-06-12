---
title: "Who needs 4 GB of RAM?"
date: 2009-07-07
forum: The Cafe
---

### Post by tom66 on 2009-07-07
I think I've noticed a new trend. Heck, it's probably not new, but anyway... I'm seeing more and more consumer laptops and desktops being shipped with 4 (or more gigabytes) of RAM. I'm confused, for two reasons:

[list][*]Windows, in 32-bit, which most manufacturers ship by default  with consumer laptops/desktops (they're too scared of 64-bit because not everything works with it), can only access 3 to 3.5 GB.
[*]Who needs 4 GB of RAM, apart from extreme gamers or video editors? which these laptops/desktops would not work well with due to their mediocre processors, GPUs, and HDD(s). Can Vista really use 4 GB of RAM for *normal tasks* (reading email, browsing web, word-processing, playing flash games), whom these computers are aimed at? I don't even think that it could do that.[/list]

Ubuntu, on my laptop, which has 3 GB of physical RAM, and 256 MB dedicated graphics RAM, rarely uses more than 900MB for most tasks. On bootup it's using 240MB, which rises to 350MB within a few minutes as everything starts up. The highest I've ever had it was 2.3GB, when I opened a very large (about 10000x10000, full 24-bit uncompressed colour) image in the GIMP.

On an unrelated note, why does Vista seem to prefer page file to physical RAM (using gigabytes of page file as seen in Task Manager). Linux prefers physical RAM to swap file (using physical RAM and almost no swap whenever possible). I know physical RAM is faster... so Linux's behaviour makes sense.

Maybe I'm being stupid and missing a point, but...

---

### Post by sertse on 2009-07-07
RAM is cheap, and good value. There's minimal benefit in shipping with less ram.

---

### Post by Rhubarb on 2009-07-07
The more RAM I have, the more I can use it.

For starters, I'd load up stellarium and add in some extra big star catalogues to it.
Then I'd install an osmarender server for rendering tiles for openstreetmap.org

And then perhaps I'd experiment with RAM drives.
Though indeed Linux tends to be very efficient with it's memory usage ... and 4GB on a laptop that shouldn't be doing servery stuff is a little bit on the silly side.

heh, good points :)

---

### Post by kashey_be on 2009-07-07
I think you got it wrong.
Windows prefer RAM over page at any cost, moreover it loads as many RAM as it can during startup process so that you'll have fast access to your apps.
Oh and ubuntu should use the free RAM as cache exactly the same way.
you shouldn't need more than 800MB swap.
I am no gamer, i have only 2GB of RAM and it is not enought, so I probably expand to 4GB.
The reason for this is because I need to run virtual machines to test stuff, and this is very memory consuming.

---

### Post by K.Mandla on 2009-07-07
My fastest machine has only 512Mb in it, and even with the full Ubuntu Gnome suite running, I have never used all 512Mb. I am with the OPer; it mystifies me to think that everyday users -- especially Linux users -- somehow "need" 4Gb of memory. Must be the Windows "bigger-faster-newer" mindset at work.

---

### Post by kashey_be on 2009-07-07
The reason you only used 512 is because your system reserves some for cache and application (so it would run properly).
With today's RAM prices, there is no reason to have less than 2GB.

---

### Post by toupeiro on 2009-07-07
2 words:

Virtual Machines.

---

### Post by credobyte on 2009-07-07
I've been thinking about this for the past few months and still .. I can't seem to find a reason for buying 4 or even 8 GB of RAM ! I'm currently ( for the past few years ) using 512MB of RAM and it seems only a little bit too short .. I may upgrade it to 1 or 2 GB's, but never to 4GB ( which might be useful only for new PC's with dual/quad core processors ).

---

### Post by dentharg on 2009-07-07
/tmp in RAM

---

### Post by PurposeOfReason on 2009-07-07
> **dentharg said:**
> /tmp in RAM
Why stop there? Put firefox in ram. Compile in ram. Anything that can be in ram should be. I have 6GB and I go through it quickly if I want to.

---

### Post by Th3_uN1Qu3 on 2009-07-07
> **kashey_be said:**
> The reason you only used 512 is because your system reserves some for cache and application (so it would run properly).
With today's RAM prices, there is no reason to have less than 2GB.

And the second reason is that you're hitting that swapfile A LOT. Of course the system will not use every last byte of memory because that would make it crash. But i bet you're using at least 85%, which basically means the memory is full and you're swapping and swapping and swapping, killing that HDD.

I have 8GB RAM in my main system running Vista 64. What's wrong with that? When i start up my virtual machines 3.5GB go poof. And then i still have another 3.3GB left (Vista uses around 1.2GB on my system at idle). I have also disabled the pagefile.

Tell me, can you disable swap with 512MB of memory? I don't think so.

I agree that 2GB is generally enough with Ubuntu, but my laptop in sig still hits the swap partition sometimes, and this 5400rpm drive can be REALLY slow.

Hmm. "Nobody will need more than 640k of memory". :lolflag:

---

### Post by SoftVision on 2009-07-07
> **toupeiro said:**
> 2 words:

Virtual machines.

+1

---

### Post by cenzorrll on 2009-07-07
well, at the moment i'm using vista (i know, leave me alone) and my pagefile is at 1650M and physical memory is 1.14gb and all i have open is some cd burning software and firefox. everything else i can attribute to windows bloat. so, if i were to run any sort of memory hungry app, i would need at least 2 gb. 

as for the pagefile question. windows has so many services ready to go at any time that to keep it in ram would leave no room for anything else(in my current state i would be using near 3gb of ram if no pagefile was used), when an application or service goes idle, the OS would automatically move it to pagefile or swap in order to free up ram for applications that are running and need ram.  ubuntu and linux would use swap less because there's not so much crap running at once and 2gb of ram is more than enough to run most programs.

so... windows, lots of ram needed. linux not really any at all unless, as has been mentioned before, virtual machines, etc.

---

### Post by SunnyRabbiera on 2009-07-07
> Who needs 4 GB of RAM?

Vista and windows 7 users after opening 1 application...
Yeh baby ;)

---

### Post by kashey_be on 2009-07-07
You need RAM in linux if you want firefox with many open tabs, compiz running and 2-3 more applications open.
Firefox will consume all your memory because firefox is memory hungry app.

---

### Post by Sand &amp; Mercury on 2009-07-07
Virtual machines and games can eat it all up. If you're not into either, you're unlikely to need it all... but it's cheap and you get a lot of bang for your buck with it.

---

### Post by jespdj on 2009-07-07
My laptop has 4 GB.

One application for which I need it is VirtualBox - running for example Windows XP in a virtual machine takes up a lot of RAM.

Also, some of the software development tools, database, etc. that I use need a lot of RAM.

RAM is very cheap, so why limit yourself to 2 GB or less.

---

### Post by drawkcab on 2009-07-07
It is especially nice for running resource-hungry games.

---

### Post by ohbuntu on 2009-07-07
It certainly helps while playing the latest games. For example, Crysis has a massive appetite for RAM. GTA4 is another RAM and VRAM hog.

---

### Post by s3a on 2009-07-07
> **PurposeOfReason said:**
> Why stop there? Put firefox in ram. Compile in ram. Anything that can be in ram should be. I have 6GB and I go through it quickly if I want to.

Firefox is not 100% in RAM??? How do I make it be 100% in RAM? (so that I could get it to be even faster)

---

### Post by the8thstar on 2009-07-07
I'm interested in this one too.

---

### Post by ssam on 2009-07-07
when linux reads a file it gets cached in RAM (this is why big programs start much faster the second time you launch them). the more spare RAM you have the more that can be cached.

install preload. it automatically tries to keep useful files in the cache.

---

### Post by binbash on 2009-07-07
virtual machines...

---

### Post by catlow on 2009-07-07
The only thing i use 4 GB of RAM for is gaming

---

### Post by snerd on 2009-07-07
My box is a 7 year-old Dell Dimension with only 384mb ram. Granted, all I do is mainly e-mail and FF web browsing, but it's all this machine is gonna ever see!  ):P

---

### Post by the8thstar on 2009-07-07
> **ssam said:**
> when linux reads a file it gets cached in RAM (this is why big programs start much faster the second time you launch them). the more spare RAM you have the more that can be cached.

install preload. it automatically tries to keep useful files in the cache.

That's what I thought. I have preload installed but FF takes 10s to launch. Maybe the addons are causing the lag?

Nautilus also takes a long time to load (even with preload)... I wonder why.

---

### Post by .Maleficus. on 2009-07-07
> Windows, in 32-bit, which most manufacturers ship by default with consumer laptops/desktops (they're too scared of 64-bit because not everything works with it), can only access 3 to 3.5 GB.
I work at Best Buy and I can tell you this certainly is not the case.  Every computer that has 4GB or more of memory (whether it be RAM, RAM + graphics, whatever) has a 64-bit version of Vista.  A good portion of <4GB machines have 64-bit as well.  Manufacturers realize that 64-bit is the way of the future.

I have 4GB of RAM because it was cheap and I still play the occasional game.  I've even considered buying 4GB more, simply because I'll be set for years and it's only ~$60 on Newegg.

---

### Post by H3g3m0n on 2009-07-07
I have 6gb myself on my desktop (another 4gb in server), only about 1gb in use and this is a fairly normal level usage for me. I do from time to time run virtual machines which can be handy, or render 3d but not often.

RAM will likely keeping growing much faster than we can use it, I believe Samsung have already shown a 32gb ram stick.

Storage is starting to do this too with 1TB HDDs being so cheap now (although I've mostly filled 4tb myself). They will slow down though because of SSDs and other technologies such as the square plater designs (where are square plater is moves foward/back/left/right over multiple heads giving a high I/O) or laser read magnetic ones and other technologies favoring speed over space since a majority of drives don't need more that 64gb.

It seems fairly inevitable to me that RAM and storage will combine in the future and we will either do away with ram using swap space or everything will be on a ramdisk that doesn't clear over reboots (its only really a superficial choose with the way the BIOS/OS choose to do things and some hardware stuff with the Mobo).

Just need a fast non-volatile RAM, there are quite a few technologies out there for that, but cheap and mass producible is some ways off.

Battery backed up ramdisks are another idea.

---

### Post by amitabhishek on 2009-07-07
Still I don't see the point beyond 4GB because a 32-bit processor can address only that much (2^32 = 4294967296 ). Why still 32 bit (OS) machines come with memory > 4GB!!!? e.g. Sony Vaio FW480J/T

---

### Post by 3rdalbum on 2009-07-07
I'm also interested in how to put files and programs fully into RAM. Specifically the programs.

I don't know about the machines shipped by Best Buy, but a large number of gaming machines come with 4 GiB of RAM or MORE and 32-bit Windows.

---

### Post by sebbouckaert on 2009-07-07
Homerecording folks who use their machines as a DAW.

---

### Post by .Maleficus. on 2009-07-07
> **amitabhishek said:**
> Still I don't see the point beyond 4GB because a 32-bit processor can address only that much (2^32 = 4294967296 ). Why still 32 bit (OS) machines come with memory > 4GB!!!? e.g. Sony Vaio FW480J/T
Core 2 Duo P7350 is 64-bit.  Windows Vista Home Premium is 64-bit.

---

### Post by tom66 on 2009-07-07
I'm mostly referring to consumer-grade entry-level laptops you buy for about £300 - £500, which seem to come with large amounts of memory. For example I saw an ad for the Dell Inspiron 15 series, which is clearly aimed to people as an entry-level laptop (hey, you can get it in red, green, pink, blue...), and it comes with 4 GB of RAM. 

Anyway, I did a little experiment, to see how difficult 3 GB of RAM was to use. I tried opening every picture in my Pictures folder (65 pictures, 85.8 MB, most are 1280x800 desktop wallpapers) in GIMP. It took a few minutes. I then loaded a 11000x6000 pixel image of a galaxy, also in GIMP. Total RAM usage: ~2.5 GB, total swap: ~100 MB. This was also while I had OpenOffice.org Writer, Inkscape, Firefox, KDevelop, gedit and Compiz running. 

Virtual machines and gaming are all good reasons to have a large amount of RAM, but the processors and GPUs in these systems I refer to couldn't do most of what's mentioned, or could only really do it at a slow pace.

---

### Post by geoken on 2009-07-07
> **tom66 said:**
> 

Anyway, I did a little experiment, to see how difficult 3 GB of RAM was to use. I tried opening every picture in my Pictures folder (65 pictures, 85.8 MB, most are 1280x800 desktop wallpapers) in GIMP. It took a few minutes. I then loaded a 11000x6000 pixel image of a galaxy, also in GIMP. Total RAM usage: ~2.5 GB, total swap: ~100 MB. This was also while I had OpenOffice.org Writer, Inkscape, Firefox, KDevelop, gedit and Compiz running. 

Create an 11000x6000 image in Inkscape and start working with it and you'll see the memory start filling up.

And before anyone wrights that example off as being completely unrealistic, it's pretty common for me to work with files of that size when I'm designing vinyl banner or posters.

---

### Post by mousestalker on 2009-07-07
+1 on virtual machines.

I have Ubuntu 9.04 64 bit with 8 gigs RAM. Running Vista, XP and Linux will easily put me over 6 gigs (I loathe slow). Throw in that I use GIMP heavily and there you are.

Of course gaming has absolutely nothing to do with me having excess RAM. It's all for work, I swear!

;)

---

### Post by PurposeOfReason on 2009-07-07
> **s3a said:**
> Firefox is not 100% in RAM??? How do I make it be 100% in RAM? (so that I could get it to be even faster)

> **the8thstar said:**
> I'm interested in this one too.
[http://forums.gentoo.org/viewtopic-t-717117-highlight-firefox.html](http://forums.gentoo.org/viewtopic-t-717117-highlight-firefox.html)

---

### Post by LowSky on 2009-07-07
A few things I need 4GB of RAM for
CAD
Virtual machines (newest VWmware needs 64bit processor too)
HD video recording and watching, 2GB works but not as well as 4GB
Encoding video
Multitasking any of the above mentioned stuff
MS Windows 7-- 2GB works OK but 4 is better, less bottleneck

---

### Post by chriskin on 2009-07-07
i do :)

if you NEVER shut down the pc, after some days even the perfect os goes too slow on 2gb ram or less

---

### Post by HappyFeet on 2009-07-07
> **K.Mandla said:**
> My fastest machine has only 512Mb in it, and even with the full Ubuntu Gnome suite running, I have never used all 512Mb. I am with the OPer; it mystifies me to think that everyday users -- especially Linux users -- somehow "need" 4Gb of memory. Must be the Windows "bigger-faster-newer" mindset at work.

If you like being such a minimalist, why not get rid of some RAM and see how it goes? Why not just use 128? Heck, the average person should not need more than 64mb.

As we all know, we all use our computers just like you, therefore no one should need more than 512. I'll alert the manufacturers to the fact that they are wasting memory and should start shipping with 512 or less. OK?
;)

---

### Post by RiceMonster on 2009-07-07
4GB ram on my desktop, 2GB on my laptop. I could get away with 1GB just fine on either for sure (probably even 512MB), but why not? Ram is cheap.

> **chriskin said:**
> i do :)

if you NEVER shut down the pc, after some days even the perfect os goes too slow on 2gb ram or less

eh... I didn't shutdown my laptop with 2GB for a month, and that definietly didn't happen. It was using ~200MB ram on idle.

---

### Post by chriskin on 2009-07-07
> **RiceMonster said:**
> 
 eh... I didn't shutdown my laptop with 2GB for a month, and that definietly didn't happen. It was using ~200MB ram on idle.


having what apps running that month though?
if you were using it heavily along side with compiz at its full, you would see a lot of problems

---

### Post by blur xc on 2009-07-07
> **tom66 said:**
>  On an unrelated note, why does Vista seem to prefer page file to physical RAM (using gigabytes of page file as seen in Task Manager).

I've noticed this too.  I recently read an article that stated if you had plenty of ram ot shrink your page file to force the os to use more ram, thus improving system performance.  I tried that and windows got mad and increased my page file size.  When viewing the task manager performance tab, it tells me I have 2gigs of ram available, (maybe I'm reading it wrong) but I've got a 1 gig page file running.

Has anyone tried using a ssd for a swap/page file drive?

BM

edit- running xp sp3 btw

---

### Post by PurposeOfReason on 2009-07-07
> **Barna Madau said:**
> I've noticed this too.  I recently read an article that stated if you had plenty of ram ot shrink your page file to force the os to use more ram, thus improving system performance.  I tried that and windows got mad and increased my page file size.  When viewing the task manager performance tab, it tells me I have 2gigs of ram available, (maybe I'm reading it wrong) but I've got a 1 gig page file running.

Has anyone tried using a ssd for a swap/page file drive?

BM

edit- running xp sp3 btw
With a SSD you should disable the page/swap for wear reasons.

---

### Post by blur xc on 2009-07-07
you can wear out a ssd?

BM

---

### Post by PurposeOfReason on 2009-07-07
Yes, quite easily too. They've gotten a lot better but you still should take care with it.

---

### Post by andras artois on 2009-07-07
You don't need a bed frame or more than 1 cup but you still have them right?

---

### Post by Grant A. on 2009-07-07
The worst thing is that a lot of manufacturers ship 32 bit operating systems with more than 1.8gb of RAM, even when they have 64 bit processors.

The woman on one of those Windows commercials was sad because the Macbook only had one gig of RAM, so she bought the **32 bit** Windows notebook with **4gb of RAM**. That was the only thing she liked about it to, she mentioned nothing else. -_-

---

### Post by H3g3m0n on 2009-07-10
> **amitabhishek said:**
> Still I don't see the point beyond 4GB because a 32-bit processor can address only that much (2^32 = 4294967296 ). Why still 32 bit (OS) machines come with memory > 4GB!!!? e.g. Sony Vaio FW480J/T

It is actually possible for 32bit OSes to use more than 4gb of ram using PAE, even Windows can (although MS seem to artificially limit it to sell more expensive versions).

[http://msdn.microsoft.com/en-us/library/aa366796%28VS.85%29.aspx](http://msdn.microsoft.com/en-us/library/aa366796%28VS.85%29.aspx)

---

