---
title: "linux and memory"
date: 2005-12-02
forum: The Cafe
---

### Post by tikal26 on 2005-12-02
hey I keep on reading the unixes including linux handle memory better than windows.  is this true?
I am wondering because I was having a conversation with someone at school and they had a  good explanation as to how macs and specially tiger handle memory better than windowo but hen I google all I get is that linux handles memory better but not how or if its true I even get article on how linux is supposed to be worst and handling memory.

---

### Post by public_void on 2005-12-02
[Link](http://www.tldp.org/LDP/tlk/tlk.html). IMO a good read about the Linux Kernal, but a deep read. So if your not too sure about the workings of memory and other aspects it can quickly overwhelm you.

---

### Post by darkmatter on 2005-12-02
Yes, they do....one of the reasons is better code sharing.

In windows...only a small portion of the code is located in shared libraries (dll's). In the unicies, a large portion of the code is shared....so opening a second instance of an application does not require loading the entire program to ram a second time...only the differences need to be loaded.

I'll find you some links...

---

### Post by tikal26 on 2005-12-02
ok now my friends say that linux does not mange memory well bacause I have a swap partition and he saya that it a prrof of it. DO I really need a swap partition

---

### Post by darkmatter on 2005-12-02
Having a swap partition does not equate to poor memory management...I've always set up swap...but my system has never used it...

Having a swap partition is not 100% necessary, but it should exist anyway...in the event that the system should need to do a memory dump...not all that likely...but still, you should always run a system that supports any possible eventuality....especially on lower ram setups.

---

### Post by xmastree on 2005-12-02
[QUOTE=tikal26]ok now my friends say that linux does not mange memory well bacause I have a swap partition and he saya that it a prrof of it. DO I really need a swap partition[/QUOTE]Windows also has a swap **file** but they call it virtual memory.
Having it in its own partition makes it faster to access.

---

### Post by darkmatter on 2005-12-02
[QUOTE=xmastree]Having it in its own partition makes it faster to access.[/QUOTE]

It also makes it a lot less ugly by isolating it from the rest of the file system....install a default windows setup *without* moving it to its own partition and watch how quickly it fragments....<shudder>

---

### Post by René Kabis on 2005-12-10
With all of the talk about memory here, does anyone know how to turn off the swap file, or prevent its creation during initial install? I have plenty of memory, and I do NOT require a swap file of any kind.

---

### Post by ssam on 2005-12-10
mac os x and windows use a swap file, linux usually uses a swap partition (but can use a swap file if you want.) one advantage with a swap file is that it can be enlarged as needed.

i am not sure about windows, but mac os x does not like it when the harddrive is to full for it to make a swap file. with the flexible linux method you can allways add a new disk and use that as swap

mac os x uses similar memory management to linux. there maybe a few tricks in the os x kernel that linux does not have, but linux probably has a few that os x doesn't.

René Kabis:
the easiest way is to comment out (put a hash at the front of the line) the swap line in /etc/fstab. some people claim that linux works faster with a swap, even if you have lots of ram though. you might still want to do it to save battery life on a laptop though.

---

### Post by jdong on 2005-12-10
[QUOTE=René Kabis]With all of the talk about memory here, does anyone know how to turn off the swap file, or prevent its creation during initial install? I have plenty of memory, and I do NOT require a swap file of any kind.[/QUOTE]

Edit /etc/fstab to remove all "swap" lines, repartition your swap partition to something more useful...

In install time, just don't let it make a swap partition -- delete it and use the space on something else....


All in all, are you really short a couple hundred MB of space? Having a swapfile around under Linux doesn't hurt performance (unlike how it does under Windows for some strange reason)

---

### Post by René Kabis on 2005-12-10
[QUOTE=jdong]Edit /etc/fstab to remove all "swap" lines, repartition your swap partition to something more useful...

In install time, just don't let it make a swap partition -- delete it and use the space on something else....


All in all, are you really short a couple hundred MB of space? Having a swapfile around under Linux doesn't hurt performance (unlike how it does under Windows for some strange reason)[/QUOTE]

Thanks!

Actually, yes, at this moment I need the space for a friend’s computer. They’ve maxed out the memory, but they only have a 4Gb hard drive. They aren’t going to use their ’puter for anything other than surfing, e-mail and listening to music, but their mp3 collection is nearly 1.5Gb in size... I’ve recommended an external drive, but it'll be a while before they can afford one (they’ve just had a baby...). By preventing the use of a swap file, they can make use of the whole 4Gb, rather than wasting 300+mb on a partition that probably won’t get used at all...

BTW, I've noticed that my initial (test) install (i’ve since wiped to zero and Spinrite the hard drive due to some problems) of Ubuntu was MUCH faster than their install of Windows XP! as well, Ubuntu used only about 90 MB of memory, which was MUCH better than the 200+Mb that XP sucked up upon booting (even with a basic install). Under XP, they NEEDED the swap file, but I believe that Ubuntu can run very happily without one at all.

---

### Post by jdong on 2005-12-10
Ok, then have fun removing the swap files. You may need a Knoppix LiveCD + QtParted to expand the existing partition(s) to take advantage of the new space.

---

### Post by René Kabis on 2005-12-10
[QUOTE=jdong]Ok, then have fun removing the swap files. You may need a Knoppix LiveCD + QtParted to expand the existing partition(s) to take advantage of the new space.[/QUOTE]

I’ll remember that if I have to modify an existing install. Right now I’ve just finished Zero-ing and Spinrite-ing the hard drive and begun a new install. The partitioning screens took a second or two to get used to, but I’ve set up a single partition on the drive without any swap at all. Now all I have to do is see how things go.

Off topic for this thread, but does a standard partition setup set the block size at 512b, or does it keep it at 4Kb? I also can't remember if Partition Magic 8.x handles the Ext3 (sp?) file system... I’d prefer to set the cluster size to 512b, but didn’t see that option in the partition wizard during the setup...

---

### Post by jdong on 2005-12-10
Blocksize is set at whatever mkfs.ext3 defaults to:
> If omitted, mke2fs  block-
              size is heuristically determined by the file system size and the
              expected usage of the filesystem (see the -T option).


In other words, it's pretty good by default.


P.S. Don't use "clusters" when talking about Linux. The term does not apply to most Linux and *nix filesystems (we use *extent*-based allocation, not cluster)... Sometimes *nix'ers get twitchy if you say Cluster too much ;)

---

### Post by poofyhairguy on 2005-12-11
[QUOTE=xmastree]Windows also has a swap **file** but they call it virtual memory.
[/QUOTE]

I just had to bump that!

---

### Post by LordHunter317 on 2005-12-11
[QUOTE=darkmatter]Yes, they do....one of the reasons is better code sharing.[/quote]Not especially.  The amount of memory shared between tasks has almost nothing to do with VM design or performance.

It only does under VM pressure.  That being said, the fact code is shared to a lesser degree can cause higher VM pressure in the same amount of physical memory.  

> In the unicies, a large portion of the code is shared....so opening a second instance of an application does not require loading the entire program to ram a second time...only the differences need to be loaded.No, it requires loading no extra code whatsoever on either platform.  

Why would you need *different code* for two instances of *the same thing*?

[quote=tikal26]ok now my friends say that linux does not mange memory well bacause I have a swap partition and he saya that it a prrof of it. DO I really need a swap partition[/quote]All modern general-purpose virtual memory systems need swap to perform optimally.

[quote=xmastree]Windows also has a swap file but they call it virtual memory.[/quote]No, they call it a paging file, and that's what's done to it.  Technically speaking, that's what is done to a Linux swap file or partition as well: paging, not swapping.  There's a small technical difference, not especially relevant here.

Both operating systems use virtual memory all the time, regardless of whether swap is enabled or not.  Virtual memory simply refers to the fact the addresses applications use aren't physical addresses in RAM, but virtual (fake for all purposes) addresses that are translated to physical ones.

> Having it in its own partition makes it faster to access.No, it doesn't.  In 2.6, there is no speed advantage to have it in a partition.  In 2.4, there was an advantage, because of the way the blocks were mapped.  AFAIK, NT always as fast as a partition would be.  It certainly is now: both NT and 2.6 keep a map of the physical blocks of the pagefile on the HDD and address them directly, bypassing the filesystem (ignoring the case where NT grows the page file).

[quote=darkmatter]It also makes it a lot less ugly by isolating it from the rest of the file system....install a default windows setup *without* moving it to its own partition and watch how quickly it fragments....<shudder>[/quote]Which cause no measurable performance loss except in some corner cases.  EXT3 and XFS get quite fragmented as well.  Ideally speaking, having your often used data, programs, and pagefile as close together as possible is the best scenario to be in.  Think about why: if the disk has to seek, you want it to seek as little as possible. 

[quote=jdong]All in all, are you really short a couple hundred MB of space? Having a swapfile around under Linux doesn't hurt performance (unlike how it does under Windows for some strange reason)[/quote]Yes, it does.  It artifically reduces the VM's ability to page out when necessary: you force it to keep older pages in memory even when they should be evicted for something newer and more important.

Moreover, you can't stop paging on either operating system: both demand page executables and memory-mapped I/O files.  That paging activity cannot be stopped no matter what, so disabling a swap file doesn't help anything.  The VM will still force other pages out to disk, and read them back in when needed.

If you want to avoid disk I/O due to memory pressure, then add more RAM.  There's nothing else you can do, and disabling swap prevents the VM from evicting anonymous data pages when it would be the best choice.

> The term does not apply to most Linux and *nix filesystems (we use extent-based allocation, not cluster)...It does if you're talking about the size of the smallest extent the FS will allocate: in this case block and cluster are interchangable.  NTFS uses extent-based allocation for it's clusters too.

If anyone has any more questions about this sort of stuff, the authortative references are *Microsoft Windows Internals, Fourth Edition* (for NT), the *IA-32 Intel Architecture System Developer's Manual, Volume Three: System Programming Guide* (for x86-specific VM and protected-mode operation) and any good Operating Systems text (the classical one by Andrew Tanenbaum is probably a good start).  You'll need a strong programming or CS background to grok any of these books.

---

### Post by psusi on 2005-12-11
> **tikal26]hey I keep on reading the unixes including linux handle memory better than windows.  is this true?[/QUOTE]

