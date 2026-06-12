---
title: "Should I switch to the 64-bit version of Ubuntu ?"
date: 2009-12-06
forum: The Cafe
---

### Post by lightningfox on 2009-12-06
Hello

Right now I use Ubuntu 9.10 32-bit version on my desktop
computer (a 64-bit Pentium 4 with 1 GB RAM).

I was thinking if I should switch to the 64-bit version of Ubuntu?


Will all media codecs and web browser plugins work on the
64-bit version of Ubuntu?


Also, is switching to the 64-bit version of Ubuntu worth it.

Will there be any performance increase?

---

### Post by SunnyRabbiera on 2009-12-06
I would say its optional, even though you might see a performance boost in 64bit there are downsides like certain apps not supporting 64bit.

---

### Post by beastrace91 on 2009-12-06
Most all applications support 64bit as well as 32bit these days.

Odds are you will see at least a tiny performance increase changing to 64bit, but if I where you I'd follow the golden rule of "Don't fix what isn't broken" - in other words if 32bit is running fine just leave it be ;)

Cheers,
~Jeff

---

### Post by SunnyRabbiera on 2009-12-06
Yeh for me 32bit is fine, so why go 64?
I tried it but so far see little reason to use it fulltime.

---

### Post by Paqman on 2009-12-06
> **SunnyRabbiera said:**
> there are downsides like certain apps not supporting 64bit.

Generally only 3rd party apps. Some folks outside normal Linux circles still seem to think it's ok to only provide a 32-bit version, but thankfully that's pretty rare. Some notable examples are Gears and Air, both of which are pretty easy to get working.

I'd say go for it. I've been using 64-bit for a few years now. It used to be a bit of a hassle, but now it's great. Why throttle your chip down?

---

### Post by phrostbyte on 2009-12-06
No, not with 1 GB of RAM. Stick with 32-bit.

This is the phrostbyte algorithm for picking 32-bit or 64-bit

```

If your processor only supports 32-bit, use 32-bit.
Else if your processor supports 64-bit, but you have 2 GB or less of RAM, use 32-bit.
Else if you have *MORE* THAN 2 GB of RAM, use 64-bit.

```


Why? Because 64-bit OSes consume more RAM. This is because a fundamental datatype, the pointer, is 8 bytes long in 64-bit (4 byes in 32-bit). 

32-bit OSes are limited by 4 GB of address space (not including PAE). This means if you have a lot of RAM, your computer might not be able to address it all. So RAM is a very big part of if you go 64-bit or 32-bit.

---

### Post by whoop on 2009-12-06
If you have 4Gigs of ram or less, stick with 32 bit...

---

### Post by NoaHall on 2009-12-06
> **whoop said:**
> If you have 4Gigs of ram or less, stick with 32 bit...

No. If you have 2GB or less, stick with 32 bit. If you have 2GB < ram < 4GB , upgrade to 64 bit.

---

### Post by phrostbyte on 2009-12-06
> **whoop said:**
> If you have 4Gigs of ram or less, stick with 32 bit...

No. If you have 4GB of RAM, you will not be able to address it all in 32-bit. 32-bit is limited to 4 GB of *address spac*e, not 4 GB of RAM. RAM consumes address space, but so does many other devices.

Eg: if you have a 512 MB video card, that will consume 512 MB of address space. Even your keyboard and mouse consumes address space.

Most of the time you can only have about ~3GB of RAM on the 32-bit system, but it varies depending on hardware. I personally consider 2 GB the safe limit, as it's unlikely all your I/O devices will the other 2 GB of address space.

---

### Post by FuturePilot on 2009-12-06
Not with that processor and not with that amount of RAM.

---

### Post by whoop on 2009-12-06
> **NoaHall said:**
> No. If you have 2GB or less, stick with 32 bit. If you have 2GB < ram < 4GB , upgrade to 64 bit.
> **phrostbyte said:**
> No. If you have 4GB of RAM, you will not be able to address it all in 32-bit. 32-bit is limited to 4 GB of *address spac*e, not 4 GB of RAM. RAM consumes address space, but so does many other devices.

Eg: if you have a 512 MB video card, that will consume 512 MB of address space. Even your keyboard and mouse consumes address space.

Most of the time you can only have about ~3GB of RAM on the 32-bit system, but it varies depending on hardware. I personally consider 2 GB the safe limit, as it's unlikely all your I/O devices will the other 2 GB of address space.

I was under the impression that 32 bit could generally see about 3.3 of 4... So therefore I put the threshold on 4.

I wouldn't necessarily install 64bit on a machine with 4 Gigs; on 6 or more I would, as I would consider it a loss otherwise.

---

### Post by lidex on 2009-12-06
If you have spare hdd or extra hdd space you can install x64 separately (dual-boot) and see for yourself. It may not be for everyone right now but at some point it will be. My 64 bit system hums along and any issues stemming from architecture are negligible IMO. Your mileage may vary - I won't be going back.

