---
title: "Are OS's getting too TOP HEAVY"
date: 2009-11-03
forum: The Cafe
---

### Post by jward3010 on 2009-11-03
I've had this thought in my mind for a long time and I don't know what angle to approach it.

The performance gains that PC's and laptops have made in the last few years have been exponential, unbelievably large. The speed of CPU's, there cache amounts, FSB speeds, memory performance and amount - all of these factors are increasing quickly and the hardware end of things seems incredible.

**But the OS's are still SLOW!**

I say OS's because I'm not just talking about Windows and Mac but Ubuntu as well. There are many factors to this, and I'll address a few:

- On a lot machines I try, X is sluggish and makes the system feel sluggish and always "1 second behind" the user, not the case on a fresh XP install.
- Boot times fluctuate in Ubuntu, Jaunty was great, Karmic has returned back to slow again.
- Kernel's have a huge amount of code in them throughout the lifetime of a system, maybe a lot not needed, can clever discovery software be used to remove the unnecessary?

What is causing this degradation: 
- Are we filling up the constant overhead we get with crud rather than finding efficiencies. 
- Is the reliance on scripting with high level languages slowing things down. I've heard this criticism before in regards Python and Java.
- Do other GUI and compositing systems needed to be used. Should we re-write X, involve it more or less with the kernel etc.
- Linux is 100% customisable to the point we can take the kernel and completely re-write it (not easy but possible) and customise it even to a particular machine with particular hardware, but we don't develop tools to remove the rubbish when it's fully installed.

What are peoples view on this, am I in the right area on this, am I CRAZY!

---

