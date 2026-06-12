---
title: "Netflix , in Vista , in VirtualBox"
date: 2008-03-26
forum: Virtualisation
---

### Post by zami on 2008-03-26
Netflix, in Vista, in VirtualBox

I've got Netflix's "watch now" running in Vista, running in VirtualBox, on my Ubuntu laptop.

But!  The movies are so choppy they are pretty much useless.

Has anyone had success with this?  Vista is the only legit copy of Windows I own and I'd rather not have go and... acquire a copy of XP if I can avoid it.  I paid for Vista (okay it was a Christmas present, but someone dear paid dearly for it) so I may as well use it.

Right now I'm running with VirtualBox and I have the "Guest Additions" software installed, and I've fiddled with the VirtualBox settings and tweaked Vista to perform better every which way I can.  Hasn't affected the Netflix video one iota.  

Is this choppyness a video-card issue, since VirtualBox is feeding Vista a virtual 2d graphics card?  Is there anything more I can do with this?

Should I try VMWare or another such program?

Is it my computer?  I might just not have enough oomph to run both operating systems - 
Memory = 1.2GB , Processor = Pentium 1.6GHz

Any suggestions would be much appreciated.  Thanks!

-zami

---

### Post by TransitMan on 2008-03-26
How much memory are you allocating to Vista?
And how much video memory are you allocating?

From the looks of your specs, you might need to bump your system memory to at least 2gb.

I am running XP in VB with a 4gb system, and allocatted 1gb to the OS and 16mb for video. So far so good.

---

### Post by zami on 2008-03-27
Thanks TransitMan!

It's good to know at least it CAN work.   

I've been trying settings all over the board and honestly can't find any rhyme or reason to why some settings are faster then others.

The default video memory is 8, but it goes faster at 16, locks up at 32, and goes fastest still at 7.  (Seven?!  Yes, seven.)

Anything over 1000mb to memory and I've got problems as well, but at least this I understand.

Anyhow I'm stumped now until I can call Netflix because all these changes are showing to Netflix as different computers, so I've been locked out from instant viewing.

-zami

---

### Post by russo.mic on 2008-03-27
So,  It's almost certainly not a Video adapter issue, as your not rendering anything in 3D.  

I would guess it's a network bandwidth thing.  Try looking at the ctrl + alt + delete, then tab networking as your watching a video.  bet it spikes everytime there is a "skip"

Good luck!

Russo

---

### Post by TransitMan on 2008-03-27
> **russo.mic said:**
> So,  It's almost certainly not a Video adapter issue, as your not rendering anything in 3D.  

I would guess it's a network bandwidth thing.  Try looking at the ctrl + alt + delete, then tab networking as your watching a video.  bet it spikes everytime there is a "skip"

Good luck!

Russo

Exactly what I was thinking. Streaming video from NetFlix or any other video source will occassionaly cause a hic-cup in my system, be it in Ubuntu or VirtualBox/Windows. Has nothing to do with the setup, but the traffic on the net.
Also, streaming from NetFlix may get choppy because you may not be the only one watching the show, and the server at NetFlix is having a hard time to keep up.

---

### Post by zami on 2008-03-27
Thanks for the input, both of you!  I'll definitely investigate networking, once I get around to calling Netflix. 

I'm starting to think I just don't have enough ooomph in my machine for Ubuntu+Vista+IE+Netflixplayer.

It's not that it's chunky like watching youtube over dial-up, it's very pixelated and the chunky-ness is even.  It looks like some cheesey time-delay cam-corder effect!

I'll update if I find anything useful out.

-zami

---

### Post by billybag on 2008-04-06
zami, have you confirmed that it works? i ran into the same problem and when i called netflix they told me i can only install it one more time... so the desision is this... reinstall my vista on a seperate partition or install it on my vista in VB...

i would hate to put it on vb only to find that i cant change the video quality
and i would hate to install windows on another partition only because i want to watch netflix....

 Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
2025 MB

any input will be awesome

---

### Post by billybag on 2008-04-06
after some careful thinking. i desided to simply install a seperate windows. I realized that their is always the possibility of me installing a new linux distro or something and having to reinstall virtualbox anyway