---

### Post by lightningfox on 2009-12-06
Thank you for your answers.

I've decided to stay with 32-bit Ubuntu.

---

### Post by lovinglinux on 2009-12-06
> **lightningfox said:**
> Thank you for your answers.

I've decided to stay with 32-bit Ubuntu.

This was helpful for me too, since I just upgraded from 32bit to 64bit processor, but still have 2Gb of RAM. I have asked the same thing on another thread, but this issue with RAM wasn't addressed.

The performance boost from the hardware upgrade was already enough, so I will stick with 32 bit. I'm happy with it. 

Thanks.

---

### Post by Psumi on 2009-12-06
64-bit machines nowadays should be PAE-enabled, it wouldn't matter since Ubuntu will use PAE if enabled on the system with more than 3.1 GB of RAM.

For example, my 64-bit machine has PAE, so a 32-bit linux distro can use the linux pae kernel to see the 6 GB of RAM.

---

### Post by NoaHall on 2009-12-06
> **Psumi said:**
> 64-bit machines nowadays should be PAE-enabled, it wouldn't matter since Ubuntu will use PAE if enabled on the system with more than 3.1 GB of RAM.

For example, my 64-bit machine has PAE, so a 32-bit linux distro can use the linux pae kernel to see the 6 GB of RAM.

Still, you should use 64 bit instead of the 36bit(PAE), because it's faster.

---

### Post by joey-elijah on 2009-12-06
I had to reinstall Ubuntu the other day after an error which no-one was able to help me fix... worse still i had no blank media to burn 64bit Karmic to, installation from my USB failed and all i had was an official 32bit copy of Karmic...

*sigh*

Thankfully i only have 4GB RAM and 1GB GPU RAM so it's not like i'm missing out of more than 2GB of RAM atm.

Previously i had only ever used x64 bit and was happy happy. I don't notice any decrease in performance with 32bit (it's hard trying to break the habit of downloading x86_64 versions of stuff), but i really want to go x64 ASAP! (But my Ubuntu install isn't just for fun, i need to be able to work etc from it so i can't install/reinstall 24/7.

---

### Post by OrangeCrate on 2009-12-06
> *  "You don't need 64-bit software with less than 3 GB RAM"

          Performance improvement even on systems with less than 3 GB RAM

[http://forums.amd.com/devblog/blogpost.cfm?threadid=93648&catid=317](http://forums.amd.com/devblog/blogpost.cfm?threadid=93648&catid=317)

-----

> A common misconception is that 64-bit architectures are no better than 32-bit architectures unless the computer has more than 4 GB of main memory...

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by FuturePilot on 2009-12-06
> **Psumi said:**
> 64-bit machines nowadays should be PAE-enabled, it wouldn't matter since Ubuntu will use PAE if enabled on the system with more than 3.1 GB of RAM.

For example, my 64-bit machine has PAE, so a 32-bit linux distro can use the linux pae kernel to see the 6 GB of RAM.

PAE is a hack.

---

### Post by oldos2er on 2009-12-06
> **lovinglinux said:**
> This was helpful for me too, since I just upgraded from 32bit to 64bit processor, but still have 2Gb of RAM.

 I ran 64-bit Ubuntu with 2GB RAM for quite awhile. Video encoding was noticeably faster on 64-bit; day-to-day tasks like email and web-surfing, not so much.

 I'm not certain how this urban legend of needing 4GB RAM or more for 64-bit got started, but you see it a lot here in the forums.

---

### Post by FuturePilot on 2009-12-06
I too ran 64bit with 2GB of RAM. It worked fine.

---

### Post by Nerd King on 2009-12-06
> **phrostbyte said:**
> No. If you have 4GB of RAM, you will not be able to address it all in 32-bit. 32-bit is limited to 4 GB of *address spac*e, not 4 GB of RAM. RAM consumes address space, but so does many other devices.

Eg: if you have a 512 MB video card, that will consume 512 MB of address space. Even your keyboard and mouse consumes address space.

Most of the time you can only have about ~3GB of RAM on the 32-bit system, but it varies depending on hardware. I personally consider 2 GB the safe limit, as it's unlikely all your I/O devices will the other 2 GB of address space.
The 32-bit PAE kernel resolves that problem.

---

### Post by NoaHall on 2009-12-07
> **Nerd King said:**
> The 32-bit PAE kernel resolves that problem.

The 36 bit PAE kernel ;)
That's how it can "support" more RAM ;)

---

### Post by phrostbyte on 2009-12-07
> **Nerd King said:**
> The 32-bit PAE kernel resolves that problem.

I thought I mentioned PAE (maybe in an earlier post?). There are some hardware limitations and kernel trickery that goes on in PAE mode. IMO at the point where you have to use PAE you might as well go 64-bit anyway. I have no scientific reasoning for this btw. :) It just goes with the assumption that if you have a lot of RAM, 64-bit mode will result in overall better performance because of the improved instruction set and registers. While if you have 1 GB of RAM, you have to cope with the fact that you have 64-bit pointers. So I feel you are more likely to hit page faults (which KILL performance in modern OSes).