### Post by Icehuck on 2009-11-03
You might want to look into this [http://sta.li/](http://sta.li/) It's a Linux distro from the Suckless guys. They just started it but it will probably end up being pretty minimal and pretty quick. They prefer to stick as close to the Unix philosophy as possible.

Oh and their take on why things are getting slow is located [http://sta.li/](http://sta.li/)

Basically, most developers don't want to write efficient code. They go with what they know and when they come across features and problems they add/fix them in a non optimal way.

---

### Post by s3a on 2009-11-03
Try Debian. Ubuntu works similarly to Debian but Debian gives you more choice on the initial installation procedure to reduce bloat. Alternatively, you can remove things in Ubuntu but I personally find it easier to choose to install things than to track things down to remove them.

---

### Post by Regenweald on 2009-11-03
I agree with icechuck, for an example of efficiently written 32 bit code that runs circles around 32 and 64 bit implementations, check out Haiku.

---

### Post by jward3010 on 2009-11-03
Yes, I agree but I'm being more broad in my argument. Or possibly I'm being very narrow minded in just using Ubuntu systems and it's derivatives (Crunchbang, Xubuntu, Mint etc.) and thinking this is Linux (it's certainly useable Linux). 

I did use Slackware in the past but found a lot of it over my head. Now I think I'd go back and try again.

At the same time I didn't find it monumentally faster than Ubuntu and worse I find Ubuntu similar to XP in terms of performance (in fact XP would have an edge early on, then it would deteriorate and Ubuntu would have a long term edge). Realistically I thought a useable Linux system (like Ubuntu) would have a momentous edge over any Windows system with it being free from closed source created problems and an overtly complicated system of organisation etc. etc. I understand the typical problems with us not having support from hardware manufacturers and basically making our best attempt at our own drivers and so on. But some of the fundamentals of Linux and UNIX are obviously in our favour...

---

### Post by Warpnow on 2009-11-03
You want speed, you lose features. You want features, you lose speed.

Its that simple. Ubuntu is the ultimate for features...not speed.

Yes, you can compile your own kernel and software...or simply use a much more lightweight distribution.

Try gentoo, Slackware, DSL, Puppy, Slitaz. Ubuntu is slow because of its features, not in spite of them.

---

### Post by SomeGuyDude on 2009-11-03
It's worth mentioning that as code is improved/maintained/fixed, trying to completely overhaul it for maximal efficiency becomes a nightmare. Sure you can do that if your code is a few hundred lines long, I'm sure each time a new version of DWM pops out they have no problem keeping it sleek, but something like KDE? Forget about it. Good luck slogging through a few million lines of code for all of the redundancies and bloat.

Jward makes a good point, too. On a fresh install of two systems, I don't really see a huge difference between Linux and even Windows 7. The difference is over the long haul. That without defragging or cleaning the system or doing any kind of disk scanning my computer will be as fast as it was at the beginning with Linux.

---

### Post by hessiess on 2009-11-03
X defiantly should not be in the kernel, Putting stuff into the kernel breaks the extreme modularity of the OS.

---

### Post by Regenweald on 2009-11-03
I don't get the speed complaint though, are we talking about database/or just plain intensive processing tasks, or how fast a program opens? Because Ubuntu is pretty fast with all the functionality it offers and in recent benchmarking done at phoronix, I don't really see any other contenders leaps and bounds ahead(and thusly worth the installation trouble) of Ubuntu. Only one immensely faster is Haiku, and that is alpha software and not ready for my primary desktop.

So how many more milliseconds of response need to be shaved for Ubuntu to be considered fast ?

---

### Post by Dark Aspect on 2009-11-03
I don't notice Ubuntu being slow and my computer is not completely up to date in terms of hardware. I think its just people have all that memory sucking eye candy enabled and than they complain that their speed is not up to par.

Learn to overclock or get a job and buy a new computer.

---

### Post by handy on 2009-11-03
Ubuntu is a heavy weight as it has to try to please as many people as possible; the weight is the cost.

Mint does something different under the hood which makes it a bit faster whilst still offering all the stuff.

There are other distro's that are lighter & let you build in what you want to various degrees.  Though I don't think any of them are a great place to start out with Linux.

Ubuntu/Mint is a great place to start out & stay if you like, in Linux.

The question for any individual Ubuntu user is whether a slight increase in speed is enough to motivate them to go to the trouble of distro hopping in an effort to find a distro that suits them better?

It worked for me, but it doesn't work for everyone. :)

---

### Post by BuffaloX on 2009-11-03
My C64 booted in 3 seconds.
But it didn't have to load anything, everything was mapped directly in ROM.

The Amiga had a boot sequence a bit more similar to modern computers.
It had hardware and drives auto detection and booted in about a minute.

Todays computers are thousands of times faster, but take about the same time to boot.

The Amiga could detect hardware and load a complete preemptive multitasking graphical OS about as fast as a modern computer, and with about the same basic features, and it even had the slowest file system.

I suspect modern PCs have legacy problems with the bus, dating all the way back to the old ISA bus, but I don't know because nobody cares today, we only have one architecture, take it or leave it.

The Bios alone takes some 10 seconds to get ready to actually boot the OS.
This is outrageous, that's longer than the C64 took to show ready.

There really should be only one limitation, and that's the hard-drive spin-up time, which will probably soon be irrelevant, because we switch to SSD drives, and all this boot waiting will be history.

One thing's for sure, PCs are kludges plain and simple.

Anyways Karmic is probably the fastest OS to boot for me since I switched to PCs back in the early 90's.

---

### Post by dragos240 on 2009-11-03
> **Icehuck said:**
> You might want to look into this [http://sta.li/](http://sta.li/) It's a Linux distro from the Suckless guys. They just started it but it will probably end up being pretty minimal and pretty quick. They prefer to stick as close to the Unix philosophy as possible.

Oh and their take on why things are getting slow is located [http://sta.li/](http://sta.li/)

Basically, most developers don't want to write efficient code. They go with what they know and when they come across features and problems they add/fix them in a non optimal way.

Hmm.... didn't they create dwm?

---

### Post by gnuisancev3 on 2009-11-03
i would say Gnome (especially when looking at the 3.x branch), KDE4.x, Windows Vista and 7 and OS X are all getting too top heavy.

Xfce is the heaviest environment i will run.  Openbox and wmii are pretty nice.

---

### Post by gnuisancev3 on 2009-11-03
> **Icehuck said:**
> You might want to look into this [http://sta.li/](http://sta.li/) It's a Linux distro from the Suckless guys. They just started it but it will probably end up being pretty minimal and pretty quick. They prefer to stick as close to the Unix philosophy as possible.

Oh and their take on why things are getting slow is located [http://sta.li/](http://sta.li/)

Basically, most developers don't want to write efficient code. They go with what they know and when they come across features and problems they add/fix them in a non optimal way.
now THAT is cool.   I always loved the suckless guys. dmenu rocks.

---

### Post by jward3010 on 2009-11-04
It might be completely perception on my part, although I doubt it. I'm talking about the speed at which the system reacts, specifically X and metacity and the desktop environment, not the command line (although gnome-terminal has been criticised for it's enormous weight). Opening explorer in XP compared to Ubuntu with Nautilus is slow (not horribly, just noticeably slower) and it feels like it slows down productivity and flow. It's as if Windows keeps you recently opened things in memory for an extra five minutes after you've closed them, because if you re-open a minute or two later it just pops up and thats IT, same with certain KDE. The new

I have used the likes of Backtrack in the past and it absolutely flys, and thats what I compare it to. It also does a lot but it's as if it pre-caches and is just ready.

> Learn to overclock or get a job and buy a new computer.
I know how to overclock, in fact I have an Athlon64 3700+ clocked at 2.53GHz, compared to default of 2.2GHz. I even bought particular Corsair memory (DDR550) so as to give me overhead to do it. I also have a 7800GTX which compiz flys with (although most of the time disabled) but starting a process has an annoying half-second delay, like Nautilus. So wobbling windows around is easy and smooth but opening that window to begin with takes around a second, like there not pre-cached and preload does not help, doesn't seem to anyway.

---

### Post by Skripka on 2009-11-04
> **jward3010 said:**
> 

I know how to overclock, in fact I have an Athlon64 3700+ clocked at 2.53GHz, compared to default of 2.2GHz. I even bought particular Corsair memory (DDR550) so as to give me overhead to do it. I also have a 7800GTX which compiz flys with (although most of the time disabled) but starting a process has an annoying half-second delay, like Nautilus. So wobbling windows around is easy and smooth but opening that window to begin with takes around a second, like there not pre-cached and preload does not help, doesn't seem to anyway.

The reason why things seem slow is because you're running very obsolete hardware.  You're basically 3 generations of hardware behind on every single part in your box.

---

### Post by RiceMonster on 2009-11-04
> **dragos240 said:**
> Hmm.... didn't they create dwm?

By quickly looking at the site, you can see the answer.



Yes.

---

### Post by jward3010 on 2009-11-04
> Basically, most developers don't want to write efficient code. They go with what they know and when they come across features and problems they add/fix them in a non optimal way.

Personally I think this is the case, lots of people can code but doing it efficiently I assume is a difficult task, but in another sense because the workload of Linux is spread out so much it should be an absolute priority. It IS the case with terminal only apps - they are efficient and light, but when it comes to GUI stuff things change. Maybe in the case of Ubuntu it's just one particular pillar, maybe X is the culprit, maybe metacity, maybe Gnome and at the back of it all the programs are rippingly quick.

---

### Post by jward3010 on 2009-11-04
But that destroys the idea of Ubuntu being OK for old derelict PII machines. My computer may be 3 generations back (very fast moving generations) but it was high end for the time and that is pretty much my whole point. The basic system shoudln't require a &#8364;2,500 system - it's only a desktop OS for Linux sake! You should only buy advanced, expensive hardware for specific intensive things like heavy 3D gaming, 3D design, video and audio encoding, frequently accessed database stuff etc.

Most OS's should run like stink on modern basic systems, but the point is they run medicorally on basic cheap systems, slightly better on mid-range and JUST OK on high-end systems. Thats ridiculous! Clean it up!

---

### Post by jward3010 on 2009-11-04
> **Skripka said:**
> The reason why things seem slow is because you're running very obsolete hardware.  You're basically 3 generations of hardware behind on every single part in your box.

I don't agree and that destroys the idea of Ubuntu being used for re-powering (OK, maybe Xubuntu) old derelict PII machines. My computer may be 3 generations back (very fast moving generations) but it was high end for the time and still quick and that is pretty much my whole point. The basic system shoudln't require a &#8364;2,500 system - it's only a desktop OS for Christ sake! You should only buy advanced, expensive hardware for specific intensive things like heavy 3D gaming, 3D design, video and audio encoding, frequently accessed database stuff etc.

Most OS's should run like stink on modern basic systems, but the point is they run slowly on basic cheap systems, slightly better on mid-range and JUST OK on high-end systems. Thats ridiculous! Clean it up!

---

### Post by SomeGuyDude on 2009-11-04
Observation: just because your computer can run a SYSTEM doesn't mean all the APPLICATIONS aren't going to kill it.

Okay, great, you're on XFCE or Openbox or whatever. That doesn't change the fact that if you have Firefox and Pidgin and Deluge and you're editing something in GIMP, your CPU's going to need to have some oomph to it.

---

### Post by jward3010 on 2009-11-04
> **gnuisancev3 said:**
> i would say Gnome (especially when looking at the 3.x branch), KDE4.x, Windows Vista and 7 and OS X are all getting too top heavy.

Xfce is the heaviest environment i will run.  Openbox and wmii are pretty nice.

I agree completely, especially on KDE4.X. I installed it on a 6 month old laptop a few weeks ago (2.4GHz Dual core, 2GB DDR2, Intel graphics), implemented the UXA mode and settings for Intel graphics (before which it really ran bad) and it ran like crap. I kept it on for about 2 days, using constantly, mostly Konqueror and Firefox, occasionally Amarok and it wasn't acceptable at all. Only your principled stand on using Open Source software may have kept you plugging away but it was in no way efficient.

I wonder how an iPod touch with all it's flashiness and effects runs so flawlessly (It does on mine), I know it's probably down to only one type of hardware that it has been optimised for it to the nth degree.

---

### Post by Skripka on 2009-11-04
> **jward3010 said:**
> 
I wonder how an iPod touch with all it's flashiness and effects runs so flawlessly (It does on mine), I know it's probably down to only one type of hardware that it has been optimised for to the nth degree.

That is PRECISELY it.  It is EASY to have a system that runs GREAT-when you only write it and optimize it for 1 VERY specific set of hardware, made to your EXACT specifications, by ONE manufacturer.

Supporting 30+ years of hardware, by gawd knows how many OEMs, is a loosing battle.  Apple realized this around the mid-90s, and cut legacy support.  OF COURSE old hardware runs it terribley in comparison to the new toys.

The problem with Linux, is that you can't just cut the legacy strings.  You have millions of disconnected users/devs around the globe...some wanting to run 20 year old hardware...and getting everyone to agree to only support i686 and above has YET to even happen...Debian and Ubuntu STILL inisist on optimizing 32bit for i386, even though Ubuntu is only officially supported to run on i486+.


PS-Intel drivers are known to have issues

PPS-Kubuntu is known to run like a pig, in case that was the environment where you were trying to run KDE.

---

### Post by jward3010 on 2009-11-04
Thats very true, and I find it with Xubuntu which I'm trying out at the moment. All the heavy Gnome apps are there which means their libraries and everything are loaded when you start them up and basically there is no difference between Ubuntu and Xubuntu in terms of performance.

---

### Post by jward3010 on 2009-11-04
> That is PRECISELY it. It is EASY to have a system that runs GREAT-when you only write it and optimize it for 1 VERY specific set of hardware, made to your EXACT specifications, by ONE manufacturer.

Supporting 30+ years of hardware, by gawd knows how many OEMs, is a loosing battle. Apple realized this around the mid-90s, and cut legacy support. OF COURSE old hardware runs it terribley in comparison to the new toys.

The problem with Linux, is that you can't just cut the legacy strings. You have millions of disconnected users/devs around the globe...some wanting to run 20 year old hardware...and getting everyone to agree to only support i686 and above has YET to even happen...Debian and Ubuntu STILL inisist on optimizing 32bit for i386, even though Ubuntu is only officially supported to run on i486+.

And hardware manufacturers keeping their driver code "cards close to their chests" doesn't help.

---

### Post by Skripka on 2009-11-04
> **jward3010 said:**
> And hardware manufacturers keeping their driver code "cards close to their chests" doesn't help.

Even if they didn't the 6-12 month release cycles of new cards basically ensures that FOSS driver writing is very much a loosing battle.  You cannot even get another generation of cards supported and maintain support for legacy cards--before 2 or more new generations of hardware are released.

---

### Post by jward3010 on 2009-11-04
God I effing know, it ain't an easy battle. Some dudes somewhere (sorry I have no coding experience, just experience in complaining) should take a decent laptop system and work hard on writing Linux into it, make a customised system with efficient code that suits it beautifully, a bit like a MacBook (although I've never tried one enough) or iMac or other Apple products.

I would LOVE to see that happen in the Linux world!

---

### Post by Warpnow on 2009-11-04
> **jward3010 said:**
> 
I know how to overclock, in fact I have an Athlon64 3700+ clocked at 2.53GHz, compared to default of 2.2GHz. I even bought particular Corsair memory (DDR550) so as to give me overhead to do it. I also have a 7800GTX which compiz flys with (although most of the time disabled) but starting a process has an annoying half-second delay, like Nautilus. So wobbling windows around is easy and smooth but opening that window to begin with takes around a second, like there not pre-cached and preload does not help, doesn't seem to anyway.

Download Slitaz or Damn Small linux. 30mbs and 50mbs each. Boot off the live CD, and watch how windows open instantly instead of with a delay.

The delay is caused by reading the hard drive mostly. If your OS is small enough to load into ram you can get rid of it.

There are options to do this with Ubuntu, but you'd need alot of ram.

Alternatively, newer hard drives are much faster in real world scenarios (even if they spin at the same speed), so using a system with a faster hard drive will also solve this problem.

On my machine, text editors, file managers, ect, load instantly, but anything more complex takes that half a second lag you talk about.

Also, your system is like 6 years old. Run an OS from six years ago and I bet it will run alot faster.

---

### Post by Skripka on 2009-11-04
> **Warpnow said:**
> Download Slitaz or Damn Small linux. 

Last I knew, DSL had closed shop, dev wise.

---

### Post by jward3010 on 2009-11-04
> **Warpnow said:**
> Download Slitaz or Damn Small linux. 30mbs and 50mbs each. Boot off the live CD, and watch how windows open instantly instead of with a delay.

The delay is caused by reading the hard drive mostly. If your OS is small enough to load into ram you can get rid of it.

There are options to do this with Ubuntu, but you'd need alot of ram.

Alternatively, newer hard drives are much faster in real world scenarios (even if they spin at the same speed), so using a system with a faster hard drive will also solve this problem.

On my machine, text editors, file managers, ect, load instantly, but anything more complex takes that half a second lag you talk about.

Also, your system is like 6 years old. Run an OS from six years ago and I bet it will run alot faster.
The thing is I have fairly modern hard drives. I'm mostly using 250GB S-ATA II's which when benchmarked acheive around 70 - 90MB/s read/write. The problem is that pre-caching doesn't seem to happen in Ubuntu (even though I have in most cases piles of RAM, up to 4GB on this laptop). There is undoubtedly a problem with hd speeds and modern PC's (maybe the whole PC needs a redesign really) but RAM speeds are amazing and there are buckets of RAM avaialable nowadays even in the cheapest laptops.

I'm also writing in another thread about Karmic and bugginess and the fact that Ubuntu keep adding new stuff and failing to fix old bugs and improve the efficiency of something already stable enough. Some are calling for consolidation releases (bug fixing only releases) and I would add to that efficiency release - Clean up the code as well, strip the crap out in some release and see what happens!

---

### Post by Warpnow on 2009-11-04
> **Skripka said:**
> Last I knew, DSL had closed shop, dev wise.

That's sad. Luckily its useful even if outdated. Slitaz is very nice, too. Better package management than DSL, especially if you don't use the gui wrapper for it.

---

### Post by SomeGuyDude on 2009-11-04
> **Skripka said:**
> That is PRECISELY it.  It is EASY to have a system that runs GREAT-when you only write it and optimize it for 1 VERY specific set of hardware, made to your EXACT specifications, by ONE manufacturer.

Supporting 30+ years of hardware, by gawd knows how many OEMs, is a loosing battle.  Apple realized this around the mid-90s, and cut legacy support.  OF COURSE old hardware runs it terribley in comparison to the new toys.

The problem with Linux, is that you can't just cut the legacy strings.  You have millions of disconnected users/devs around the globe...some wanting to run 20 year old hardware...and getting everyone to agree to only support i686 and above has YET to even happen...Debian and Ubuntu STILL inisist on optimizing 32bit for i386, even though Ubuntu is only officially supported to run on i486+.

This, a million times over.

Linux users seem to expect Linux to not only run on every piece of hardware ever made, but to do so SMOOTHLY on it all, AND still be a slim and sleek system.

At some point the Linux community is going to have to decide on what is best overall. It's only going to get heavier and heavier if people insist on having full support for old P1's with 16MB of RAM all the way up to new hardware, and it's also going to mean throttling potential development.

I'm all for Linux being a system for LOW-END hardware, but if you bought your computer in 1994 and still haven't upgraded... sorry, but you missed the boat. In a day and age where you can get a NEW laptop for $350, still holding onto machines that run in Megahertz and kilobytes is just inexcusable, and demanding that OS's keep their systems built with your limitations in mind is insane.

---

### Post by jward3010 on 2009-11-04
Can I ask how does backward compatibility slow these systems - I mean why can't a kernel detect a certain type of hardware and leave out the crap it doesn't need, how does including support for old stuff actually slow it down?

Are there not optimised kernels, specific ones that have taken a large chunk of old-school out and if not WHY NOT! It seems to me incredibly strange with the unbelievable flexibility of Linux that things like this are not done.

I don't mean that as a criticism, but an actual thing I'm trying to understand.

---

### Post by SomeGuyDude on 2009-11-04
> **jward3010 said:**
> Can I ask how does backward compatibility slow these systems - I mean why can't a kernel detect a certain type of hardware and leave out the crap it doesn't need, how does including support for old stuff actually slow it down?

Are there not optimised kernels, specific ones that have taken a large chunk of old-school out and if not WHY NOT! It seems to me incredibly strange with the unbelievable flexibility of Linux that things like this are not done.

Arch, for example!

Or you could go bananas and do something like Lunar or Gentoo where you build your own kernel.

---

### Post by Skripka on 2009-11-04
> **SomeGuyDude said:**
> This, a million times over.

Linux users seem to expect Linux to not only run on every piece of hardware ever made, but to do so SMOOTHLY on it all, AND still be a slim and sleek system.

At some point the Linux community is going to have to decide on what is best overall. It's only going to get heavier and heavier if people insist on having full support for old P1's with 16MB of RAM all the way up to new hardware, and it's also going to mean throttling potential development.

I'm all for Linux being a system for LOW-END hardware, but if you bought your computer in 1994 and still haven't upgraded... sorry, but you missed the boat. In a day and age where you can get a NEW laptop for $350, still holding onto machines that run in Megahertz and kilobytes is just inexcusable, and demanding that OS's keep their systems built with your limitations in mind is insane.

The Arch Linux April Fool: Dropping 32bit support, really exemplified the problem.  LOTS of folks taking it seriously, suddenly realised that they actually DID have 64bit hardware and that there really wasn't much of a reason for them still to be running 32bit anymore....BUT...it took an April Fool prank to get them to realise this.

---

### Post by jward3010 on 2009-11-04
> **SomeGuyDude said:**
> Arch, for example!

Or you could go bananas and do something like Lunar or Gentoo where you build your own kernel.

I'll give Arch a try, I notice the ISO's are small (around 380MB). And to be honest Ubuntu has given me a good base at this stage to dive into conf files and get complicated so I'll give it a lot of credit there.

> **Skripka said:**
> The Arch Linux April Fool: Dropping 32bit support, really exemplified the problem.  LOTS of folks taking it seriously, suddenly realised that they actually DID have 64bit hardware and that there really wasn't much of a reason for them still to be running 32bit anymore....BUT...it took an April Fool prank to get them to realise this.
I was even surprised when I realised the AMD64 meant any 64-bit architecture yet Ubuntu still call it AMD64. And yes, lots of my machines now run 64-bit Ubuntu.

---

### Post by RiceMonster on 2009-11-04
> **Skripka said:**
> The Arch Linux April Fool: Dropping 32bit support, really exemplified the problem.  LOTS of folks taking it seriously, suddenly realised that they actually DID have 64bit hardware and that there really wasn't much of a reason for them still to be running 32bit anymore....BUT...it took an April Fool prank to get them to realise this.

That was funny. I thought it was even funnier when they switched the site to German for April fools :D.

---

### Post by Skripka on 2009-11-04
> **jward3010 said:**
> 
I was even surprised when I realised the AMD64 meant any 64-bit architecture yet Ubuntu still call it AMD64. And yes, lots of my machines now run 64-bit Ubuntu.

With the Arch April Fool, it was a case of people suddenly realizing that their CPU DID actually support x86_64 instructions.  With Intel's and AMD's different ways of differentiating product lines, knowing for certain requires looking.

---

### Post by Skripka on 2009-11-04
> **RiceMonster said:**
> That was funny. I thought it was even funnier when they switched the site to German for April fools :D.

That was a CLASSIC! :lolflag:

---

### Post by kavon89 on 2009-11-04
Bottleneck in the majority of computers is a slow disk drive, and solid state disks are the solution (but still expensive).

Linus has recently said the Linux kernel is getting too slow/fat. Go use FreeBSD if you're nuts about performance.

---

### Post by jward3010 on 2009-11-04
> Go use FreeBSD if you're nuts about performance.
I did once before, back in my desktop needing days and I was left at the command line. 10 minutes later I formatted the hard drive.

I assume KDE and Gnome we're in there somewhere...

---

### Post by SomeGuyDude on 2009-11-04
> **kavon89 said:**
> Bottleneck in the majority of computers is a slow disk drive, and solid state disks are the solution (but still expensive).

Linus has recently said the Linux kernel is getting too slow/fat. Go use FreeBSD if you're nuts about performance.

That he did, and my response is still the same: I'm sure Linux's kernel was totally sleek when the only people who were able to use it were people who could program their whole effing computer by hand, but in a day and age when Linux is to be seen as a legitimate alternative OS, it's going to NEED that "bloat" in order to make sure the maximal number of users are covered.

---

### Post by Shibblet on 2009-11-04
We like our GUI's, our web-browsers, our point and click interface, our download percentage notification bars, our installation information, our goofy desktop clock, our album art, and our assorted eye candy.  I think that desktop OS's, by design, are all top-heavy.  A streamlined system is a prompt.

But it's not a practical approach for 99% of the world.  Prompts are what people would refer to as "unfriendly".  It's what caused people to not use computers back in the late 80's and early 90's.  And made them "geek" machines.

It really comes down to what you want.  Ever run Puppy Linux?  Great, fast, simple, and quick distribution.  But it looks like poo compared to Ubuntu, or Kubuntu for that matter.  Gnome is great, KDE is even better.  Please don't argue with that statement, some like Gnome better than KDE, and that's fine, but the argument is simply that Gnome OR KDE are better looking interfaces than a prompt.)

[Linus even said recently that Linux has turned into a bloated OS.]("http://news.cnet.com/8301-13505_3-10358024-16.html")
But in my opinion, that is the evolution of the computer.  I would imagine that even people who are very comfortable with the terminal, or shell, still prefer to work in a desktop environment.

There are people out there who prefer XDE, QT, and FluxBox.  Because they want a streamlined, yet graphical user interface.  Then there is the other side of that coin.   Look at how MS Windows has evolved over the years, more and more and more ram is eaten up inefficiently just for the flippin' window manager.  Are transparent window frames useful?  Is making the window shrink and fade into the desktop necessary?  No, but it looks nice, and most of us like it.

Compiz is the same way.  Do I need my windows to burn up when closed?  Do they need to wobble around when I drag them?  Is it necessary that they bounce when I open one?  No, but it's pretty to look at and fun to play with.

So in a nutshell, OS's are Top Heavy, but we like it.  Fortunately for those of us who don't like it, there are alternatives.

---

### Post by jward3010 on 2009-11-04
Unfortunately, I think you make the wrong argument in thinking that eye-candy and GUI based software is inherently slow. Often to suit mainstream needs it's written inherently badly and bulky, thats my argument. Eye-candy can be really fast if it's written well and the system it's installed in communicates with it correctly.

Back to my other argument that the OS on an iPod touch is unbelievably fast yet with such fantastic eye-candy that it leaves compiz in the shade and it's stable as a rock. No doubt it's specific hardware helps and they can optimise like crazy but as I've read in this post the Linux kernel devs are not attempting optimistaion but instead unbelievably wide support.

Same is true of Apple Mac's - they're attractive, complex yet quick and stable as a rock. I know why - they've one type of hardware to worry about only - Linux worries about thousands and manufacturers don't make the job any easier by helping with driver development.

The linux kernel is like a Toyota Corolla, carries lots of people, comfy enough but it ain't going anywhere fast.

---

### Post by Shibblet on 2009-11-04
> **jward3010 said:**
> Unfortunately, I think you make the wrong argument in thinking that eye-candy and GUI based software is inherently slow. Often to suit mainstream needs it's written inherently badly and bulky, thats my argument. Eye-candy can be really fast if it's written well and the system it's installed in communicates with it correctly.

That's true.  But my argument was that GUI's are slow as compared to a prompt.  Ironically, the slowest part of a prompt is the user interface.

---

### Post by SomeGuyDude on 2009-11-04
> **jward3010 said:**
> Unfortunately, I think you make the wrong argument in thinking that eye-candy and GUI based software is inherently slow. Often to suit mainstream needs it's written inherently badly and bulky, thats my argument. Eye-candy can be really fast if it's written well and the system it's installed in communicates with it correctly.

Back to my other argument that the OS on an iPod touch is unbelievably fast yet with such fantastic eye-candy that it leaves compiz in the shade and it's stable as a rock. No doubt it's specific hardware helps and they can optimise like crazy but as I've read in this post the Linux kernel devs are not attempting optimistaion but instead unbelievably wide support.

Same is true of Apple Mac's - they're attractive, complex yet quick and stable as a rock. I know why - they've one type of hardware to worry about only - Linux worries about thousands and manufacturers don't make the job any easier by helping with driver development.

The linux kernel is like a Toyota Corolla, carries lots of people, comfy enough but it ain't going anywhere fast.

Well yeah, that's exactly it. Since you can only get OSX on an Apple brand computer, they can write the code EXACTLY to the specs of the machines it's going on, which in turn vary very little from one to another. Additionally, as others have said, they scrap legacy support after a while. So it'd be like if Linux only had to worry about HP's Pavilion series laptops. If that were the case, you can bet Linux would have some VERY efficient code.

---

### Post by Frak on 2009-11-04
> **RiceMonster said:**
> That was funny. I thought it was even funnier when they switched the site to German for April fools :D.
I thought I was still going through my proxy. Didn't phase The Frak any. (Ich spreche Deutsch.)

---

### Post by handy on 2009-11-05
My understanding is that the kernel is faster now than it used to be, even though it is larger & growing, mostly due to hardware support.

Trimming the kernel &/or compiling it to suit your own hardware will in most cases have no noticeable effect on performance these days.  
Unless a person is dead short on space it is a waste of time.

This is due to the kernel now being smarter at how it deals with hardware than it used to be.

This topic has gone from top heavy to bottom heavy.

---

### Post by Arup on 2009-11-05
I find with every release its getting faster. Hardware getting better utilized.

---

### Post by [h2o] on 2009-11-05
If I remember things clearly Linus never said that Linux was becoming slow. He mentioned that the code base is getting "big and scary". This has no implication of the kernel execution speed.
So can we please drop the "Linus says Linux is bloated and slow" crap?

As for operating systems (or desktop systems) getting slower. Yes, sure, they are, because they do more now than they did a few years ago. So nothing strange really.
Also, the CPU might have had an extreme increase in speed, but lots of other parts of the computer has not. The disk drive is most likely the bottleneck since everything the CPU does must first be loaded from the disk.

---

### Post by Harshana on 2009-11-05
I think i can agree with you for some points.I don't know nothing about souce codes.But i do agree that OS is 1 (some times few) second behind the user.OS's should be Faster than old one.Facilitating should be impove.But after the speed.

;)

---

### Post by SonicSteve on 2009-11-05
I just thought I would chime in with my experiences.
1. The intel driver fiasco was well..... a fiasco. 
2. My machines are;
2 laptops
-1.5ghz centrino 1gb ram, 80gb hdd - intel graphics. I don't see any unacceptable delay unless you count 3d stuff. running 9.10 ubuntu
- 1.9ghz Athlon X2, 2gb ram, 160gb hdd- works great, nvidia graphics. running 9.10 ubuntu

2 desktops
work -2.2ghz core2duo, 2gb ram, intel graphics. running 9.04 ubuntu. works very well minus the intel graphic issue. I hope 9.10 will has fixed it.

Home 1.8ghz sempron 3000+ 1gb ram, nvidia graphics. running 9.04. works very well no issues at all. 

So while none of machines are hopelessly old, the cetrino laptop is 5yrs old. The desktop was only decent 4 yrs ago. They both run the system more than acceptably. The other two systems don't have any lag at all. 

Having said that, I would would love to see optimized / cleaned up code. Though it seems to be quite a arduous task.

---

### Post by oldrocker99 on 2009-11-05
> **BuffaloX said:**
> My C64 booted in 3 seconds.
But it didn't have to load anything, everything was mapped directly in ROM.

The Amiga had a boot sequence a bit more similar to modern computers.
It had hardware and drives auto detection and booted in about a minute.

Todays computers are thousands of times faster, but take about the same time to boot.

The Amiga could detect hardware and load a complete preemptive multitasking graphical OS about as fast as a modern computer, and with about the same basic features, and it even had the slowest file system.

I suspect modern PCs have legacy problems with the bus, dating all the way back to the old ISA bus, but I don't know because nobody cares today, we only have one architecture, take it or leave it.

The Bios alone takes some 10 seconds to get ready to actually boot the OS.
This is outrageous, that's longer than the C64 took to show ready.

There really should be only one limitation, and that's the hard-drive spin-up time, which will probably soon be irrelevant, because we switch to SSD drives, and all this boot waiting will be history.

One thing's for sure, PCs are kludges plain and simple.

Anyways Karmic is probably the fastest OS to boot for me since I switched to PCs back in the early 90's.

I had a C64, and an Amiga (I was one of the first people in my area to use an Amiga, and one of the last to switch to a PC. Boy, was that Amiga file system slow](*,), but I still loved that system (and never progressed beyond AmigaOS 2.0). 

I put up with 95, 98, ME and XP. Finally, 18 months ago, I had an XP metdown and switched to Ubuntu, and I'm not looking back. It even felt like an Amiga.

Karmic seems to run pretty well on my aging desktop, although there are a couple of wireless issues.  

It boots up pretty quickly and I don't have the problems I had on my ATI laptop with Xorg, since I have a 512MB nVidia 8600.

In other words, so far so good.

---

### Post by jward3010 on 2009-11-05
> **handy said:**
> This topic has gone from top heavy to bottom heavy.

Well I would say a bit of both. Boot Ubuntu into pure command line and it is quick, in fact I often jump to one of the consoles and kill gdm and even get better battery life and everything. Start up gdm and it ain't all that quick. That suggests that although the kernel is fairly weighty desktop environments add their own problems to it.

---

### Post by jward3010 on 2009-11-05
> **'[h2o] said:**
> Also, the CPU might have had an extreme increase in speed, but lots of other parts of the computer has not. The disk drive is most likely the bottleneck since everything the CPU does must first be loaded from the disk.
But thats where pre-caching comes in and Ubuntu doesn't do it all that well, even with preload installed. I don't find preload makes much of a difference at all. I install it mostly on performance systems i.e. I don't have many old PC's lying around to test it on.

I don't see why this should be the case. Laptops and PC's are coming with buckets of RAM nowadays, and please don't tell me that the kernel or some simple app can't detect how much there is in a machine and hence begin some kind of pre-caching to the extent that there *is* RAM.

---

### Post by Shibblet on 2009-11-05
The "Linus says Linux is bloated" argument is not something to use as a crutch.  However, he does have a point.  I think his point is primarily that the Kernel that he has wrote, has now evolved into a community wide project with more potential than he ever thought it had.

So when you say the Linux Kernel is Linus Torvalds baby, it was, but that baby has grown up now.  And is no longer small, compact, eating formula, and pooping in diapers.  Disregard the last two of the four.

How many different Linux distributions are there out there?  And most of which are community maintained.  Every distribution adds custom stuff to their Kernel.  People add their little bits and pieces here and there, desktop environments, applications, utilities, etc. etc. etc.

Next thing you know you have a complete OS like Ubuntu, that fits into a 700meg ISO file.  That's a heck of a lot of data on top of the kernel.

So, yes, OS's are getting top heavy, but it's necessary.  Even the most hardcore user who loves their prompt, still whips out a web-browser in their desktop environment of choice, every now and again.

---

### Post by handy on 2009-11-06
Just a little one for those interested in the kernel who may not have heard of this little gem.

The BFS-kernel has become some people's favourite:

**_[http://en.wikipedia.org/w/index.php?title=Brain_****_Scheduler](http://en.wikipedia.org/w/index.php?title=Brain_****_Scheduler)_**

I think as far as the speed benefits are concerned, it depends on what you use your computer for in the end. There have been very good reports from a heavy duty 3D gamer or two on the Arch forums... 

**[Edit:]** The Ubuntu forum software is censoring the URL for the link I have embedded above.  So you will have to use your imagination to replace the four asterisk in your browser's address field. 

Though I can give you some clues, it goes just like this (take particular note of the upper case please?) BFS = "Brain_F*ck_Scheduler" note the underscores, they are in the URL & therefore critically important, so are the upper case letters at the start of each of the three words.  When you replace the four asterisk in the URL, make sure you use an upper case **F** in front of the other three lower case letters.  

I have never struck a URL before that was case sensitive, but THIS one IS.:roll:

If you use a lower case **f**, you will get the wrong site.

---

### Post by seenthelite on 2009-11-06
> **jward3010 said:**
> God I effing know, it ain't an easy battle. Some dudes somewhere (sorry I have no coding experience, just experience in complaining) should take a decent laptop system and work hard on writing Linux into it, make a customised system with efficient code that suits it beautifully, a bit like a MacBook (although I've never tried one enough) or iMac or other Apple products.

I would LOVE to see that happen in the Linux world!

Totally agree, if only the computer hardware manufacturers could start to standardize the components the OS's would not need to ship so bloated.

---

### Post by SaintDanBert on 2009-11-07
I confess that I ripped this comment without reading all the way through all of the other remarks... bad geek!

While in computer science grad school, the Operating Systems course used an onion metaphor.

[list]
[*]at the core is the hardware
[*]hardware needs drivers
[*]the kernel implements multi-tasking, multi-threading, etc, and manages interactions between the various drivers and the process and thread run queues.
[*]applications use SPI (system services) to interact with the kernel and with the hardware drivers.
[*]applications use API (application services) to interact with other applications
[*]some applications are themselves a form of "system service" -- for example many of the daemons
[/list]

Now I ask you to pick your favorite parts of your workstation software and locate it within the onion. Now which part of the onion has all of the "top heavy" "bloat ware"?

As far as "too slow" is concerned, all of those processes and threads take some part of the available processing cycles. How much is going on on your workstation? Use **htop** or similar to get some clues.
Are there things started at boot-time or at login-time that you seldom use? What can you eliminate? All of that eye-candy uses cycles that are no longer available to your running foreground session.

Good luck,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2009-11-07
> **seenthelite said:**
> 
Totally agree, if only the computer hardware manufacturers could start to standardize the components the OS's would not need to ship so bloated.

Standards and commonality are well and good. I don't care how much ships with a distro so long as (1) I can get all the parts that my workstation demands, and (2) I don't need to keep un-needed or un-wanted parts on disk or otherwise in the way.

~~~ 0;-Dan

---

### Post by misfitpierce on 2009-11-07
Only thing I have noticed on Karmic was maybe about 50MB extra ram auto used by default because of Ubuntu One and other new technologies but as for boot speed it seems to be faster than Jaunty for me and I don't mind an extra 50MB or so of extra ram being used since regardless I never seem to pass 500MB with fox and all open and I have 1GB so I think you should try lighter window managers if looking for speed and less resources to be used which will always be avail in the world of linux and you will always have the option to go Ubuntu default which is still pretty light compared to Mac and Windows yet fast as hell with functionality and very nice looking, especially Karmic!

---

### Post by handy on 2009-11-07
**@SaintDanBert:** I'm not complaining. 

My old systems are faster than I need.

I thoroughly enjoy participating in this community, therefore I am found herewith thread.

Actually I'm a redundant use of resources...

---

### Post by handy on 2009-11-07
.

---

### Post by hobo14 on 2009-11-07
> **jward3010 said:**
> But thats where pre-caching comes in and Ubuntu doesn't do it all that well, even with preload installed. I don't find preload makes much of a difference at all. I install it mostly on performance systems i.e. I don't have many old PC's lying around to test it on.

I don't see why this should be the case. Laptops and PC's are coming with buckets of RAM nowadays, and please don't tell me that the kernel or some simple app can't detect how much there is in a machine and hence begin some kind of pre-caching to the extent that there *is* RAM.

Not just re this post of yours, but all your posts in general:

You don't seem to be able to make up your mind whether it's disk access or X/etc that's causing your problem.

Preload is only related to the first, not the second.  It's loading stuff from disk based on what it thinks you are going to want.  That's going to increase boot time, or give you sluggish performance just after boot.
I'll admit I haven't looked at the inner workings of Preload, but if it's doing it's best to keep apps in memory waiting for you to use them, and doesn't like letting them be removed, then it's a serious memory hog, and every time you use an app that isn't preloaded, and won't fit in memory thanks to all the preloaded stuff, it's going to have to wait while pages are copied to disk, and then your target app can be loaded into memory...

Eye candy has a cost, no two ways about it.  Most of us like some eye candy (some more than others), and it looks like you do too, else you wouldn't still be using Ubuntu.
No matter how "efficient" or "clean" or "crap-free" code is, **more eye candy means more resources used**.
If you're happy with something less pretty, less of a resource hog, there are plenty of alternatives.

Bottom line is you need to match your hardware with your OS/apps.  If your software is more than your hardware can comfortably handle you need to buy new hardware, or go back to less demanding (older) software.
Like you say, iPods run smooth, that's because Apple chose a hardware/software combo where the hardware can easily handle the load that software puts on it.
That's something you haven't chosen, and there's really no-one to blame but yourself.

---

### Post by Frak on 2009-11-07
> **hobo14 said:**
> Eye candy has a cost, no two ways about it.  Most of us like some eye candy (some more than others), and it looks like you do too, else you wouldn't still be using Ubuntu.

I'll be happy when Compiz comes close to matching Apple or Microsoft at the efficiency of their compositioner. Apple's runs directly on the graphics, consuming around 30MB of VRAM, unless it's emulated, at which it's about 35MB of RAM. Microsoft's runs at around 12MB at any given time.

Compiz has a gigantic footprint compared to those, and, at least in my view, doesn't belong in a business OS. Once it reaches the stability and footprint as shown by Apple or Microsoft, then it should be OK to put back into the OS.

---

### Post by jward3010 on 2009-11-07
> **hobo14 said:**
> You don't seem to be able to make up your mind whether it's disk access or X/etc that's causing your problem.

First, of all this isn't the case. I rarely mention disk access, albeit the worst bottleneck of the system because I understand it's limits but I also realise the benefits of the aggressive pre-caching that some Live systems do and how quick they can be in general use (specifically Backtrack, that was a particularly quick and full featured KDE system, if not always quite finished). To be honest I lay the blame mostly at X and Gnome (maybe Metacity, but I don't know it's performance levels).

> **hobo14 said:**
> I'll admit I haven't looked at the inner workings of Preload, but if it's doing it's best to keep apps in memory waiting for you to use them, and doesn't like letting them be removed, then it's a serious memory hog, and every time you use an app that isn't preloaded, and won't fit in memory thanks to all the preloaded stuff, it's going to have to wait while pages are copied to disk, and then your target app can be loaded into memory...
When you have 4GB's of RAM (and an average of 2GB nowadays on cheap models) thats hardly a worry, not only that but we are talking about lightweight stuff here. Gnome is not a massive bundle of megs and never is in memory. Basic Firefox is not big when it starts out, espeically in regards to what it can do. Linux apps are generally lightweight and nothing compared to Windows system, certainly in comparison to Vista and probably Windows 7.

> Eye candy has a cost, no two ways about it.  Most of us like some eye candy (some more than others), and it looks like you do too, else you wouldn't still be using Ubuntu.

If basic Gnome desktop with compiz switched off is eye-candy then I'm on the wrong planet, I have no interest in eye-candy, at the same time I'm not engrossed in the terminal either (although I do a lot of work there and like it to be fair) and I like a desktop, everyone who comes to Ubuntu does. If you're talking about my iPod touch well that comes by default.

> Bottom line is you need to match your hardware with your OS/apps.  If your software is more than your hardware can comfortably handle you need to buy new hardware, or go back to less demanding (older) software.

I feel you're not listening or reading my posts - the point is I'm using good hardware across the board. On this laptop I have a Core 2 Duo P8700, 4GB DDR2 RAM, nVidia 9300GM with 512MB of it's own RAM (better than on onboard Intel anyway) and I'm using 64-bit Karmic. We are talking about a basic desktop OS here, I'm not playing Crysis or FarCry2 or trying to put a Pixar 3D film together. Jaunty had bad problems with the old Intel drivers and we KNEW full well that the drivers we're being atrociously inneficient with X and it ran like shite even on good machines, thats still happening with other drivers - or is it just "OS's are more bloated, they've more stuff!"

They have nothing more than XP had back in the day.

> Like you say, iPods run smooth, that's because Apple chose a hardware/software combo where the hardware can easily handle the load that software puts on it.
That's something you haven't chosen, and there's really no-one to blame but yourself.

My God, your sounding like I'm a nuisance for pointing out bloat. With these OS's you're going to have to be critical, if other Linux distributions can be lightweight, useable, functional, attractive then so can Ubuntu. There are many areas in which Linux falls flat, which it can do NOTHING about (apart from community pressure) and that is with hardware drivers, manufacturer support and a big area where performance could be improved. Are you suggesting that theres no point in saying this is an area where maybe Linux will slow down because it obviously is.

Generally you're making it sound as if modern OS's are just by default heavy, and they NEED to be, to be basically functional, eye-candy or no eye-candy. I know that this isn't the case.

---

### Post by jward3010 on 2009-11-07
> **Frak said:**
> I'll be happy when Compiz comes close to matching Apple or Microsoft at the efficiency of their compositioner. Apple's runs directly on the graphics, consuming around 30MB of VRAM, unless it's emulated, at which it's about 35MB of RAM. Microsoft's runs at around 12MB at any given time.

This is what I mean, even the Windows compositor is quicker than metacity and gnome. And I typically stay there to get things done. It's horrible to think that a user is quicker getting things done with a mouse than the OS is able to keep up.

---

### Post by Frak on 2009-11-07
> **jward3010 said:**
> This is what I mean, even the Windows compositor is quicker than metacity and gnome. And I typically stay there to get things done. It's horrible to think that a user is quicker getting things done with a mouse than the OS is able to keep up.
Realized I just wrote compositioner. No wonder my spellcheck was throwing flags at me. [NOPARSE]:P[/NOPARSE]

---

### Post by jward3010 on 2009-11-07
> **Frak said:**
> Realized I just wrote compositioner. No wonder my spellcheck was throwing flags at me. [NOPARSE]:P[/NOPARSE]
Don't worry, I wont mention it to anyone.

---

### Post by hobo14 on 2009-11-07
> **jward3010 said:**
> First, of all this isn't the case. I rarely mention disk access, albeit the worst bottleneck of the system because I understand it's limits but I also realise the benefits of the aggressive pre-caching that some Live systems do and how quick they can be in general use (specifically Backtrack, that was a particularly quick and full featured KDE system, if not always quite finished). To be honest I lay the blame mostly at X and Gnome (maybe Metacity, but I don't know it's performance levels).
Then you should stop complaining about Preload, shouldn't you?
You say disk access is the bottleneck in your system, but you blame the OS for being too "top heavy"??
What do you actually think X/Gnome is doing to slow you down? 

The apps have to be read from disk, and that takes time. No amount of "efficiency", and no matter how un-top heavy OS's are, nothing will change that.



> If basic Gnome desktop with compiz switched off is eye-candy then I'm on the wrong planet, I have no interest in eye-candy, at the same time I'm not engrossed in the terminal either (although I do a lot of work there and like it to be fair) and I like a desktop, everyone who comes to Ubuntu does. If you're talking about my iPod touch well that comes by default.
Of course it is.  Most of us here like Gnome or KDE, and they will consume resources, no matter how efficient they are.
Go for something lighter if you don't like it.



> I feel you're not listening or reading my posts - the point is I'm using good hardware across the board. On this laptop I have a Core 2 Duo P8700, 4GB DDR2 RAM, nVidia 9300GM with 512MB of it's own RAM (better than on onboard Intel anyway) and I'm using 64-bit Karmic. We are talking about a basic desktop OS here, I'm not playing Crysis or FarCry2 or trying to put a Pixar 3D film together. Jaunty had bad problems with the old Intel drivers and we KNEW full well that the drivers we're being atrociously inneficient with X and it ran like shite even on good machines, thats still happening with other drivers - or is it just "OS's are more bloated, they've more stuff!"
That's not the machine you were complaining about when you started this thread though.  Try 5-6 year old software on your 5 year old machine for a performance increase. 


> They have nothing more than XP had back in the day.
Spoken like someone stuck in the past. All mainstream OS's (and I include Ubuntu in that) consume more resources, and offer more services with every major release.  The trend is up, and will continue to be up as long as consumers keep buying new hardware.



> My God, your sounding like I'm a nuisance for pointing out bloat. With these OS's you're going to have to be critical, if other Linux distributions can be lightweight, useable, functional, attractive then so can Ubuntu. There are many areas in which Linux falls flat, which it can do NOTHING about (apart from community pressure) and that is with hardware drivers, manufacturer support and a big area where performance could be improved. Are you suggesting that theres no point in saying this is an area where maybe Linux will slow down because it obviously is.
Is this thread about Ubuntu now? Or all Linux distros?  Or all OS's, like the title says?


> Generally you're making it sound as if modern OS's are just by default heavy, and they NEED to be, to be basically functional, eye-candy or no eye-candy. I know that this isn't the case.
Mainstream OS's _are_ "top-heavy", yes. (By top-heavy I assume you mean they are large consumers of hardware resources?)
Yes they do need to be, to satisfy the majority of users with their appearance and services provided.
Two identical OS's, A and B, except that A uses a GUI, and B doesn't have one: B will outperform A.  Accept it.  You can't magic away absolute levels of resource consumption with your concept of "efficiency".

Get new hardware, or older software, or a lighter distro.  But bear in mind you'll always have to wait for disk access.

> This is what I mean, even the Windows compositor is quicker than metacity and gnome. And I typically stay there to get things done. It's horrible to think that a user is quicker getting things done with a mouse than the OS is able to keep up.
You can't be serious.  There isn't any OS anywhere that a user couldn't swamp with tasks until it became slow or unresponsive.


I don't think you really understand what you are talking about.  The most perfect app on a perfect OS on perfect hardware will still need time to perform tasks.

---

### Post by jward3010 on 2009-11-08
> **hobo14 said:**
> Then you should stop complaining about Preload, shouldn't you?
You say disk access is the bottleneck in your system, but you blame the OS for being too "top heavy"??
What do you actually think X/Gnome is doing to slow you down?
ONCE AGAIN I dont say that the disk is the bottleneck in my system, it's the guaranteed bottleneck in EVERYBODY'S system! It's the main bottleneck during the first minute of startup as everything is not in working memory but as stuff goes into memory or preload starts to work that should be alleviated to a great extent. I don't feel it is. I still fell general work with the Gnome desktop is sluggish, opening the Applications and Systems menu and the need for them to load all there icons (I think it should be done when Gnome is loaded), jumping between tabs and folders in nautilus is not that quick, moving a window around a screen is jerky, scrolling in Firefox is awful sometimes (true, often down to heavy webpages), opening nautilus for the sixth time in a session and it's still delayed - it creates the perception of an awkward system. I don't leave the rap there, eventually Window's system grind to a terrible halt, most of us know this and this is a much worse result than Ubuntu which will happily carry on, or even another case: You reinstall a windows system, you do drivers, updates and your favourite programs and then eventually you notice the slow creep in.

> **hobo14 said:**
> The apps have to be read from disk, and that takes time. No amount of "efficiency", and no matter how un-top heavy OS's are, nothing will change that.
This is where I disagree, like the example I gave in the other posts even Firefox appeared instantly on a LiveUSB or LiveCD version of Backtrack with addons built in. I wouldn't have created this post if I didn't notice this.

> **hobo14 said:**
> Of course it is.  Most of us here like Gnome or KDE, and they will consume resources, no matter how efficient they are.
Go for something lighter if you don't like it.
How come the compositor and explorer in Windows 7 is more ready for me, XP is a quick system, I used Slackware for a time and found a big improvement, Backtrack had everything and ran crazy fast. It used resources more efficiently or was generally lighter. I'm not a coder and I don't know whether you are either but it's well known that things could be done with more elegance often in the Linux world.

> **hobo14 said:**
> That's not the machine you were complaining about when you started this thread though.  Try 5-6 year old software on your 5 year old machine for a performance increase.
I never mentioned a PC at the start of this post and the interesting thing is I'm using Jaunty and Windows 7 on a 6 week old performance laptop and still I'm suffering slowness. This argument also puts to bed the idea that even Ubuntu should be used to revive old machines in the wardrobe. It definitely shouldn't.

> **hobo14 said:**
> Spoken like someone stuck in the past. All mainstream OS's (and I include Ubuntu in that) consume more resources, and offer more services with every major release.  The trend is up, and will continue to be up as long as consumers keep buying new hardware.

> **hobo14 said:**
> Is this thread about Ubuntu now? Or all Linux distros?  Or all OS's, like the title says?
Just like the title says, I want to encompass general computing into it. 

I'm being semantic in eventually singling Ubuntu out as a bit of a slow coach (depending on what you use it on) as certain people are going down a particular path, just go back and read the posts, but XP, Vista, 7, Crunchbang, Xubuntu and everything else are not really running any quicker nowadays compared to the early days of slower CPU's, less memory etc. regardless of the fact that they do the same damn things with only minor improvements. And yes I say MINOR improvements. 

I could easily go back to Hardy now (if it would only work on this laptop - graphics + networking dead, due to unsolved bugs) and find everything in it that I needed. I still find XP a completely acceptable OS to do most of my work on apart from it's closed source nature, the problems with infections, the often heavy bloated apps you have to use in the closed source world. I mean can somebody tell me of a major difference between XP and Windows 7 apart from flashier graphics and a slightly improved desktop, is the kernel fundamentally fater, is networking efficiency increased, is CPU polling different, is memory mapping improved, have they utilised Dual core CPU's any differently. 

The cosmetic stuff doesn't matter and consumers never really want flashy effects - they GET them from the manufacturers! And then expect them in the next release as well. The OS creators dig their own graves a lot of the time, especially when they insert stuff which might satisfy superficial want but mess up basic practicality.

> **hobo14 said:**
> Mainstream OS's _are_ "top-heavy", yes. (By top-heavy I assume you mean they are large consumers of hardware resources?)
Yes they do need to be, to satisfy the majority of users with their appearance and services provided.
And here's my rallying cry - "CAN WE HAVE AN OPERATING SYSTEM THAT SATISFY'S EVERYBODY'S NEEDS AND IS YET FAST AND EFFICIENT?"
I think we can answer YES to that, but when is another thing



> **hobo14 said:**
> You can't be serious.  There isn't any OS anywhere that a user couldn't swamp with tasks until it became slow or unresponsive.
Thats how I feel about karmic at the moment, fact, in my world anyway. I think you are using Ubuntu on a system that runs it very well, I'm not and I'm pissed off because the hardware is great, but understand that there's no warranty and I can't get a refund and all I can keep doing is using away, file bug reports which I like doing because it can pretty responsive on Launchpad (and that fundamental difference is a great one, compared to Microsoft support, I mean WOW!)

> **hobo14 said:**
> I don't think you really understand what you are talking about.  The most perfect app on a perfect OS on perfect hardware will still need time to perform tasks.
And I'm stuck in the past for wanting improvements, I think you are. There is even a split off kernel developer (I can't remember his name, if I find it I'll come back) who's different ideas on CPU polling and tasking created great efficiencies in CPU performance for the desktop but was ignored for such a long time that he eventually left kernel development. His kernels are still available. 

Here's an example of something which might change your mind: [http://www.linuxnewstoday.org/linux-news-sep-2009-archives/1199-sep-18-2009-linux-news.shtml](http://www.linuxnewstoday.org/linux-news-sep-2009-archives/1199-sep-18-2009-linux-news.shtml)

> 
**Kernel 2.6.31 - improved for the desktop:**
1) Improved desktop speed -- Due to some recent changes in the kernel, when Linux systems started running out of memory, the kernel was set up so that PROT_EXEC pages, memory pages that usually belong to currently running foreground programs were being mishandled. Instead of being kept in the memory cache, they were being written to disk until they were needed.

