---
title: "Why is writing to NTFS sucha  taboo?"
date: 2006-01-02
forum: The Cafe
---

### Post by Deaf_Head on 2006-01-02
(wasnt'e sure where to put this one ... so I put it in community hehe)

I've seen alot of people say "NO, don't do it, it'll kill your first born" etc. etc. but nobody every says why?

How come so many other features seem to work flawlessly in linux, but the one thing that'd make multiple OS systems easier to work with "no good"?

Is writing to NTFS really that unsafe .. and most importantly why?

---

### Post by mazelado on 2006-01-02
I'm not 100% sure about this answer, but from what I understand, the reason they tell you not to write to NTFS is because most of the software used to read/write NTFS partitions wasn't 100% complete and bug-free and you could damage the NTFS file system resulting in lost or corrupt files or even a destroyed disk. Since reading doesn't change the disk it was easy enough to try it without anything bad happening.

I still don't write to my NTFS partition even though a lot of the NTFS programs claim to be able to do so without problems. Instead, I created a FAT partition that both Linux and Windows can read and write without problems.

---

### Post by briancurtin on 2006-01-02
[QUOTE=Deaf_Head](wasnt'e sure where to put this one ... so I put it in community hehe)

I've seen alot of people say "NO, don't do it, it'll kill your first born" etc. etc. but nobody every says why?

How come so many other features seem to work flawlessly in linux, but the one thing that'd make multiple OS systems easier to work with "no good"?

Is writing to NTFS really that unsafe .. and most importantly why?[/QUOTE]
from what i have read on the topic, it really isnt safe and could cause unfixable damage. for the most part, people use it and get by fine, but there are some bugs and it could cause some trouble for you.
personally, if i am messing with data, i dont want there to be unfixable errors. of course there is always this possibility with any file system, even just writing from NTFS to NTFS or ext3 to ext3. the thing that allows writing to NTFS from some linux filesystems just isnt that trusted yet, but thats just what i have read. i personally dont have windows and if i did, i woulndt use whatever it is that lets you write to NTFS.

---

### Post by vayu on 2006-01-02
What I wonder is are filesystems in general that complicated or is only ntfs that way?

---

### Post by kingsidy on 2006-01-02
i think that the problem is that ntfs is propritery and prolly developper are having a hard time with the specs to come up with a reliable open source program that would allow you to write to ntfs from linux.

---

### Post by ninotob on 2006-01-02
I think filesystems in general are complex.  Take a look at a description of the common filesystems used in linux:
[http://www.linuxgazette.com/issue55/florido.html](http://www.linuxgazette.com/issue55/florido.html)

And you can go right to the source of all linux NTFS goodness:
[http://www.linux-ntfs.org/component/option,com_frontpage/Itemid,1/](http://www.linux-ntfs.org/component/option,com_frontpage/Itemid,1/)

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=vayu]What I wonder is are filesystems in general that complicated or is only ntfs that way?[/QUOTE]

The problem is that NTFS has many legal restrictions that make it harder to mes with.

Current NTFS write support in Linux is a HORRIBLE hack the way it is. Its hacked together illegally (for my nation at least I'm pretty sure) with parts from Windows. Thats why it does not work worth a darn and is legally troubling.

There is a reason that MS wanted a patent on FAT. Its the one file system Windows supports they can't control legally. They DO control ntfs, its kinda amazing Linux can read it at all. Fedora doesn't ship with that feature, as even it is a little non libre.

So basically its bad because:

1. Current support comes from a really bad hack that could destroy your data quite easily.

2. Better support could/can never be made do to the control (legal and otherwise) that MS has over NTFS. 

3. It sounds like a magical bridge, but Windows (the system) has a magical bridge that works better- FAT. So if us nerds need to share partitions we use FAT.

Just like WINE (a project that tries to build Windows backwards with blindfolds on) does not have complete support, NTFS write support is lacking because its hood is welded shut.

Maybe in a few years or so if someone figures out a way to write to NTFS that is not an ugly/scary/semi-illegal hack (through reverse engineering) Ubuntu will have it. Till then...stay away.

[http://en.wikipedia.org/wiki/Captive_NTFS](http://en.wikipedia.org/wiki/Captive_NTFS)
> 
Captive NTFS is an open-source project within the Linux programming community, started by Jan Kratochvil, to create a "software wrapper" around the original Microsoft Windows NTFS file system driver. By taking this approach captive NTFS aims to provide safe write support to NTFS partitions.

Captive NTFS requires NTFS.SYS which cannot be distrubuted for legal reasons. It can either be obtained from an installed Windows system (which most computers with NTFS partitions are likely to have) or extracted from certain Microsoft service packs.

In early 2005 Jan Kratochvil discontinued the development of Captive NTFS. By the end of this year, no other developer has taken over maintenance of this project. Consequently, transparent access to NTFS file systems through LUFS does not work with Linux kernels higher than 2.6.8. Due to the rapid progress of the Linux NTFS project, Kratochvil says that his creation might become obsolete anytime soon.

Decent write support might not be that far away :

[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

---

### Post by GeneralZod on 2006-01-02
[QUOTE=Deaf_Head](wasnt'e sure where to put this one ... so I put it in community hehe)

I've seen alot of people say "NO, don't do it, it'll kill your first born" etc. etc. but nobody every says why?

How come so many other features seem to work flawlessly in linux, but the one thing that'd make multiple OS systems easier to work with "no good"?

Is writing to NTFS really that unsafe .. and most importantly why?[/QUOTE]

As many have said, NTFS is a completely closed specification and, as such, attempts to provide a native Linux driver must come through reverse-engineering.  Reverse-engineering is an *immensely* difficult task, relying greatly on trial-and-error and out and out luck.  The products of reverse engineering are often doomed to be just 99% perfect - for example, you may note that event A seems to always occur under conditions B and C and so hack this special case into your driver, but without knowledge of what's *really* going on with the file system driver (knowledge which, of course, only Microsoft has) you may well completely miss the fact that A also occurs under condition D, or A does in fact not occur when B is true but E is also true.  In short, reverse-engineering tends to give you 100s of tiny little pieces of information in isolation, and you have to somehow re-construct what's going on behind the scenes and giving rise to these little pieces of information by cobbling them together as best you can via logic, intuition, and guesswork.  Getting even one of these things wrong (like stating that A always occurs under condition B) can be utterly disastrous with a file system as it could lead to seemingly "random" data loss which may not even be detected as it occurs - every programmers "nightmare" kind of bug :)

[QUOTE=vayu]What I wonder is are filesystems in general that complicated or is only ntfs that way?[/QUOTE]

I don't think it's even a matter of complexity, really; I'm willing to bet that reiser4 knocks NTFS into a hat complexity-wise, but reiser4 is much easier to implement because the specs are open.  Even fairly simple programs can be obfuscated to the point where trying to work out how they work takes skilled hackers ages.  And, as mentioned, file-system drivers are "mission-critical" programs where even a high degree of correctness (say, 995) simply isn't good enough and will almost *definitely* wipe some of your data eventually.

---

### Post by prizrak on 2006-01-02
As is normal with MS not a damn spec exists for NTFS and even if some stuff is documented most isn't. MS has no reason to give us NTFS specs since only the OS needs to know how to deal with your storage 3rd party software does not. So of course there is no way to reliably write to it as it was said that it's reverse engineered (read they guessed it works like that). There is a way to read Ext3 file systems from Windows (there is 3rd party progs that do that) which makes it a bit easier to share files w/o creating a FAT partition.

---

### Post by Rugger on 2006-01-03
Actually, I have a Gentoo box where I just upgraded the kernel to 2.6.14-r5 and it has built in kernel support for ntfs read/write.  It's new in that kernel where it was experimental before, so I believe they have got the bugs worked out.  I just havn't figured how to recompile ubuntu's with the newest kernel (I'm new to ubuntu but have been using gentoo for years.)

---

### Post by gruffy-06 on 2006-08-15
I got annoyed by legal restrictions of NTFS, so I deleted Windows and installed Ubuntu over it. My Laptop works 100 times better now.

A suggestion is to look for ext2 drivers for Windows. Or mount the volume using SMB from another PC under GNU/Linux.

--Gruffy--

*GNU/Linux is about being free. The propietary firms shall fade one day.*

---

### Post by Brunellus on 2006-08-15
There do exist solutions for reading and writing to ntfs from Linux.  As everybody else on this thread has stated, though, they are *experimental*.

The thing about experimental software is this--if it works for you, great!  You've just discovered a new tool.  If it doesn't--not so great.  So when thinking about whether or not you want to write to a filesystem with experimental software do the following:

Find a scrap piece of paper and write DATA on it.  Stick that on your computer.

Then meditate:  are you willing to trade all of the data on that filesystem for the little scrap of paper with DATA written on it?  If yes, go ahead and do what you will.  If no...well..there's your answer.

---

