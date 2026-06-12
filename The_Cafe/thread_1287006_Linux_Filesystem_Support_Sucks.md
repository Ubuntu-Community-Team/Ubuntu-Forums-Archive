---
title: "Linux Filesystem Support Sucks"
date: 2009-10-09
forum: The Cafe
---

### Post by Penguin Guy on 2009-10-09
Okay well this whole thread pretty much boils down to the fact that it is quite hard to make an operating system compatible with a closed source filesystem. It does annoy me a bit, but not so much now I realize there's a good reason for it not being possible. I've listed arguments made in this topic, with any counter-argument indented below them:

```

Linux has bad filesystem compatibility in general
--[Windows filesystem support is worse (less filesystems supported)]("http://ubuntuforums.org/showpost.php?p=8079254")
--[Not many people want to defrag' NTFS in Linux]("http://ubuntuforums.org/showpost.php?p=8079639")
--EXT is the superior filesystem anyway, [even Windows doesn't like NTFS]("http://ubuntuforums.org/showpost.php?p=8079654")
--[Patents limit filesystem module development]("http://ubuntuforums.org/showpost.php?p=8079454")
--[There is no FAT/NTFS/HFS+ spec]("http://ubuntuforums.org/showpost.php?p=8079134")
----There is [official NTFS and FAT spec']("http://www.ntfs.com/") and [official HFS+ source code]("http://www.opensource.apple.com/source/xnu/xnu-1228.15.4/bsd/hfs/").

Hidden files don't work on FAT or NTFS for Linux
--[It would break a lot of Linux programs if this was done]("http://ubuntuforums.org/showpost.php?p=8079851")
--[The dot at the start of a hidden file is a POSIX standard]("http://ubuntuforums.org/showpost.php?p=8079482")
--Not many people care weather hidden files are shown or not
--[NTFS specification says that special characters are allowed]("http://ubuntuforums.org/showpost.php?p=8081832")

iPod's don't work very well
--Not true

```

I've marked this topic as solved because I think it's ran it's course and there isn't much point in continuing the discussion. Thanks to everyone who contributed, sorry again for the original, unfair topic title.

---

### Post by jeremyswalker on 2009-10-09
Is Windows filesystem support any better?

---

### Post by hoppipolla on 2009-10-09
> **jeremyswalker said:**
> Is Windows filesystem support any better?

Very well said...

I have never had any problems with filesystem support on Linux I find it to be very good... maybe there are little niggles that I haven't spotted yet but they can't be that bad!

---

### Post by Penguin Guy on 2009-10-09
> **jeremyswalker said:**
> Is Windows filesystem support any better?
Yes - Windows has full support for NTFS which is used on every Windows instillation (about 95% of computers), whereas Linux doesn't, but instead has support for EXT, ReiserFS, JFS, etc (probably around 3%?). On top of that, Linux doesn't support FAT hidden files (FAT is used on most USB drives).

---

### Post by -grubby on 2009-10-09
I'd say it's pretty good considering I don't know of any available NTFS, FAT, or HFS+ specs.

---