These are obvious inefficiencies and due to the server nature of the Linux kernel they will continue - this is a really good area for Linux to improve, because it has the freedom to do so. Possibly even create a separate desktop optimised kernel. Windows will be sluggish for other reasons, a historically bloated kernel which isn't effiecient, probably needs a rewrite, a development model which is disconnected, the favouring of hollywood and the music industry over consumers and the protection measures they put in to deal with this (two layers of AES encryption to pump through a BluRay film just to suit Hollywood! I mean thats disgusting and requires an Alienware machine!)

You should get it into your head that LINUX is not perfect, nothing is, software development has not caught up with hardware performance, it's just not using it well enough. 

And there are easy ways to fix it, just not taken up yet and in the mean time the devs are possibly going down a few wrong paths in developing a desktop system. As are Windows and probably MAC, we are not at our most efficient yet - thats the point I'm making.

---

### Post by hobo14 on 2009-11-08
> **jward3010 said:**
> ONCE AGAIN I dont say that the disk is the bottleneck in my system, it's the guaranteed bottleneck in EVERYBODY'S system! It's the main bottleneck during the first minute of startup as everything is not in working memory but as stuff goes into memory or preload starts to work that should be alleviated to a great extent. I don't feel it is. I still fell general work with the Gnome desktop is sluggish, opening the Applications and Systems menu and the need for them to load all there icons (I think it should be done when Gnome is loaded), jumping between tabs and folders in nautilus is not that quick, moving a window around a screen is jerky, scrolling in Firefox is awful sometimes (true, often down to heavy webpages), opening nautilus for the sixth time in a session and it's still delayed - it creates the perception of an awkward system. I don't leave the rap there, eventually Window's system grind to a terrible halt, most of us know this and this is a much worse result than Ubuntu which will happily carry on, or even another case: You reinstall a windows system, you do drivers, updates and your favourite programs and then eventually you notice the slow creep in.
Somebody else want to tell this guy the lag is stuff being read from disk to memory?  He obviously doesn't believe me.


