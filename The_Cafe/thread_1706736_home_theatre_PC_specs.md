---
title: "home theatre PC specs?"
date: 2011-03-14
forum: The Cafe
---

### Post by sdowney717 on 2011-03-14
I was looking at getting an Intel quad core2 775 with 8gb memory and a decent pci-e nvidia card with TV out.

would even the lowest end intel quad core core 2 CPU be ok?

---

### Post by Paqman on 2011-03-14
Yes. For an HTPC (assuming you're using software that's VDPAU capable) then all the work is being done by the graphics card anyway.

My HTPC uses an Athlon X2 4850e chip, and it works perfectly. You don't need heaps of grunt. 8GB of memory sounds like overkill, too. Mine has 1GB (I run XBMC on top of a minimal install of Ubuntu). Not sure what memory requirements for MythTV are, but I can't imagine you'd need 8GB.

---

### Post by LowSky on 2011-03-14
My HTPC:

Phenom II X4 B50
12GB of DDR3 1600 RAM
5TB of Hard drive Space (5 hard drvies of varius sizes)
Nvidia GTX 460

Running plain vanilla Ubuntu with mythtv installed. I run a dual x servers so I can work on one monitor and have my HDTV run mythtv.

Some might call my system overkill, but when you are recording 5 shows at once, playing a recording, and maybe surfing the net at the same time, while someone on the network also watches form another PC... it feels good to know your system is no bogged down.

Now if your going for a single user system, you can skimp on things like RAM and processor speed, and graphics. When you run a multihead media server like I am it all comes in handy.

---

### Post by Dustin2128 on 2011-03-14
That's way overkill in my opinion. My HTPC (standard definition though) has 1GB RAM, Pentium 4,  a GeForce 4 64Mb video card, and approximately 500GB of storage. Storage is the only thing I really wish I had more of.

---

### Post by Paqman on 2011-03-14
> **Dustin2128 said:**
> (standard definition though)

Mine has an embedded Nvidia 8200 and it outputs 720p nice and smoothly. For 1080 you might need something a bit gruntier I guess. But you don't need to go far up the GPU foodchain to get good playback IMO.

> Storage is the only thing I really wish I had more of.

Lol, I actually couldn't find a hard drive small enough for mine. It's got an 80GB drive, smallest I could find, and uses about 4GB of it. Needless to say, my media storage is on the network, not the HTPC...

---

### Post by sdowney717 on 2011-03-14
I want to be able to watch things like this

