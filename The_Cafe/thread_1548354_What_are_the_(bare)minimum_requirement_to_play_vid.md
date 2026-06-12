---
title: "What are the (bare)minimum requirement to play video &amp; audio in a computer"
date: 2010-08-08
forum: The Cafe
---

### Post by neoargon on 2010-08-08
I am wondering what the minimum hardware and software requirements  to play video & audio in a computer are? Video should be output as actual video and not as ASCII ART . Let the video not be HD . Audio be a 192 kbps mp3 . Any idea?
I wish to know the bare minimum requirement . Without a desktop environment or even a window manager . Is X11 a requirement? 
How much RAM or processor will be required?  
What would the requirements be if the video is HD or if mp3 is 320 kbps .


Iam thinking of buying an old laptop if I get one at a very CHEAP price . But before that , I need to know whether I can put it for any use .

---

### Post by szymon_g on 2010-08-08
> **neoargon said:**
> I am wondering what the minimum hardware and software requirements  to play video & audio in a computer are? Video should be output as actual video and not as ASCII ART . Let the video not be HD . Audio be a 192 kbps mp3 . Any idea?
I wish to know the bare minimum requirement . Without a desktop environment or even a window manager . Is X11 a requirement? 
How much RAM or processor will be required?  
What would the requirements be if the video is HD or if mp3 is 320 kbps .

the minimum for mp3 is, afaik, 10mHz (on ARM platform)- but i guess, than old pentium 166 will have no problems with MP3's... about video- as long as it's not a hd, something like 300-400mhz will be sufficient (on x86)

---

### Post by neoargon on 2010-08-08
When using ARM ,performance per clock speed would be much better than that of x86 ,wouldn't it?

---

### Post by szymon_g on 2010-08-08
> **neoargon said:**
> When using ARM ,performance per clock speed would be much better than that of x86 ,wouldn't it?

it depends. the good think about ARM is that it is much more power-efficent, i.e- it can give you a decent performance using much less power (and thats why it is in smartphones etc)- but, compared clock-to-clock, they aren't much faster in general usage (but, because they are often used in mp3/4 player- they can be optimised to do that stuff)

---

### Post by neoargon on 2010-08-08
> **szymon_g said:**
> the minimum for mp3 is, afaik, 10mHz (on ARM platform)- but i guess, than old pentium 166 will have no problems with MP3's... about video- as long as it's not a hd, something like 300-400mhz will be sufficient (on x86)

Thanks . But if the mp3 player is running over linux,  linux alone will require some more resources

---

### Post by NMFTM on 2010-08-08
> **neoargon said:**
> I am wondering what the minimum hardware and software requirements  to play video & audio in a computer are? Video should be output as actual video and not as ASCII ART .
I'm certainly not an AV expert. But I would think that it'd actually make more processing power to insert a DVD or play a video file and have it played as ASCII art (MPlayer has a plugin that does this I think) rather than just playing the video in it's original format. Because your not only processing the original video, but your also using your processing power to convert the video to another format. So your doing two things instead of one.

---

### Post by cascade9 on 2010-08-08
> **neoargon said:**
> I am wondering what the minimum hardware and software requirements  to play video & audio in a computer are? Video should be output as actual video and not as ASCII ART . Let the video not be HD . Audio be a 192 kbps mp3 . Any idea?
I wish to know the bare minimum requirement . Without a desktop environment or even a window manager . Is X11 a requirement? 
How much RAM or processor will be required?  
What would the requirements be if the video is HD or if mp3 is 320 kbps .


MP3 requirements are so low it doesnt matter. I've played MP3s on a 486 in the past. 192k MP3s will use more CPU power to decode and play than 320k MP3 (more compression, more CPU power needed to decode)

As for video.....complicated. Depends on the format, the frame size, etc.. 

HD requrements to decode and play was considered to be about 3.5GHz (single core) or 2.5GHz (dual core) but those numbers have issues. Newer CPUs have a lot more power per MHz than older CPUs. 

The requirements for video or HD video are a huge amount lower if you using VDPAU (or similar). 


> **neoargon said:**
> When using ARM ,performance per clock speed would be much better than that of x86 ,wouldn't it?

As far as I know, x86 is faster per MHz than ARM. I'm pretty sure that the ARM manufacturer at some point boasted that ARM could match Atom 'clock for clock'. Atom is not even that close to the most powerful x86 CPUs (Intel i7, AMD Phenom II)