> This is where I disagree, like the example I gave in the other posts even Firefox appeared instantly on a LiveUSB or LiveCD version of Backtrack with addons built in. I wouldn't have created this post if I didn't notice this.
You don't agree that loading apps from disk is necessary and takes time?
You're living in a dream world.


> How come the compositor and explorer in Windows 7 is more ready for me, XP is a quick system, I used Slackware for a time and found a big improvement, Backtrack had everything and ran crazy fast. It used resources more efficiently or was generally lighter. I'm not a coder and I don't know whether you are either but it's well known that things could be done with more elegance often in the Linux world.
I am.  This paragraph really doesn't sound like you have a problem with all/most OS's, as per the thread title.


> I never mentioned a PC at the start of this post and the interesting thing is I'm using Jaunty and Windows 7 on a 6 week old performance laptop and still I'm suffering slowness. This argument also puts to bed the idea that even Ubuntu should be used to revive old machines in the wardrobe. It definitely shouldn't.
At the start of the **thread:**
> I know how to overclock, in fact I have an Athlon64 3700+ clocked at 2.53GHz, compared to default of 2.2GHz. I even bought particular Corsair memory (DDR550) so as to give me overhead to do it. I also have a 7800GTX which compiz flys with (although most of the time disabled) but starting a process has an annoying half-second delay, like Nautilus. So wobbling windows around is easy and smooth but opening that window to begin with takes around a second, like there not pre-cached and preload does not help, doesn't seem to anyway.
If you want to use Ubuntu on an old machine, use an **old Ubuntu**.
The root of your problem is that you have unrealistic expectations: an OS+hardware combo that reacts _instantly_ to your requests.



