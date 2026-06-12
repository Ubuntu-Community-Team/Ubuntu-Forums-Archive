---
title: "With enough RAM..."
date: 2010-06-07
forum: The Cafe
---

### Post by 98cwitr on 2010-06-07
couldn't I create a tmpfs by adding this line to /etc/fstab and run my entire OS from RAM? Say 12GB of RAM should be enough (maybe even as low as 6?), and then store files on the hard drive as a slaved disk?

```

tmpfs / tmpfs defaults,noatime,mode=1777 0 0
```

Something like what's outlined here: [http://kevin.vanzonneveld.net/techblog/article/create_turbocharged_storage_using_tmpfs/](http://kevin.vanzonneveld.net/techblog/article/create_turbocharged_storage_using_tmpfs/)
What would be the implications or problems in doing this?

---

### Post by [h2o] on 2010-06-07
You would have to reinstall your OS every time your computer reboots.

---

### Post by 98cwitr on 2010-06-07
> **'[h2o] said:**
> You would have to reinstall your OS every time your computer reboots.

no, you wouldn't. see link

---

### Post by LowSky on 2010-06-07
Anyone remember this:
[Gigabyte's i-RAM]("http://www.tomshardware.com/reviews/gigabyte,1111.html")
[IMG]http://img.tomshardware.com/us/2005/09/07/can_gigabyte/i-ram-top.jpg[/IMG]

---

### Post by sydbat on 2010-06-07
Why not try it and let us know. Although I agree with [h2o] that once you shut off or reboot, you will lose your OS.

---

### Post by Shining Arcanine on 2010-06-07
Making a tmpfs your root directory seems like a bit of an issue to me, because the init scripts are stored on root and assuming you mounted stuff on the tmpfs directory as a temporary measure so that it would work, you would not be able to copy the files below the mount points to be able to unmount things without having them suddenly disappear.

Using a ram disk for your entire OS is not a bad idea and it probably can be done, but I do not see how to accomplish that with a tmpfs. I believe I read on the Gentoo Linux forums about Gentoo Linux users configuring their init scripts to mount tmpfs drives, copy files to them and then when the systems shutdown, copy the files back and unmount the drive, but I do not know much about it. I also do not think that they did it with their root drives.

---

### Post by LowSky on 2010-06-07
> **sydbat said:**
> Why not try it and let us know. Although I agree with [h2o] that once you shut off or reboot, you will lose your OS.

Read the link, everything is backed up on a hard drive, then loaded to RAM at boot.
This is purely for running large amounts of continuously changing data without read/writing to the disk. The hard drive can be set to take a snap shot to save data when you wish.

---

### Post by Shining Arcanine on 2010-06-07
> **98cwitr said:**
> no, you wouldn't. see link
In that link, the contents of the tmpfs directory are being lost every time the system reboots. This is not a problem because it is meant to be used as a read only device (ignoring the initial writes that need to be done to put the files there), but with a read/write device, the files need to be stored before shutdown, otherwise you lose them.

---

### Post by 98cwitr on 2010-06-07
that's where I write a cronjob to move any modified files from tmpfs to nonvolatile storage at shutdown.

> **sydbat said:**
> Why not try it and let us know. Although I agree with [h2o] that once you shut off or reboot, you will lose your OS.

again, no you wont...see link in OP.

I think the part you guys are missing is that the HD (SSD) is still connected to the mobo and will mount with fstab, but then transfer its ENTIRE contents into RAM.

The only problem I see is loading 6+ GB of data into memory everytime the system boots might take a little while, but if I just left my machine on...then that would be ok...Im not sure how the kernel handles volatile memory cleanup though :?

---

### Post by Shining Arcanine on 2010-06-07
> **LowSky said:**
> Read the link, everything is backed up on a hard drive, then loaded to RAM at boot.
This is purely for running large amounts of continuously changing data without read/writing to the disk. The hard drive can be set to take a snap shot to save data when you wish.
I do not believe that snapshots are possible with tmpfs drives unless you can stop everything else from writing to it (via some sort of a barrier) while you read it (e.g. mount readonly). Unless you do that, backups have the issue that files are copied in a particular order, and if you start copying, file A that you already copied is modified and then file B that has yet to be copied is also modified, your backup will contain a filesystem that your tmpfs never had, because file B would be modified, but file A would not be modified. This usually is not a big problem, but it can be, so it is important to know about it.

---

### Post by juancarlospaco on 2010-06-07
*got UPS?*

---

### Post by [h2o] on 2010-06-07
Ok, I missed the part about loading the installed OS from disk.

I still think it's a bad idea since every modification to your operating system (new applications, kernel, configuration, ...) would have to be synced to disk to not disappear at reboot.

Instead of copying the entire OS from hard drive you could load only the applications that you actually use. Which coincidentally is exactly what every major operating system already does :)

