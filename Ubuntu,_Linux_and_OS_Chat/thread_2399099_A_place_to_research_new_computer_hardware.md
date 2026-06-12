---
title: "A place to research new computer hardware?"
date: 2018-08-21
forum: Ubuntu, Linux and OS Chat
---

### Post by SagaciousKJB on 2018-08-21
My computer is getting pretty dang old, but I still do quite a lot with it.  Some days I just notice it getting pretty laggy.  I run security cameras on it, a home theater, a DVR for over-the-air programming, and a couple of VirtualBoxes. I run that all on top of browsing the web, photo editing, and pretty mundane average-computer-user tasks. I don't currently watch or have much HD content, but it's getting kind of hard to avoid, so I'd like something setup for HD content. Also hoping that I can avoid some of the heat output and energy consumption with newer hardware.

I just really don't know what's out there now, and what fits my needs.  A lot of people when you talk about wanting a new PC just go full overboard and think I need some kind of gaming beast, but I'm fairly sure I can be happier with a lot less.  On the other hand, I don't necessarily want to buy "budget" or "value" hardware that isn't going to last very long, or will be obsoleted very quickly.  I mean, my hardware now is not exactly top of the line nor was it ever, but it's lasted me nearly 10 years so I think I did a pretty good job picking it out.

Anyway I figured I'd get better answers here than other types of forums because most other PC hardware types of forums are populated by Windows users ( for obvious reasons ) and then that tends to lead to suggestions more from gamers or people with a need for much more powerful systems.

Meanwhile, Linux users are pretty adept at eeking out long lives out of underpowered systems, and I just trust that you folk could recommend me something and more accurately project that it will last me another 10 years.

Basically all I think I really want/need is...