> And here's my rallying cry - "CAN WE HAVE AN OPERATING SYSTEM THAT SATISFY'S EVERYBODY'S NEEDS AND IS YET FAST AND EFFICIENT?"
I think we can answer YES to that, but when is another thing
Not a chance.  You can have one or the other.




> Thats how I feel about karmic at the moment, fact, in my world anyway. I think you are using Ubuntu on a system that runs it very well, I'm not and I'm pissed off because the hardware is great, but understand that there's no warranty and I can't get a refund and all I can keep doing is using away, file bug reports which I like doing because it can pretty responsive on Launchpad (and that fundamental difference is a great one, compared to Microsoft support, I mean WOW!)
I'm running 8.10, 9.04 and XP on systems older than yours. Of course I have a lag when opening apps too, but I don't think "That's outrageous!" when it happens.


> And I'm stuck in the past for wanting improvements, I think you are. There is even a split off kernel developer (I can't remember his name, if I find it I'll come back) who's different ideas on CPU polling and tasking created great efficiencies in CPU performance for the desktop but was ignored for such a long time that he eventually left kernel development. His kernels are still available. 
Now you're shuffling my paragraphs for your replies.

> Here's an example of something which might change your mind: [http://www.linuxnewstoday.org/linux-news-sep-2009-archives/1199-sep-18-2009-linux-news.shtml](http://www.linuxnewstoday.org/linux-news-sep-2009-archives/1199-sep-18-2009-linux-news.shtml)
Change my mind?  I've been telling you that the lag is disk access, you've been pointing the finger at "inefficiently coded" GUIs....



