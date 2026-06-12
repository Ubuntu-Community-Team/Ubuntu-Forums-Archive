---
title: "Intro to Ubuntu DAW Programs Please"
date: 2012-08-05
forum: Ubuntu Studio
---

### Post by Bluphx on 2012-08-05
Hi

I'm an ex Apple genius, been running Ableton Live and Logic Studio on a 24" iMac but was given a Sony VPCZ1 laptop. I've been having a hell of a time getting Windows n Ubuntu to play nice together, or 64bit version of Ubuntu to install at all for that matter =P Before I continue to battle to install 64bit I just wanted an intro on Ubuntu Studio too see if the juice is worth the squeeze, or if I should try too hackintosh this..

1. Was wondering what DAW Programs (Logic/Live/Protools/etc) are available for ubuntu?

2. Also how much of a pain are drivers for interfaces/midi devices?
(I'm mainly concern'd w/ Live and my Novation Launchpad)

3. Does swap-space help cut down on latency or lag from too many tracks/effects/etc? Also can thumbdrives or SD Card/Sony Memory Cards be used for RAM/Swap-Space?

Thanx in advanced, hopefully someone can sell my on moving too Ubuntu ~.o

---

### Post by CrocoDuck on 2012-08-06
Hi. For the point 1:

No, those programs ar not avaible under linux. I'm not usually use those programs (I know, is strange, but I don't like them:p), but when I do I'm usually use them just for editing, using a windows virtual machine on virtualbox. If you like Protools you should be confortable with Ardour, a multitrack recorder with exquisite features: [http://ardour.org/](http://ardour.org/) , it's actually my favourite DAW ever! At the current version midi recording and editing is not included, but it will be included at version 3. You can also install a native Harrison Consoles Mixbus for linux. If you need Midi recording Qtractor is the choice. If you really want to use the programs you listed you may try installing their windows version with wine and try to make them deal with jack (see below) with wineasio.

For the point 2:

Drivers and daemons are not so clear at first sight, but when you understand the basis a world opens to you. Basically, for a DAW setup things works like this: there are hardware drivers (ALSA, OSS, FFADO,..) and a low latency server (jack: [http://jackaudio.org/](http://jackaudio.org/)), that allows the audio applications to run with low latency (5.33 ms for my 10 years old AMD64 with 512Mb of ram are good!) dealing with the driver you want. Jack is the main program, and the most of audio configuration is done using it (or QjackCtl, his GUI). The most common driver is ALSA: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page), actually a linux kernel component (default and configured on every ubuntu flavour). Setting up interfaces/midi devices could be simply as plug 'n' play (as happened with my M-Audio keystation 88 es and Behringher UCA 202) or hard as hell (or just need a little tweaking). Have a look if the hardware you want to use is supported. If you don't get infos for your hardware googling around or in the relative projects sites (ALSA, jack, FFADO) post a questiona about it on forums.

For the point 3:

Actually, a good idea is to set swappiness to 10 on a proaudio system: is better to move the laod on the RAM, using less Hard Drivers. Actually, the main parameter to keep an eye after latency are the xruns ([http://ubuntuforums.org/showthread.php?t=1125198](http://ubuntuforums.org/showthread.php?t=1125198)). Basically, they are like sample loss. Jack gives to us statistics on them, in order to optimize the setup. When you get a stable setup (low latency and very rare xruns, just running jack) stress on machine could produce xruns. It depends on your machine, how many programs you run, how heavy they are, and  how long  they are running. Things are usually stable with recent computers (sometimes, on my 10 years old computer, I have to stop and restart jack every hour, but have no problems with my dual core 64bit with 4 Gb of RAM laptop). Using a SD or a flash drive for swap should be possibile, and could be a good idea giving a try (after had pointed out how much memories and controllers are fast).

I've written a lot of things, hope this infos are usefull for you (and understandable, my english is bad)... So: actually things are getting usually work good out of the box. Native linux audio programs are getting better and better. So, check if your hardware is supported, give a try to ubuntu studio in order to view if things works (and if the software fits your needings). If not, try to check if you can solve the issues (the comunity is very helpfull). Another important thing is the choice of the Kernel: I reccomend a lowlatency one (default on ubuntu studio 12.04).

Please, let me say why I prefer open source software in audio: It lets me to be creative. It comes with a lot of tools that are scientifical, and accurate. They can make you learn a lot of things on informatics, acoustic, audio editing etc..etc... just because they comes with no commercial purpose, they are tools for your immagination. They are a blank paper with a collection of tools to paint it. You can really point out your sound from your mind, without being conditioned by advertising presets.

---

### Post by Bucky Ball on 2012-08-06
Flash drive (you mean USB?) not good idea for low latency DAW swap. SD card better.

---

### Post by Bluphx on 2012-08-07
Yo yea the info help'd a lot, thanx. For live DJ'ing I think I'm going to stick with ableton live and my novation launchpad, but am excited too test studio for more the recording side of things.

I finally got a 64bit version to install on the computer (Raid 0 was my problem, turned raid off n just treating as 2 separate HDs) but the drivers aren't there for my MemoryStick/SD Card so will have to test swap-space later. (and too answer your question bucky yea I was asking if Thumbdrives/SD/MemoryCard was a good option for swap b/c i know sometimes the bus speed for xfering data can be slower than normal and actually end up causing more lag)

I'll have to try out the DAW you mentioned. Im not emotionally attached to any DAW other than Ableton Live (for playing live and clip launching for recording)

Last noobish question can does VM or WINE utilize swap-memory (I know VM you can set the max ram usage but don't know about WINE)?

---

### Post by jejeman on 2012-08-07
I don't know why are you so interested in swap. How much RAM does that Sony have? If you have < 2GB use 32bit OS.
Anyway in my experience even with swap on HDD OS becomes almost useless. It slows down dramaticly.

---

### Post by Bucky Ball on 2012-08-07
Off topic, but yea, Ableton rocks. To be honest, my desktop is dual-boot with XP where I have Ableton, Pro-Tools, Cubase, Premiere .... etc ...

For pro A/V stuff I just don't bother with Linux. I know that will put a lot of people's noses out of joint, but I just don't. Why would you when the Pro-level software works great in XP and is a tweaking nightmare in Wine and *buntu?

Love my Buntu but the line is drawn, for me at least. Is there a Reason? Only if it's Reason Adapted. ;)

---

### Post by CrocoDuck on 2012-08-08
> **Bluphx said:**
> Yo yea the info help'd a lot, thanx. For live DJ'ing I think I'm going to stick with ableton live and my novation launchpad, but am excited too test studio for more the recording side of things.

I finally got a 64bit version to install on the computer (Raid 0 was my problem, turned raid off n just treating as 2 separate HDs) but the drivers aren't there for my MemoryStick/SD Card so will have to test swap-space later. (and too answer your question bucky yea I was asking if Thumbdrives/SD/MemoryCard was a good option for swap b/c i know sometimes the bus speed for xfering data can be slower than normal and actually end up causing more lag)

I'll have to try out the DAW you mentioned. Im not emotionally attached to any DAW other than Ableton Live (for playing live and clip launching for recording)

Last noobish question can does VM or WINE utilize swap-memory (I know VM you can set the max ram usage but don't know about WINE)?

As Wine and Virtual machines are programs that runs under a OS, the swap memory will be used how and when the OS is configured to do it.
Actually there is some audio programs that runs great under wine+wineasio (Reaper, for example). Those program could be very usefull, expecially if you need to run native windows VST together with linux programs. I have a copy of Ableton Live (it came with my Keystation) and I've installed it on a VM, but if you need it to perform live latency will be an issue (and maybe sample loss and/or some kind of digital distortion too, depending on your computer performances). You see, not good for DJ'ing. Even if I never tried to run Ableton Live or Protools with wine+wineasio (I've installed only NI's Bandstand and GuitarRig on my full linux pro audio machine. They works very good but I think I don't used them for a year:P) I think is better to run those programs in a real windows environment, because they are complex. When I was usually use Nuendo, Sonar and Audition I was usually setup my system with a dual boot, as Bucky Ball does. I think that linux (with his native audio programs) is a great audio environment but, as always, if you need to run a lot of applications that are not linux-native, even if a lot can be done to run them good under linux too, the best idea is to choose to run them in their native architecture.

---

### Post by Sylos on 2012-08-08
> **Bucky Ball said:**
> 

For pro A/V stuff I just don't bother with Linux. I know that will put a lot of people's noses out of joint, but I just don't. Why would you when the Pro-level software works great in XP and is a tweaking nightmare in Wine and *buntu?



Because all that pro-audio software costs thousands - as a hobbyist I couldnt afford it. Would love omnisphere - cant shell out that sort of cash on a hobby (lets be honest, playing in my spare time I wouldnt even scratch the surface of that kind of software).

And of course it means I dont have to run windows - which annoys the hell out of me at the best of times.

Linux audio may be a little behind the pro software in some respects (as you would expect for FOSS) but I look at it this way - I still love the albums I have that were recorded circa 2000 (in fact many are still my favourites). I dont think the recording sounds poor etc - and linux audio offers me capabilities comparable to those used for those recordings (excepting standards of mic, cable, musician, producer etc).


Anyhow, Im not trying to start and argument (if I was running a pro studio I may actually follow the same path). Horses for courses as they say. 

Cheers

---

### Post by maciekpruski on 2012-08-08
Hi, I can't help you with point 3 but can say a little about 1 & 2

1. my favourite DAW is Renoise. It costs pennies compared to Ableton or other "pro" stuff. It may seem weird/limited at first glance but it just isn't. Actually working with Ableton was a real pain for me and renoise really opened things up for me. definitely worth checking out. If you buy the license you can use it on any system, including windows, so it is valuable even if you don't stick with Ubuntu. 
Ardour is also cool for more traditional multitrack recording/editing. 
The cool thing is that you can route signals from one program to another using Jack

2. as previous posters mentioned getting soundcard to work can be plug'n'play or really hard. look around the alsa matrix and see if your gear is supported. also use search function here, it probably was discussed. and take some time reading about linux audio to avoid embarrasing mistakes. I for example thought my soundcard wasn't supported while I simply didn't know how to configure stuff in alsamixer and jack:P
I highly recommend searching "sound troubleshooting" in this forum for amazing step-by-step guides

---

### Post by Bucky Ball on 2012-08-08
> **Sylos said:**
> Horses for courses as they say. 

Cheers

+1. My main reason for a lack of interest in the Linux audio path (I do use Kino for rough cuts of raw vid) is I just don't have a month or six spare at the moment to set up a Linux audio box and get my head around what's available and how to do what I already do now with XP. Performance is not an issue. What I have twiddled with seems great in that respect. (I just bought a USB TV tuner. Not quite pro but it DOES work better in Linux, once I actually got it up and scanning channels.) ;) 

Hopefully over christmas I'll have time to have a better look at the Linux audio world (I've had UStudio installed on the desktop since 8.04).

---

### Post by CrocoDuck on 2012-08-09
> **maciekpruski said:**
> Hi, I can't help you with point 3 but can say a little about 1 & 2

1. my favourite DAW is Renoise. It costs pennies compared to Ableton or other "pro" stuff. It may seem weird/limited at first glance but it just isn't. Actually working with Ableton was a real pain for me and renoise really opened things up for me. definitely worth checking out. If you buy the license you can use it on any system, including windows, so it is valuable even if you don't stick with Ubuntu. 
Ardour is also cool for more traditional multitrack recording/editing. 
The cool thing is that you can route signals from one program to another using Jack


I forgot to say this thing: if open source software doesn't fit your needings (I think that open source is getting very cool, having little to envy to commercial software at now) commercial audio software for linux actually exist, and could be cool for you!

---