### Post by Penguin Guy on 2009-10-09
> **-grubby said:**
> I'd say it's pretty good considering I don't know of any available NTFS, FAT, or HFS+ specs.
[NTFS/FAT Spec']("http://www.ntfs.com/")
However you seem to be right about HFS - I couldn't find any spec' for that.

---

### Post by mikewhatever on 2009-10-09
If you need full and comprehensive support of the Windows file systems, the solution is obvious, use Window. These are closed source file system which may never be fully supported by Linux. It's quite obvious, so why bitch about it?

---

### Post by Xbehave on 2009-10-09
> **Penguin Guy said:**
> Yes - Windows has full support for NTFS which is used on every Windows instillation (about 95% of computers), whereas Linux doesn't, but instead has support for EXT, ReiserFS, JFS, etc (probably around 3%?). On top of that, Linux doesn't support FAT hidden files (FAT is used on most USB drives).
Windows has no read (let alone write) support for:
[LIST]
[*]ext2 (3rd party drivers available)
[*]ext3 (ext2 drivers available)
[*]ext4
[*]btrfs
[*]xfs
[*]JFS
[*]resierfs (3rd party drivers available, apparently)
[*]OCFS2
[*]GFS
[*]ADFS file system support 
[*]Amiga FFS file system support
[*]eCrypt filesystem layer support 
[*]Apple Macintosh file system support
[*]Apple Extended HFS file system support 
[*]BeOS file system (BeFS) support (read only)
[*]BFS file system support 
[*]EFS file system support (read only) 
[*]Journalling Flash File System v2 (JFFS2) support 
[*]UBIFS file system support 
[*]Compressed ROM file system support (cramfs) 
[*]SquashFS 4.0 - Squashed file system support 
[*]FreeVxFS file system support (VERITAS VxFS(TM) compatible) 
[*]Minix file system support 
[*]SonicBlue Optimized MPEG File System support 
[*]OS/2 HPFS file system support 
[*]QNX4 file system support (read only) 
[*]ROM file system support 
[*]System V/Xenix/V7/Coherent file system support 
[*]UFS file system support (read only) 
[*]NILFS2 file system support
[/LIST]

linux at least has read/write support for FAT,NTFS even if doesn't offer  defragmentation!

---

### Post by Bodsda on 2009-10-09
> **Penguin Guy said:**
> Yes - Windows has full support for NTFS which is used on every Windows instillation (about 95% of computers), whereas Linux doesn't, but instead has support for EXT, ReiserFS, JFS, etc (probably around 3%?). On top of that, Linux doesn't support FAT hidden files (FAT is used on most USB drives).

So what your saying is that it is terrible that Linux supports Linux filesystems and has relatively good support for other filesystems but its wonderful that windows can support its own filesystem... interesting

---

### Post by Penguin Guy on 2009-10-09
> **Bodsda said:**
> So what your saying is that it is terrible that Linux supports Linux filesystems and has relatively good support for other filesystems but its wonderful that windows can support its own filesystem... interesting
Yes; NTFS is used more than all the open source ones combined, so it is actually a lot more useful than support for ReiserFS and suchlike - if the Linux people can make a filesystem, why can't they make Linux compatible with an existing one?

---

### Post by jeremyswalker on 2009-10-09
> **Penguin Guy said:**
> Yes; NTFS is used more than all the open source ones combined, so it is actually a lot more useful than support for ReiserFS and suchlike - if the Linux people can make a filesystem, why can't they make Linux compatible with an existing one?

I would be very curious to see your source on this information. What filesystems do you suppose the vast majority of the Internet and various other areas outside of the desktop world use?

---

### Post by solitaire on 2009-10-09
> **Penguin Guy said:**
> Yes; NTFS is used more than all the open source ones combined, so it is actually a lot more useful than support for ReiserFS and suchlike - if the Linux people can make a filesystem, why can't they make Linux compatible with an existing one?

Then blame MICROSOFT for crappy NTFS support in Linux. 

**They** own the file system and keep it closed source. So it can only get better in very small stages by people, who are a lot smarter than you or me, reverse engineering the file system and bringing that into the support.

File systems are VERY complicated things, you can't just whip one up in a few months using your little netbook and expect it to be stable, It takes YEARS of testing and trials before it ever reaches the public.

If YOU want better NTFS support then complain to Microsoft!! They can produce a Linux Module for NTFS support in a few months, since they have access to ALL the internal documentation and coding.

Or here's another Idea! if you don't like the current NTFS support....

...
...

Write your own!!

I'm sure you can pick up a copy of the current ntfs-3g source code somewher and take a look and see where all those other smarter people went wrong....

---

### Post by Penguin Guy on 2009-10-09
> **jeremyswalker said:**
> I would be very curious to see your source on this information. What filesystems do you suppose the vast majority of the Internet and various other areas outside of the desktop world use?
That is a fair point, yes until now I had only been considering the desktop side of things. As I have added to my original post, I mean no offense by this topic and when I say it 'Sucks' I am of course exaggerating - compared to Windows, it is very good, but compared to the rest of Linux, I still think it falls short.

---

### Post by Xbehave on 2009-10-09
> **Penguin Guy said:**
> Yes; NTFS is used more than all the open source ones combined, so it is actually a lot more useful than support for ReiserFS and suchlike - if the Linux people can make a filesystem, why can't they make Linux compatible with an existing one?Why is NTFS more useful? FAT is useful because its widely used by devices (which more often than not are running linux) and FAT support in the kernel is pretty good (even if it is cripled by patents in the US)

---

### Post by scragar on 2009-10-09
What is the complaint about hidden files? Linux does things differently to windows, I don't hear the OP complaining that hidden files on linux show up on a windows machine. At least linux is following the POSIX standards for that(and microsoft make it up as they go along, not that there's a problem with that, but it does cause compatibility problems).