---

### Post by linux18 on 2010-08-08
OGG VORBIS 
it decodes faster than mp4 and mplayer is a more lightwieght video player.
lastly, play the videos through xinit ( just type " xinit " where you would normally type "startx" )

---

### Post by neoargon on 2010-08-08
> **linux18 said:**
> OGG VORBIS 
  play the videos through xinit ( just type " xinit " where you would normally type "startx" )
What change would that make ? I couldn't find any

---

### Post by neoargon on 2010-08-08
It may be a stupid question, but ,Is X a must to play back video?

---

### Post by neoargon on 2010-08-08
> **cascade9 said:**
>  192k MP3s will use more CPU power to decode and play than 320k MP3 (more compression, more CPU power needed to decode)
I didn't think about it . 

> 

The requirements for video or HD video are a huge amount lower if you using VDPAU (or similar). 

Should we need to install Fluendo's official codecs? Would free codecs be enough?

---

### Post by cascade9 on 2010-08-08
> **neoargon said:**
> Should we need to install Fluendo's official codecs? Would free codecs be enough?

VDPAU is not a a decoder, exactly. It is just a way for teh decoding of the video to be moved from the CPU to the GPU. 

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

Paying for the fluendo codec wont make much, if any, difference to the CPU power needed to decode video.

---

### Post by linux18 on 2010-08-08
> **cascade9 said:**
> VDPAU is not a a decoder, exactly. It is just a way for teh decoding of the video to be moved from the CPU to the GPU. 

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

Paying for the fluendo codec wont make much, if any, difference to the CPU power needed to decode video.
but then you would to jam an nvidia [GeForce 8 series]("http://en.wikipedia.org/wiki/GeForce_8_series") or laterinto an old machine, why not just upgrade ram/cpu in that case

---

### Post by neoargon on 2010-08-08
> **cascade9 said:**
> VDPAU is not a a decoder, exactly. It is just a way for teh decoding of the video to be moved from the CPU to the GPU. 

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

Paying for the fluendo codec wont make much, if any, difference to the CPU power needed to decode video.
I know it . Isn't it the Gstreamer plugin that decodes the file? If that plugins doesn't use VDPAU, we won't get the advantage . That's what I thought

---

### Post by cascade9 on 2010-08-08
> **linux18 said:**
> but then you would to jam an nvidia [GeForce 8 series]("http://en.wikipedia.org/wiki/GeForce_8_series") or laterinto an old machine, why not just upgrade ram/cpu in that case

That is getting away from what neoargon was wonder (minimum requrements to play audio/video) but I'll answer anyway. ;) 

Cheaper- you can get a VDPAU capable card cheaper than CPUs. 
Power Use- As long as you dont get some silly 'gamers' card, playing videos with VDPAU in mosy cases will have a lower power requirement than CPU decoding. 
Easy- Much, much easier to install a new video card than it is to strip out the current motherboard, or CPU. 

Its also nice for systems that would never have enough power to play HD video, no matter how much you upgraded the CPU. 

BTW, as long as you have a decent mount of RAM adding RAM will not help at all for video decoding. I play was playing .avis on a very old P3 866/256MB system up till recently.....running with 512MB didn't help video playing at all. 

> **neoargon said:**
> I know it . Isn't it the Gstreamer plugin that decodes the file? If that plugins doesn't use VDPAU, we won't get the advantage . That's what I thought

Honestly, I dont know the relationship between gstreamer and VDPAU. I havent had any issues with VDPAU and plugins myself. :) 

Not everything uses gstreamer anyway. VLC doesnt, and you can get VDPAU running with VLC. Or so I've heard anyway, I havent tried it myself, I'm mainly using mplayer for VDPAU.

---

### Post by linux18 on 2010-08-08
> **cascade9 said:**
> That is getting away from what neoargon was wonder (minimum requrements to play audio/video) but I'll answer anyway. ;) 

Cheaper- you can get a VDPAU capable card cheaper than CPUs. 
Power Use- As long as you dont get some silly 'gamers' card, playing videos with VDPAU in mosy cases will have a lower power requirement than CPU decoding. 
Easy- Much, much easier to install a new video card than it is to strip out the current motherboard, or CPU. 

Its also nice for systems that would never have enough power to play HD video, no matter how much you upgraded the CPU. 

