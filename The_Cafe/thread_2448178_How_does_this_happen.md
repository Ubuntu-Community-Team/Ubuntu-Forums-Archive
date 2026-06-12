---
title: "How does this happen?"
date: 2020-08-03
forum: The Cafe
---

### Post by Tadaen_Sylvermane on 2020-08-03
On various forums I've seen the occasional thread about people with 32 bit installations to modern hardware. My question is how does this happen? 64 bit has been the standard for 10, 15, maybe 20 years now? Who would actually intentionally do this? Is there some kind of good reason? Irrelevant now I know as it's being deprecated, I just can't figure why anyone would use 32 bit these days on new machines...

---

### Post by monkeybrain20122 on 2020-08-03
There are people who make it a hobby of running Linux on 20 year old machines. ;)

---

### Post by TheFu on 2020-08-03
A chromebook that has been wiped of ChromeOS for some Ubuntu flavor, but only has 2GB of RAM is one example.
A raspberry pi v3 or older is another - those ARM CPUs are all 32-bit.

I had a 64-CPU on my desk at work in 1994.  When they became available for home prices, I was a very late adopter, because I knew most of it was hype and only really, really, really bloated software would need more than 4G for code and 16G for RAM access.  That's the situation today, still.  But don't worry, toolkits and programmers are working very hard to make bloated code for us all!

And some games only run in 32-bit systems.

---

### Post by crip720 on 2020-08-03
A few reasons, one it is what they always used, maybe they have a low ram machine and don't think 64 is needed or maybe they were given a machine with 32 bit OS and don't know.

---

### Post by poorguy on 2020-08-04
I'm still using desktops from 2009 with dual core processors and integrated graphics adapters and only 4.0GB DDR2 memory and don't want to spend the money for DDR2 memory so a 32 bit OS isn't a bad choice even though all of my desktops will run 64 bit OS.

Some of us are just cheapskates and I'm one of them and besides when all I do is basically search the internet why do I need to buy a newer computer.

FWIW I do run 64 bit Linux distros however I would still run a 32 bit distro and find no reason not to however I could be wrong about that.

---

### Post by mastablasta on 2020-08-04
we had 32bit install on 2GB ram machine. the machine was upgraded to that in 2011 or 2012. but used old CPU that could handle 64 bit just the board couldn't handle more ram. the issue was also that until few years ago many apps had 32 bit version only. some old apps still do. but in general on modern hardware there is no need for 32 bit OS.

---

### Post by TheFu on 2020-08-04
I thought the original question was for why someone with recently new hardware - say under 2 yrs old "modern hardware" - might have a 32-bit OS installed? 
But I suppose it depends on how different people define "modern hardware", doesn't it?

Many of my "servers" have no need for 64-bits - heck, most of them. More I think about it, none of them need 64-bits.

---

### Post by sdsurfer on 2020-08-04
> **Tadaen_Sylvermane said:**
> Who would actually intentionally do this?

<raises hand> Although, only theoretically . . . I haven't yet. But . . . . it comes with a dark admission.

I am not a gamer per se with one exception. The only game I ever played, and continue to play, is . . . Duke Nukem 3D. Think what you want, I love this game, the cheesy FPS graphics, sexist themes, creepy aliens, all of it. The best part is the BUILD program that came with it, the ability to create your own maps has allowed thousands of DN3D fans to create custom maps, some of them quite ingenious. I have purchased a few collections off eBay for pennies on the dollar and still haven't played them all.

So it is was with great sadness when Windows 95 came about, the architecture for DN3D was no longer supported and it died. Just died, with no hope of further development. There was a brief comeback with DN3D Forever through Steam but it just wasn't the same.

When I converted to Linux I was elated to find the eduke32 port for Linux, which plays GREAT on Ubuntu, I made the build and DN3D is back. I play two or three times a week as a distraction from the insanity we call life nowadays.

The point of my reply: I have always wanted to resurrect a couple old 32 bit machines just for this purpose. One of the things the eduke32 port does not do is support multiplayer Dukematch, in which you play either against each other or in co-op mode. We used to have so much fun with it. A couple old computers and network cards and you can run the native DN3D in multiplayer mode.

The reasons may not be as be trivial for each user, but there are some reasons. For example believe it or not, I still know of a few users around the world using a PS II running Windows 3.1. What they have does what they need and never needed anything else.

---

### Post by TheFu on 2020-08-04
> **sdsurfer said:**
> The reasons may not be as be trivial for each user, but there are some reasons. For example believe it or not, I still know of a few users around the world using a PS II running Windows 3.1. What they have does what they need and never needed anything else.

Just run the older OS inside a virtual machine. No need for the old hardware anymore, not really. DOSBOX is pretty good too.

---

### Post by CatKiller on 2020-08-04
> **TheFu said:**
> Many of my "servers" have no need for 64-bits - heck, most of them. More I think about it, none of them need 64-bits.

Because essentially everyone is using 64-bit hardware, the 32-bit codebases aren't really maintained. The Spectre and Meltdown mitigations, for example, weren't ported to the 32-bit code.

---

### Post by mastablasta on 2020-08-04
> **sdsurfer said:**
> 
The point of my reply: I have always wanted to resurrect a couple old 32 bit machines just for this purpose. One of the things the eduke32 port does not do is support multiplayer Dukematch, in which you play either against each other or in co-op mode. We used to have so much fun with it. A couple old computers and network cards and you can run the native DN3D in multiplayer mode.

32bit apps work on 64bit OS. they just need 32 bit libraries installed. i hope they at least keep the ability to add them. most older games and some new ones need them.

---

### Post by sdsurfer on 2020-08-05
> Just run the older OS inside a virtual machine. No need for the old hardware anymore, not really. DOSBOX is pretty good too.

I have experimented with VM's, DOSBOX, and Wine. The networking, which is the whole point of co-op/deathmatch, is a nightmare I never sorted out. Then there is the challenge of convincing someone who has access to Steam and all the uber cool FPS games out there to even play. :-D

>  			 		 	 32bit apps work on 64bit OS. they just need 32 bit libraries  installed. i hope they at least keep the ability to add them. most older  games and some new ones need them. 				

The goal in this theoretical situation was to go with native Windows. Probably never happen anyway, life has a way of prioritizing stuff. :-D

---

### Post by lammert-nijhof on 2020-08-06
To run ZFS on my Pentium 4 backup server, I had to install 32-bits FreeBSD 12.1 and since 1 year it receives weekly my desktop backup on its 1.2 TB storage (2 x IDE; 3.5" and 2 x SATA-1; 2.5"). 
So the magic  is:
Linux to BSD
64-bits to 32-bits
2019 AMD to 2003 Intel
nvme to IDE
The only two common elements are Ethernet and ZFS :)

---

### Post by mastablasta on 2020-08-08
yes, but the question was why would someone install it on a new machine. hmm...

---

### Post by MoebusNet on 2020-08-08
I don't do this personally, but could one possible reason be to utilize software for a particular task that was originally written as 32-bit, was never ported to 64-bit, and is not available as 64-bit? I believe I can can think of one example, the original *Myst* game for Windows 95. I'm pretty sure we could come up with some others, too. How about Word Perfect? I had some family genealogy text files written in Word Perfect that are as applicable today as when they were written. The translators for Word Perfect to Word or Libre Office are no longer available, I believe.

---

### Post by Skaperen on 2020-08-08
i still have 32-bit OS on my 4 old ASUS netbooks.  i don't use 'em anymore.  but i wouldn't even try to put a 64-bit OS on one, at least not intentionally.  i did once when i accidentally picked up the wrong memory stick.

---