[http://video.google.com/videoplay?docid=-5918471867139755892#docid=3212648888254086831](http://video.google.com/videoplay?docid=-5918471867139755892#docid=3212648888254086831)

[http://www.cbs.com/primetime/ncis/video/?pid=ZgnMuhuMbYgtoB_f88BHYZR39ZwTC_VY](http://www.cbs.com/primetime/ncis/video/?pid=ZgnMuhuMbYgtoB_f88BHYZR39ZwTC_VY)

and HULU and Netflix
so It will have to be dual booted for Netflix.

It has to have enough power to watch video decently. 
Not choke, like some older cards will.
So I am thinking to put more effort into the video card.
I wont be running this as a media server .
Mostly I want to be streaming video onto the TV.

---

### Post by cariboo on 2011-03-14
My media center pc is atom 220 powered, with Intel 945 graphics and 1Gb ram, it runs XBMC, but it doesn't have enough cpu power to watch 720p files of any sort. I have a file server with 4Tb of storage, so internal storage isn't needed, although it does have a 160Gb hard drive. When I built it 3 years ago 720p wasn't as prevalent as it is now, and as time goes on we should see a lot more 1080p content coming. I plan on building a new one later this year, this time I'll go with at minimum a quad core cpu, 4Gb ram and HDMI out.

---

### Post by Paqman on 2011-03-14
> **sdowney717 said:**
> 
It has to have enough power to watch video decently. 
Not choke, like some older cards will.


I think you'll be fine. Pretty much any card you'd be buying new will have more than enough smash for HD video. Mines pretty rubbish, and it manages fine. Streaming off the internet isn't going to push your card at all, Netflix tops out at 720p and Hulu is only 480p.

---

### Post by matthewbpt on 2011-03-14
That cpu will be an extreme overkill. You can build an HTPC with an Intel Atom processor and an nvidia 9000 series video card which will play full HD 1080p video with absolutely no problems. The video card is the important bit, but you don't even need to spend a lot on that because it's not gaming performance graphics you need. My PC has integrated nVidia 9300 graphics and is able to play any HD files I throw at it perfectly ... I reckon you could easily build a nice htpc for under $200.

---

### Post by SeijiSensei on 2011-03-14
Little machines like [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883103297") are pretty popular as HTPCs.  This has 2 GB RAM, a 250GB hard drive, and an NVIDIA ION chip.  Machines built on the ION platform support hardware decoding of H.264 streams using NVIDIA's VDPAU interface.  Most 720p and 1080p source material should play seamlessly.  Modern Linux media players, like [smplayer]("http://smplayer.sourceforge.net/"), support VDPAU decoding by default.  I'd dual-boot with the existing Win7 if you want to watch Netflix streams or run Win7 in a VirtualBox VM if you can manage the licensing.

Anyone planning on building an HTPC with Linux will find [this forum]("http://www.avsforum.com/avs-vb/forumdisplay.php?f=76") very helpful.

---

### Post by sdowney717 on 2011-03-26
I got my gtx260 card and it does work.
you plug in an svideo cable and configure it.
You can adjust the overscan size since all TV's are slightly different, but it never keeps that setting between reboots.

Now, a couple things, it does play hulu desktop perfectly proportioned.
HOWEVER, full screening a video in the browser, the picture is totally cropped. Is there something I can do about that?
currently the video resolution for the TV out is set to 1024 by 768.

since Hulu desktop fits the screen so well, I know somehow it can be done.

---

### Post by wizard10000 on 2011-03-26
> **Dustin2128 said:**
> That's way overkill in my opinion. My HTPC (standard definition though) has 1GB RAM, Pentium 4,  a GeForce 4 64Mb video card, and approximately 500GB of storage. Storage is the only thing I really wish I had more of.

This.  Unless you're rendering video on the machine you don't need much.

---

### Post by uRock on 2011-03-26
Whatever specs are in my Wii. I don't torrent movies and Netflix doesn't work on ubuntu, so I have no need for hooking my TV to my PC just yet.

---

### Post by sdowney717 on 2011-03-26
made some discoveries comparing full screen flash screen position in windows vista versus ubuntu.

Ubuntu, in order to get flash full screen on the other screen to the right, the TV screen, you need to setup xinerama and a separate x screen

Then the flash will appear full screen on the TV, BUT
the flash video is not properly centered, the top portion is significantly cropped!

Ok, in vista, you can full screen on the TV, and the video is properly positioned not cropped.
So, I am good to go with video running in the browser on windows full screen on the TV.
Really, I plan on this HTPC running windows since I want Netflix.

Anyone know why the flash full screen is cropped badly in ubuntu?

---

### Post by sdowney717 on 2011-04-06
I have some results in on Netflix streaming using silver-light 4 and windows media center.

Basically is is ok, although it tends to drop frames. The result is the motion is not perfectly fluid. It is very subtle, meaning you barely notice it and you can live with it.
I am hoping MS gets on the ball with this for version 5.
I think this is due to silver-light 4 not using hardware acceleration. Version 5 of silver-light will use hardware acceleration.

Hulu is fine. In fact hulu desktop in windows or Ubuntu is fine. Smooth fluid video. I am very happy to see Hulu desktop for Linux work so well.

My ubuntu machine is using a 8400 GS 256 mb PCIE  core2 duo running at 3 ghz

My windows pc is using a phenom x4 quad core at 2.3 GHZ, a gtx 260 core 216 nvidia card with 1 gb memory, and 8 GB of ddr2 memory. and windows 7 64 bit.

my connection is always from 24 to 30 mpbs download so the connection speed is good. I can stream both PC at the same time.

The Nvidia driver for windows you MUST downgrade to 197 OR the svideo out image is too small. The adjustment for desktop size and position for TV is missing and on the Nvidia forums, appears to have a lot of complaints regarding second monitors and TV,** INCLUDING HDTV**, which surprised me. I thought Nvidia would not have such issues.
The Nvidia driver for Linux allows me to increase the TV out size (over scan adjustment) but not position . HOWEVER, reboots that has to be readjusted.
Nvidia has problems with outputting TV as second monitors.
The downgrade to 197 lets me see the picture as intended on the TV. I set it to clone the outputs.

here are some interesting user comments about netflix and how silverlight has ruined it.
[http://timheuer.com/blog/archive/2009/05/20/silverlight-powers-netflix-windows-media-center.aspx](http://timheuer.com/blog/archive/2009/05/20/silverlight-powers-netflix-windows-media-center.aspx)

I installed ie9 since Hulu is offering a free month with it.
There was an update specifically mentioning improved streaming. It did improve it. (KB2454826)
[http://www.microsoft.com/downloads/en/details.aspx?FamilyId=c6760e93-ce84-4cce-91cf-30cce0668de7&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyId=c6760e93-ce84-4cce-91cf-30cce0668de7&displaylang=en)

I was reading some people call this judder.
lot of good info written into the discussion on this site.
[http://www.projectorcentral.com/judder_24p.htm](http://www.projectorcentral.com/judder_24p.htm)

---

