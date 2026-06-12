---
title: "32bit or 64bit on 2GB of ram?"
date: 2010-04-14
forum: The Cafe
---

### Post by KrisInfinity on 2010-04-14
I have a Core 2 Duo E4500 processor and 2GB of ram. 

I'm planning to do a clean install when Lucid is released. 

Would 64bit bring any advantage to me?

---

### Post by Paqman on 2010-04-14
> **KrisInfinity said:**
> 
Would 64bit bring any advantage to me?

Yes, computationally intensive tasks like video transcoding will be a lot faster.

---

### Post by Cabs21 on 2010-04-14
64-bit would be helpful in Processor intensive tasks and multitasking with them. Ex) Compressing a video and surfing the net at the same time or ripping music.  However since you only have 2GB of RAM that is the only advantage you will get and you probably wont notice a huge difference due to lower RAM.  Also 32-bit programs are a bit more stable and numerous.  However if you can upgrade your RAM to over 3GB (and you plan on doing so) then 64-Bits is the way to go.  It is the easiest way to recognize more then 3GB of RAM since 32-bit can not see more then 3 GB.  Also just make sure your system is on a 64-bit architecture.

---

### Post by Bachstelze on 2010-04-14
Go 64-bit unless you have a compelling reason not to (and I really don't know of any).

---

### Post by sandyd on 2010-04-14
ive seen 64 bit users with <4 GB ram complain about performance issues, so even though 64 but will have better multimedia, I would stick with 32 bit

---

### Post by llawwehttam on 2010-04-14
64 bit has got a lot better on linuxz recently. The speed difference for me was very noticable.

---

### Post by KrisInfinity on 2010-04-14
> **Cabs21 said:**
> 64-bit would be helpful in Processor intensive tasks and multitasking with them. Ex) Compressing a video and surfing the net at the same time or ripping music.  However since you only have 2GB of RAM that is the only advantage you will get and you probably wont notice a huge difference due to lower RAM.  Also 32-bit programs are a bit more stable and numerous.  However if you can upgrade your RAM to over 3GB (and you plan on doing so) then 64-Bits is the way to go.  It is the easiest way to recognize more then 3GB of RAM since 32-bit can not see more then 3 GB.  Also just make sure your system is on a 64-bit architecture.

Yeah I know the memory limit in 32bit, that's why I asked if there are other reasons for going to 64bit instead. But I don't think I'll be upgrading the RAM as there are no empty slots.

---

### Post by PC_load_letter on 2010-04-14
As Carlee said. Expect the same applications to take twice as much RAM, so your situation is very similar to running 32 bit on 1GB RAM.

Memory prices are really low right now, I've maxed out the RAM in all my computers, and put 64bit Ubuntu on all but one of them.

---

### Post by Paqman on 2010-04-14
> **Cabs21 said:**
> Also 32-bit programs are a bit more stable and numerous.

That's not my experience at all. Finding an app that's not available in 64-bit is extremely rare. I certainly don't think they're less stable either. 64-bit on Linux is very mature.

---

### Post by Cabs21 on 2010-04-14
> **Paqman said:**
> That's not my experience at all. Finding an app that's not available in 64-bit is extremely rare. I certainly don't think they're less stable either. 64-bit on Linux is very mature.

I was basing this from my experience with Flash a few months ago and asking this same question about my computer.  64-Bit programs might be just as stable but I did notice after I switched from 32-bit to 64-bit I saw a drop in the size of the Repos and read a lot about some 64-bit versions of programs being less stable then their 32-bit counterparts also some programs that only were 32-bit did not always work great in the 64-bit OS.  That does not mean that 64-bit is unstable.  64-bit is still relatively new and replacing 32-bit slowly so both options are still out there.  Eventually 32-bit arch and software will phase out like 16-bit did but I dont see that happening within the next 10 to 15 years due to the numerous 32-bit servers still in use.

---

### Post by speedwell68 on 2010-04-14
> **Paqman said:**
> That's not my experience at all. Finding an app that's not available in 64-bit is extremely rare. I certainly don't think they're less stable either. 64-bit on Linux is very mature.

Firefox.:D

---

### Post by Paqman on 2010-04-14
> **Cabs21 said:**
> I was basing this from my experience with Flash

Ah well, Flash is a little bit "special". Yes, Flash on 64-bit is even buggier than on 32-bit.

Protip for people fed up with Flash: Use Chrome and opt in to Youtube's HTML5 beta and you can watch any Youtube video without Flash. Woot!

---

### Post by chappajar on 2010-04-14
> **PC_load_letter said:**
> As Carlee said. Expect the same applications to take twice as much RAM, so your situation is very similar to running 32 bit on 1GB RAM.
  
This is not correct.
Yes, pointers will now effectively take 64 bits of memory, but that is not enough to double the memory needed for a program. 

