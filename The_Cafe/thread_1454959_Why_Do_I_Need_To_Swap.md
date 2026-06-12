---
title: "Why Do I Need To Swap"
date: 2010-04-15
forum: The Cafe
---

### Post by Khakilang on 2010-04-15
Why do I need to swap memory when my System monitor show that I am using half of my 1.5GB RAM being used? As you can see on the attachment. How do I disable the swap memory? So that I can maximise my disk storage. Thanks in advance.:confused::confused::confused:

[ATTACH]153348[/ATTACH]

---

### Post by PhilMize on 2010-04-15
Well, I'm fairly sure swap is mainly used for sleep/suspend sort of functions. Or if you have really low about of memory swap will be used. I posted a similar question that taught me a little more about swap partitions. Maybe it'll help you out a bit.

[http://ubuntuforums.org/showthread.php?t=1454296](http://ubuntuforums.org/showthread.php?t=1454296)

If you open up terminal and type "free -m". It shows you if your swap partition is even enabled to be used.

```
phil@phil-netbook:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2005       1276        728          0         92        483
-/+ buffers/cache:        700       1304
Swap:         1309          0       1309

```

---

### Post by undecim on 2010-04-15
```
sudo swapoff -a
``` will disable all swap devices (until you reboot)

There is also the swappiness variable. If you run
```
echo 0 | sudo tee /proc/sys/vm/swappiness
``` It will disable swap except for when you run out of memory. The default is 60, which will start using swap after you have used 40% of your memory for programs. Some people think this is better or worse for various reasons and misunderstandings as to the definition of "fast". If you often use most of your ram for programs, then you may want to leave this around 20-40 or so.

To make that setting permanent, just add this line to /etc/sysctl.conf
```
vm.swappiness=0
```
for example
```
echo "vm.swappiness=0" | sudo tee -a /etc/sysctl.conf
```

And if you just want to completely do away with swap, you can remove the swap line from /etc/fstab, boot a live cd, and use GParted to remove the swap partition and expand your / or /home partition. If you do this though, you won't be able to hibernate.

---

### Post by Frogs Hair on 2010-04-15
If you use hibernate you need swap . search swapiness or swap in the forum and you find threads on this topic .

---

### Post by juancarlospaco on 2010-04-15
***Why not?***

---

### Post by Astenorh on 2010-04-15
To temporarily disable swap without freeing space:

```
swapoff /dev/sdaX 
```

Where X is the number of your swap partition.

To disable permanently: 

- you will have to edit your /etc/fstab, simply add an "#" in front of the line containing swap. That will desactivate the swap, but the disk space will still be allocated. 

```
gksudo gedit /etc/fstab
```

- Then you will have to modify our partition table, i.e, remove the partition and increase the size of your main partition. To do that you need to boot a live cd, and use GParted (or some other partitioning program).

However having a swap is useful, it extends your physical memory using some which is on the disk. It comes handy when you using a big of chunk of memory, the operating system will automatically move some of the memory "not in use" to the disk. By "not in use" I mean some application is using that memory but it hasn't been for some time. So I would rather recommend to make the swap partition smaller.

---

### Post by Eisenwinter on 2010-04-15
> **juancarlospaco said:**
> ***Why not?***

Because 1.5GB of RAM is plenty.

I run a system which has 1GB of RAM, and I don't even have a swap partition. Never ran into any problems.

---

### Post by NightwishFan on 2010-04-15
I would use at least 512mb of SWAP just in case, but you still probably will not be able to hibernate. It is not strictly needed, but I would advise having a small bit at least to avoid a kernel panic if you accidentally run 2 copies of a game or open a big image in gimp. I actually have swap on a flash drive for my one system. (Not sure how that differs from a disk, but it seems to work well.)

I think swappiness is more pressure based than percentage based. The value of 60 is fine, even higher like 100 should be used on desktop systems. Sure swap is slower, but it keeps the more recent memory in RAM, and swaps out the older stuff. Besides, swapped memory is faster than loading it fresh from the disk again because it is already memory mapped.

Really do not worry about swap. If you do not use hibernate, make sure you have 512-1000mb of swap. If you do use hibernate, have about 1.3x your memory. If you are not low on disk space, leave it as it is.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by aysiu on 2010-04-15
If you really don't like swap, don't use it.

I don't use it on my HP Mini now, and I didn't use it on my Asus Eee PC before. (If you have a 16 GB or 4 GB SSD, you don't want to spare even 512 MB of disk space for a swap partition.)

No problems whatsoever, and that's with only 2 GB of RAM.

---

### Post by sydbat on 2010-04-15
It always depends on what you do. 

If you do video editing, for example, swap is good. Or if you multi-task to the point of having a LOT of apps open at one time (and are running stuff in each app), then swap is good.

However, if you do NOT do anything memory intensive, swap is likely just taking up HDD space *for you*. Follow some of the above instructions to disable/remove it.

Personally, I have 2GB of RAM and 2GB of swap. I do not require the swap all the time, but it's there when I need it.

---

### Post by aysiu on 2010-04-15
I should also mention that I always suspend to RAM (or "sleep") instead of suspending to disk (or "hibernating").

For hibernation, you need a swap partition.

---

### Post by juancarlospaco on 2010-04-15
Swap is optional on Linux, 
you can install it without any error if theres no Swap.

---

### Post by saulgoode on 2010-04-15
[http://forums.debian.net/viewtopic.php?f=5&t=50738&p=291623#p291623](http://forums.debian.net/viewtopic.php?f=5&t=50738&p=291623#p291623)

---

### Post by Xbehave on 2010-04-15
Disk space is cheap (100x cheaper than ram), swap space lets you free up ram to use for cache, which in turns speeds up disk access (which is 100x slower than ram).

If you don't want to use a swap partition that's fine but you won't get any sympathy from me when a flash plug-in crashes your window manager because of an OOM choice!

---

### Post by aysiu on 2010-04-15
> **Xbehave said:**
> Disk space is cheap (100x cheaper than ram) Not SSD space. > , swap space lets you free up ram to use for cache, which in turns speeds up disk access (which is 100x slower than ram). I've experienced no slowness without a swap partition.

> If you don't want to use a swap partition that's fine but you won't get any sympathy from me when a flash plug-in crashes your window manager because of an OOM choice! Haven't had Flash crash my window manager.

---

### Post by Warpnow on 2010-04-15
The bigger issue with SSDs is swap increases drastically the number of reads and shortens the life of the drive.

---

### Post by NightwishFan on 2010-04-16
Mount the ssd with a fifo queue and noatime, that should inprove performance and life a great deal.

---

### Post by chappajar on 2010-04-16
> **Xbehave said:**
> Disk space is cheap (100x cheaper than ram), swap space lets you free up ram to use for cache, which in turns speeds up disk access (which is 100x slower than ram).

If you don't want to use a swap partition that's fine but you won't get any sympathy from me when a flash plug-in crashes your window manager because of an OOM choice!

There seems to be some circular logic here...?
Increase your use of swap, and so have more RAM available for caching - ok
But the cost of this is more disk access (swap, not whatever's cached)

 So you are decreasing your disk access by increasing your disk access... 
(I have nothing against swapping, btw)

> **NightwishFan said:**
> Mount the ssd with a fifo queue and noatime, that should inprove performance and life a great deal.

Curious: What is the default disk scheduling for SSDs, and why isn't it FIFO?

Also, I can't think of a reason why FIFO will result in less SSD wear. 
EDIT: on second thought, perhaps you only meant FIFO would improve performance, and the noatime suggestion was the only one related to life?

---

### Post by Khakilang on 2010-04-16
The more I use Linux the more I learn. Thanks!

---

### Post by saulgoode on 2010-04-16
> **chappajar said:**
> There seems to be some circular logic here...?
Increase your use of swap, and so have more RAM available for caching - ok
But the cost of this is more disk access (swap, not whatever's cached)

 So you are decreasing your disk access by increasing your disk access... 
(I have nothing against swapping, btw)
It depends on how often the swapped/cached data is being accessed. If (as a simplified example) you have a large image loaded in your web browser and decide to compile a large program such as the kernel or GIMP, the compiler will need to access the contents of <stdio.h> thousands of times. It makes sense to save the browser's data to swap (one disk operation, plus a later restoration of the data) so that the contents of <stdio.h> can remain cached in memory obviating the need for thousands of disk accesses during the compilation.

---

### Post by NightwishFan on 2010-04-16
Using the noop scheduler will avoid latency and overhead due to seeks that do not occur on ssds, and noatime will avoid needless file writes. (Though they are not always needless).

---

### Post by K.Mandla on 2010-04-16
You can run without swap if you want to; generally speaking there's no huge risk involved unless you crush your system with a huge memory load. Then scientific progress goes "boink."

I ran a system with Xorg et al. on 16Mb of physical memory once, [and no swap]("http://kmandla.wordpress.com/2009/09/08/a-thousand-words-10mb/"). It was terrible. ;)

---

### Post by chappajar on 2010-04-16
> **saulgoode said:**
> It depends on how often the swapped/cached data is being accessed.
...

Yeah, of course whether it's an improvement or not will depend on what you do.
Personally I do use a swap partition, with plain old default swappiness.

 > **NightwishFan said:**
> Using the noop scheduler will avoid latency and overhead due to seeks that do not occur on ssds, and noatime will avoid needless file writes. (Though they are not always needless).

I don't quite follow the first half of that sentence NwF.  
Of course I agree that a FIFO algorithm is best for SSD (see my last post), but you say it will avoid seek latency, and that seek latency isn't present anyway...
There will be no seek latency regardless of scheduling algorithm on SSD, so I wonder if you have written something slightly different to what you meant? 

And for noatime I agree again ;) (I wasn't asking about this.)
I use noatime on my HDDs, and recommend noatime or relatime to any newb who asks. 

Sill curious: do you know the default algorithm that will be used for an SDD in Ubuntu? (I don't, but I'd like to)

---

### Post by NightwishFan on 2010-04-16
The SSD wont seek but the i/o scheduler (CFQ) will try.

---

### Post by chappajar on 2010-04-16
> **NightwishFan said:**
> The SSD wont seek but the i/o scheduler (CFQ) will try.

I haven't read any details on CFQ, so I could be missing something here, but once the read/write is complete CFQ isn't going to just hang until an expected completion time, it's going to go straight to whatever is queued next.
For an SSD there's never going to be any seek latency. 

I'm not quite sure how we got to this point, because we both seem to think a FIFO algorithm is a better algorithm for SSDs.

---

### Post by NightwishFan on 2010-04-16
CFQ optimizes for the physical movement of a drive, but not as much as anticipatory.

---

### Post by chappajar on 2010-04-16
> **NightwishFan said:**
> CFQ optimizes for the physical movement of a drive, but not as much as anticipatory.

I'm really struggling to find your point now.  There is no physical movement in an SSD.

---

### Post by WinterRain on 2010-04-16
I just make my swap about 300mb and call it a day. I never use any swap though.

---

### Post by NightwishFan on 2010-04-17
The **scheduler itself** pauses to optimize for the physical movement of a drive.
[QUOTE='Wikipedia']While CFQ does not do explicit anticipatory IO scheduling, it achieves the same effect of having good aggregate throughput for the system as a whole, by allowing a process queue to idle at the end of synchronous IO thereby "anticipating" further close IO from that process. It can be considered a natural extension of granting IO time slices to a process.[/QUOTE]
[QUOTE='Wikipedia]NOOP scheduler is best used with solid state devices such as flash memory or in general with devices that do not depend on mechanical movement to access data (meaning typical "hard disk" drive technology consisting of seek time primarily, plus rotational latency). Such non-mechanical devices do not require re-ordering of multiple I/O requests, a technique that groups together I/O requests that are physically close together on the disk, thereby reducing average seek time and the variability of I/O service time.[/QUOTE]

[http://en.wikipedia.org/wiki/Anticipatory_scheduling](http://en.wikipedia.org/wiki/Anticipatory_scheduling)
[http://en.wikipedia.org/wiki/CFQ](http://en.wikipedia.org/wiki/CFQ)
[http://en.wikipedia.org/wiki/Noop_scheduler](http://en.wikipedia.org/wiki/Noop_scheduler)

---

### Post by chappajar on 2010-04-17
> **NightwishFan said:**
> The **scheduler itself** pauses to optimize for the physical movement of a drive.



Thanks, this is what I needed to know.  Anticipatory explicitly pauses, and CFQ does so implicitly, no?
It's quite difficult to get information out of you when you only give single sentence answers.

---

### Post by NightwishFan on 2010-04-17
I fail to see why you are being rude to me. Not being a developer and only an layman researcher on such topics. I only know single sentence answers. I am not mad at you for being curious, I just did not know how to explain what I meant.

---

### Post by chappajar on 2010-04-17
> **NightwishFan said:**
> I fail to see why you are being rude to me. Not being a developer and only an layman researcher on such topics. I only know single sentence answers. I am not mad at you for being curious, I just did not know how to explain what I meant.

Sorry if that came across as rude, it wasn't my intention.
Just pointing out that single sentence posts are usually a slow and tedious way to share information.

---

### Post by NightwishFan on 2010-04-17
You are quite correct. I see what you mean. I am not offended I just was not sure if your question was answered to your satisfaction or not. Do not trust me entirely, I read a lot about this and have used a lot of configurations extensively, but anything I am used to could be out of date at the next kernel update. For example CFQ recently has got improvements to being interactive, which may help for SSDs as well.

---

### Post by chessnerd on 2010-04-18
If you want, you can remove your swap partition, as described by astenorh above, and then use a swap file. This is what I have to do on my laptop because it has four partitions in use (Vista, Windows 7, Ubuntu, and Recovery). For details on how to create and activate this file, you can look at Mr Swillis' post in this thread: [http://ubuntuforums.org/showthread.php?t=1263432](http://ubuntuforums.org/showthread.php?t=1263432)

With a swap file, as opposed to a partition, if you run into problems with storage space you can deactivate the swap, delete the file, make a new one that is smaller, and reactivate it again without even having to reboot.

---