> You should get it into your head that LINUX is not perfect, nothing is, software development has not caught up with hardware performance, it's just not using it well enough. 

And there are easy ways to fix it, just not taken up yet and in the mean time the devs are possibly going down a few wrong paths in developing a desktop system. As are Windows and probably MAC, we are not at our most efficient yet - thats the point I'm making.
No, Linux isn't perfect. (Don't forget this thread is about all OSs, not just Linux distros)
Complaints about coding ("devs don't code right!") aren't likely to ever be taken seriously when they come from someone who can't code.

---

### Post by MasterNetra on 2009-11-08
I don't know what your talking about. Ubuntu is still pretty darn fast and low on resource consumption. It beats windows in login speed and beats Windows 7 on shutdown...well I suppose almost every other OS beats it in shutdown time...but still Ubuntu is very light. Maybe not as light as DSL or Puppy but still.
As for Windows for sure, but did you expect anything different from them? Can't speak for Macs though, Only occasionally use OS X in my college's lab which seem to do alright, though much more resource heavy then Ubuntu. Ubuntu is still at the lighter end if I do say so myself.

---

### Post by Seishuku on 2009-11-08
You know, I'm a terrible person. 

I read the title and in my head responded "Like YOUR MOM?".

---

### Post by jward3010 on 2009-11-09
Christ, this is getting annoying - You are obsessed with disk lag as the problem. I fully acknowledge that disk lag causes a time lag between clicking and operation, i have NO problem with that early on in operation - BUT NOT WHEN IT IS LOADED. You may notice in my posts that I talk about jerky windows, slow scrolling, tab opening - these things are already in memory, at least should be, and they can be slow. Not everything is related to disk lag. Why keep talking about disk lag, when I say the windows move around the screen jerkily? Is that disk lag? No, it's slow X, bad drivers, inefficient use of resources or something else but the disk activity indicator stays completely still when I do those things.