---

### Post by jespdj on 2009-12-07
With PAE, a 32-bit OS can address more than 4 GB RAM, but programs are still limited to addressing 3 GB. So if you have programs that need a huge amount of RAM (there aren't many that need more than 3 GB), PAE isn't really going to help.

There are some performance improvements with 64-bit (because the processor has more registers available and because of a more efficient calling convention, in which arguments for subroutines are passed in registers instead of on the stack), but for most software those performance improvements will not be noticeable.

You might get noticeable performance improvements in CPU-heavy applications, for example with audio or video encoding. If you're not running CPU-heavy applications, you're not going to notice a major performance improvement.

---

### Post by lidex on 2009-12-07
No offense, and not picking on anyone in particular;) , but when I see comments like this: > You might get noticeable performance improvements in CPU-heavy applications, for example with audio or video encoding. If you're not running CPU-heavy applications, you're not going to notice a major performance improvement. I have to wonder if those expressing these sentiments have actually tried running x64 recently on later hardware, or are just espousing (think I worded that right) the leaning of the blogosphere. :-&

---

### Post by LinuxFanBoi on 2009-12-07
> **lightningfox said:**
> Also, is switching to the 64-bit version of Ubuntu worth it.

Will there be any performance increase?

I don't have any issues with 64 bit.  Haven't run into any media I couldn't play back as of yet.

I would say it's worth it if you have more that 3 Gig of ram, but only if your going to do a clean install anyway.

Basically I'm saying,  don't go out of your way to do it,  Just have a plan to do it the next time you have a reason to start from scratch.

---

### Post by cascade9 on 2009-12-07
> **lidex said:**
> No offense, and not picking on anyone in particular;) , but when I see comments like this:  I have to wonder if those expressing these sentiments have actually tried running x64 recently on later hardware, or are just espousing (think I worded that right) the leaning of the blogosphere. :-&

*Scratches head* Are you saying you will notice a difference, or you wont notice a difference?

From everything I've seen, there is a difference, and 64 bit is slightly faster on most things (with the possible exception of gaming). You might need a stopwatch to notice the difference in a lot of cases though LOL

---

### Post by soni1770 on 2009-12-07
yes:popcorn:

---

### Post by fela on 2009-12-07
I reckon you should only switch if you really need to use more than 4GB of RAM.

Otherwise, IMO it's more hassle than it's worth. Unless of course you love to break apart and rearrange your system from the ground up all the time :)

---

### Post by fela on 2009-12-07
> **jespdj said:**
> With PAE, a 32-bit OS can address more than 4 GB RAM, but programs are still limited to addressing 3 GB.

Where did you pluck the 3GB figure from?

---

### Post by lidex on 2009-12-07
> A common misconception is that 64-bit architectures are no better than 32-bit architectures unless the computer has more than 4 GB of main memory. This is not entirely true:
[http://en.wikipedia.org/wiki/64-bit]("http://en.wikipedia.org/wiki/64-bit")

[32-Bit Vs. 64-Bit Windows]("http://www.lockergnome.com/windows/2009/01/07/32-bit-vs-64-bit-windows/")

---

### Post by Hallvor on 2009-12-07
> **lightningfox said:**
> Hello

Right now I use Ubuntu 9.10 32-bit version on my desktop
computer (a 64-bit Pentium 4 with 1 GB RAM).

I was thinking if I should switch to the 64-bit version of Ubuntu?


Will all media codecs and web browser plugins work on the
64-bit version of Ubuntu?


Also, is switching to the 64-bit version of Ubuntu worth it.

Will there be any performance increase?


With just 1 GB RAM I`d run 32 bit. The 64 bit version will use more RAM, but if it causes your computer to run out of memory and use swap it is probably not worth it with plain vanilla Ubuntu.

If you added a gigabyte or two and like encoding video or music, 64 bit would be much better.

---

### Post by oldos2er on 2009-12-07
> **lidex said:**
> No offense, and not picking on anyone in particular;) , but when I see comments like this:  I have to wonder if those expressing these sentiments have actually tried running x64 recently on later hardware, or are just espousing (think I worded that right) the leaning of the blogosphere. :-&

 My comments are from actual experience.

---

### Post by pricetech on 2009-12-07
I'm running hardware less than a year old and I have 2 gigs of RAM.

I tried both winders and Ubuntu, both 32 and 64 bit.  I noticed an improvement with 64 bit in both OSs.  I did have a few wrinkles to iron out, but nothing I couldn't handle with a little help from the forum.

I'd have to agree though that you should wait until you have more RAM before you upgrade.

---

### Post by BrokenKingpin on 2009-12-07
Yes you should switch. If you have a 64-bit machine there is no reason not to. There is a performance gain when running CPU intensive applications.

---