> **KrisInfinity said:**
> Yeah I know the memory limit in 32bit, that's why I asked if there are other reasons for going to 64bit instead. But I don't think I'll be upgrading the RAM as there are no empty slots.

More registers, wider registers, and wider data paths, all of which can improve performance.

---

### Post by FuturePilot on 2010-04-14
If you have 64bit hardware, go 64bit. I used the 64bit version of Ubuntu with 2GB of RAM with no problem.

---

### Post by cascade9 on 2010-04-14
> **KrisInfinity said:**
> I have a Core 2 Duo E4500 processor and 2GB of ram. 

I'm planning to do a clean install when Lucid is released. 

Would 64bit bring any advantage to me?

Even at 2GB, for everyday tasks 64bit is (marginally) faster, and things like audio/video encoding are much faster- 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

That test was for 9.04 as well, I would expect that over time the 64bit advantage will get bigger.

---

### Post by Half-Left on 2010-04-14
> **cascade9 said:**
> Even at 2GB, for everyday tasks 64bit is (marginally) faster, and things like audio/video encoding are much faster- 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

That test was for 9.04 as well, I would expect that over time the 64bit advantage will get bigger.

It's a myth that you need some kind of monster machine to run 64bit. Microsoft and Apple are the ones who dumbed it down, since Linux has supported 64bit for ages now.

The up side is that it will take advantage of 4Gb of ram and above, since 32bit can only support upto 4Gb and but 64bit can address more memory which will make apps run faster.

PAE in 32bit kernels will run more than 4Gb but at cost of an overhead and only still being able to address memory in 32bits.

---

### Post by lovinglinux on 2010-04-14
I was exactly in your spot a couple of months ago, after upgrading my CPU from a P4 single core to a Core2 Duo E7500.

In terms of performance, I can't tell the difference, even when doing video encoding and other CPU intensive tasks. I didn't see a reason to go back to 32bit either.

Mozilla doesn't provide an official build of Firefox 64bit, which is important for me, but it is available from Ubuntu repositories and if you need testing build, you can get it from Mozilla nightlies repositories. I feel kind of discriminated by this policy, but I can get it anyway, one way or the other.

---

### Post by PC_load_letter on 2010-04-14
> **chappajar said:**
> This is not correct.
Yes, pointers will now effectively take 64 bits of memory, but that is not enough to double the memory needed for a program. 
...

Would you mind to elaborate? A link to an info source would also suffice. 
And if the memory requirements do not increase by 100%, do they increase by 50%, 60%? Or does this depend on what kind of programs running?

---

### Post by Half-Left on 2010-04-14
> **PC_load_letter said:**
> Would you mind to elaborate? A link to an info source would also suffice. 
And if the memory requirements do not increase by 100%, do they increase by 50%, 60%? Or does this depend on what kind of programs running?

Ultimately 64bit lets the application address more memory in bigger chunks. The more memory it can have and address, the more faster it is usually.

64bit can take more memory but make it work better, since it doesn't have the limits that 32bit has.

---

### Post by Grenage on 2010-04-14
Don't bother with x32 unless you're having problems; it's 2010, not 1999.

---

### Post by KrisInfinity on 2010-04-14
> **Half-Left said:**
> Ultimately 64bit lets the application address more memory in bigger chunks. The more memory it can have and address, the more faster it is usually.

64bit can take more memory but make it work better, since it doesn't have the limits that 32bit has.

Ok I'll be giving 64bit a try. I can always switch back if something isn't right.

Thanks everyone.

---

### Post by Paqman on 2010-04-14
> **PC_load_letter said:**
> Would you mind to elaborate? A link to an info source would also suffice. 
And if the memory requirements do not increase by 100%, do they increase by 50%, 60%? Or does this depend on what kind of programs running?

It depends greatly on what's running.

Not sure i've read anything with hard numbers, but annecdotally i'd say that I don't recall losing anything like 50%. Maybe 10-20% or so, if that.

---

### Post by WinterRain on 2010-04-14
> **Cabs21 said:**
> Also 32-bit programs are a bit more stable

Do you have proof of this? Or is it just your own conjecture? I don't have a link (I'll look) but I read that 64bit is inherently more stable.

---

### Post by Half-Left on 2010-04-14
> **WinterRain said:**
> Do you have proof of this? Or is it just your own conjecture? I don't have a link (I'll look) but I read that 64bit is inherently more stable.

It's simply not the case that 32bit apps run more stable, that's just conjecture for sure.

If an application cannot get the memory it needs in 32bit, it's more likely to be unstable, unlike 64bit where it can access much, much more.

---

### Post by KrisInfinity on 2010-04-14
Just booted the beta 2 of lucid (64bit) and sound doesn't work. The sound card isn't detected, in "Sound Preferences > Output" it's listed Dummy Output. Strangely enough it worked on 32bit beta 1 live cd. Seems like missing drivers.

---