I refute completely that my hardware is horribly old, it's decent hardware and thats what bugs me, it's hardware for gaming, not for an OS i.e. it has immense overhead. Most OS's I throw at it run absolutely fine (in Windows case, for a while at least, in Linux case, they tend to run great (yes, you heard me right) BUT with that annoying lag even with preload installed, and an area that Windows beats it in). So my PC is not the issue, at least I don't think it is.

I have 9.04, XP and 7 installed and there is a definite marked readiness with XP and 7 compared to the Gnome desktop, it's anticipating what you want to do. With preload installed in Ubuntu it's still behind. I tried 8.04, found no difference in speed between karmic and it plus I kept getting kernel panics (another unsolved bug and a bit annoying for an LTS release) so I couldn't stick with it.

Stop obsessing over disk lag in my posts - it's not the only issue. When pre-caching can be performed by a system it should be much less an issue - not gone but much less, in Ubuntu I don't find thats the case. In regards slow X and Gnome desktop, I find that on this laptop I'm writing to you on. I try Ubuntu on hundreds of laptops all the time, I'm an IT technician involved in repair work, networking and other areas and often get the chance to install Ubuntu on numerous machines. Depending on their graphics hardware they will run great or atrociously - FACT! And sometimes proprietary drivers help, sometimes not, nothing to do with disk lag, as the testing of this has to do with opening an already opened menu, moving a windown around a screen, performing an action with the mouse and having to wait 1.5 seconds for something to happen on a program thats already open, scrolling in Nautilus or Firefox, opening new tabs - NOT DISK LAG RELATED THINGS. It really feels as if the commands being from the hardware up to the screen are just being delayed, being passed through slowly.

