---
title: "Well if ext3 is so good why don't Windows use it"
date: 2007-06-03
forum: Windows
---

### Post by jonward0690 on 2007-06-03
I have been wondering if the ext3 filesystem is so good, not saying it is not why does'nt Win use it so they could brag to that there os does not need defragmenting.

---

### Post by Chayak on 2007-06-03
That's because Microsoft didn't make it and can't charge for it. :D  That and they would never agree to the GPL's license requirements.

---

### Post by zorkerz on 2007-06-03
and if they did then it would be compatible with all the non ms operating systems and encourage us not to use ms.

---

### Post by jonward0690 on 2007-06-03
Well the why don't MS just make there own more efective filesystem that they have.

---

### Post by KaroSHiv0n on 2007-06-03
> **jonward0690 said:**
> Well the why don't MS just make there own more efective filesystem that they have.

if you built something half assed and millions paid for it and diddnt complain, would YOU build something more effective? i sure as hell wouldent and i dont see any reason ms will either.

---

### Post by kevinlyfellow on 2007-06-03
I've wondered the same thing with a different emphasis.  I wonder if windows is so great, then why doesn't it use ext3 (or any other decent filesystem) by default.  They use proprietary fs's so that they can say "if you install linux, it will cause you pain and frustration!"

---

### Post by Pobega on 2007-06-03
Microsoft won't (Yet) admit that NTFS is an inferior filesystem, just like Apple wouldn't admit that PowerPC processors are inferior to Intel. It's just what businesses do, they give hype to even the most ridiculous, incorrect things.

---

### Post by samjh on 2007-06-03
> **jonward0690 said:**
> I have been wondering if the ext3 filesystem is so good, not saying it is not why does'nt Win use it so they could brag to that there os does not need defragmenting.

All file systems will fragment, ext3 is no exception.

Ext3 doesn't have any definitive advantages over the proprietary NTFS.  It's a good file system, but what does ext3 have to offer that NTFS needs?  Nothing really.  NTFS is good file system with a long history, and continues to evolve.  It makes no sense for Microsoft to throw it away.

NTFS: [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)