BTW, as long as you have a decent mount of RAM adding RAM will not help at all for video decoding. I play was playing .avis on a very old P3 866/256MB system up till recently.....running with 512MB didn't help video playing at all. 



Honestly, I dont know the relationship between gstreamer and VDPAU. I havent had any issues with VDPAU and plugins myself. :) 

Not everything uses gstreamer anyway. VLC doesnt, and you can get VDPAU running with VLC. Or so I've heard anyway, I havent tried it myself, I'm mainly using mplayer for VDPAU.
adding ram will help if you increase buffer size an enable frame skipping.

---

### Post by cariboo on 2010-08-08
I use an Apple G4, 350Mhz PPC cpu 160Mb ram, 5Gb hard drive, for playing mp3s, It has Karmic PPC cli installed, using randomplay and mpg321 to play everything, the bit rates range from 192 to 320, plus VBR. This really is to much  hardware, as the thing does't even break a sweat during daily usage.

---

### Post by cascade9 on 2010-08-08
> **linux18 said:**
> adding ram will help if you increase buffer size an enable frame skipping.

That is only going to help if you dont have enough RAM to begin with.

---

### Post by neoargon on 2010-08-08
> **cascade9 said:**
> That is getting away from what neoargon was wonder (minimum requrements to play audio/video) but I'll answer anyway. ;) 

Cheaper- you can get a VDPAU capable card cheaper than CPUs. 
VDPAU requires NVIDIA Graphics card . Is there any cheap Nvidia card?

> 

Not everything uses gstreamer anyway. VLC doesnt, and you can get VDPAU running with VLC. Or so I've heard anyway, I havent tried it myself, I'm mainly using mplayer for VDPAU.
Do we have to get VDPAU running? I mean do we have to change the configuration? I thought a VDPAU supported video player would use it automatically

---

### Post by neoargon on 2010-08-08
What's the minimum software requirement? 
X + mplayer?

---