### Post by Half-Left on 2010-04-14
> **KrisInfinity said:**
> Just booted the beta 2 of lucid (64bit) and sound doesn't work. The sound card isn't detected, in "Sound Preferences > Output" it's listed Dummy Output. Strangely enough it worked on 32bit beta 1 live cd. Seems like missing drivers.

Looks like a bit of bad luck there. Maybe file a bug report.

---

### Post by JamezQ on 2010-04-14
> **Grenage said:**
> Don't bother with x32 unless you're having problems; it's 2010, not 1999.

*But we party like it is...*


Ahem,

I have used 64 bit, I can tell you that it is faster, and really just as stable as 32 it seems.

---

### Post by WinterRain on 2010-04-14
> **JamezQ said:**
> [I]
I have used 64 bit, I can tell you that it is faster, and really just as stable as 32 it seems.

I've come to the same conclusion. My computer has never run better since switching to 64bit. It seems a bit snappier, and has been *very* stable.

The thing that annoys me is when people spread FUD about 64bit, and it's usually the people that don't run it.

---

### Post by mikewhatever on 2010-04-14
> **KrisInfinity said:**
> Just booted the beta 2 of lucid (64bit) and sound doesn't work. The sound card isn't detected, in "Sound Preferences > Output" it's listed Dummy Output. Strangely enough it worked on 32bit beta 1 live cd. Seems like missing drivers.

Try restarting pulseaudio:

pulseaudio -k

;)

---

### Post by hellmet on 2010-04-14
I've been using 64 bit ever since I upgraded to a Core2Duo 1-1/2 years ago, which is 3 Ubuntu distributions ago. The experience has gotten smoother with every release and I have absolutely no problems with my karmic install AND I have "only" 2 GB RAM without Swap. Go 64!

---

### Post by cguy on 2010-04-14
I too vouch that 64bit feels faster.

Unfortunately, Ubuntu's 64bit alternate installer CD has a serious bug with Optiarc/Sony CDROMs (reported and unresolved for years) and I can't install it. 

The 64bit Live CD is running ok, but you don't have RAID, LVM etc. available with it.

---

### Post by chris200x9 on 2010-04-14
Go 64 there is no real reason not to

---

### Post by WinterRain on 2010-04-14
> **cguy said:**
> I too vouch that 64bit feels faster.

Unfortunately, Ubuntu's 64bit alternate installer CD has a serious bug with Optiarc/Sony CDROMs (reported and unresolved for years) and I can't install it. 

The 64bit Live CD is running ok, but you don't have RAID, LVM etc. available with it.

You can install the alternate iso to a flash drive via usb startup disk creator. ;)

---

### Post by cguy on 2010-04-14
> **WinterRain said:**
> You can install the alternate iso to a flash drive via usb startup disk creator. ;)

I know, I did just that some while ago, but here's the surprise:
You still need the CD. If it isn't present in the tray, the installation would start but would soon give "Files not found" errors. ;)

---

### Post by Lightstar on 2010-04-14
I had some issues on Karmic as 64bit (sound problems, and SCIM input problems ( maybe more, I can't remember)
I went back to 32bit

Anyway, Ubuntu comes with pae now, even 32bit Ubuntu accepts over 4gb of ram.

I might retry 64 with Lucid.

---

### Post by FuturePilot on 2010-04-14
> **Lightstar said:**
> I had some issues on Karmic as 64bit (sound problems, and SCIM input problems ( maybe more, I can't remember)
I went back to 32bit

Anyway, Ubuntu comes with pae now, even 32bit Ubuntu accepts over 4gb of ram.

I might retry 64 with Lucid.

PAE is a dirty hack.

---

### Post by chappajar on 2010-04-15
> **PC_load_letter said:**
> Would you mind to elaborate? A link to an info source would also suffice. 
And if the memory requirements do not increase by 100%, do they increase by 50%, 60%? Or does this depend on what kind of programs running?

Pointers to memory addresses will now be 64 bit instead of 32 bit, but not all data in a program are pointers.  Multiple other data can be combined into a single 64 bit memory location, and so take no extra memory.
Of course, you will also lose some memory to padding, as even the best compilers can't hope to fit ALL smaller pieces of data exactly into 64 bit locations. 

So yes, memory requirements for a program increase when you go 64 bit, but they do NOT double. (I don't have a percentage for you, sorry, but it will vary from program to program).

The massive increase in the amount of addressable memory possible, and the ever decreasing, already low cost of buying RAM means this isn't really an an issue for most people in the short term, and won't be an issue for anyone in the long term.

---

### Post by Khakilang on 2010-04-15
I only had Dual core and 1.5GB RAM and I use 64 bit 9.10 Karmic Koala. I think Lucid shouldn't be a problem. Work just great.

---

### Post by Eisenwinter on 2010-04-15
You have a 64-bit CPU? Use a 64-bit OS.

That's how I see it.

Out of ideology, I only use 64-bit systems (with the exception of Windows XP).

---

