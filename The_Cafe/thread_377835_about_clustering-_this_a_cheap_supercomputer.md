---
title: "about clustering- this a cheap supercomputer?"
date: 2007-03-06
forum: The Cafe
---

### Post by billdotson on 2007-03-06
I have heard of people getting a bunch of older computers like 500MHz processors even and linking them together through a LAN and using them as a supercomputer.  How exactly does this work? Is it only possible with Unix/Linux OSes?  Can any program utilize this?

So say I wanted to attempt to build one of these supercomputers.. where would you recommend I find those old computers?

Also, computers that old.. how would you set up a LAN with them.. as I doubt they have ethernet ports?

If I can figure out how to find enough old PCs and figure out how to link this up maybe I will donate it to some organization or sell it off to a business or something.

here is a website I was looking at earlier: [http://www.cacr.caltech.edu/beowulf/tutorial/building.html]("http://www.cacr.caltech.edu/beowulf/tutorial/building.html")

---

### Post by K.Mandla on 2007-03-06
I've looked into this, but never actually done it. I know [OpenMosix]("http://openmosix.sourceforge.net/") (if I remember right) is the OS of choice for a cluster system. 

The issue for me, as I saw it, was that the multiprocessor effect was only useful if you had a single, large-scale number-crunching task that could be farmed out to several machines over a period of time. So average applications like word processors or browsers wouldn't see much benefit. But rendering in Blender, supposedly, would. Someone correct me if I'm wrong, or if that's changed.

If you want to buy old computers like that, check out [http://www.publicsurplus.com/](http://www.publicsurplus.com/) ... they've got Pentium II-500Mhz machines by the **palletload**, and the bids aren't usually too high. You get to transport them, though. :shock:

Aside from that, look at yard sales, want ads and local thrift shops. Harass your local IT department into giving you their junk (my IT crew has boxloads of old junk they won't give me because they're afraid they'll need a 32Mb stick of PC66. :roll: ) If it's so old that it has no value on ebay, it'd probably be perfect for a cluster.

Give it a shot. It's always worth the effort. Let us know how it goes. ;)

---

### Post by OffHand on 2007-03-06
Seriously... how much power do you need? Processors are amazingly fast nowadays.
I would say today's desktops are already small supercomputers.

---

### Post by hardyn on 2007-03-06
the cluster systems wont really behave like one big powerful computer, because networks are so slow when compared to FSB speeds, the only way that the clusters become efficient is if each computer is given a very discrete task that can be assbled after a LONG period of time.  such as animation rendering.  each computer can render a frame, save, render anther frame, then one machine assembles them at the end.  its not going to behave like a SMP system at all.

---

### Post by Anthem on 2007-03-06
If you're mixing and matching discarded hardware to save money when building a supercomputer, just realize that you're going to pay out the wazoo for electricity.

Long-term, a properly-built beowolf cluster is probably cheaper than picking up discarded computers and cobbling them together.  But it's probably cheaper to rent cycles from somebody else's grid.

Do you need that power for anything in particular?  Or is it just for bragging rights?

---

### Post by Bezmotivnik on 2007-03-06
> **Anthem said:**
> If you're mixing and matching discarded hardware to save money when building a supercomputer, just realize that you're going to pay out the wazoo for electricity.
Never mind the expense and major hassle of legally disposing of this trash, which is really shocking in California.

Old computers are nothing but toxic waste.  They consume far more electricity than they are worth (so they're ecologically offensive there) if they are still running, and they are (allegedly) a biohazard to dispose of if they're not.

---

### Post by billdotson on 2007-03-06
I mean I really just want to try and do something new and this sounds like a fun and interesting networking feat.  I already know of one PC at the local church that I can probably get and I would like to get 3 or 4 other ones.  If I did get it up and working I would probably use it but not much as I have a system with the following specs:
   Intel Core 2 Duo E6600
   Corsair XMS2 DDR2 800MHz RAM (dual channel)
   nVidia 7800GT 256MB PCI Express x16
   Asus P5B Deluxe/Wi-Fi AP edition
   Creative Soundblaster Audigy 4 
   Antec TruePower Trio 550watt PSU
   Seagate 7200RPM 250GB SATA HDD
   USB 2.0 external 300GB Maxtor HDD

and I can do anything that I need to do.  Encoding a video that is about 2 hours long (like if I recorded a movie off of cable using my DVD recorder) into a xvid w/ avi container or mpeg-2 file takes about an hour assuming I transcode using two-pass instead of one, and I can play all my Windows games maxed out as of right now ( I have not upgraded to Vista or a fancy Direct3D10 videocard and do not plan to.  When DX10 is the gaming standard I will probably just bite the bullet and only play games on the X360)

Really I just want to do something fun with it.  I might boot it up every now and then to just be like " yeah this is cool, it is 4 computers working together" and then use it to transcode/encode some videos or something.  If I have a friend over or something they can use my PC to play games and I will just use my cluster to do some video work or I will just unplug all the other PCs and just use the frontend one to surf the internet or something. 

I should be able to find old PCs around the community that people do not want, as I think I have already found one but really this isn't an attempt to get a powerful, "modern" computer to play games on or something.  It is just something for me to do for fun and to hopefully learn something/more about networks, Linux, etc.

If I have all the computers hooked up by ethernet I should still be able to use them in unison for programs shouldn't I.. or will I just most of the time be running off one of the machines unless I am encoding a video or something?

I really don't understand what you mean by making a properly maintained Beowulf cluster as opposed to getting old PC and hooking them together.  Apparently a beowulf cluster isn't just a bunch of PC's put together??

---

### Post by punkinside on 2007-03-07
Actually its a bit more complicated than that. A friend of mine is doing his thesis on distributed file systems, the oil company here is building a medium sized cluster (something in the order of 1000 PIII machines) to make some sort of calculations and the university is very involved in the whole thing, using all free software. 

Theres some GNU software called "gluster" or something like that that basically makes all of the computers behave like one big file system. Then theres another program called Glight or something like that  that helps manage distributed calculations. all this is only what I hear from him, I don't have a clue about how any of this is spelled... I'm more into software engineering.

All in all, its not like you just hook a bunch of computers together and do :

```
sudo apt-get install cluster
```

I don't think you can make it your "weekend project" unless you're really serious about learning a bunch of stuff, and installing another whole bunch of stuff. In the end I don't think its worth it just to have them sit there and go: cool.

---

### Post by troymcdavis on 2007-03-07
> **punkinside said:**
> All in all, its not like you just hook a bunch of computers together and do :

```
sudo apt-get install cluster
```

[ParallelKnoppix certainly does project itself as being that easy]("http://idea.uab.es/mcreel/ParallelKnoppix/ParallelKnoppix.html#Documentation_"). 

[Tutorial here.]("http://pareto.uab.es/mcreel/ParallelKnoppix/Tutorial/Tutorial.html")

---

### Post by hizaguchi on 2007-03-07
Like has been said here, the network speed and other factors contributing to the computers communicating with each other is a huge bottleneck.  Aside from that though, alot of software isn't really designed to take advantage of a distributed computing environment.

If you had some application for heavy number crunching, and you had software to run it on that was designed for parallel computing, and you had several fastish computers on a fast network, then yeah, there's reason to build a cluster.  But for just encoding video and stuff, right now I'm pretty sure one fast processor is still faster than a slower dual core processor, and that's without the network bottleneck.  You'd probably see some improvement on a cluster if all of your computers were fast enough to outweigh the network's speed, but since you're wanting to use older hardware you don't even have that on your side.  You'd have to make up for it with *lots* of nodes, and by "lots" I mean "I hope you're not attached to parking your cars in the garage because we need that space for a ton of old computers."  And that space thing is the real killer here.  Even if you had the hardware for free and the time and willpower to install an OS and the cluster-related tools on 30 or so computers, you'd still have to find somewhere to put them.

You could do it, even using Ubuntu, I'd say, on just a few old machines, for novelty.  You'd just need the hardware, an encoder that can run parallel on the nodes, and alot of patience.  Just don't go into all that trouble expecting it to be any faster than (or even as fast as) just encoding it on your desktop.

---

### Post by billdotson on 2007-03-07
so if I just found like 4 computers or something it wouldn't be worth the time + effort + possibly money (for PCI ethernet cards to hook them together) to get them setup as a cluster?  I am mainly doing it for something that would be both fun and a learning experience.. not really to have them be incredibly useful by having some massive supercomputer that would outperform my Core 2 Duo system or anything.

---

### Post by troymcdavis on 2007-03-08
Time: 5 minutes to set-up with ParallelKnoppix. However, you might end up spending hours just exploring/discovering.

Effort: Depends on your overall level of competence. Everything beyond what we've posted here will require a little research.

Money: At newegg, you can get a switch for $11, Linux supported network cards for $4 a piece, so at most that's $40 with ship. But any computer you ever find should come with a LAN port standard, so you're probably looking at $15.

Fun/learning experience factor: Priceless.

This would definitely be something fun to set-up, if you're into "setting things up", which is undoubtedly an attribute that a small minority of the human race possesses. What's difficult is finding software that can actually take advantage of it. [Here's a list of software that can take advantage of it]("http://www.clusterbuilder.org/pages/software/applications.php") (look to the submenu at the left... that site also has a lot of good info). If you're feeling philanthropic, there's any one of the [BONIC projects]("http://boinc.berkeley.edu/").

I've heard that the Linux kernel is just good at splitting up tasks, so you could just try running a bajillion applications at once.

---

### Post by billdotson on 2007-03-08
now I just have to find 4-5 old PCs that nobody wants anymore... hmm

I guess I am going looking around for some old PCs.  Hopefully I can get a small 4-5 PC cluster set up to where it would actually work pretty well.  Even a PIII 1GHz can run a web browser.. just depends on the RAM it has got.. but I can try those cluster apps also.

Let's hope I can find them.. then I can start my cluster :)

---

### Post by PatrickMay16 on 2007-03-08
> **billdotson said:**
> If I did get it up and working I would probably use it but not much as I have a system with the following specs:
   Intel Core 2 Duo E6600
   Corsair XMS2 DDR2 800MHz RAM (dual channel)
   nVidia 7800GT 256MB PCI Express x16
   Asus P5B Deluxe/Wi-Fi AP edition
   Creative Soundblaster Audigy 4 
   Antec TruePower Trio 550watt PSU
   Seagate 7200RPM 250GB SATA HDD
   USB 2.0 external 300GB Maxtor HDD

Keen to find any opportunity to show off?

---

### Post by hizaguchi on 2007-03-08
> **billdotson said:**
> so if I just found like 4 computers or something it wouldn't be worth the time + effort + possibly money (for PCI ethernet cards to hook them together) to get them setup as a cluster?  I am mainly doing it for something that would be both fun and a learning experience.. not really to have them be incredibly useful by having some massive supercomputer that would outperform my Core 2 Duo system or anything.

It's up to you whether it's worth it or not.  I don't think it'll be any faster than your desktop other than *possibly* for programs that require alot of calculations and very little communication (and even then not significantly faster).  And in all likelihood it will be slower than your desktop for most tasks.  But, as long as you aren't just looking for performance, that doesn't mean it wouldn't be worthwhile to play around with.  It'd be an interesting learning experience if nothing else.

---

### Post by punkinside on 2007-03-08
> **troymcdavis said:**
> [ParallelKnoppix certainly does project itself as being that easy]("http://idea.uab.es/mcreel/ParallelKnoppix/ParallelKnoppix.html#Documentation_"). 

[Tutorial here.]("http://pareto.uab.es/mcreel/ParallelKnoppix/Tutorial/Tutorial.html")

That certainly looks good. I won't know what to say until I ask that friend of mine.  I see its meant to be temporary as its a live CD. That might be just what you need if you're trying to make a cluster for fun.

---

### Post by billdotson on 2007-03-08
PatrickMay16: I was not showing off. I was saying my system specs to illustrate the point that my PC does everything I want it to and that the only reason I wanted to put a super PC together was to do it for a learning experience.

---

### Post by punkinside on 2007-03-08
It is unlikely it'll be a super pc. 

As a learning experience though, its great :)

---

### Post by Zinnin on 2007-03-12
I tried out setting up open mosix on a couple machines last weekend, and it was a blast, once I got it configured correctly I did see a power increase in normal computer because openmosix is designed to work with any program.

---

### Post by billdotson on 2007-03-15
so you had a perf. boost on normal applications like a web browser or a word processor??

So is that because Open Mosix allows for programs to do that or only includes programs that take advantage of the other PCs on the LAN?

well if what you say is true and I can get a good perf. boost using open mosix I need to look around for a few old PCs that nobody wants.
I do have a question though.. is OpenMosix a pretty difficult distro compared to say Ubuntu?  I ask because I am new to Linux and have only been using it for ~6 weeks and do not yet know how to do alot of things Linux is capable of.

---

### Post by tutomlin on 2007-04-05
Just thought I'd throw in my $.02.

I haven't actually put together a cluster but I'm looking into it strongly, and I have a couple of comments about openMosix:  First, as far as I can tell this is not really a "true" cluster in the sense that most newb's like myself think of one.  It's really designed to be a load sharing system that let's programs "migrate" from one system to another.  so if you tend to have a bunch of stuff running all the time this could speed things up since, firefox would be off on one computer rendering video on another etc.  But for the most part you shouldn't see big performance increases running one task on a single 1Ghz system versus on an openMosix cluster of 5 1Ghz systems.  That having been said I still think it's pretty cool.

One last point is that as of now openMosix is only available for the 2.4 kernel series (2.6 support is still in the alpha stage apparently), so you'll have to either install a new 2.4 series kernel in your current system or get one of the old distribution cd's that uses a 2.4 series kernel and fresh install from that.

If you're interested in what I tend to think of as "True" clustering where a single job is spread across multiple cpu's check out [http://www.clustermonkey.net/](http://www.clustermonkey.net/) They've got some really nice tutorials including one on a budget cluster: $2000 for an 8 node system using all new parts.  They also have a full series of articles on the basics of clustering which I thought were really nice.  The downside to this setup is that as far as I can tell you're basically running custom code here, which won't speed up any of your typical aps.  (I'm a little new to linux but I don't see a reason you can't set up an openMosix cluster and then force Jobs to distribute like a "True" cluster)

That's about all I've got,
Cheers  :)

---

### Post by tehkain on 2007-04-05
I looked into this too. The only thing I came up with was that getting 8-10 <1ghz machines is pretty inefficient. I would just buy around 3 $32 mobos, a few pentium Ds for about $50, some budget memory, and mount them to some cheap rack with box fans. Then goto a PC junk area and gather PSUs and Hard drives from PCs that families throw out when they only get viruses. You would three times the performance and a eighth of the power bill.


> **K.Mandla said:**
> If you want to buy old computers like that, check out [http://www.publicsurplus.com/](http://www.publicsurplus.com/) ... they've got Pentium II-500Mhz machines by the **palletload**, and the bids aren't usually too high. You get to transport them, though. :shock:
If I lived in Cali I would jump on the $25 1.8ghz systems.

---

### Post by tutomlin on 2007-04-06
I just remembered another clustering resource/program called "kerrighed" [http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)  Like OpenMosix it's a kernel extension that appears to support process migration (I'm not 100% on that since I haven't done a lot of background looking into this particular project)  

The real bonus as far as I can see is that they have a version up and ready that works with the 2.6.11 kernel, which is the main stumbling block with openmosix in ubuntu.

I'm not sure that the graphical user tools are quite as developed as the ones for openmosix but there are a bunch of forum threads here where people didn't quite manage to make openmosix work in the 2.6 kernel, so this might be a better alternative.

If anybody knows more about this project I'd love to hear more, especially if you've ever used kerrighed.

---

### Post by ajt on 2009-01-12
Hello,

I've started a new discussion, to try and bring together threads in different forums about Ubuntu clustering at:

[http://ubuntuforums.org/showthread.php?p=6495259]("http://ubuntuforums.org/showthread.php?p=6495259")

    Tony.

---

