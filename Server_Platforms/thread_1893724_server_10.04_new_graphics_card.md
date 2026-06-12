---
title: "server 10.04 new graphics card"
date: 2011-12-10
forum: Server Platforms
---

### Post by siegemaster on 2011-12-10
Hey there! First off, I'm new here in these forums, and I decided to check it out because I'm having a problem with a new graphics card that I installed, and figured I would see if anyone on here could help me out.

So I have this server to run XMBC off of. It used to work with the Nvidea 8600 i got quite some time ago, but now I got a new(er) radeon hd 4350 card that I wanted to get to work. 

I have tried installing and configuring this driver: 

xorg-driver-fglrx

but I couldn't seem to get it to work with it. So what I have done now is purge fglrx and deleted my xorg.conf. Then I can get my server to fully boot right, but XMBC won't run now because there is no OpenGL support. 

Am I trying to install the wrong thing? From what I read, fglrx seems to be deprecated, but that's all I came across while doing google searches. 

Thanks for your help,
-Siege

---

### Post by papibe on 2011-12-10
Hi siegemaster. Welcome to the forums.

First of all, if it isn't to late, I would recommend getting an Nvidia card. This is is because they are much easier to set up on Ubuntu. Also, it easier to get video hardware acceleration for HD videos.

I don't have experience with ATI cards, but these couple of threads in the XBMC forums could be interesting for you: [this]("http://forum.xbmc.org/showthread.php?t=106898&highlight=ati+vaapi") and this [other]("http://forum.xbmc.org/showthread.php?t=80940&highlight=ati+vaapi") one.

Regards.

Edit: I just found [this basic]("http://ubuntuforums.org/showthread.php?t=1893566") one (before even considering XBMC)

---

### Post by siegemaster on 2011-12-14
Thanks for the response papibe. Sadly, I it is already too late to get an Nvidea card unless I want to spend more money, which I am actually debating at this point. I have had no luck what-so-ever with this card and drivers. 

Thanks for the links. I took a look at them, and followed their steps, but it doesn't seem to work for me. 

Do you know of any good links to installing Radeon's proprietary drivers from their site?

That is probably my last ditch effort to trying to get this to work. If I can't get that, then I will probably just put my old 8600 back in until I can spend more money on a newer Nvidea card. 

Thanks,

-siege

---

### Post by arrrghhh on 2011-12-14
> **siegemaster said:**
> Thanks for the response papibe. Sadly, I it is already too late to get an Nvidea card unless I want to spend more money, which I am actually debating at this point. I have had no luck what-so-ever with this card and drivers. 

Thanks for the links. I took a look at them, and followed their steps, but it doesn't seem to work for me. 

Do you know of any good links to installing Radeon's proprietary drivers from their site?

That is probably my last ditch effort to trying to get this to work. If I can't get that, then I will probably just put my old 8600 back in until I can spend more money on a newer Nvidea card. 

Thanks,

-siege

I'm confused, why are you putting XBMC or a gfx card in a Server..?  I imagine you don't actually have Ubuntu Server installed...

Googling that card turned up this post - [http://ubuntuforums.org/showthread.php?t=985774](http://ubuntuforums.org/showthread.php?t=985774)

---

### Post by siegemaster on 2011-12-14
> **arrrghhh said:**
> I'm confused, why are you putting XBMC or a gfx card in a Server..?  I imagine you don't actually have Ubuntu Server installed...

Googling that card turned up this post - [http://ubuntuforums.org/showthread.php?t=985774](http://ubuntuforums.org/showthread.php?t=985774)

Thanks for your response arrrghhh. I put XBMC on Ubuntu Server 10.04 because I wanted to build a central media server for my apartment. I didn't want to be limited by just using the XBMC live cd however, because I planned on using the server for mysql and apache as well. Hence my decision to put it onto Ubuntu Server. Since it is foremost a media server, I put a graphics card into it so that I can decode and watch media on my television. This server was mainly thrown together from spare pieces I had laying around, hence the old hardware (Nvidia 8600). I may be new to this forum arrrghhh, but I am not new to Ubuntu. I know what I have installed. 

I do appreciate the  link though. I will need to try those suggestions from the link when I have some more time.

---

### Post by arrrghhh on 2011-12-14
> **siegemaster said:**
> Thanks for your response arrrghhh. I put XBMC on Ubuntu Server 10.04 because I wanted to build a central media server for my apartment. I didn't want to be limited by just using the XBMC live cd however, because I planned on using the server for mysql and apache as well. Hence my decision to put it onto Ubuntu Server. Since it is foremost a media server, I put a graphics card into it so that I can decode and watch media on my television. This server was mainly thrown together from spare pieces I had laying around, hence the old hardware (Nvidia 8600). I may be new to this forum arrrghhh, but I am not new to Ubuntu. I know what I have installed. 

I do appreciate the  link though. I will need to try those suggestions from the link when I have some more time.

Well, assuming I'm following this correctly - the TV is directly plugged into the server, correct?  So you would need a DE to manage XBMC.

Why not just install Ubuntu Desktop?  Kinda lost as to why you installed the Server edition, only to taint it with a DE :p.

---

### Post by siegemaster on 2011-12-15
> **arrrghhh said:**
> Well, assuming I'm following this correctly - the TV is directly plugged into the server, correct?  So you would need a DE to manage XBMC.

Why not just install Ubuntu Desktop?  Kinda lost as to why you installed the Server edition, only to taint it with a DE :p.

Lol, no you are correct. The TV is directly plugged into the server. In hindsight, not the most amazing decision to put it onto server edition, but I didn't know much about the server edition (only knew desktop edition), and wanted to learn more about it. Instead of Googleing the differences between the two, I decided to dive right in. So I may know what have installed, but I was a bit ignorant at the time of installation :D

So at the moment, I am trying to install the drivers from amd's site. Going all right at the moment, and have only run into a small hiccup along the way. For some reason, /etc/ati/control was not installed, nor was the /etc/ati directory even made. Might be broken packages I think? Going to try to purge, then check for broken packages, and reinstall. hopefully I will see a difference there. As soon as finals are over, then I can really focus on this problem.

---

### Post by siegemaster on 2011-12-21
So unfortunately, I was unable to get this working. I ended up putting my old 8600 back in just so that XBMC can function graphically again. Going to be buying a 430 gt as a replacement soon. 

Thanks for all the help on this problem.

---