In older versions of linux, there were VM policies in place that I strongly disagreed with, and so I would have said that NT was better.  Specifically the kernel prefered to completely exhaust the filesystem cache before finally discarding memory that had not been needed for days, and won't be for days more.  This meant less cacheing, and a slower system.  I believe this has been fixed now.  

In general though, people making such claims are full of it, and should be ignored unless they can back it up.  Modern versions of linux, windows, OSX, and whatever prety much all work just as well for most purposes.  

[QUOTE=darkmatter]Yes, they do....one of the reasons is better code sharing.

In windows...only a small portion of the code is located in shared libraries (dll's). In the unicies, a large portion of the code is shared....so opening a second instance of an application does not require loading the entire program to ram a second time...only the differences need to be loaded.

I'll find you some links...[/QUOTE]

This is not true.  Loading multiple instances of an application allways shares the code pages.  Breaking out reusable code into shared libraries saves memory when multiple applications use that code, then they can all share, rather than having that code be statically linked into each program.  I am not aware of any specific code that multiple typical programs on windows statically link to, and it certainly has plenty of dlls.  

[QUOTE=darkmatter]It also makes it a lot less ugly by isolating it from the rest of the file system....install a default windows setup *without* moving it to its own partition and watch how quickly it fragments....<shudder>[/QUOTE]

This is also false.  Typically the page file is created when you install on a clean partition, and so it will likely not be fragmented.  From then on it doesn't move, so it won't ever increase in fragmentation.  

[QUOTE=jdong]Blocksize is set at whatever mkfs.ext3 defaults to:


In other words, it's pretty good by default.


P.S. Don't use "clusters" when talking about Linux. The term does not apply to most Linux and *nix filesystems (we use *extent*-based allocation, not cluster)... Sometimes *nix'ers get twitchy if you say Cluster too much  said:**
> 

The default is pretty good, but the most Linux filesystems certainly do use clusters, they just prefer to call them blocks.  IIRC, the default for ext3 is 1kb, and for reiserfs it is 4kb.  

[QUOTE=LordHunter317]
All modern general-purpose virtual memory systems need swap to perform optimally.

Only when memory is under load.  If you have a gig of ram and never use more than 200 megs, having swap space won't do you one bit of good.  Now if you typically use 80% of your ram, then some swap might be good since there may be some anonymous pages in memory that are't needed, so they can be thrown out and that ram used for caching files you're accessing, but in typical real world use, you aren't going notice any performance change with or without swap unless you're using nearly all of your physical ram.  

Other than that though, I completely agree with everything you said.

---

### Post by jdong on 2005-12-11
[QUOTE=LordHunter317]
Which cause no measurable performance loss except in some corner cases.  EXT3 and XFS get quite fragmented as well.  Ideally speaking, having your often used data, programs, and pagefile as close together as possible is the best scenario to be in.  Think about why: if the disk has to seek, you want it to seek as little as possible. 
[/quote]

XFS I disagree with. It's one of the least fragmented filesystems, thanks to delayed allocation and multiple allocation groups. It also comes with a defragger, which I run once every 6 months or so (and even then, it picks up like 5 files and calls it a day)!
> 
Yes, it does.  It artifically reduces the VM's ability to page out when necessary: you force it to keep older pages in memory even when they should be evicted for something newer and more important.

I was unsure what he meant by "plenty of RAM" -- If he meant a system with 1GB of RAM running Fluxbox with the Dillo web browser, then I'd agree that never ever would the swap ever get touched.

---

### Post by LordHunter317 on 2005-12-11
[QUOTE=psusi]This is also false.  Typically the page file is created when you install on a clean partition, and so it will likely not be fragmented.  From then on it doesn't move, so it won't ever increase in fragmentation. [/quote]No, it will become fragmented when it grows.  Fragmentation of an NT pagefile matters quite little: access to it is almost entirely random I/O anyway, so you're always seeking.  On average, the extra time from a slightly longer seek is lost in the noise.  It would only be noticable in pathological cases where the fragments were spaced very far physically apart and Windows was forced to constantly seek between them.  Needless to say, this isn't a common occurance, even with pagefile growing.

> Only when memory is under load.Well, obviously.  Talking about paging out isn't relevant in the least unless you have something to page out.

[quote=jdong]XFS I disagree with. It's one of the least fragmented filesystems, thanks to delayed allocation and multiple allocation groups. It also comes with a defragger, which I run once every 6 months or so (and even then, it picks up like 5 files and calls it a day)![/quote]It, just like NTFS or any other filesystem, can become quite heavily fragmented under certain cases.  My data partition on my filesystem was at ~20% fragmentation last I checked.

---

### Post by prizrak on 2005-12-11
The only real speed increases I ever noticed with swap files (on Windows since I never did play with Linux handling of it) was when I would statically set the swap to be 3 times the amount of RAM (recommended by one of my comp professors). Another case was when I moved the paging file to an HDD on a different controller (in the case of the IDE interface it would make little difference on the same controller since the drives cannot be accessed sumiltuneously). Disabling the paging file never did anything for performance on my Windows machines (on the laptop it killes the battery in about an hour tho). With Linux I never really had a chance to play with it or needed to really. The pre-2.6 kernels did generally fill up all of my RAM before using the swap at all, and now with half a gig of RAM I rarely even get to 50% usage under normal conditions :)
The memory management myth probably comes from the fact that most Linux application  are better optimized than Windows (including the OS itself) so they use less memory and it APPEARS to the end user that the OS is better at handling memory. Having said that though, Win2K was excellent on memory usage since it lacked all the hardware intensive eye candy and you could disable more services (w/o hurting useability) than in XP. 
Note: This is completely anecdotal and based on my experience with the OS's so the dataset is very limited, your performance may vary.