A quad-core or higher processor
8 GB or more of RAM
4 TB or more of HDD space
USB 3.0 or eSATA so I can connect old drives without having to put them into the PC
A Blu-Ray Drive since DVDs are getting rarer
A Graphics card capable of 720p tv-out with a 1600x1200 main screen ( not even a challenge from what I've seen, but I wanna save some money here)


That's pretty much it.  I'm not sure if I'm asking for too much, or perhaps even too little?

Current specs...

Phenom 9950 BE Quad-Core
6 GB PC6400 DDR 2 Ram
3.5 TB of HDDs connected to SATA 3.0 GB/s
A DVD-ROM/RW
A NVIDA GeForce 7950 running 1600x1200 main screen and 1024x768 TV-Out

SO yeah not gonna be too hard to top, I think most of my cost will come with the RAM and the HDDs and otherwise I'm guessing I could probably buy any random bargain/bare-bones system and be happy with the processing power in comparison?  The last time I even looked fore bare-bones systems, I couldn't find any, so I don't know if I was looking in the wrong place, or I'm just out of touch with the way the market is now.

Anyway, thoughts, suggestions, pointers to other places I should research?  I'm in no real hurry, so I'd like to read up and make sure I can avoid decisions I'll regret later on.  Case in point: The Phenom.  Had I actually read benchmarks at the time, I'd have realized the Core 2 line Intel had was MUCH better, so I want to avoid a pitfall like that again.

---

### Post by TheFu on 2018-08-21
So, the passmark (a commonly used benchmark) for your current system is about 3000.  My 2015 Core i3 chromebook is a little faster, to give you an idea. 

I'm with you on making a system last, though we have very different uses.  My "workhorse" system is a 1st Gen Core i5-750 from 2010.  I've been looking to upgrade it, but RAM prices have stopped me.  I want a CPU with less than 65W and in the $170 or less price.   The best bang-for-$ in that area is an AMD Ryzen 5 2600.  With that picked out, you can work backwards into a motherboard and compatible RAM.  I won't add a new GPU,  since mine isn't going to be a desktop, if I even put any GPU in.  If you don't care about 4K TV support (and you probably should at this point), all current video cards easily handle on-card video decoding for mpeg2 and h.264 video.  I suspect that the next TV standard in 2022 will be h.265, so getting a card with support for that video codec onboard would be smart too.

If you want TV out, get a card that can put out HDMI or you can buy a cheap  converter to get to HDMI.  Oddly, this isn't automatic since the new-fangled DisplayPort has become popular.

RAM is extremely pricy now.  It is predicted that in 2019 RAM prices will drop 50%, so if you can wait ... Sadly, there isn't a way to use DDR3 that you might have in a new system.  Forced RAM changes are part of the collusion between CPU, MB, RAM vendors.  Also be aware that with Intel CPUs, they effectively ship 1 socket for a year, so upgrading to a faster CPU means getting a new motherboard almost always.  AMD has a much better history with same socket upgrades - AM4 being the current one.  I have 2 AMD systems, but both are dedicated for specific tasks.  All my current server/laptop/desktop systems run on Intel CPUs because the performance/watt for Intel was much better before Ryzen.  Things are different now.

pcpartpicker is useful to find compatible combinations.

Always google for linux issues with any motherboard. I've been eyeing an X470 myself, but I won't buy the parts until RAM gets affordable.

---

### Post by SagaciousKJB on 2018-08-21
> **TheFu said:**
> So, the passmark (a commonly used benchmark) for your current system is about 3000.  My 2015 Core i3 chromebook is a little faster, to give you an idea. 

I'm with you on making a system last, though we have very different uses.  My "workhorse" system is a 1st Gen Core i5-750 from 2010.  I've been looking to upgrade it, but RAM prices have stopped me.  I want a CPU with less than 65W and in the $170 or less price.   The best bang-for-$ in that area is an AMD Ryzen 5 2600.  With that picked out, you can work backwards into a motherboard and compatible RAM.  I won't add a new GPU,  since mine isn't going to be a desktop, if I even put any GPU in.  If you don't care about 4K TV support (and you probably should at this point), all current video cards easily handle on-card video decoding for mpeg2 and h.264 video.  I suspect that the next TV standard in 2022 will be h.265, so getting a card with support for that video codec onboard would be smart too.

If you want TV out, get a card that can put out HDMI or you can buy a cheap  converter to get to HDMI.  Oddly, this isn't automatic since the new-fangled DisplayPort has become popular.

RAM is extremely pricy now.  It is predicted that in 2019 RAM prices will drop 50%, so if you can wait ... Sadly, there isn't a way to use DDR3 that you might have in a new system.  Forced RAM changes are part of the collusion between CPU, MB, RAM vendors.  Also be aware that with Intel CPUs, they effectively ship 1 socket for a year, so upgrading to a faster CPU means getting a new motherboard almost always.  AMD has a much better history with same socket upgrades - AM4 being the current one.  I have 2 AMD systems, but both are dedicated for specific tasks.  All my current server/laptop/desktop systems run on Intel CPUs because the performance/watt for Intel was much better before Ryzen.  Things are different now.

pcpartpicker is useful to find compatible combinations.

Always google for linux issues with any motherboard. I've been eyeing an X470 myself, but I won't buy the parts until RAM gets affordable.

Thanks, given me some good things to think about so far.  One thing that happened with my current setup is that for a long time I only had S-Video out, so I was reluctant to even get a newer TV.  I waited until a friend was giving away his older HDTV and was going to just do a DVI->HDMI cord to that, but discovered my GPU wouldn't support the dual-screen resolutions I wanted setup like that. Luckily that TV still has an S-Video in port, so I just reverted back to the DVI and S-Video setup.

It sounds like I should try to find something with onboard H.265 and 4k support so that I don't get forced into using an older TV for another ten years for lack of input/output support.  I also really want to get into encoding with H.265, is there any chance of getting a card that has hardware based encoding and decoding for H.265 plus 4k support without crossing over the $100 boundary?

That's also good food for thought with the Intel sockets.  I had hoped to be able to upgrade to the AM3 socket Phenoms when I learned they were planning to make them backward compatible, but I don't want to have to flash my BIOS to achieve that--or more succintly, I don't want to wind up having my motherboard manufacturer suddenly decide to stop selling on the consumer level and be high and dry for BIOS updates.  With that in mind I think I'm gonna try to invest some money on the motherboard and go with one of the makers like Gigabyte or Asus that have been around and probably won't disappear.  I'm leaning towards Gigabyte as I really like their features on some of their Intel boards I've worked on.

I also was worried about Linux compatibility.  I was thinking that for that reason it might not be such a good idea to go with bleeding edge hardware?  The Ryzen and X470 looked pretty good to me as well, but maybe one of the AM3 line ups would suit me well too.

---

### Post by QIII on 2018-08-21
For Linux-specific test results and objective reviews, [Phoronix]("https://www.phoronix.com") is a great resource.

---

### Post by TheFu on 2018-08-22
Decoding in the GPU just requires good driver support and a current generation GPU (onboard GPUs do it). This is why a $50 android tablet can playback highdef videos from youtube or amazon or netflix. There was a revolution in video around 2012.  Any modern, mid-range, CPU will encode video nicely.  I've never gotten any GPU support working for encoding. It hasn't been worth the  effort, plus none of my GPUs are new enough to support h.264 encoding.   I really can't help with ideas about any GPUs. They simply don't matter to me at all. For video playback, I use raspberry pi Kodi machines connected to large screens, not computers 98% of the time. And when I do use a computer for video, I'm on vacation or travelling with a chromebook.

I think going with AM3 today would be a mistake, but you haven't mentioned budget. AM3 uses much more power. For less than $500, you can build a 13,000+ passmark system with a Ryzen 2600, if you reuse old parts like the case, PSU, HDDs, and video card.

Gigabyte has ZERO linux support, but that doesn't mean their motherboards don't work fine.  But you need to do your homework, because some do have issues.  I always choose a motherboard with Intel networking, not marvell or realtek. It avoids dumb hassles, IME.  

Avoiding bleeding edge hardware is good, but being 3 yrs behind on a system that will last 10+yrs doesn't make sense either.  X470 isn't really bleeding edge.  It is 2nd generation Ryzen and includes all they learned last year doing X370 for the 1st generation Ryzen CPUs, which had support issues.  Ryzen motherboards are still picky about RAM, but that is getting better.  If I had to build a box today, I'd get the minimum RAM possible and plan to buy 16G next spring/summer.   [https://www.pcworld.com/article/3175005/computers/amd-ryzen-motherboards-explained-the-crucial-differences-in-every-am4-chipset.html](https://www.pcworld.com/article/3175005/computers/amd-ryzen-motherboards-explained-the-crucial-differences-in-every-am4-chipset.html) has a nice overview of the different Ryzen MB setups.

+1 on Phoronix

---

### Post by SagaciousKJB on 2018-08-22
> **TheFu said:**
> Decoding in the GPU just requires good driver support and a current generation GPU (onboard GPUs do it). This is why a $50 android tablet can playback highdef videos from youtube or amazon or netflix. There was a revolution in video around 2012.  Any modern, mid-range, CPU will encode video nicely.  I've never gotten any GPU support working for encoding. It hasn't been worth the  effort, plus none of my GPUs are new enough to support h.264 encoding.   I really can't help with ideas about any GPUs. They simply don't matter to me at all. For video playback, I use raspberry pi Kodi machines connected to large screens, not computers 98% of the time. And when I do use a computer for video, I'm on vacation or travelling with a chromebook.

I think going with AM3 today would be a mistake, but you haven't mentioned budget. AM3 uses much more power. For less than $500, you can build a 13,000+ passmark system with a Ryzen 2600, if you reuse old parts like the case, PSU, HDDs, and video card.

Gigabyte has ZERO linux support, but that doesn't mean their motherboards don't work fine.  But you need to do your homework, because some do have issues.  I always choose a motherboard with Intel networking, not marvell or realtek. It avoids dumb hassles, IME.  

Avoiding bleeding edge hardware is good, but being 3 yrs behind on a system that will last 10+yrs doesn't make sense either.  X470 isn't really bleeding edge.  It is 2nd generation Ryzen and includes all they learned last year doing X370 for the 1st generation Ryzen CPUs, which had support issues.  Ryzen motherboards are still picky about RAM, but that is getting better.  If I had to build a box today, I'd get the minimum RAM possible and plan to buy 16G next spring/summer.   [https://www.pcworld.com/article/3175005/computers/amd-ryzen-motherboards-explained-the-crucial-differences-in-every-am4-chipset.html](https://www.pcworld.com/article/3175005/computers/amd-ryzen-motherboards-explained-the-crucial-differences-in-every-am4-chipset.html) has a nice overview of the different Ryzen MB setups.

+1 on Phoronix

Yeah see I feel like I'm way over my head, so many new things have come out that I don't really know about.  I've been curious about those Raspberry Pi computers, and mini-ATX boards as well.  I use a program called MythTV for watching the media I rip and record, and it uses a backend and frontend system where several frontends connect to a networked backend.  I wonder if having a Raspberry Pi mini computer to put that on and act as a media front-end would be better than worrying too much about a dual-screen setup.  

The budget is kind of an issue.  I don't really expect to actually have funds for this for a while, and maybe not even $500 worth.  I'd love to upgrade to something more capable for like $100-$200, but I just don't know the likelihood that I'll be able to get hardware that will keep me happy for another 10 years at that price range.  ON the other hand, since I've been pretty happy with THIS hardware for 10 years, I don't know that I'm really that demanding.

Had no idea that GIGABYTE had no Linux support, I thought they were one of the manufacturers that were better about that?  In any case I had forgot all about Phoronix, so I'm cruising around looking at the reviews right now.

Just noticed this one...  [https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1](https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1)

It might be moving the goal post a little, but if I could off-load a lot of the services and higher-resource intensive tasks (like media watching and ripping) I do off to a little mini-computer like that, then it would probably make this one a bit quicker for web-browsing and other types of tasks that it's currently lagging with.  Different strategy but it could save me some money.  I would eventually like to get untethered from my desktop again, I had a Chromebook I put Gallium linux on that was great until it died, but I came to really appreciate laptop life.  It seems like these smaller computers and netbooks/laptops are so capable now, a desktop may be impractical for me anyway.

Anyway like I said there's so much new out there I feel like as soon as I decide to go one angle, I'll be overlooking a different angle.

Is there anyway I can look up passmark ratings for popular pre-built systems to get an idea of what kind of hardware out-ranks mine and by what degree?  I know you mentioned I'm about on par with an i3 laptop.  A 13k rating sounds phenomenal if I'm only at 3k, but perhaps I should look at say, 6k rated systems.

---

### Post by TheFu on 2018-08-22
Raspberry pis are playback devices, not do-everything media devices.  The only reason they can handle mpeg2 and h.264 hidef video is the GPU and drivers. The mpeg2 drivers require a license(~ $2).  You don't need the h.264 license, since that is provided world-wide royalty free for any player. A r-pi cannot handle h.265 or 4K video today.  There are other, SBCs (Single Board Computers), which can playback h.265 and 4K video, but those are usually 3-5x more cash.  By that point, IMHO, everyone is better with a $50 Intel CPU which will be 5-10x faster, but there are people for whom silence and size matter more than anything else.  I have a r-pi v2 and v3.  The v2 is connected to our projector system.  We also have a Plex server that will transcode media on-the-fly to h.264 so the r-pi doesn't have to use the CPU for playback.  The only time the mpeg2 license gets used it when we watch live TV on the projector.  We have HDHomerun network tuners which are available to any device on the LAN.  A v3 Pi has a fast enough CPU that it can handle highdef content without the licenses, I think. Don't quote me, since my v3 Pi isn't used for media.

There are mythTV client solutions for raspberry pi systems.  I don't use Myth, so I can't comment on how well or poorly it works.

A $200 Upgrade wouldn't be worth it in my book, but if you could be happy with a $50 motherboard and $160-ish CPU, then RAM would be the only problem (probably), assuming you will reuse everything else.  In general, I look to spend just under $200 for a new CPU when I'm upgrading. MiniATX is fine, assuming the board comes with the extra ports, slots for cards, and capabilities you need.  I have a few MicroITX and miniATX systems.  For me, the big issue with ITX is that an additional NIC requires extra risers to fit and there's only 1 PCI slot.  For the miniATX, it only supports 6 SATA ports, so connecting up extra storage beyond that requires alternatives that aren't as good.

I have built out other systems for $126 and they are fantastic at what they do, but they do not transcode video for me. Too slow.  My Plex Server runs on that machine, but it can't handle transcoding for the Pi and doing batch transcoding of other media concurrently.  Calibre is also running on the machine, as is the house NFS server for all other systems.

Gigabyte Support
There's a huge difference between not working and not being supported. As a Linux user, you already know that.  If you are running Linux, don't call Gigabyte and expect them to help.  That is all that *non-supported* means.


> Is there anyway I can look up passmark ratings for popular pre-built systems to get an idea of what kind of hardware out-ranks mine and by what degree? I know you mentioned I'm about on par with an i3 laptop. A 13k rating sounds phenomenal if I'm only at 3k, but perhaps I should look at say, 6k rated systems. 

Did you try google? It is this amazing tool that finds all sorts of data. Really amazing.  Also, there are many different passmark ratings for Core i3s.  There are some that are faster and some that are slower. That applies to all CPU lines.  Look up the EXACT model CPU, so you don't get burned.  There can be a 6,000 range in passmark scores with Core i7 CPUs, for example.

---

### Post by SagaciousKJB on 2018-08-22
> **TheFu said:**
> 
Did you try google? It is this amazing tool that finds all sorts of data. Really amazing.

I meant do you know of any place specifically, like Phoronix, which would have this data in a more tailored presentation?

Well thanks for your help, I'll go see what I can disseminate from the massive pile of data that is Google then. ):P

---

### Post by TheFu on 2018-08-22
There are basically 2 sites with passmark information.

---

### Post by oldfred on 2018-08-22
Almost all vendors when you call support will immediately say they do not support Linux. It just is not in their scripts for support.
But almost all systems work, but some better than others.

The Phoronix site has a link to this. And you can see other users configurations & performance.
[http://openbenchmarking.org/](http://openbenchmarking.org/)

---