---

### Post by Shining Arcanine on 2010-06-07
> **98cwitr said:**
> couldn't I create a tmpfs by adding this line to /etc/fstab and run my entire OS from RAM? Say 12GB of RAM should be enough (maybe even as low as 6?), and then store files on the hard drive as a slaved disk?

```

tmpfs / tmpfs defaults,noatime,mode=1777 0 0
```

Something like what's outlined here: [http://kevin.vanzonneveld.net/techblog/article/create_turbocharged_storage_using_tmpfs/](http://kevin.vanzonneveld.net/techblog/article/create_turbocharged_storage_using_tmpfs/)
What would be the implications or problems in doing this?
By the way, I would like to mention that the article you linked does things incorrectly. Instead of using a tmpfs for serving from read only data files, it should be using a SquashFS inside a fixed size RAM disk or a regular fixed size RAM disk. A SquashFS stores files with very good memory efficiency because it compresses them, but it has the downside of the decompression overhead, which is so small that it usually is not an issue. A fixed size RAM disk has basically no overhead, but it has the downside that it cannot expand or contract as files are added to it or deleted from it. A tmpfs addresses the drawbacks of a RAM disk, but it introduces its own drawback in that there is dynamic memory allocation overhead associated with expansion and its book keeping should be more complicated than that of a regular RAM disk, which should make accesses a bit slower than a regular RAM disk.

Anyway, memory is a premium and a tmpfs is not the epitome of efficiency. It just looks that way because memory is so fast. A squashfs inside a fixed size RAM disk should be used for read only data when memory is a premium (when is it ever not?). A fixed size RAM disk should be used for read only data when read/write times are the most important consideration. A tmpfs should be used for data that must be written and rewritten, where the dynamic memory allocation and book-keeping penalties are insignificant and memory efficiency is important. A fixed size RAM disk should be used for data that must be written and rewritten, where there must be zero penalties whatsoever in terms of read/write latencies and memory efficiency is not an issue.

---

### Post by dragos240 on 2010-06-07
Well, the computer would boot a lot faster. But at the cost of ram usage.

---

### Post by RiceMonster on 2010-06-07
> **98cwitr said:**
> that's where I write a cronjob to move any modified files from tmpfs to nonvolatile storage at shutdown.

That sounds pretty dodgy, like an accident waiting to happen.

---

### Post by Shining Arcanine on 2010-06-07
> **'[h2o] said:**
> Ok, I missed the part about loading the installed OS from disk.

I still think it's a bad idea since every modification to your operating system (new applications, kernel, configuration, ...) would have to be synced to disk to not disappear at reboot.

Instead of copying the entire OS from hard drive you could load only the applications that you actually use. Which coincidentally is exactly what every major operating system already does :)
I seem to have trouble organizing my thoughts since I keep making new replies. Your post made me think of something else, which is that the original poster would probably be better off doing kernel modifications to add the following features, assuming that they are not already present in the kernel:

[LIST]
[*]The ability to preload all files from mounted file systems into the disk cache in the background.
[*]The ability to tell the kernel which file systems should be preloaded via flags passed to it from the boot loader.
[*]The ability to compress infrequently accessed things in the disk cache, with an internal book-keeping daemon that will figure out what needs to be compressed and what does not need to be compressed on some interval.
[*]A hook in the space recovery mechanism to see if compression for space reclamation is a good idea before anything is deleted.
[/LIST]

Then at startup, he could have his kernel preload everything in the background, which should accomplish the same thing as if he were to adopt a less granular approach where everything would be loaded into a tmpfs and then synchronized when he turns off his system. Doing things this way would have the benefit of continuous synchronization and less of a possibility of data loss should he have a kernel panic or power outage. This of course assumes that data is not deleted from the disk cache upon modifications to it on the disk. If that assumption is false, then the disk cache's behavior would need to be modified so that it can modify the stuff in its cache while it sends changes to the disk.