---

### Post by Houstonjdd on 2008-06-17
Don't know if anyone is still searching for a resolve on this but I was able to get it to run ALMOST flawlessly in Vista+VirtualBox version 1.6. The only time it ever shows any choppy video is when I open a new application. Then it might chop alittle but not enough to mess up the movie. 

Dual Monitor setup - Vista with 1gb of memory and 32mb of video memory towards the VB. 

2gb of memory total. 

More would be better but heck it's what I got!

:P 

Enjoy! :popcorn:

---

### Post by grimdeath on 2008-06-29
ok, this may be too many hoops for some people to get working but there is a new beta plugin available for windows media player that allows you to do two things:

1. stream to a media extender like a xbox 360 (watch the orphanage the other day, cool stuff on my vista boot)
2. DOWNLOAD a movie and watch it later (this is the important one)

The reason I mention the download is because most people seem to complain about the choppiness of streaming. If you were able to get this plugin working with vista media center on virtual box or vmware, etc.. you could have the option of using the download version and watching it locally which might make for better viewing! At least it works better for me watching downloaded copies on my xbox vs streaming.

I havent had any luck getting vmware installed yet otherwise I might try it myself. The one gotcha is that the plugin require VISTA media center, older versions will not work.
[http://myweb.cableone.net/eluttmann04/projects/vmcNetFlix/default.htm](http://myweb.cableone.net/eluttmann04/projects/vmcNetFlix/default.htm)

The author has been updating OFTEN and maybe someone could tug on his sleeve to look into a native linux option? he is just editing the netflix api afterall

---

### Post by chudder on 2009-08-19
> **Houstonjdd said:**
> Don't know if anyone is still searching for a resolve on this but I was able to get it to run ALMOST flawlessly in Vista+VirtualBox version 1.6. The only time it ever shows any choppy video is when I open a new application. Then it might chop alittle but not enough to mess up the movie. 

Dual Monitor setup - Vista with 1gb of memory and 32mb of video memory towards the VB. 

2gb of memory total. 

More would be better but heck it's what I got!

:P 

Enjoy! :popcorn:

Hi, I realize these posts are a year old but I'm now running into the same problem.  

I've never tried VirtualBox (or anything like it) but I have both an XP and a Vista CD.  My current laptop was designed for vista and both the CDs I have are recovery discs.  

My specs are:
3 GB RAM

Question 1: can I run vista or xp in VB even though they are recovery discs?

Question 2: which one (disc) should I use?  the laptop was designed for vista and it seemed to run well on it

Question 3: What memory, etc should I divert to VB?

Question 4: what are some good tutorials/threads about VB?

Thanks in advance!

---

### Post by danbaatar on 2009-11-20
Can somebody who successfully uses the VirtualBox/Windows method give more details about their hardware and settings?  I'm trying XP on VirtualBox and can’t seem to get decent streaming. While watching, I get one of the cores of my CPU maxed out at 100%.  The video is very choppy and often becomes out of sync with the audio (by as much as a minute).  I'm pretty sure it's not a networking issue (that is I've ruled out non-VM related networking issues), because my MBP will stream the same movies very smoothly and at high quality.

I’ve played with the amount of RAM/VRAM/CPUs allocated to the VM, and enabling/disabling the various other options. Nothing seems to help. I have all of the guest additions installed as well.

My system (for reference):

Mythbuntu 9.10 x64
XP SP 3 on VirtualBox (latest)
Dual Core Intel Celeron E3300 @ 2.50GHz (with VT)
Integrated Intel G4500HD video @ 1080p
2GB RAM

Thanks in advance to anyone that can offer some insight.

---

### Post by redcharlie on 2010-06-24
I had issues with choppy netflix playback with the following setup:

Gigabyte ma78gpm-d2sh (micro atx, ATI Radeon 3200 integrated video)
Athlon X2 4450e (2.3 GHz dual core "Brisbane")
2GB DDR2 800
Cool and Quiet disabled in Bios, AMD-V enabled in bios