In 9.04, there was a well known bug with Intel graphics drivers, a serious regression in the used framework. If you used an Intel graphics card you'd know exactly what I meant - it caused the GUI to be atrociously inefficient, windows would drag and open slowly, mouse and keyboard input we're delayed (as it was all controlled by X), performing basic GUI functions like opening menus in Nautilus, maximising, minimising we're all slow and arduous. If you used some decent nVidia card, X was much improved. Are you going to now say that this acknowledged X and driver problem was disk related? Of course it wasn't, as soon as you moved to the slightly unstable UXA driver mode (now default in Karmic for Intel hardware) things improved a lot, so it was a driver issue and not disk related, or are you going to say this is disk related.

There's more to say but not enough time at the moment.

---

### Post by Arup on 2009-11-09
Ubuntu is way faster in response than XP or 7 and I have installed both, that too on kick *** hardware with dual quad cores and Samsung Spinpoint drives. To say that Karmic has the same response as 8.04 is preposterous. I have LTS installed on different PCs here and none gives me any kernel panic.

Statements like this negate the hard work of the dedicated developers who develop Ubuntu or other linux distros. Speaking of regressions and bugs, has anyone heard of a thing called service pack where many pending regressions and issues are fixed. MS uses its paid customers as guinea pigs and then turns around and releases a fixed OS and charges them again for it.

---

### Post by PryGuy on 2009-11-09
> **Arup said:**
> Ubuntu is way faster in response than XP or 7 and I have installed both, that too on kick *** hardware with dual quad cores and Samsung Spinpoint drives. To say that Karmic has the same response as 8.04 is preposterous. I have LTS installed on different PCs here and none gives me any kernel panic.

Statements like this negate the hard work of the dedicated developers who develop Ubuntu or other linux distros. Speaking of regressions and bugs, has anyone heard of a thing called service pack where many pending regressions and issues are fixed. MS uses its paid customers as guinea pigs and then turns around and releases a fixed OS and charges them again for it.
+1
Well, some guys here say that Compiz is so bloody slow and all, they say it is a memory hog. Well, I'm not sure about all that but my Ubuntu with Compiz eats far less memory compared to WindowsXP let alone Vista.

---

### Post by MasterNetra on 2009-11-09
> **PryGuy said:**
> +1
Well, some guys here say that Compiz is so bloody slow and all, they say it is a memory hog. Well, I'm not sure about all that but my Ubuntu with Compiz eats far less memory compared to WindowsXP let alone Vista.

+1

Yeah really I idle at 160-170mb of ram, less then XP. Gnome doesn't seem like a memory hog to me. For me KDE eats more.

---

### Post by Arup on 2009-11-09
Even with KDE, it outpeforms XP and 7, that too with a cheap nvidia video card. With Gnome its far less memory footprint.

---

### Post by RiceMonster on 2009-11-09
> **Arup said:**
> Ubuntu is way faster in response than XP or 7 and I have installed both, that too on kick *** hardware with dual quad cores and Samsung Spinpoint drives. To say that Karmic has the same response as 8.04 is preposterous. I have LTS installed on different PCs here and none gives me any kernel panic.

Statements like this negate the hard work of the dedicated developers who develop Ubuntu or other linux distros. Speaking of regressions and bugs, has anyone heard of a thing called service pack where many pending regressions and issues are fixed. MS uses its paid customers as guinea pigs and then turns around and releases a fixed OS and charges them again for it.

Are you suggesting service packs cost money? They're free, and you don't have to upgrade your Windows version. Windows XP is supported until 2014. That's 13 years of support, and far longer than any Ubuntu version; even LTS. With Ubuntu, you have to upgrade every 6 months to get recent software. You can run the newest version of pretty much anything on XP easily. Who's really being forced to upgrade?

---

### Post by PryGuy on 2009-11-09
> **RiceMonster said:**
> Are you suggesting service packs cost money? They're free, and you don't have to upgrade your Windows version. Windows XP is supported until 2014. That's 13 years of support, and far longer than any Ubuntu version; even LTS. With Ubuntu, you have to upgrade every 6 months to get recent software. You can run the newest version of pretty much anything on XP easily. Who's really being forced to upgrade?So stay with your XP and don't troll here please! Thank you!

---

### Post by Arup on 2009-11-09
> **RiceMonster said:**
> Are you suggesting service packs cost money? They're free, and you don't have to upgrade your Windows version. Windows XP is supported until 2014. That's 13 years of support, and far longer than any Ubuntu version; even LTS. With Ubuntu, you have to upgrade every 6 months to get recent software. You can run the newest version of pretty much anything on XP easily. Who's really being forced to upgrade?

Yes they do, especially when they are typically peddled off as new OS and support for the older OS is withdrawn. Thats what new MS OS are, service pack finally done right and with some added glitz. You don't have to upgrade but they have a way of making things difficult so that you are eventually pressured into a costly upgrade.

For a free OS, LTS support is quite good. No one is telling you to upgrade to latest Ubuntu, we do as we are curious to enjoy the benefits of newer stuff being given out and yes, it doesn't cost a dime.

---

### Post by RiceMonster on 2009-11-09
> **PryGuy said:**
> So stay with your XP and don't troll here please! Thank you!

lol

I'm not trolling. Disagreeing with you is not trolling. I only use XP at work. Is it so wrong that I point out misinformation in someone's post?

---

### Post by Arup on 2009-11-09
> **PryGuy said:**
> So stay with your XP and don't troll here please! Thank you!

Ha ha........you will see many, don't worry.

---

### Post by Arup on 2009-11-09
> **RiceMonster said:**
> lol

I'm not trolling. Disagreeing with you is not trolling. I only use XP at work. Is it so wrong that I point out misinformation in someone's post?

But all your posts here so far vehemently defend Windows. Every post you make here chastises anyone who dare make a comparison on your favorite OS. Its not disagreement here, its just pure fan following. Why do you hang out here if Windows is so good? So when it comes to criticism against your favorite OS, its misinformation. You just made a blatant statement that with Ubuntu you have to upgrade every six months or so, where did you get that nonsense may I ask?

---

### Post by Sef on 2009-11-09
Closed.  Too arguementative.

---