If he does this, I suggest that he use a system like Gentoo Linux as a development vehicle, because it is very easy to make user modifications to its kernel sources without potentially breaking other parts of the system (e.g. update scripts). It is of course possible to do this under Ubuntu Linux, but it is strongly discouraged:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Whatever he does, assuming that he tries modifying the kernel, it probably would be best to do it inside of a virtual machine using software like VirtualBox to avoid possibly messing up his system. Then when everything is working inside the virtual machine, including applying the changes to his distribution of choice, he could make the changes to his machine's kernel, although it would probably be a better idea to send the patches to upstream for review and then use the official sources (even if they are from git) to build his kernel.

---

### Post by Shining Arcanine on 2010-06-07
> **juancarlospaco said:**
> *got UPS?*

A UPS would not do anything about kernel panics or system misconfigurations (e.g. non-functional hibernation feature).

---

### Post by ssam on 2010-06-07
or install preload. that will read files so that they get cache into RAM (though i think it currently only does executables and libraries).

you could write  a script to read every file you need at boot time.

---

### Post by [h2o] on 2010-06-07
> **dragos240 said:**
> Well, the computer would boot a lot faster. But at the cost of ram usage.

So instead of loading just what it needs from the harddrive at boot it would load the entire operating system/root file system. Can you give any explanation on how that would give you a faster boot?

My guess is that boot time would skyrocket, while the time won by the system running slightly faster would be next to impossible to measure (since most used applications are loaded at boot anyway).

---

### Post by McRat on 2010-06-07
I think this will happen in the next 5 years.

The SSD's will get so fast, that you "run in place"

You will need an O/S that is tailored for it.

You will never load the O/S or programs.  Memory is allocated at the time the program is installed or updated.  The ram the application uses is not separated from the allocated area.

You can turn off the computer at any time, and turn it back on instantly.  

It will happen to save power.

---