---

### Post by jdong on 2005-12-11
[QUOTE=LordHunter317]
It, just like NTFS or any other filesystem, can become quite heavily fragmented under certain cases.  My data partition on my filesystem was at ~20% fragmentation last I checked.[/QUOTE]

XFS provides no fragmentation meaasurement features, so I'm sure you're not talking about XFS there. The conditions for XFS fragmentation is that no AG's have enough continuous extents to store the file OR that the amount of time spent searching the free data trees overshadows just shoving it somewhere. For condition 1 to be true, it must be either a VERY large file (hard drive size/ 16 AG's) in which case fragmentation makes no big difference. For condition 2 to be true, it must be a small file (since there XFS has an additional free extent table in every AG sorted by size).

NTFS provides no such optimizations, and fragmentation goes crazy.

Ext3 only provides AG-like characteristics, spreading out files evenly over the free space to minimize fragmentation. This actually works quite effectively.

---

### Post by LordHunter317 on 2005-12-11
[QUOTE=jdong]XFS provides no fragmentation meaasurement features, so I'm sure you're not talking about XFS there.[/quote]Yes, it does, on a per-file basis even.  Look at the xfs_db(8) command.

> NTFS provides no such optimizations, and fragmentation goes crazy.Nope.  NTFS tries to space out files so there are adjacent blocks for them, and small files are stored directly in the MFT and aren't allocated directly on disk at all.

However, there are ways to force the former to behave very poorly: writing to two large files, one block round-robin style sequentially can cause NTFS to end up interleaving the two files on disk.

So it's not ideal, but such features do exist.

The original points were anyway that all Linux filesystems can become fragmented, just like NTFS; and that fragmentation doesn't matter generally anyway, regardless of filesystem.

---

### Post by az on 2005-12-11
[QUOTE=LordHunter317]
No, they call it a paging file, and that's what's done to it.  Technically speaking, that's what is done to a Linux swap file or partition as well: paging, not swapping.  There's a small technical difference, not especially relevant here.
[/QUOTE]

I thought it was a balance between paging and swapping set by /proc/sys/vm/swappiness

Although, with a lot of physical memory, you are probably only going to be paging, on a desktop system with typically less than 256 megs of memory, are you not doing both?

---

### Post by LordHunter317 on 2005-12-11
[QUOTE=azz]I thought it was a balance between paging and swapping set by /proc/sys/vm/swappiness[/quote]No, that controls much the kernel favors using swap space in the first place.

AFAIK, the Linux kernel will never actually swap out a process ever: evict all the pages belonging to a process to memory in a single operation.

I could be mistaken however.

---