Hidden files on a USB device show up as normal files in linux, so what?

---

### Post by Penguin Guy on 2009-10-09
> **scragar said:**
> What is the complaint about hidden files? Linux does things differently to windows, I don't hear the OP complaining that hidden files on linux show up on a windows machine. At least linux is following the POSIX standards for that(and microsoft make it up as they go along, not that there's a problem with that, but it does cause compatibility problems).

Hidden files on a USB device show up as normal files in linux, so what?
Well actually what I was trying to say was that an operating system should respect the filesystem spec, rather than Linux should stop suing dot-hidden-files, but if the whole dot-hiidden-file thing is actually a POSIX standard, then I guess that's okay.

---

### Post by Frak on 2009-10-09
> **-grubby said:**
> I'd say it's pretty good considering I don't know of any available NTFS, FAT, or HFS+ specs.
If you want, you can browse through the HFS source code. [http://www.opensource.apple.com/source/xnu/xnu-1228.15.4/bsd/hfs/](http://www.opensource.apple.com/source/xnu/xnu-1228.15.4/bsd/hfs/)

---

### Post by Shibblet on 2009-10-09
> **Penguin Guy said:**
> This has been annoying me for a while, just wanted to know what everyone else thinks.

[LIST]
[*]No support for NTFS and FAT hidden files (adding a dot hides them on Linux but obviously not on Windows)
[*]HFS+ map partitions not detected (so we can't actually copy files onto/off of an ipod without extra software)
[*]No NTFS defrag module (we can't even see how much space is being used up)
[/LIST]

Just a guess... but NTFS, being proprietary Microsoft technology, wouldn't be given out to the open source community, making complete compatibility a secondary factor to basic functionality.

---

### Post by lykwydchykyn on 2009-10-09
I suppose the real problem is translating file attributes like "hidden" into a POSIX filesystem.  

Think about what a "hidden file" means; it basically means that any kind of file browser/lister (including terminal apps) are supposed to suppress listing this file by default.

The NTFS-3G driver CAN read AND write hidden-file flags (see [http://www.tuxera.com/community/ntfs-3g-advanced/extended-attributes/](http://www.tuxera.com/community/ntfs-3g-advanced/extended-attributes/)).  

I suppose if there were a real clamour and movement to honor this flag in various file-browsing applications/libraries, maybe it would happen.  I don't know offhand what it would take to make this happen in the code.

---

### Post by Dimitriid on 2009-10-09
Well my logic is this: Until wine is virtually fail proof for most applications there is no need to fine tune or have extra control on windows volumes, read/write of non-hidden files suffices at this point.

Once ( or sadly maybe if ) virtualization and other techniques improve for windows applications under linux, then I might see the point of improving windows filesystem support on GNU Linux.

---

### Post by Penguin Guy on 2009-10-09
> **solitaire said:**
> 
Write your own!!

I'm sure you can pick up a copy of the current ntfs-3g source code somewher and take a look and see where all those other smarter people went wrong....
Firstly; I took a look at the source code and yes it is a lot more complicated than I thought, sorry for underestimating the diffuculty of creating a filesystem.
As for writing my own: I only started using Linux about half a year ago, and writing my own ntfs module would require me to:

[LIST]
[*]Know C (I know a little, but not nearly enough)
[*]Know the structure of Debian packages (I'm working on this by trying my skills on a simple Debianization of an icon theme)
[*]Know basically how the whole kernel works so I can change what the dot at the start of a file does (probably best to get better at C before messing around with the kernel)
[/LIST]
Otherwise, yeah - I'd give it a go.

---

### Post by Faolan84 on 2009-10-09
> **lykwydchykyn said:**
> I suppose the real problem is translating file attributes like "hidden" into a POSIX filesystem.  

Think about what a "hidden file" means; it basically means that any kind of file browser/lister (including terminal apps) are supposed to suppress listing this file by default.

The NTFS-3G driver CAN read AND write hidden-file flags (see [http://www.tuxera.com/community/ntfs-3g-advanced/extended-attributes/](http://www.tuxera.com/community/ntfs-3g-advanced/extended-attributes/)).  

I suppose if there were a real clamour and movement to honor this flag in various file-browsing applications/libraries, maybe it would happen.  I don't know offhand what it would take to make this happen in the code.

In that case you could add an option in the file management libraries (lister and viewers respectively) to something to the effect of:

======================================================
( ) Display hidden files by POSIX standard
( ) Display hidden files by file system standards
( ) Hybrid display mode
======================================================

I could dig an option like that, but I don't want Nautilus to one day just start doing that after an upgrade and leave me wondering "WTF?!". I prefer the POSIX standard myself, rather than the idea of using an actual file system attribute associated with the file to store this data. It's a lot easier secondly it's a known standard that's been used longer than the Windows / DOS style "hidden" attribute.

I just wish Microsoft would get on board with simple standards like this. Adhering to POSIX by default and not through some subsystem that you have to buy special business version, activate, run separately just to get it to work. That's not supporting POSIX.

---

### Post by hoppipolla on 2009-10-09
is this thread a joke? lol :)

---

### Post by Shibblet on 2009-10-09
> **hoppipolla said:**
> is this thread a joke? lol :)

No, this thread is an educational experience.

---

### Post by hoppipolla on 2009-10-09
> **Penguin Guy said:**
> Yes - Windows has full support for NTFS which is used on every Windows instillation (about 95% of computers), whereas Linux doesn't, but instead has support for EXT, ReiserFS, JFS, etc (probably around 3%?).

That's because those are LINUX FILESYSTEMS... lol

---

### Post by Penguin Guy on 2009-10-09
> **Frak said:**
> If you want, you can browse through the HFS source code. [http://www.opensource.apple.com/source/xnu/xnu-1228.15.4/bsd/hfs/](http://www.opensource.apple.com/source/xnu/xnu-1228.15.4/bsd/hfs/)
Wow. I'm guessing we aren't allowed to use this then..?

---

### Post by oldsoundguy on 2009-10-09
The mantra has to be invoked here:

"Linux is NOT Windows" (repeat ad nausium)

You are lucky that Linux provides methods of running Windows at ALL!  (Windows does not provide for the running of Linux within it's system .. until Win7 hits and they will have VM loaded already.  As to IF it works .. jury is out!)
Using Wine for running some programs, or using a dual boot, or using VM ware, or using a SECOND hard drive, or (as some now are doing) resorting to a SEPARATE computer for Windows.

The OP complaint that Linux does not MAINTAIN the Windows crap should be looked at as simply WHY SHOULD IT?

Most migrate to Linux to get away from the constant need for protection and maintenance and vigilance required to keep a Windows system in operation.

---

### Post by koenn on 2009-10-09
> **Penguin Guy said:**
> Firstly; I took a look at the source code and yes it is a lot more complicated than I thought, sorry for underestimating the diffuculty of creating a filesystem.
As for writing my own: I only started using Linux about half a year ago, and writing my own ntfs module would require me to:

[LIST]
[*]Know C (I know a little, but not nearly enough)
[*]Know the structure of Debian packages (I'm working on this by trying my skills on a simple Debianization of an icon theme)
[*]Know basically how the whole kernel works so I can change what the dot at the start of a file does (probably best to get better at C before messing around with the kernel)
[/LIST]
Otherwise, yeah - I'd give it a go.
yet you feel qualified to criticize the people who went through the trouble of learning all that and the spend their time trying to accomplish compatibility with a filesystem that was designed to only work with 1 operating system ...

impressive.

---

### Post by Screwdriver0815 on 2009-10-09
errmmm...

just some questions:

hidden files: if Linux shows files on an USB stick (for example) which are hidden in windows: so whats the problem? You see it... and can ignore it
If you want to see a hidden file (because it has a dot in front of the file name), simply press ctrl-h and you'll see it.

defrag on NTFS: why does anyone want to use Linux to defrag a NTFS-drive? here some explaination would be very very useful. :D

---

### Post by cariboo on 2009-10-09
It's my understanding that even Microsoft is not happy with NTFS, They've been working for years to replace it with [WinFS]("http://en.wikipedia.org/wiki/WinFS").

---

### Post by Penguin Guy on 2009-10-09
> **Faolan Devyn Aodfin said:**
> In that case you could add an option in the file management libraries (lister and viewers respectively) to something to the effect of:

======================================================
( ) Display hidden files by POSIX standard
( ) Display hidden files by file system standards
( ) Hybrid display mode
======================================================

The idea I had in my head was to treat [COLOR="Green"]**.**[/COLOR] as a special character, so all FAT/NTFS files with a hidden flag would displayed as [COLOR="Green"].file[/COLOR], and if you ran [COLOR="Green"]mkdir .folder[/COLOR] in a FAT/NTFS filesystem it would create a folder called 'folder' with the hidden flag (which, in turn remember, will be displayed as [COLOR="Green"].folder[/COLOR]). This won't make any difference to the end Linuxer, but will keep compatibility with FAT and NTFS. Of course, as previously stated many times, this will not follow the POSIX standard. I guess that's what this whole argument boils down to.

---

### Post by hoppipolla on 2009-10-09
> **Penguin Guy said:**
> The idea I had in my head was to treat [COLOR="Green"]**.**[/COLOR] as a special character, so all FAT/NTFS files with a hidden flag would displayed as [COLOR="Green"].file[/COLOR], and if you ran [COLOR="Green"]mkdir .folder[/COLOR] in a FAT/NTFS filesystem it would create a folder called 'folder' with the hidden flag (which, in turn remember, will be displayed as [COLOR="Green"].folder[/COLOR]). This won't make any difference to the end Linuxer, but will keep compatibility with FAT and NTFS. Of course, as previously stated many times, this will not follow the POSIX standard. I guess that's what this whole argument boils down to.

Sorry, don't get me wrong I obviously do support improvements in the way Linux interacts with NTFS filesystems. It's just I think your thread title was very unfair - NTFS and FAT my both be popular but they are closed source and they are not designed for Linux. I really am grateful I can access them at all.

We have excellent filesystems on Linux, the only lacking function as far as I can tell is undeleting on ext and possibly on reiser as well.

---

### Post by Keyper7 on 2009-10-09
I agree with the OP. And Linux has several other critical issues:

- Executables should .exe files instead of those weird "Linux binaries". Most people run .exe files.

- Nautilus, Thunar and Dolphin should all be replaced by Windows Explorer. People are much more used to it.

- Why this OpenGL nonsense instead of the much more popular DirectX?

- There is no version of Internet Explorer for Linux. For shame! Have not the Linux developers seen the size of IE's market share?

- A big K, a foot, an Ubuntu logo... very unintuitive. Why not a button with a "Start" label or a Windows logo in it? Everyone is used to this.

- I want transluscent window borders! With blur behind! ALL THE COOL KIDS IN MY CLASS HAVE THOSE!!!

---

### Post by hoppipolla on 2009-10-09
> **Keyper7 said:**
> I agree with the OP. And Linux has several other critical issues:

- Executables should .exe files instead of those weird "Linux binaries". Most people run .exe files.

- Nautilus, Thunar and Dolphin should all be replaced by Windows Explorer. People are much more used to it.

- Why this OpenGL nonsense instead of the much more popular DirectX?

- There is no version of Internet Explorer for Linux. For shame! Have not the Linux developers seen the size of IE's market share?

- A big K, a foot, an Ubuntu logo... very unintuitive. Why not a button with a "Start" label or a Windows logo in it? Everyone is used to this.

- I want transluscent window borders! With blur behind! ALL THE COOL KIDS IN MY CLASS HAVE THOSE!!!

Man I thought you were serious there for a minute!! lol :)

---

### Post by Faolan84 on 2009-10-09
> **hoppipolla said:**
> We have excellent filesystems on Linux, the only lacking function as far as I can tell is undeleting on ext and possibly on reiser as well.

You actually can undelete on EXT files systems. There's a tool for it -- albeit for version 2 of the filesystem -- and it's a pain in the *** and don't always work.

---

### Post by NoaHall on 2009-10-09
Haha! Nice one. That sure put the OP in his place.

---

### Post by hoppipolla on 2009-10-09
> **Faolan Devyn Aodfin said:**
> You actually can undelete on EXT files systems. There's a tool for it -- albeit for version 2 of the filesystem -- and it's a pain in the *** and don't always work.

yeah it's so weird that it is lacking! As far as I am aware ZFS (opensolaris' FS) is the only related filesystem with support for it ... I wish it was in ext4 or reiser4...

I hope I am wrong on this one though as it seems like quite a big fault with otherwise excellent filesystems :)

---

### Post by Ekeluo on 2009-10-09
> **Keyper7 said:**
> I agree with the OP. And Linux has several other critical issues:

- Executables should .exe files instead of those weird "Linux binaries". Most people run .exe files.

- Nautilus, Thunar and Dolphin should all be replaced by Windows Explorer. People are much more used to it.

- Why this OpenGL nonsense instead of the much more popular DirectX?

- There is no version of Internet Explorer for Linux. For shame! Have not the Linux developers seen the size of IE's market share?

- A big K, a foot, an Ubuntu logo... very unintuitive. Why not a button with a "Start" label or a Windows logo in it? Everyone is used to this.

- I want transluscent window borders! With blur behind! ALL THE COOL KIDS IN MY CLASS HAVE THOSE!!!

Aaaahhhh, that's just cruel.

---

### Post by jeremyswalker on 2009-10-09
> **Keyper7 said:**
> I agree with the OP. And Linux has several other critical issues:

- Executables should .exe files instead of those weird "Linux binaries". Most people run .exe files.

- Nautilus, Thunar and Dolphin should all be replaced by Windows Explorer. People are much more used to it.

- Why this OpenGL nonsense instead of the much more popular DirectX?

- There is no version of Internet Explorer for Linux. For shame! Have not the Linux developers seen the size of IE's market share?

- A big K, a foot, an Ubuntu logo... very unintuitive. Why not a button with a "Start" label or a Windows logo in it? Everyone is used to this.

- I want transluscent window borders! With blur behind! ALL THE COOL KIDS IN MY CLASS HAVE THOSE!!!

LOL!! I felt my blood pressure rising for a minute.

---

### Post by Chronon on 2009-10-09
> **Penguin Guy said:**
> The idea I had in my head was to treat [COLOR="Green"]**.**[/COLOR] as a special character, so all FAT/NTFS files with a hidden flag would displayed as [COLOR="Green"].file[/COLOR], and if you ran [COLOR="Green"]mkdir .folder[/COLOR] in a FAT/NTFS filesystem it would create a folder called 'folder' with the hidden flag (which, in turn remember, will be displayed as [COLOR="Green"].folder[/COLOR]). This won't make any difference to the end Linuxer, but will keep compatibility with FAT and NTFS. Of course, as previously stated many times, this will not follow the POSIX standard. I guess that's what this whole argument boils down to.

That sounds like a horrible idea.  This would break a lot of software.  If I create a directory named .folder or a file named .file then I darn well expect for there to be a directory or file with the given name in the file system.  This would break installation of Rockbox, for instance, because the bootloader looks for the binary in a directory named ".rockbox".  This folder would exist if installed from a Windows system, but not from Linux.

Edit: Maybe "horrible" is a tad strong and I mean no offense.  I just anticipate that this sort of change would needlessly break a lot of software.

---

### Post by LookTJ on 2009-10-09
From my understanding of NTFS and FAT, hidden files go by "$" not "."

I'll tell you that NTFS file system sucks no matter what OS it's mounted on, even on Windows.  This is Microsoft, not Linux.

---

### Post by Frak on 2009-10-09
> **Penguin Guy said:**
> Wow. I'm guessing we aren't allowed to use this then..?
It isn't GPL compatible, so userland only. Other than that, it's fully open source. Many BSD's have it integrated.

---

### Post by LookTJ on 2009-10-09
> **Keyper7 said:**
> I agree with the OP. And Linux has several other critical issues:

- Executables should .exe files instead of those weird "Linux binaries". Most people run .exe files.

- Nautilus, Thunar and Dolphin should all be replaced by Windows Explorer. People are much more used to it.

- Why this OpenGL nonsense instead of the much more popular DirectX?

- There is no version of Internet Explorer for Linux. For shame! Have not the Linux developers seen the size of IE's market share?

- A big K, a foot, an Ubuntu logo... very unintuitive. Why not a button with a "Start" label or a Windows logo in it? Everyone is used to this.

- I want transluscent window borders! With blur behind! ALL THE COOL KIDS IN MY CLASS HAVE THOSE!!!
:lolflag: I see copyright infringement coming. :)

---

### Post by hessiess on 2009-10-09
NTFS is an awful filesystem, the verry fact that it even needs defragging is proof enough. EXT* are smarter and actively try to avoid fragmenting files, it only starts fragmenting when disk space is low.

---

### Post by Xbehave on 2009-10-09
> **Chronon said:**
> Edit: Maybe "horrible" is a tad strong and I mean no offense.  I just anticipate that this sort of change would needlessly break a lot of software.
No horrible is too nice, unfortunately i don't want another warning so i won't ssay how i really feal however we have 3 options
[LIST]
[*]Keep what we have and do not use FAT/NTFS anywhere we would want hidden files (why would you hid a file on a pen drive?)
[*]rewrite all our file managers (and as a result add more bugs) to make OP happy even though most linux users will not use ntfs anywhere serious
[*]Manipulate file names at driver levels to add . to hidden files (what happens to files that really start with a .)
[/LIST]
So basically we can either break stuff to make OP happy or we can stick to well designed filesystems and only use fat/ntfs when forced to!

> NTFS is an awful filesystem, the verry fact that it even needs defragging is proof enough. EXT* are smarter and actively try to avoid fragmenting files, it only starts fragmenting when disk space is low.
Don't forget that it will unfragment itself by using it with more space left (although the fragments will stay until the file is next written to disk)

I think there is more than just licensing stopping HFS code being used in the actual kernel (like the FS stacks are completely different), however I believe in kernel support for HFS+ is being worked on (however it's not a priority). I also don't think OPs assumption that it would make using ipods easier is correct (especially as they have encrypted firmware and all that jazz)

---

### Post by Faolan84 on 2009-10-09
> **LookTJ said:**
> From my understanding of NTFS and FAT, hidden files go by "$" not "."

I'll tell you that NTFS file system sucks no matter what OS it's mounted on, even on Windows.  This is Microsoft, not Linux.

no, those aren't hidden files. yes, they are hidden, but they are special attribute files containing data telling the system how to operate within a directory or storing a certain setting or what have you. Sometimes they are file system related, other times they are not.

---

### Post by gletob on 2009-10-09
Guess what.  Linux is free, and people develop it on their own means.  If you have programming knowledge and want to help build support, go ahead.  Those who know these things might not use NTFS or FAT and particularly get no benefit from these things.  They're not paid for what they do, so either do it yourself or stop whining.

---

### Post by perce on 2009-10-10
> **gletob said:**
>  They're not paid for what they do, so either do it yourself or stop whining.

They are, but people who pay them (IBM, Red Hat, Novell and others) don't give a damn about Windows hidden files, and neither do I.

In fact I see the fact that Linux doesn't care of Windows files attributes as a plus: I had to use Linux once to remove a file I didn't want, that Windows was stubbornly refusing to remove.

---

### Post by 3rdalbum on 2009-10-10
Linux supports "special characters" in filenames on the NTFS filesystem. Windows doesn't. The NTFS specification says that special characters are allowed.

---

### Post by Exodist on 2009-10-10
> **Penguin Guy said:**
> Yes - Windows has full support for NTFS which is used on every Windows instillation (about 95% of computers), whereas Linux doesn't, but instead has support for EXT, ReiserFS, JFS, etc (probably around 3%?). On top of that, Linux doesn't support FAT hidden files (FAT is used on most USB drives).

M$ designed NTFS, of course they have support for it. DUHH!

Also Linux DOES IN FACT support FAT file systems and has for well over 10 years.


Boy your a bucket full of miss information this morning. :P

---

### Post by Penguin Guy on 2009-10-10
> **Xbehave said:**
> I think there is more than just licensing stopping HFS code being used in the actual kernel (like the FS stacks are completely different), however I believe in kernel support for HFS+ is being worked on (however it's not a priority). I also don't think OPs assumption that it would make using ipods easier is correct (especially as they have encrypted firmware and all that jazz)
Surely Mac supports iPods? And if it does, and it's open-source, wouldn't it be easy to add support?

---

### Post by aysiu on 2009-10-10
I don't really see a problem here.

Out of the box, a Linux distro like Ubuntu supports read/write for NTFS and FAT32. HFS+ read-only support can be installed via the repositories. It obviously has native support for Ext3 and other popular Linux filesystems.

Out of the box, Windows supports NTFS and FAT32. That's it. No native support for Ext3. No native support for HFS+

Out of the box, Mac OS X supports FAT32 and HFS+. That's it. No native support for Ext3. No native support for NTFS.

---

### Post by hanzomon4 on 2009-10-10
hfs+ read workd otb

---

### Post by Chame_Wizard on 2009-10-10
> **Keyper7 said:**
> I agree with the OP. And Linux has several other critical issues:

- Executables should .exe files instead of those weird "Linux binaries". Most people run .exe files.

- Nautilus, Thunar and Dolphin should all be replaced by Windows Explorer. People are much more used to it.

- Why this OpenGL nonsense instead of the much more popular DirectX?

- There is no version of Internet Explorer for Linux. For shame! Have not the Linux developers seen the size of IE's market share?

- A big K, a foot, an Ubuntu logo... very unintuitive. Why not a button with a "Start" label or a Windows logo in it? Everyone is used to this.

- I want transluscent window borders! With blur behind! ALL THE COOL KIDS IN MY CLASS HAVE THOSE!!!

Classic :lolflag: [IMG]http://images.fok.nl/s/static.gif[/IMG]

---

### Post by OpenGuard on 2009-10-10
If files system support in Linux sucks, in Windows, there are no support at all. Take a look at cfdisk - you don't know half of what's listed there ( under types ) :D

---

### Post by infestor on 2009-10-10
ext3 was one of the reasons I fell in love with linux...no defrag, works great

---

### Post by billdotson on 2009-10-10
You know, if you want to give suggestions as to what could be improved you should present them as suggestions, not as "LINUX FILESYSTEM SUCKS!" You forget that the system you are using is FREE, which generally means they don't *have* to support anything. Supporting anything is just a result of someone being nice for the most part. Yes, I have ranted a bit before about some things (my friend recently had a terrible time trying to get flash working in Fedora but you can't entirely blame that on Linux; in fact, a large portion of the blame must go to Adobe) but it is really infuriating to the people that poured hours into the work.

Next time try naming the title "Linux filesystem support suggestions" and say "It would be a nice feature if I had hidden file support for FAT and NTFS partitions. I am having lots of issues currently because of it. Thanks for all the work so far in implementing support for an entirely closed technology, it is very helpful." You should try it.

---

### Post by Xbehave on 2009-10-10
> **Penguin Guy said:**
> Surely Mac supports iPods? And if it does, and it's open-source, wouldn't it be easy to add support?
windows has no support for HFS+, yet it still supports iPods. I **think** if you read about libgpod,etc you'll find that HFS+ support is the least of your worries when syncing iPods.

---

### Post by Frak on 2009-10-10
> **aysiu said:**
> Out of the box, Mac OS X supports FAT32 and HFS+. That's it. No native support for Ext3. No native support for NTFS.
Mac OS X 10.4.11, 10.5.x, and 10.6.x have Read-Only support for NTFS out of the box.

---

### Post by Bachstelze on 2009-10-10
People must get rid of the idea that filesystems are, or are meant to be, interoperable. They're not. I don't know of *any* filesystem that works perfectly (i.e. with all its features available) in more than one OS (*any* OS).

At least as far as popular OSes are concerned. Filesystems like XFS and JFS, who originate from IRIX and AIX, have been ported on Linux and seem to work well.

---

### Post by Frak on 2009-10-10
> **Bachstelze said:**
> People must get rid of the idea that filesystems are, or are meant to be, interoperable. They're not. I don't know of *any* filesystem that works perfectly (i.e. with all its features available) in more than one OS (*any* OS).

At least as far as popular OSes are concerned. Filesystems like XFS and JFS, who originate from IRIX and AIX, have been ported on Linux and seem to work well.
+9001

It's good to remember that a filesystem was created as a solultion to a problem, not as another X to throw into a pool of Y.

---

### Post by Bachstelze on 2009-10-10
> **Bachstelze said:**
> People must get rid of the idea that filesystems are, or are meant to be, interoperable. They're not. I don't know of *any* filesystem that works perfectly (i.e. with all its features available) in more than one OS (*any* OS).

At least as far as popular OSes are concerned. Filesystems like XFS and JFS, who originate from IRIX and AIX, have been ported on Linux and seem to work well.

Actually not true for JFS:

[http://en.wikipedia.org/wiki/JFS_%28file_system%29#Compression](http://en.wikipedia.org/wiki/JFS_%28file_system%29#Compression)

---

### Post by MellonCollie on 2009-10-12
> **cariboo907 said:**
> It's my understanding that even Microsoft is not happy with NTFS, They've been working for years to replace it with [WinFS]("http://en.wikipedia.org/wiki/WinFS").


WinFS wasn't going to replace NTFS because WinFS wasn't a file system. You can see a diagram of the WinFS architecture in the 'Architecture' section of the Wikipedia page you linked to; note what's at the bottom of the diagram.

---