### Post by Zerocool Djx on 2010-06-07
> **LowSky said:**
> Anyone remember this:
[Gigabyte's i-RAM]("http://www.tomshardware.com/reviews/gigabyte,1111.html")
[IMG]http://img.tomshardware.com/us/2005/09/07/can_gigabyte/i-ram-top.jpg[/IMG]

where can I   buy something like this with DDR2 ram?

---

### Post by luceerose on 2010-06-07
> **LowSky said:**
> Anyone remember this:
[Gigabyte's i-RAM]("http://www.tomshardware.com/reviews/gigabyte,1111.html")
[IMG]http://img.tomshardware.com/us/2005/09/07/can_gigabyte/i-ram-top.jpg[/IMG]
I remember one's a lot older than that, my friend.
I might have an old ISA slot one of these hanging around somewhere.

> **'[h2o] said:**
> ...boot time would skyrocket, while the time won by the system running slightly faster would be next to impossible to measure...
Bingo.

When Solid State drives are big enough & cheap enough, they'll be pretty much on par with the ram speed anyway.

---

### Post by 98cwitr on 2010-06-07
My SSD max is 285MBps

SATAII max is 375MBps theoretically.

DDR2-800 RAM is around 12,800MBps 

(400 million hertz * (2 interfaces) * (64 lines/interface) * (2 bits/line-cycle)) = 102,400 Mbit/s, or 12,800 MB/s, or 12.8 GB/s.

That's an astronomic throughput increase by comparison...thus the concept intrigues me.

---

### Post by alphaniner on 2010-06-07
> **Zerocool Djx said:**
> where can I   buy something like this with DDR2 ram?

[ACARD]("http://www.acard.com/english/fb0101.jsp?type1_title=%20Solid%20State%20Drive&type1_idno=13")

---

### Post by Shining Arcanine on 2010-06-07
> **McRat said:**
> I think this will happen in the next 5 years.

The SSD's will get so fast, that you "run in place"

You will need an O/S that is tailored for it.

You will never load the O/S or programs.  Memory is allocated at the time the program is installed or updated.  The ram the application uses is not separated from the allocated area.

You can turn off the computer at any time, and turn it back on instantly.  

It will happen to save power.
That is unlikely because:
[LIST=1]
[*]NAND Flash has a write limit, so using it in place of DRAM would ensure systems die quickly.
[*]The only reason NAND seems fast is because mechanical hard drives are slower by an order of magnitude. NAND is several orders of magnitude slower than DRAM, so replacing DRAM with NAND would cause a major system slow-down
[*]There is no way that NAND could ever improve within the span of 5 years or within the span of 1000 years to fix the above issues. They are design flaws inherent to the technology. Phase Change Memory might be able to resolve that, but it is nothing like SSDs as you know them and it still by far more than 5 years away.
[/LIST]

---

### Post by Shining Arcanine on 2010-06-07
> **98cwitr said:**
> My SSD max is 285MBps

SATAII max is 375MBps theoretically.

DDR2-800 RAM is around 12,800MBps 

(400 million hertz * (2 interfaces) * (64 lines/interface) * (2 bits/line-cycle)) = 102,400 Mbit/s, or 12,800 MB/s, or 12.8 GB/s.

That's an astronomic throughput increase by comparison...thus the concept intrigues me.

The theoretical limit of SATAII is 300MBps. The extra 75MBps you are quoting has to do with parity data that is required to be transmitted as per the specification, so the theoretical throughput will never exceed 300MBps.

Note that the SATAII specification defines a MB as being 10^6 bytes instead of the 2^20 bytes it should be. Actual throughputs for SATAII are very close to the theoretical maximum when this is taken into account. Bandwidth between the CPU and system memory uses the 1MB = 2^20 bytes definition, which means that the gap between NAND and DRAM in terms of throughput is a little wider than it would appear to be. This of coursee ignores the write limit issues, random write issues, and latency issues, which will keep NAND from ever being a replacement for DRAM. It simply is not possible, because NAND uses tiny capacitors to store bits and DRAM uses flip-flop circuits if I recall correctly.

---

### Post by McRat on 2010-06-07
> **Shining Arcanine said:**
> That is unlikely because:
[LIST=1]
[*]NAND Flash has a write limit, so using it in place of DRAM would ensure systems die quickly.
[*]The only reason NAND seems fast is because mechanical hard drives are slower by an order of magnitude. NAND is several orders of magnitude slower than DRAM, so replacing DRAM with NAND would cause a major system slow-down
[*]There is no way that NAND could ever improve within the span of 5 years or within the span of 1000 years to fix the above issues. They are design flaws inherent to the technology. Phase Change Memory might be able to resolve that, but it is nothing like SSDs as you know them and it still by far more than 5 years away.
[/LIST]

I'm not a computer engineer, that's for sure.  I just have watched the parade.  It's very hard to predict anything in the computer industry.

The amount of super-fast cache RAM in the CPU and mass storage device is growing to the point where whole programs could be preloaded.  8 mb is a pretty big program as far as executable code goes.  

Years ago, it was CPU/RAM/MSD (mass storage device).  Then they started adding cache to the CPU and MSD, and started to use MSD area as extended RAM.  At some point, the RAM becomes unnecessary as time goes on.

---

### Post by bondo101 on 2010-06-07
> **LowSky said:**
> Anyone remember this:
[Gigabyte's i-RAM]("http://www.tomshardware.com/reviews/gigabyte,1111.html")
[IMG]http://img.tomshardware.com/us/2005/09/07/can_gigabyte/i-ram-top.jpg[/IMG]

It looks like the old ram doubler cards in the old at machines when you wanted more slots for ram. :)

---

### Post by mbsullivan on 2010-06-07
While this discussion seems to have gone off into the ether, I guess I'll weigh in on some of the issues:

The [original premise]("http://ubuntuforums.org/showpost.php?p=9424779&postcount=1"):

I would say "no", at least not without some difficulty. As others have said, you'd have to worry about writing changes back to disk. Also, if you lost power you'd have to worry about leaving your system in an inconsistent state.

I'd think about more heavily using swap space for things that CAN be sped up and AREN'T mission critical, like logs (/var/...), source code (/usr/src/...), and temporary files (/tmp/), if I were you.

On the possible [speed increase]("http://ubuntuforums.org/showpost.php?p=9425297&postcount=23"):

I'm skeptical that putting ALL system files in the memory would make things too much faster, even if you did make it work. Many things, at least after some warmup period, will already be cached to RAM if you have a large amount of memory and have a low vm.swappiness.

Also, the throughputs you gave are for large sequential accesses only. The max throughput for random accesses to RAM is still 1.5 GB/s, as it has been for years. While I'm not certain, my guess is that most OS activity is largely random. Things that exhibit large sequential accesses (program loads, temporary file loads, etc.) can be brought into memory, though. Try preload, as somebody mentioned above?

On [computers you can just turn back on]("http://ubuntuforums.org/showpost.php?p=9425189&postcount=20"):

I know that some researchers ARE working on this... so I wouldn't write off the notion. See "non-volatile computing" [here]("http://tsg.ece.cornell.edu/doku.php?id=research"). However, it's not too big or fast moving of a field. I think it'll happen, but change will be gradual. Look at how much quicker computers start and suspend than they did 5 years ago!

On using [Flash memory as a RAM replacement]("http://ubuntuforums.org/showpost.php?p=9425972&postcount=25"):

At this time, you're right... there's no real reason to look at flash as a RAM replacement. It's relatively expensive, and has problems (such as the write issue you said).

However, in the future, people are looking at Flash and Flash-like non-volatile memories to replace RAM in many applications. The big reasons are (1) read power is so low and (2) apparently people are having trouble scaling DRAM past the 30-something nm size. The biggest contender is called [Phase Change Memory (PCM)]("http://en.wikipedia.org/wiki/Phase-change_memory"), but I think Flash is scalable too, albeit expensively. PCM may be able to scale down to 12nm or further, greatly increasing density and saving even more power per read.

Because of this, there are lots of things people are looking at to prevent or tolerate write failures. While it's an academic paper and really dense, [this]("ftp://ftp.cs.utexas.edu/pub/dburger/papers/ISCA10.pdf") shows a new error correcting scheme from Microsoft Research (yes, they do it, :) ) that's tailored to these types of memories. It greatly increases lifetime with little overhead.

Mike

PS: I remember something very similar to the i-RAM... Go, Cenatek Rocket Drive go!!!

[IMG]http://www.productwiki.com/upload/images/cenatek_rocket_drive.jpg[/IMG]

---

### Post by McRat on 2010-06-07
> **mbsullivan said:**
> ...

On [computers you can just turn back on]("http://ubuntuforums.org/showpost.php?p=9425189&postcount=20"):

I know that some researchers ARE working on this... so I wouldn't write off the notion. See "non-volatile computing" [here]("http://tsg.ece.cornell.edu/doku.php?id=research"). However, it's not too big or fast moving of a field. I think it'll happen, but change will be gradual. Look at how much quicker computers start and suspend than they did 5 years ago!

...

Mike

You probably already have one of these computers in your car.

The OS is custom written though.  They remember injector offsets, long term fuel trims, short term fuel trims, fuel quality, spark retard tables, etc.  There is no "ram" as we know it.  Perhaps a scratch pad or cache.  IIRC, it's only about 1 MB of tables it needs to keep updated, but you can kill the power at any time, and it starts right back up (almost) instantly.

It is fast enough to determine minute changes in crankshaft acceleration between firings at 8,000 rpm while still checking up to 64 analog sensors, and timing the injector pulses, and multi-spark coil firing.  And it never "crashes".


Sidebar:

How does your engine know it had a "misfire"?  It has no idea if the spark plug is good, whether the rod went outside the block, or if the valve broke it's head off.

It has a crankshaft position sensor that carefully monitors how the crankshaft accelerates and slows down between firing of the plugs.  It compares the acceleration to the other cylinders on their last cycle and determines if it's out of spec.  There is no "misfire" sensor.

---

### Post by Shining Arcanine on 2010-06-07
> **McRat said:**
> I'm not a computer engineer, that's for sure.  I just have watched the parade.  It's very hard to predict anything in the computer industry.

The amount of super-fast cache RAM in the CPU and mass storage device is growing to the point where whole programs could be preloaded.  8 mb is a pretty big program as far as executable code goes.  

Years ago, it was CPU/RAM/MSD (mass storage device).  Then they started adding cache to the CPU and MSD, and started to use MSD area as extended RAM.  At some point, the RAM becomes unnecessary as time goes on.

DRAM's function might be replaced in a system that uses phase change memory, but its function will always need to be fulfilled by something. That something will never be NAND. It uses capacitors to store bits, which is a similar concept to vaccum tubes. The laws of physics render it unsuitable as a replacement for DRAM and that will never change. Phase Change Memory is likely to replace NAND in 10 years, so around that time, we might see systems become available that use Phase Change memory in place of both DRAM and NAND, but we will never see either DRAM or NAND replace the other.

---

### Post by Shining Arcanine on 2010-06-07
> **mbsullivan said:**
> I'm skeptical that putting ALL system files in the memory would make things too much faster, even if you did make it work. Many things, at least after some warmup period, will already be cached to RAM if you have a large amount of memory and have a low vm.swappiness.

Putting files in memory allows you to avoid having to wait 10 milliseconds to get them every time you want them, which is a huge amount of time for a computer. Currently, software is designed to load everything it needs into RAM. If something like the unified storage/memory concept some other people mentioned became popular, that would no longer be necessary and there would be performance benefits.

> **mbsullivan said:**
> I know that some researchers ARE working on this... so I wouldn't write off the notion. See "non-volatile computing" [here]("http://tsg.ece.cornell.edu/doku.php?id=research"). However, it's not too big or fast moving of a field. I think it'll happen, but change will be gradual. Look at how much quicker computers start and suspend than they did 5 years ago!

Just imagine how much slower computers start and suspend today than they did 25 years ago. Back then, anything longer than 4 seconds was considered abnormal. today, anything shorter than 4 seconds is considered well into abnormal territory. I do not think we have really progressed much in this area.

---

### Post by mbsullivan on 2010-06-08
> DRAM's function might be replaced in a system that uses phase change memory, but its function will always need to be fulfilled by something. That something will never be NAND. It uses capacitors to store bits, which is a similar concept to vaccum tubes. The laws of physics render it unsuitable as a replacement for DRAM and that will never change. Phase Change Memory is likely to replace NAND in 10 years, so around that time, we might see systems become available that use Phase Change memory in place of both DRAM and NAND, but we will never see either DRAM or NAND replace the other.

The fact that DRAM is stored in leaky capacitive cells is what makes it volatile; it is not necessarily a feature, but rather a property of the memory. It is a somewhat necessary evil since density and cost are the most important things for memory manufacturers. While it's true that non-volatile memories don't have the same properties (limitations) as DRAM, that doesn't mean they couldn't be used as a replacement.

I'm not sure if anybody's seriously looking at NAND flash as a DRAM replacement. If anything, NOR flash would be a more realistic analogue, even if speed weren't an issue. I think, however, that more people are talking about the research-grade memories (like PCM) due to their scaling properties. There are also many other non-volatile memories that also apply: magnetoresistive RAM (MRAM) and resistive RAM (RRAM) are a couple.

The bottom line is this: DRAM may not scale past 30nm. Other (non-volatile) memories will. They also have superior read power properties. But, some suffer from high write power and hard failures after X writes. So, people are doing research to fix these problems such that maybe they could be used as DRAM replacements in the future.

I'm not disagreeing that this change will come down the line, and not with current NAND flash. I'm just staying that it's not unrealistic to think that we could possibly have a non-volatile system memory sometime in the next 5-15 years, depending on (1) how POORLY we come up with improved DRAM technologies, and (2) how WELL we come up with better replacements. The 3x node is set to hit in about 4 years time; It is supposed to be the last DRAM node that is possible without expensive new processes. 

> 
Putting files in memory allows you to avoid having to wait 10 milliseconds to get them every time you want them, which is a huge amount of time for a computer. Currently, software is designed to load everything it needs into RAM. If something like the unified storage/memory concept some other people mentioned became popular, that would no longer be necessary and there would be performance benefits.


Files are already cached to memory. You won't have to wait 10 miliseconds upon every file access, except the very first one. Since most file accesses should be repeats (after some warmup period), I'm not sure the performance difference would be noticeable.

> 
Just imagine how much slower computers start and suspend today than they did 25 years ago. Back then, anything longer than 4 seconds was considered abnormal. today, anything shorter than 4 seconds is considered well into abnormal territory. I do not think we have really progressed much in this area.

You may be right... It struck me the other day how much longer it took a Playstation game to start than an NES one. We're reverting. :( It'd be nice to be able to just turn on your computer, though! 

I do hope that the continuing popularity of netbooks and ultra-portable devices will continue to cause start times, suspend times, and such to get some attention. There's a lot of improvement that can be made, I think it's just a messy situation.

>  
The amount of super-fast cache RAM in the CPU and mass storage device is growing to the point where whole programs could be preloaded. 8 mb is a pretty big program as far as executable code goes.

Years ago, it was CPU/RAM/MSD (mass storage device). Then they started adding cache to the CPU and MSD, and started to use MSD area as extended RAM. At some point, the RAM becomes unnecessary as time goes on.

One more thing this made me think of... There was a paper out of HP Labs in 2008 (found it, [here!]("http://www.soe.ucsc.edu/classes/cmpe221/Spring09/papers/13c.pdf")) that simulated a CPU with an L3 cache using eDRAM (embedded DRAM) stacked on top of the normal CPU die (a new fabrication process). It was 192MB big. You could definitely fit a fair amount into that. They had problems coming up with proper benchmarks for it. :)

I don't think that RAM's going anywhere, though. We're just going to get a more and more complex memory hierarchy to try and hide the ridiculously long and painful latencies that we suffer from accessing memory. 

Mike

---

### Post by 98cwitr on 2010-06-09
closest thing in the market is one of these...but that's A LOT of space for my needs

[http://www.ocztechnology.com/products/solid-state-drives/pci-express/z-drive-r2/ocz-z-drive-r2-p88-pci-express-ssd.html](http://www.ocztechnology.com/products/solid-state-drives/pci-express/z-drive-r2/ocz-z-drive-r2-p88-pci-express-ssd.html)

and that's still only 1.38GBps instead of 12.xGBps


and for $150-$300, I can get 10 times the speed and enough space for my OS and apps.

> **Shining Arcanine said:**
> The theoretical limit of SATAII is 300MBps. The extra 75MBps you are quoting has to do with parity data that is required to be transmitted as per the specification, so the theoretical throughput will never exceed 300MBps.


That's for a single drive though, plenty of people have breached 300MBps on SATAII using RAID0 setup.

This dude hit 2GBps on an ungodly amount of SSDs

[http://www.youtube.com/watch?v=96dWOEa4Djs](http://www.youtube.com/watch?v=96dWOEa4Djs)

---

### Post by mbsullivan on 2010-06-11
> 
That's for a single drive though, plenty of people have breached 300MBps on SATAII using RAID0 setup.

This dude hit 2GBps on an ungodly amount of SSDs

[http://www.youtube.com/watch?v=96dWOEa4Djs](http://www.youtube.com/watch?v=96dWOEa4Djs)

That IS pretty cool. 

I've found speed on a ramdrive to be fast, but not TOO blazing. On my DDR2667, copying files to files is testing at about 536.69 MB/s. That's good, but it's a far cry from the theoretical maximum of 10666 MB/s. And keep in mind that this is a purely sequential operation.

> closest thing in the market is one of these...but that's A LOT of space for my needs

[http://www.ocztechnology.com/product...press-ssd.html](http://www.ocztechnology.com/product...press-ssd.html)

and that's still only 1.38GBps instead of 12.xGBps


I think something like that might be your best bet if you'd like to put your whole system in a fast medium. Putting it in RAM (for real) is going to be a massive pain. This would give you good size, very respectable speeds, and it's bootable. Not a bad price, either. A whole lot cheaper than a bunch of DRAM would be. 

As an aside, when you originally posted the premise, I thought that you just had a system (with a server board, for instance) that just had an ungodly amount of RAM. 48-64GB, for instance, and wanted to use it for a workstation computer.

I've been thinking a bit more about it... And if this were the case, then I think that in addition to the previous things I mentioned (/tmp/, /usr/src/, /var/), you would also see the biggest performance improvement by putting (smaller) parts of your home directory in RAM. They're likely to contain sequential data files that need to be loaded by programs. Also, the /usr/share/ folder contains data (icons, themes) which are often read and not often written to and used across many programs, which would be ideal for loading into RAM @ the beginning.

I think that you would also see some performance benefit from putting dynamically linked libraries and programs into RAM, but it'd be messy to do so, since you could thrash the state of your drive. I'd use preload to do it. Also, you might see some benefit from doing /etc/, but that sounds risky to me, as well. I'd count on these files being resident in memory, given you have a lot of RAM and a low swappiness.

Mike

---

### Post by happyhamster on 2010-06-11
I've been running Jaunty from RAM for several days now. See this excellent and informative tutorial: [http://ubuntuforums.org/showthread.php?t=1499338](http://ubuntuforums.org/showthread.php?t=1499338)

There are issues, but no real showstoppers (at least not for me). It was a lot of fun to test too IMO.

---