Ubuntu 9.04 "Jaunty" hostOS, 32 bit
Windows XP Guest, 32 bit (using Virtual Box) 512MB base memory, 64MB video memory, and AMD-V extensions enabled.

Everything I read indicated I should be able to run Netflix in my VM without any problem. But when I did playback was very poor, stuttering and stopping so often it was quite unwatchable.

Then I accidentally started up the VM with the "null" audio driver, and noticed that Netflix worked fine, no stuttering or dropping frames (although of course I had no sound).

Googling around, I read that pulseaudio has issues here:
[http://ubuntuforums.org/showthread.php?t=1168194](http://ubuntuforums.org/showthread.php?t=1168194)

Sure enough, switching from pulseaudio to OSS (system->preferences->sounds, change to OSS for "music and movies") did the trick, along with changing the sound driver in the VM to OSS. Now netflix works great!

BTW, I also got netflix working w/o any issues on the following:

Asus m4a785td evo-m (micro atx, ATI Radeon 4200 integrated video)
Athlon II X3 435 (Triple core "Rana" 2.9 GHz, 4th core unlocked)
4GB DDR3 1333
Cool and Quiet disabled in bios
Ubuntu 10.04 "Lucid" HostOS, 32 bit
Windows XP 32 bit guest, with Virtual Box, 1024MB base mem and 64 MB video mem

At first I thought that the Brisbane just wasn't powerful enough, since I had no trouble with the Rana. But now I'm thinking that it may be that there are fewer issues with sound in Lucid

---

### Post by jekewa on 2010-09-25
**Executive summary**: moving mapping your temporary files folders to a shared drive instead of a VM drive can help.

I've been a long-time user of Unbuntu, abandoning Windows on hardware some time ago. I swap between VMWare and VirtualBox to run Windows for occasions where I must, since I can do just about everything native on the Ubuntu desktop.

I've got a little bit of horsepower in this system, an AMD Phenom 6-core processor, 8GB of RAM, and an NVidia 8800 video card attached to a pair of monitors (primary 24-inch running 1920x1200, and secondary 20-inch running 1680x1050).

I've mostly been using Windows for testing web sites in Windows browsers, and admittedly for Netflix streaming. For the former, running in a VM with no measurable performance impact, and for a long time even the latter was barely noticeable. 

I recently made a switch to Windows 7 (from XP) and noticed that Netflix got a lot more stutter. I've given my VM 3GB of RAM (when running it rarely breaks 2GB used) and 2-cores (tried with both 1 and 2 thinking maybe Windows SMP overhead was to blame), and I've tried with and without 2D and 3D acceleration enabled. My BIOS is configured to allow full virtualization, so the VM should be running as close to iron as allowed.

I've also turned off the eye-candy in the VM, and tested with the eye-candy off or reduced in Ubuntu (I like the wobbly windows and true transparent terminals), but neither of those seemed to make much of an impact as I tend to run my Netflix video "full screen" in a VM window sized for acceptable performance, and then leave it alone.

I also noticed that the Virtual Box virtual hard drive icon was constantly fluttering and my HDD was constantly churning. I suspected a heavy impact on performance may have to do with my choice of a dynamically sized HDD (machine has a pair of TB drives, and I've told Windows to take only 100GB (and it's only using about 20GB), and I use shared folders for real work and storage. I thought to make a quick change to my system, assigning the TEMP and TMP environment variables and setting my IE temporary file folder to folders on the shared drive. This dropped the HDD activity significantly, and reduced the stutter almost significantly.

I'm unsure if there's other places that could be configured to direct caching off the Windows C drive and onto the shared folder. I've also not tried making a static-sized VM virtual disk to see if that would help. I suspect there will always be a performance hit since you'd always be writing files inside another file. If I had thought ahead I may have been able to leave (or add) a physical partition so the VM would have raw hard drive access, but the shared folder does a fair job. It still suffers a little "network" latency, but it's better than file-in-file access of writing the temp files in the virtual disk.

I mostly blame the new Windows version (and kick myself for migrating and removing my XP VM) as the performance was better on the same physical hardware, in a similarly configured VM, but with the older OS and its related software.

---