### Post by doorknob60 on 2010-08-08
Mplyer can play videos in the framebuffer, so you don't need X. Here's some info on it: [http://www.gentoo-wiki.info/MPlayer/Framebuffer](http://www.gentoo-wiki.info/MPlayer/Framebuffer) I've tried it once, I think it worked.

---

### Post by ssam on 2010-08-08
> **szymon_g said:**
> the minimum for mp3 is, afaik, 10mHz (on ARM platform)- but i guess, than old pentium 166 will have no problems with MP3's... about video- as long as it's not a hd, something like 300-400mhz will be sufficient (on x86)

ARM usually has a DSP chip coupled with it for multimedia decoding.

if you want cheap, then look at the first generation of netbooks. they should be pretty cheap by now (just make sure it does not have the GMA500 graphics ship)

---

### Post by murderslastcrow on 2010-08-08
The main issue these days seems to be that these low end computers have such little value that you're better off looking for something with 512 MB of RAM or more. The only computers still being sold with these low specs (too low to run compiz) are really old iMacs, due to novelty in many cases.

I really love the idea of having a really old computer and using it very comfortably with a nice fluxbox theme or something, but it's just unrealistic for me. There aren't enough crappy computers out there, anymore. XD

Ah, the digital life of a Linux user- far too easy.

---

### Post by K.Mandla on 2010-08-08
> **neoargon said:**
> I am wondering what the minimum hardware and software requirements  to play video & audio in a computer are? Video should be output as actual video and not as ASCII ART . Let the video not be HD . Audio be a 192 kbps mp3 . Any idea?
I wish to know the bare minimum requirement . Without a desktop environment or even a window manager . Is X11 a requirement? 
How much RAM or processor will be required?  
What would the requirements be if the video is HD or if mp3 is 320 kbps .


Iam thinking of buying an old laptop if I get one at a very CHEAP price . But before that , I need to know whether I can put it for any use .
If you want something that will do both audio and video, about 300Mhz will do. Just audio, you can drop to 200Mhz or lower, but for some reason, ogg playback falls off for me around 150Mhz. It's still manageable and works fine, I'm just not sure why I get skips in playback. Still working on that. :-k

You do not need X for video. mplayer will play against the framebuffer with the *-vo fbdev* flag, and if you compile it without X dependencies it's quite a bit lighter and faster.

The caveat to that is the same as the audio though: Certain high-quality codecs require more processor power. So if you're building your library with large-size high-resolution codecs, your little 300Mhz machine might struggle. I've built two or three as experiments with normal-range, acceptable video quality and had no problem though.

---

### Post by linux18 on 2010-08-08
> **K.Mandla said:**
> If you want something that will do both audio and video, about 300Mhz will do. Just audio, you can drop to 200Mhz or lower, but for some reason, ogg playback falls off for me around 150Mhz. It's still manageable and works fine, I'm just not sure why I get skips in playback. Still working on that. :-k


if the codec has a variable bit rate, the decoding requirement might be spiking above the processing power. by increasing the ram buffer size and minimum ram buffer capacity you should be able to smooth out the processing requirements.

---

### Post by neoargon on 2010-08-09
Thanks to everyone

---

### Post by cascade9 on 2010-08-09
> **neoargon said:**
> VDPAU requires NVIDIA Graphics card . Is there any cheap Nvidia card?
 
 Do we have to get VDPAU running? I mean do we have to change the configuration? I thought a VDPAU supported video player would use it automatically
 
 Cheapest nVidia card that supports VDPAU is the 8400GS. There are PCI models as well, not just PCIe so you should be able to run one in older systems. 
 
 In my experience, even with VDPAU installed, etc, you still need to tell the player to use VDPAU. With some players, it should be as easy as changing the video output driver (like smplayer) with others it can be a far longer and more complicated task (like with VLC).

> **K.Mandla said:**
> If you want something that will do both audio and video, about 300Mhz will do. Just audio, you can drop to 200Mhz or lower, but for some reason, ogg playback falls off for me around 150Mhz. It's still manageable and works fine, I'm just not sure why I get skips in playback. Still working on that. :-k 

Interesting. 

Around 1999/2000, I simply couldnt play .ogg vorbis files on my then current computer- Cyrix 166+, 48MB, 2.1GB HDD. It would play them with minor skipping on the same system with an AMD K6 200. I always put that down to .ogg being very new at the time, and my horrible motherboard. I had a PC chips (I know, the worst name in the histroy of computers) VX Pro+, and I never figured out if it had the 512k cache it said it did, 256k cache, or none at all. 

Poor thing is deader than the dodos now so I'll never know about the cache. 

> **K.Mandla said:**
> The caveat to that is the same as the audio though: Certain high-quality codecs require more processor power. So if you're building your library with large-size high-resolution codecs, your little 300Mhz machine might struggle. I've built two or three as experiments with normal-range, acceptable video quality and had no problem though.

Yes, true. I wont even go into video, but for audio, the differences between some of the lossless codecs is huge. OptimFROG (.ofr) and monkeys audio (.ape) use a lot of CPU to decode. Flac is about the same, or even lower than MP3. Yet another reason why I use flac.

> **linux18 said:**
> if the codec has a variable bit rate, the decoding requirement might be spiking above the processing power. by increasing the ram buffer size and minimum ram buffer capacity you should be able to smooth out the processing requirements.

RAM helps, but it wont make up for CPU power. 

On my old cyrix166+/AMD200, I tried throwing a lot more RAM at it (up to 128MB)and it made no difference to .ogg playback.

---

### Post by linux18 on 2010-08-09
> **cascade9 said:**
> 


RAM helps, but it wont make up for CPU power. 

On my old cyrix166+/AMD200, I tried throwing a lot more RAM at it (up to 128MB)and it made no difference to .ogg playback.
but did you increase the buffer size and minimum buffer capacity?

---

### Post by blueturtl on 2010-08-09
> If you want something that will do both audio and video, about 300Mhz will do. Just audio, you can drop to 200Mhz or lower, but for some reason, ogg playback falls off for me around 150Mhz. It's still manageable and works fine, I'm just not sure why I get skips in playback. Still working on that.

(Can't believe I'm attempting to advice K.Mandla :D )

Have you tried a different video card? I know it sounds silly but I had this exact problem with a really old computer and I thought it just couldn't handle proper playback. The cause was later determined to be the video card (S3 ViRGE) which when doing any intensive drawing operations would completely hog up the bus and the CPU. Swapped to another card and suddenly the old Pentium had no problem decoding mp3/ogg.

Also some old sound cards have crappy ALSA drivers.

---

### Post by blueturtl on 2010-08-09
To the OP:

A Pentium II 350 MHz is the official minimum requirement for software decoding a DVD. Trick is it runs on 100 MHz bus. I also have a 400 MHz K6-III Socket 7 system that is capable of playing most XVid movie rips, though it's system bus runs at 66 MHz.

---

### Post by cascade9 on 2010-08-09
@ blueturtl- those S3 Virge cards were awful. No wonder S3 got bought out. Pity that your K6-3+ is running on socket7 motherboard, not a super socket7 (100MHz FSB), but the good super 7 boards are hard to find these days. You might be able to bump the FSB to 75MHz aqnd drop the multi to keep it at 400MHz, or even run it at 450MHz....thats a long way from how far I've seen the old K6-3s pushed. 

> **linux18 said:**
> but did you increase the buffer size and minimum buffer capacity?

LOL, playing with the buffers on win98 isnt a good idea. 

You could say that by increasing the memory size, I would have increased the buffer size as well. 

> A [buffer]("http://en.wikipedia.org/wiki/Data_buffer") is a temporary memory location, that is traditionally used because CPU [instructions]("http://en.wikipedia.org/wiki/Instruction_%28computer_science%29") cannot directly address data stored in peripheral devices. Thus, addressable memory is used as intermediate stage. 

[http://en.wikipedia.org/wiki/Cache](http://en.wikipedia.org/wiki/Cache)

---

### Post by linux18 on 2010-08-09
> **cascade9 said:**
> @ blueturtl- those S3 Virge cards were awful. No wonder S3 got bought out. Pity that your K6-3+ is running on socket7 motherboard, not a super socket7 (100MHz FSB), but the good super 7 boards are hard to find these days. You might be able to bump the FSB to 75MHz aqnd drop the multi to keep it at 400MHz, or even run it at 450MHz....thats a long way from how far I've seen the old K6-3s pushed. 



LOL, playing with the buffers on win98 isnt a good idea. 

You could say that by increasing the memory size, I would have increased the buffer size as well. 

 

[http://en.wikipedia.org/wiki/Cache](http://en.wikipedia.org/wiki/Cache)
I'm talking about the music player's buffer,  mplayer sets it to 4096KB with a minimum capacity of 2% if you change that to 8192KB and 20% music won't skip. just increasing the ram wont increase the buffer.

---

### Post by cascade9 on 2010-08-09
> **linux18 said:**
> I'm talking about the music player's buffer,  mplayer sets it to 4096KB with a minimum capacity of 2% if you change that to 8192KB and 20% music won't skip. just increasing the ram wont increase the buffer.

I cant remember exactly what I did with the poxy version of winamp (thank the gawds I never have to see winamp again) and some creative media player circa 2000, but I do remember poking every setting I could with no joy. 

When I tired it later with foobar (maybe 2005?), still no joy, and I know I did increase the buffer with it. 

RAM wont make up for a shortfall of CPU power.

---

### Post by blueturtl on 2010-08-09
> **cascade9 said:**
> @ blueturtl- those S3 Virge cards were awful. No wonder S3 got bought out. Pity that your K6-3+ is running on socket7 motherboard, not a super socket7 (100MHz FSB), but the good super 7 boards are hard to find these days. You might be able to bump the FSB to 75MHz aqnd drop the multi to keep it at 400MHz, or even run it at 450MHz....thats a long way from how far I've seen the old K6-3s pushed. 


I know that now... they were even referred to as graphics deaccelerators. :D The sound would skip every time I dragged a scrollbar... even without X! I could not run links2 and scroll webpages without the sound screetching to a halt. Imagine my surprise when I swapped the video card (for completely unrelated reasons) and suddenly I could play MP3s fine.

I also know the K6-III in my comp could do 600 MHz with stock cooling and voltage (it is a notebook model CPU), but unfortunately the mobo I am stuck with cannot withstand just the tiniest amount of overclocking. In fact the mobo is not supposed to support this chip at all, but due to the genious engineers at AMD I am able to run it at a multiplier that allows me to achieve the full specced speed of 400 MHz. It's a 4x100 chip, but also interprets the 2x multiplier as 6x, so one thing led to another and bang: 6x66 == 400 MHz. :)

---

### Post by juancarlospaco on 2010-08-09
*Without LAG:*

HTML5: a Casio Calculator
Adobe Flash: 8 Cores required

:)

---

### Post by linux18 on 2010-08-09
> **juancarlospaco said:**
> *Without LAG:*

HTML5: a Casio Calculator
Adobe Flash: 8 Cores required

:)
I yhink your off a little bit 

HTML5: TI-84
Adobe Flash: all of google's servers

I have 8 cores and full screen flash is still laggy

---

### Post by cascade9 on 2010-08-09
> **blueturtl said:**
> I know that now... they were even referred to as graphics deaccelerators. :D The sound would skip every time I dragged a scrollbar... even without X! I could not run links2 and scroll webpages without the sound screetching to a halt. Imagine my surprise when I swapped the video card (for completely unrelated reasons) and suddenly I could play MP3s fine.

I also know the K6-III in my comp could do 600 MHz with stock cooling and voltage (it is a notebook model CPU) 

LMAO. Yep, had the same here when I ran a Virge. Funny thing was that it was better for gaming than the cirrus logic card I swapped to, and for a while there I was running 2x HDDs with 2 OSes, swapping cards in and out depeding on what I want to do with the computer. 

Ohh.....the notebook model. They are really, really nice. Not many boards that have offical support for them, even less than the normal desktop K6-3.  IIRC it was like 2-3 boards that had offical support :( Pity, the K6-3+ is IMO one of the best CPUs ever, amazing for its time.

> **linux18 said:**
> I yhink your off a little bit 

HTML5: TI-84
Adobe Flash: all of google's servers

I have 8 cores and full screen flash is still laggy

i7? 4 cores (or 6 for the really rich). Threads =/= cores, even intel says that.

[http://www.intel.com/products/processor/corei7/index.htm](http://www.intel.com/products/processor/corei7/index.htm)

[http://www.intel.com/products/processor/corei7/specifications.htm](http://www.intel.com/products/processor/corei7/specifications.htm)

---

### Post by linux18 on 2010-08-09
> **cascade9 said:**
> LMAO. Yep, had the same here when I ran a Virge. Funny thing was that it was better for gaming than the cirrus logic card I swapped to, and for a while there I was running 2x HDDs with 2 OSes, swapping cards in and out depeding on what I want to do with the computer. 

Ohh.....the notebook model. They are really, really nice. Not many boards that have offical support for them, even less than the normal desktop K6-3.  IIRC it was like 2-3 boards that had offical support :( Pity, the K6-3+ is IMO one of the best CPUs ever, amazing for its time.



i7? 4 cores (or 6 for the really rich). Threads =/= cores, even intel says that.

[http://www.intel.com/products/processor/corei7/index.htm](http://www.intel.com/products/processor/corei7/index.htm)

[http://www.intel.com/products/processor/corei7/specifications.htm](http://www.intel.com/products/processor/corei7/specifications.htm)
they are virtual cores!

---

### Post by blueturtl on 2010-08-10
> Ohh.....the notebook model. They are really, really nice. Not many boards that have offical support for them, even less than the normal desktop K6-3. IIRC it was like 2-3 boards that had offical support  Pity, the K6-3+ is IMO one of the best CPUs ever, amazing for its time.

K6-3+ indeed. The best part is that the Pentium 233 MHz that I replaced with it has about double the power consumption. :D As far as official support goes... you don't need that. ;) I used a patched BIOS from [this site]("http://web.inter.nl.net/hcc/J.Steunebrink/k6plus.htm") and it works wonderfully. Also now my mobo automatically recognizes HDDs up to 120 GB in size.

I miss the days when AMD and Intel CPUs ran in the same socket. Nowadays the upgrade path is always set to which you initially buy. Intel wouldn't make a P2 for the Socket 7 platform so AMD came to the rescue, first with the K6-2 and then K6-3!

---

### Post by szymon_g on 2010-08-10
> **linux18 said:**
> they are virtual cores!

there is no such a thing like 'virtual cores'
(you mean: 4 cores + HT, i suspect)

but the good think about cores and linux: linux supports up to 4096 cores! shame the flash has still shitty performance even on 4 cores :~/ (but, ya know, linux is perfect for desktop as some people claim)

---

### Post by linux18 on 2010-08-10
> **szymon_g said:**
> there is no such a thing like 'virtual cores'
(you mean: 4 cores + HT, i suspect)

but the good think about cores and linux: linux supports up to 4096 cores! shame the flash has still shitty performance even on 4 cores :~/ (but, ya know, linux is perfect for desktop as some people claim)
thanks for allowing me to grab an appropriate xkcd comic for the situation:
[IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]

xkcd has a comic for everything

---