ext3: [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by zorkerz on 2007-06-03
well it has permissions ntfs does not have that. I feel ntfs is pretty basic without much of the features in ext3

---

### Post by samjh on 2007-06-03
Permissions?  Do you mean ACLs?  NTFS has ACLs.

Sorry in advance, if I misunderstood.

---

### Post by kevinlyfellow on 2007-06-03
> **samjh said:**
> All file systems will fragment, ext3 is no exception.

Ext3 doesn't have any definitive advantages over the proprietary NTFS.  It's a good file system, but what does ext3 have to offer that NTFS needs?  Nothing really.  NTFS is good file system with a long history, and continues to evolve.  It makes no sense for Microsoft to throw it away.

NTFS: [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)

ext3: [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

I'm not an expert on filesystems... is it the os that determines the amount of fragmentation that goes on in the filesystem then?  Is the windows kernel to blame then?

Update:  It seems like its filesystem from this website.  Its a great read, and dispels some fragmentation myths [http://dataexpedition.com/~sbnoble/Tips/filesystems.html#Optimization](http://dataexpedition.com/~sbnoble/Tips/filesystems.html#Optimization)

---

### Post by samjh on 2007-06-03
> **kevinlyfellow said:**
> I'm not an expert on filesystems... is it the os that determines the amount of fragmentation that goes on in the filesystem then?  Is the windows kernel to blame then?

It's a combination of the operating system and the file system.  Most of the bad talk about Windows file system fragmentation dates back to the days of FAT16 and FAT32 file systems, which were truly crap.

Fragmentation is caused of gaps in a file written to disk that should be contiguous, but are not.  Basically, an OS needs to make sure it allocates enough contiguous space on the disk so that the file can written in one big block, instead of having parts of it scattered at random locations, or having to fit pieces of data in gaps between other files.  So yes, operating systems are a factor.

The other factor is the file system.  FAT16 and FAT32 were crap.  No arguments there.  NTFS is a much more capable and evolved system.  Aside from its other features, it supports extents, which pre-allocates contiguous empty space before writing data (this will be supported by the next version of ext: ext4).  Allocate-on-flush is another technique (this one allocates space in sync with other allocation demands) that will be implemented in ext4.

I think at the moment, NTFS and ext3 are standing on similar ground in terms of fragmentation performance.  Ext4 will be better when it's released, but NTFS is always being improved, so Microsoft might spring a few more features for it.  Windows Vista, for example, does background defrags that are transparent to the user.

---

### Post by jiminycricket on 2007-06-03
> **Chayak said:**
> That's because Microsoft didn't make it and can't charge for it. :D  That and they would never agree to the GPL's license requirements.

Exactly.  Microsoft is against interoperability.  They are all about maintaining and increasing barriers of entry.

NTFS = HPFS embraced and extended

NTFS was a trade secret and a big barrier until ntfs-3g was created.  In the past, there was a lot of pain in writing to NTFS in 2000, when Microsoft published a patch that caused NTFS on Linux to destroy ntfs partitions.

---

### Post by godd4242 on 2007-06-03
> **jonward0690 said:**
> Well the why don't MS just make there own more efective filesystem that they have.

NTS allows higher backwards compatibility standards.

---

### Post by init1 on 2007-06-03
> **jonward0690 said:**
> I have been wondering if the ext3 filesystem is so good, not saying it is not why does'nt Win use it so they could brag to that there os does not need defragmenting.
Because microsoft does not want to admit that their filesystem is not as good as some of the  free filesystems.

---

### Post by hanzomon4 on 2007-06-03
My ntfs would get very fragmented, so does my brothers. It could be because we do audio work but in my end user experience it wasn't too hot. However I have no way of knowing if my linux(ext3, jfs, xfs) file systems are fragmented. I don't believe that everything MS is bad, xp served me well, but the OSS world has given me many great options. That by itself is an advantage against ntfs. With ext4 coming out and the amazing(but mysterious to me) sun zfs I see MS getting further behind in the File System race. 

Is the Winfs ever going to see the light of day? And what advantages did it have over ntfs, I'm technologically ignorant.

EDIT: I see Winfs is not an ntfs replacement, more like a service or enhancement

---

### Post by stmiller on 2007-06-03
> Well if ext3 is so good why don't Windows use it

Good question. I think, however, the chances of Windows adopting ext3 for their native FS is about the same chances of them using the Linux kernel as the kernel of their next OS, unfortunately.

---

### Post by Rocket2DMn on 2007-06-03
MS is stuck in their ways.  For now, their stuff works for them.  In the end, so long as we can read it and write to it with ntfs-3g, who really cares what they do?

---

### Post by LightB on 2007-06-04
> **Pobega said:**
> Microsoft won't (Yet) admit that NTFS is an inferior filesystem, just like Apple wouldn't admit that PowerPC processors are inferior to Intel. It's just what businesses do, they give hype to even the most ridiculous, incorrect things.

hah, yes, and it will be a cold day in hades before they admit that DirectX10 is actually mostly hype once it actually comes around.

---

### Post by wolfen69 on 2007-06-04
WOW, the sparks are flyin! i love it.

---

### Post by afljafa on 2007-06-04
> **zorkerz said:**
> well it has permissions ntfs does not have that. I feel ntfs is pretty basic without much of the features in ext3

Sigh - why do people continue to post uninformed rubbish such as this.

---

### Post by Quillz on 2007-06-04
ext3 was never touted as the "best file system," to my knowledge. And, as others have said, it's open source, something that Microsoft likely wouldn't want to adapt. Besides, you do know that NTFS is a journaled file system just like ext3, right? It rarely needs defragging, despite what you may have thought to the contrary. It's only the FAT file system that needs defragging, which XP uses by default.

---

### Post by laxmanb on 2007-06-04
NTFS is quite good actually... and the only open source Filesystem with a lot of buzz around it is ZFS...

---

### Post by guitarmaniac on 2007-06-04
I've always wondered why there wasnt a defrag program fro ext3.
I mean, sure it is journalised, but my hard drive is probably doing twice the work.
I'm no expert on the subject, but it just seems logical to try to keep files in order on the disc where possible.

---

### Post by jiminycricket on 2007-06-04
There is one called pyfragtools.

Or you can move all data off the ext3 partition, then back onto it.

---

### Post by mips on 2007-06-04
> **jonward0690 said:**
> Well the why don't MS just make there own more efective filesystem that they have.

Well they are & it is called WinFS. It was hyped as one of the features of Longhorn (which is now Vista) but it never made it inot Vista.

[http://en.wikipedia.org/wiki/WinFS](http://en.wikipedia.org/wiki/WinFS)
.

---

### Post by runningwithscissors on 2007-06-04
Who the heck even "defrags" their partitions on Windows either. I've never known anybody who did that. And no, NTFS does not slow up if you don't defrag.

---

### Post by jiminycricket on 2007-06-04
Mine does, frequently (on both hard drives).  Same on my laptop.

---

### Post by hanzomon4 on 2007-06-04
Yep, same here

---

### Post by STREETURCHINE on 2007-06-04
yep have to defrag windows xp frequently and that uses ntfs,if i dont it slows right down:p

---

### Post by runningwithscissors on 2007-06-04
Strange. Last I used it, NTFS seemed to blaze along perfectly well even after months without defragging.

---

### Post by D!mon on 2007-06-04
so is it actually a disadvantage of ext3 that it doesn't have defragmentation program?

---

### Post by afljafa on 2007-06-04
> **runningwithscissors said:**
> Strange. Last I used it, NTFS seemed to blaze along perfectly well even after months without defragging.

Same. Can`t say i`ve suffered any performance hits and I never defrag.

---

### Post by Morpsemia on 2007-06-04
It's a little more complicated than that. 
Fragmented systems occur because there is a lot of disk activity, particularly creating and deleting lots of files. Just to be clear, a fragmented file is one that is not continuous on the disk, meaning it's scattered all over the hard drive. Think of a file as a few sheets of paper, if they are all next to each other in a nice file cabinet, they are easy to find quickly. If they are all over the place it can take forever to find all of it. If your not digging around through the disk much, then your not going to get a lot of fragmentation. This is where the design of the OS comes in to play. Windows, on it's own, it moving files around all the time, probably the best example is swap space. Windows uses a large swap file, verses Linux's swap partition. Because, by default, windows is usually going nuts resizing the swap file and moving it around, it can fragment a disk very quickly. Windows can be tweaked to run much better, setting the swap file to a static size in this example, and compared to a system that run Linux and is used in a similar manner will do about the same on disk fragmentation. Part of the problem is that it can be a major pain in the butt to properly tweak out windows so it runs well (Don't know about Vista, haven't played with it). Linux seems to do much better on this front out of the box.

That said, MS Won't adopt a new file system until they feel it will be profitable to do so.  Can't really fault them for that, they are a business after all. They made the jump to NTFS to support larger hard drives and new features, just like the jump from FAT16 to FAT32 before that.

Now, what I'm interested in is the choice of file systems on thumb and pen drives. They are started to approach the limits of the old FAT systems they currently use for compatibility.

---

### Post by zorkerz on 2007-06-04
> **afljafa said:**
> Sigh - why do people continue to post uninformed rubbish such as this.
My apologies afljafa. This was my understanding that you could give permissions to files in ext and not ntfs. I obviously have little idea what i am talking about. So please at least enlighten me after knocking me down instead of leaving me in the mud confused. I guess im a little harsh but could someone please explain.
cheers

---

### Post by aysiu on 2007-06-04
The assumption in the question is flawed.

The question assumes that if anything is good it will be used by Windows. This is not the case.

---

### Post by stmiller on 2007-06-04
Windows vomits bits and pieces of files all over the hard drive. Constantly. Linux does not, OS X does not. That's why you must defrag with Windows, otherwise your hard drive is racing all over the disc to read your data.



[http://www.redhat.com/support/wpapers/redhat/ext3/](http://www.redhat.com/support/wpapers/redhat/ext3/)

---

### Post by stimpack on 2007-06-04
The continued use of ext3 is disapointing, there are numerous other linux filesystems that are better, each in different ways.

WinFS held promise, I was very interested in this and kind of disapointed it was a MS thing, really funny when they dropped it, for a second there it looked like Windows would have innovated somthing.

---

### Post by shijirou on 2007-06-04
> **Quillz said:**
> . It's only the FAT file system that needs defragging, **which XP uses by default.**

I beg to differ, most new PCs that used to be bundled with Windows XP whether it be home or professional came with NTFS partitions.

---

### Post by kevinlyfellow on 2007-06-04
> **stimpack said:**
> The continued use of ext3 is disapointing, there are numerous other linux filesystems that are better, each in different ways.


Ext3 is used because it is stable, and that is why most people choose ext3.  But can you explain why it's disappointing instead of just saying that others are better?  Can you clue us in as to which ones are better?

---

### Post by juxtaposed on 2007-06-04
> Who the heck even "defrags" their partitions on Windows either. I've never known anybody who did that. And no, NTFS does not slow up if you don't defrag.

It's one of those generic things companies of any kind that do anything with computers (ISPs, etc) always say whenever something goes wrong.

"Somethings wrong"
"Defrag, scan for viruses, restart, etc"

---

### Post by jgrabham on 2007-06-04
> **runningwithscissors said:**
> Who the heck even "defrags" their partitions on Windows either. I've never known anybody who did that. And no, NTFS does not slow up if you don't defrag.

me :]

Its great so that people can ring up tech support- "My computers going slowly"

"go start>programmes>accesories>system tools >disk defragmenter"

Hang up

---

### Post by jgrabham on 2007-06-04
> **juxtaposed said:**
> It's one of those generic things companies of any kind that do anything with computers (ISPs, etc) always say whenever something goes wrong.

"Somethings wrong"
"Defrag, scan for viruses, restart, etc"

In the words of the guy on the IT crowd

"have you tried switching it off and on again"

---

### Post by mech7 on 2007-06-04
I thought that WinFS is comming with Vista SP1 not sure though..

---

### Post by Mazza558 on 2007-06-04
I have all my windows programs that are not required for the OS to function on an Ext3 Partition, shared with Ubuntu. Install the windows Ext3 drivers and you're good to go, as well as it being much faster.

---

### Post by hanzomon4 on 2007-06-04
I believe that WinFS is not a replacement for ntfs, rather an enhancement that would allow new features. What features? I'm not sure I think it has something to do with meta-data. The trackerfs is supposed to be able to do something similar in linux, trackerfs being related to tracker or meta-tracker.

EDIT:What is this? beaglefs?

---

### Post by stimpack on 2007-06-04
> **kevinlyfellow said:**
> Ext3 is used because it is stable, and that is why most people choose ext3.  But can you explain why it's disappointing instead of just saying that others are better?  Can you clue us in as to which ones are better?

I mean because it seems to require a ridiculous amount of time for people to accept things are stable, even ext3 does not have this time, but people count the ext2 base as well.

There was a brilliant article comparing the filesystems, everything from speeds on various operations to reliability. It was amazingly complex and there is no way I can state which is best without being a fool, but ext3 consistently neared the bottom on most graphs. If someone can link this article I'd be grateful.

---

### Post by ticopelp on 2007-06-04
> **KaroSHiv0n said:**
> if you built something half assed and millions paid for it and diddnt complain, would YOU build something more effective?

My favorite answer in this thread.

---

### Post by the_darkside_986 on 2007-06-05
In my experience, NTFS does get a bit fragmented when you fill it up. When I had a 40 GB NTFS partition, I installed a few games and each one was very huge so I was left with about a couple of GB. When I ran defrag it showed how seriously fragmented everything was and how much it fixed things (unless the colors are just random to mislead the user). I'm sure this is not a big issue when you don't have a lot of files.

---

### Post by Quillz on 2007-06-05
> **mech7 said:**
> I thought that WinFS is comming with Vista SP1 not sure though..
It's already here. WinFS is not a new file system at all, it's just a new way for NTFS to index files. Much of the tech has been built into Vista's Instant Search.

---

### Post by runningwithscissors on 2007-06-05
> **stimpack said:**
> I mean because it seems to require a ridiculous amount of time for people to accept things are stable, even ext3 does not have this time, but people count the ext2 base as well.

There was a brilliant article comparing the filesystems, everything from speeds on various operations to reliability. It was amazingly complex and there is no way I can state which is best without being a fool, but ext3 consistently neared the bottom on most graphs. If someone can link this article I'd be grateful.
As far as desktop use goes, ext3 is your best bet right now. JFS and XFS are quite nice and fast but meant to be used on machines with assured power supply, and ReiserFS is unmaintained.

---

### Post by Erunno on 2007-06-07
Sorry for digging up this thread but I'm curious if someone knows the answer to my question:

I've been wondering if data is flushed to disk when hibernating (suspend to disk). I'm thinking about giving  XFS a try on my laptop which has an assured power supply by design but I'm wondering if data will be corrupted if waking up from hibernate fails on an XFS partition.

---

### Post by baracuda68 on 2007-06-10
ok...
here's my take on it...
I am a Linux/Ubuntu noob.
I selected to use ReiserFS when installing kubuntu, because of performance gains hinted on these forums.
I came over to Ubuntu to get away from the " evil MS empire" when Vista came out.
For the longest time I knew that Windows was directed towards noobs. 
Noobie don't really care about the file system, or dont understand about filesystems. (I still don't, but I do much more, after many years of Windows and reading on the net)
So there is no real reason for MS to make big leaps with a new filesystem, as long as NTFS is working ok.

NOW. Is there a REAL noticeable performance/security difference be between ALL filesystems?
Is it really worth the trouble to decide in depth?

---

### Post by jgrabham on 2007-06-10
You don't have to defrag ext3!

---

### Post by regbsn on 2008-03-02
Why do you not have to defrag ext3? Did I just miss it earlier in this post. I only ask because I plan to Dual boot XP and Ubuntu, out of necessity, so I am trying to decide on what format my Data partition should be.

---

### Post by RyuenjinZero on 2008-03-02
I'm an Ubuntu noob but I think it has something to do with the way data is allocated to where fragmentation is minimized, I have my shared partition as ext3 myself. Though I'm curious about what if data is stored on ext3 by using WinXP?

---

### Post by smartboyathome on 2008-03-03
As long as you have the ext3 drivers installed, you can do it like any other drive, though I would think of it as a security risk since a virus can destroy your files. Also, it doesn't need defragmentation (from what I understand) is because it uses a journal which lessens fragmentation, and it defrags itself every 30 mounts by default in Ubuntu.

---

### Post by regbsn on 2008-03-03
I thought that ext3 couldn't be defraged...or is it that there just isn't any programs out to defrag it?

---

### Post by regbsn on 2008-03-03
Bump for statement about ext3 auto defraging evers 30 mounts.

---

### Post by aysiu on 2008-03-03
The 30 boots thing is a disk check, not defragmentation.

---

### Post by forrestcupp on 2008-03-03
> **RyuenjinZero said:**
> I'm an Ubuntu noob but I think it has something to do with the way data is allocated to where fragmentation is minimized, I have my shared partition as ext3 myself. Though I'm curious about what if data is stored on ext3 by using WinXP?

It's a pain in the butt to get Windows to recognize an ext3 partition functionally.  There is no support for it, so you have to use 3rd party apps to read the partition, and it doesn't integrate perfectly.  I'd go with NTFS for a shared partition.

A simple explanation from my limited understanding for why ext3 doesn't need defragged is because the files aren't placed on it in the same way.  On Windows partitions, they try to place files close together toward the beginning of the hard drive.  So when a file is deleted and a new one is put on, they try to use the space and files become fragmented.  Also there can be problems when file size changes.  That is a good way of doing things when there is minimal fragmentation because it takes less time to move the head around.  But after a while, the files get fragmented and it slows things down.

In ext3 file systems, they spread the files out so there is a way less chance of files becoming fragmented.

---

### Post by articpenguin on 2008-03-03
ext4 will have a defragger. It still wont be needed as ext4 will have extents and delayed allocation both which reduce fragmentation.

---

### Post by oomingmak on 2008-03-03
*> **zorkerz]well it has permissions, ntfs does not have that. I feel ntfs is pretty basic without much of the features in ext3[/quote]*
[quote=afljafa said:**
> Sigh - why do people continue to post uninformed rubbish such as this.


I know (especially when permissions are one of the lamest aspects of Ext3). It's astounding the level of denial and self delusion that some people will engage in.[INDENT][LEFT]  [IMG]http://i219.photobucket.com/albums/cc48/0omingmak/NTFSFolderPermissions.png[/IMG]
[/LEFT]
[/INDENT]Next they'll be saying that Ext3 is superior to NTFS because Ext3 keeps having to do FSCKs while NTFS *never* has to.

:roll:

---

### Post by gsmanners on 2008-03-03
NTFS never has to use fsck because it will destroy your hard drive long before scandisk is hard coded to kick in.

---

### Post by Tatty on 2008-03-03
> **RyuenjinZero said:**
> I'm an Ubuntu noob but I think it has something to do with the way data is allocated to where fragmentation is minimized, I have my shared partition as ext3 myself. Though I'm curious about what if data is stored on ext3 by using WinXP?

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

The classic "Why doesn't Linux need defragmenting?" link.

---

### Post by oomingmak on 2008-03-04
> **gsmanners said:**
> NTFS never has to use fsck because it will destroy your hard drive long before **scandisk** is hard coded to kick in.
There is no such thing as "scandisk" in NTFS (and certainly nothing "hard-coded").

Scandisk is the name of an old DOS utility used for FAT partitions. It has never been used on NTFS.

---

### Post by jrusso2 on 2008-03-04
> **oomingmak said:**
> There is no such thing as "scandisk" in NTFS (and certainly nothing "hard-coded").

Scandisk is the name of an old DOS utility used for FAT partitions. It has never been used on NTFS.

NTFS does use chkdisk which is similar in function to scandisk

---

### Post by oomingmak on 2008-03-04
> **jrusso2 said:**
> NTFS does use chkdisk
Yes, indeed it does (and anyone who was even vaguely familiar with NTFS would have known that).

Chkdsk is still not hard-coded to run though. It may be similar in *function* to Scandisk, but does not run in the same way as scandisk (i.e. full drive scan whenever there's an unclean shutdown). It also does not run after elapsed time or number of mounts. Journalling tends to take care ensuring resumable disk state. I have never seen chkdsk run in over 7 years of using NTFS.

---

### Post by K.Mandla on 2008-03-04
Moved to Windows Discussions.

---

### Post by M_the_C on 2008-03-04
> **stimpack said:**
> There was a brilliant article comparing the filesystems, everything from speeds on various operations to reliability. It was amazingly complex and there is no way I can state which is best without being a fool, but ext3 consistently neared the bottom on most graphs. If someone can link this article I'd be grateful.Do you mean [this one?]("http://linuxgazette.net/102/piszcz.html")  I found this article through these forums, it is great.

For those who don't want to read it all, the basic conclusion was that it depends on what you use it for.  XFS is best for handling large files (hence why it's recommended for mythtv, for your storage paritions) and ReiserFS for small files.  After re-reading the conclusion i found it also recommends JFS, but I can't remember the reason for that one.

---

