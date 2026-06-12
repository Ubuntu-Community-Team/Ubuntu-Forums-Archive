---
title: "Will future releases of Ubuntu support ext4?"
date: 2008-03-19
forum: The Cafe
---

### Post by keeler1 on 2008-03-19
I was reading up on the next release of fedora (I flip flop between using Ubuntu and fedora) and they are going to by default use the ext4 filesystem.  After looking at some of the new things ext4 brings I wanted to know if there were any plans to incorporate the filesystem into Ubuntu hardy or later versions.

---

### Post by 23meg on 2008-03-19
[QUOTE=keeler1]I was reading up on the next release of fedora (I flip flop between using Ubuntu and fedora) and they are going to by default use the ext4 filesystem.[/QUOTE]

No, they'll feature EXT4 among the filesystems that the user can choose at install time. They won't make it the default.

[QUOTE=keeler1]After looking at some of the new things ext4 brings I wanted to know if there were any plans to incorporate the filesystem into Ubuntu hardy or later versions.[/QUOTE]

Hardy is at beta stage; way too late. Check [https://blueprints.launchpad.net/ubuntu/intrepid](https://blueprints.launchpad.net/ubuntu/intrepid) in a few weeks.

---

### Post by el mariachi on 2008-03-19
are the improvements THAT significant? (just asking..)

---

### Post by LaRoza on 2008-03-19
> **el mariachi said:**
> are the improvements THAT significant? (just asking..)

Given the quality of EXT2 and EXT3 for general use, I would say the average user doesn't really need to be worried about it.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by Polygon on 2008-03-19
why wouldn't ext4 be default? i mean, its got to have improvements over ext3 in some form or fashion

---

### Post by LaRoza on 2008-03-19
> **Polygon said:**
> why wouldn't ext4 be default? i mean, its got to have improvements over ext3 in some form or fashion

It is too late to change. Development can't just be hapharzard, it has to be planned, tested, and approved.

---

### Post by NightwishFan on 2008-03-19
Ext4 sounds promising. I might get it when it is available.

---

### Post by keeler1 on 2008-03-19
Here is the link where I was reading about its integration into fedora.
It explains the advancements far better than I could.

[http://fedoraproject.org/wiki/Interviews/EricSandeen](http://fedoraproject.org/wiki/Interviews/EricSandeen)

I misspoke when I mentioned it being the default.  Like it was said in a previous post.  It is going to be "featured" in the release of Fedora 9.

Basically what I got out of the article was that ext4 is supposed to be ext3 but faster and with a few extra features.  While the average user may not "need" the performance gains from ext4 it would be nice to have the option.

While I know it is unreasonable to expect it in the hardy release, it is definitely something that should be considered for releases after that.

---

### Post by el mariachi on 2008-03-20
can't we just use PartedMagic or something similar to partition our drives with EXT4 and then install Hardy?

---

### Post by TenPlus1 on 2008-03-20
Supposidle Ext3 is forward compatible and can be mounted as Ext4 with all the new features...  I'll wait for it to be implemented in the kernel and give it a bash sometime...

---

### Post by Polygon on 2008-03-20
> **LaRoza said:**
> It is too late to change. Development can't just be hapharzard, it has to be planned, tested, and approved.

someone said that ext4 would never be default in ubuntu, i know its not going be in hardy, but i meant for any future release of ubuntu

---

### Post by el mariachi on 2008-03-20
> **Polygon said:**
> someone said that ext4 would **never** be default in ubuntu, i know its not going be in hardy, but i meant for any future release of ubuntu
that would be idiotic (no flame intended), because never means NEVER.
So in a few years time, when ext7 comes along, Ubuntu will still be using ext3? I don't think so :p

I believe they will make it default after Hardy, or at least an available option:)

---

### Post by NightwishFan on 2008-03-20
Finding a good default Linux filesystem has been a real headache I hear.

---

### Post by el mariachi on 2008-03-20
> **NightwishFan said:**
> Finding a good default Linux filesystem has been a real headache I hear.
hummm I must admit I never tried anything else besides ext3. As far as my understanding goes, I think the other options (ReiserFS and all others) have better perfomance on small files, but since I use big files (who doesn't nowadays?) i don't see any real point in changing. But I may be wrong, if so correct me please:KS

---

### Post by NightwishFan on 2008-03-20
I generally use ext3 because it seems to be the most supported. I figured ext2 would be better since I do not really have much data to risk losing but I saw no real performance difference.

---

### Post by el mariachi on 2008-03-20
So you're saying ext2 is safer?

---

### Post by NightwishFan on 2008-03-20
No I am saying ext3 is safer but writes to the journal. I figured I would get better performance if I used ext2 as I have all my files backed up. It really made no difference so I just use ext3.

---

### Post by djbsteart1 on 2008-03-20
It might just be my head but I think I could see a difference when comying an iso from jfs to jfs compared to jfs to ext3. But it was probably just because I knew that jfs was faster supposadly.

---

### Post by el mariachi on 2008-03-20
always faster? there must be some weird disadvantage lol (when using jfs)

---

### Post by NightwishFan on 2008-03-20
Try wikipedia.

---

### Post by Erunno on 2008-03-20
> **TenPlus1 said:**
> Supposidle Ext3 is forward compatible and can be mounted as Ext4 with **all** the new features...

Emphasis mine.

As far as I know the on-disk structure was altered for ext4 so how would it be possible for an ext3 partition to support all new features? Are they independent of the on-disk structures?

Anyway, so far I haven't seen anything really exciting about ext4. It features mostly corrections to some long-standing architectual errors (i.e. 32000 subdirectory limit, max. size limit) or introduces features already available in other filesystems (i.e. XFS has been supporting extents, delayed allocations, online defragmantation, etc. for years).

---

### Post by deepclutch on 2008-03-20
what Linux misses?well,my friends it is ZFS file system that is used by opensolaris.it is the most promised FS ever.but due to cc license,it cannot be in GNU/Linux.while zfs-fuse thing may be available. :-|
read here:
**Why Linux needs ZFS badly :-** (by a gentoo developer)
> **Linux needs ZFS - and badly!**

                      [before you flame me, I know that Linux (Gentoo, in fact) has zfs-fuze, but it is still pretty experimental, and it runs in user space, which makes it noticeably slower]
  ZFS is Sun's very cool filesystem. I won't go into detail here - just google it - but it has some eye-opening features, the most critical of which is end-to-end data integrity. Unfortunately, ZFS's license is incompatible with the GPL.
  I say "critical" because I have a strong feeling that silent data corruption is far more prevalent than most people believe. Also, I just don't buy the argument that bit-for-bit reliability is only important for servers. Yes, in certain circumstances, a bit flip here or there may not be noticed, but I think that is scary as hell. Personally, I'd rather know; I count on computers to copy the bits exactly, don't you? We simply cannot tolerate random bit errors, no matter how "unnoticeable". And you *will* notice if that bit flip hits a critical part of your file.
  With disk drives becoming larger and larger and the marketing departments of drive manufacturers knowing that the general public doesn't understand these issues, they tend to boast speed and size over reliability. We will soon be in real trouble. For an upcoming space mission I'll be working on at my job, we may have to buy *petabytes* of storage. With this much, the current hard drive uncorrectable error rates will cause multiple errors per day, letting the data potentially bit rot with current modern filesystems. And just as bad, swap space is also susceptible. So even if you have ECC memory (and I recommend it highly), if your data ends up in swap, you are vulnerable.
  In my experience with computers, I have caught *two* examples of silent data corruption. These are ones I actually discovered. It freaks me out to think there may be many more that went unnoticed. And both were due to bad IDE cables (so even the hard disk error rates don't count here) on two different computer systems. The first on the old and slow PATA and was some data pattern dependent copy glitch, where a diff found the problem. The other was this past year on a modern UDMA/80-conductor cable, and it was found by ZFS - it appears that during some reported DMA errors (probably the cable's fault), a 64K file block got written to the wrong spot on the disk (PATA does not protect the data address part of the communication).
  ZFS is the only filesystem that actually will catch silent corruption in the whole chain: ATA interface -> cable -> disk (HW and firmware). For those who say, "Why not RAID?", well, RAID will save you if a whole drive fails, but not these more insidious issues. I bet Linus and others are seriously thinking about what to do, since what once was considered rare could become commonplace. There are rumors Apple will adopt ZFS, and FreeBSD already has it in its kernel (and, of course, Solaris has it). For now, zfs-fuse is very interesting, but I think we need such protection of our data in the kernel, and soon. 
                    
[http://planet.gentoo.org/developers/lavajoe/2008/02/18/linux_needs_zfs_and_badly](http://planet.gentoo.org/developers/lavajoe/2008/02/18/linux_needs_zfs_and_badly)

this is a old review:
[http://tastic.brillig.org/~jwb/zfs-xfs-ext4.html]("http://tastic.brillig.org/%7Ejwb/zfs-xfs-ext4.html")

Hope ZFS will land in GNU/Linux without fuse! :)

[FONT=Times New Roman][SIZE=4]**[COLOR=Blue]EDIT:[/COLOR]**[/SIZE][/FONT]
**submitted to DIGG:**
[http://digg.com/linux_unix/Linux_needs_ZFS_and_badly](http://digg.com/linux_unix/Linux_needs_ZFS_and_badly)

---

### Post by igknighted on 2008-03-20
> **deepclutch said:**
> what Linux misses?well,my friends it is ZFS file system that is used by opensolaris.it is the most promised FS ever.but due to cc license,it cannot be in GNU/Linux.while zfs-fuse thing may be available. :-|
read here:
**Why Linux needs ZFS badly :-** (by a gentoo developer)

[http://planet.gentoo.org/developers/lavajoe/2008/02/18/linux_needs_zfs_and_badly](http://planet.gentoo.org/developers/lavajoe/2008/02/18/linux_needs_zfs_and_badly)

this is a old review:
[http://tastic.brillig.org/~jwb/zfs-xfs-ext4.html](http://tastic.brillig.org/~jwb/zfs-xfs-ext4.html)

Hope ZFS will land in GNU/Linux without fuse! :)

While I would LOVE to see ZFS in linux, I have to admit I laugh a little every time I see linux people complaining about incompatible (but still certified OSS) licenses.  After all we've stolen from BSD, improved, and GPL'd so they can't use it, it's a rather ironic situation now with ZFS.

---

### Post by articpenguin on 2008-03-20
ext4 will have

Extents
Mutiblock allocator
Delayed allocation
Improved Htree
defragger


and faster fsck times

---

### Post by articpenguin on 2008-03-20
ext4 will have

Extents
Mutiblock allocator
Delayed allocation
Improved Htree
defragger


and faster fsck

---

### Post by el mariachi on 2008-03-20
> **igknighted said:**
> While I would LOVE to see ZFS in linux, I have to admit I laugh a little every time I see linux people complaining about incompatible (but still certified OSS) licenses.  After all we've stolen from BSD, improved, and GPL'd so they can't use it, it's a rather ironic situation now with ZFS.
I have to agree... BSD gives everything away and then Linux people close it with GPL. I never understood exactly how these work (why can't it be distributed with Linux?). I'll have to educate myself on this matter

---

### Post by djbsteart1 on 2008-03-20
> **el mariachi said:**
> always faster? there must be some weird disadvantage lol (when using jfs)

It might still be prone to framentation, but I am not sure. I think it is also less intensive on cpu, but most of these things I imagine are neligable.

---

### Post by el mariachi on 2008-03-20
in the end, for the average desktop user just wishing to have an ordinary computer, for ordinary tasks (office, multimedia, games, browsing), there mustn't be a lot of difference between each one of the Linux FS's

---

### Post by djbsteart1 on 2008-03-20
True, but what has been said about ZFS seemsvery wooryin/important, because thechance of this occuring over a lon period of time will be exponential. 
It really does seem wron that GPL shuts the doot on the BSD's yet they have theres open.

---

### Post by deepclutch on 2008-03-20
that is what GPL is for!GPL does protect the code from "misuse" I mean even closed source projects can use BSD licensed codes.while,GPL prevents this loss,and asks the new contributor to stick with the FOSS community! :D

---

### Post by hhhhhx on 2008-03-20
4 is a bigger number than 3, so it has to be better :)

---

### Post by NightwishFan on 2008-03-20
> **xhhux said:**
> 4 is a bigger number than 3, so it has to be better :)

+1

---

### Post by LaRoza on 2008-03-20
> **xhhux said:**
> 4 is a bigger number than 3, so it has to be better :)

Windows 95 > Windows 7?

---

### Post by articpenguin on 2008-03-21
> **djbsteart1 said:**
> It might still be prone to framentation, but I am not sure. I think it is also less intensive on cpu, but most of these things I imagine are neligable.

JFS can get so fragmented that it can slow down to 5MB/s and im getting affected by it too =(

[http://www.mail-archive.com/jfs-discussion@lists.sourceforge.net/msg00708.html](http://www.mail-archive.com/jfs-discussion@lists.sourceforge.net/msg00708.html)

---

### Post by djbsteart1 on 2008-03-21
> **articpenguin said:**
> JFS can get so fragmented that it can slow down to 5MB/s and im getting affected by it too =(

[http://www.mail-archive.com/jfs-discussion@lists.sourceforge.net/msg00708.html](http://www.mail-archive.com/jfs-discussion@lists.sourceforge.net/msg00708.html)

There was an error when it tried to write large files, they weren't always put into one space. But this is ment to have been fixed. Seeing as I reinstall so often it isn't a problem for me, but from the windows years I know what you mean.

---

### Post by djbsteart1 on 2008-03-21
> **deepclutch said:**
> that is what GPL is for!GPL does protect the code from "misuse" I mean even closed source projects can use BSD licensed codes.while,GPL prevents this loss,and asks the new contributor to stick with the FOSS community! :D

Yes this is very good, but surely BSD should be able to use stuff in GPL with BSD being open source and all. Addmittagly that would let Applle in, so I guess the GPL license is fair to most.

---

### Post by el mariachi on 2008-03-21
but why can't we mix licenses? like using GPL'd code in BSD? Just that portion of code would be GPL'd.

What about ReiserFS? Has anyone got any experience with that?

---

### Post by bruce89 on 2008-03-21
> **articpenguin said:**
> ext4 will have

Extents
Mutiblock allocator
Delayed allocation
Improved Htree
defragger


and faster fsck times

> **articpenguin said:**
> ext4 will have

Extents
Mutiblock allocator
Delayed allocation
Improved Htree
defragger


and faster fsck

So good, you posted it twice.

> **deepclutch said:**
> that is what GPL is for!GPL does protect the code from "misuse" I mean even closed source projects can use BSD licensed codes.while,GPL prevents this loss,and asks the new contributor to stick with the FOSS community! :D

Unless you don't publicly distribute your modifications. The GPL allows you to modify something for personal use and not distribute your changes.

> **el mariachi said:**
> but why can't we mix licenses? like using GPL'd code in BSD? Just that portion of code would be GPL'd.

The GPL says that any "derivative works" have to also be under the GPL.

I don't think that licence proliferation is a problem, even though MS are trying their best to confuse people with their own "open source" licences.

---

### Post by djbsteart1 on 2008-03-21
> **el mariachi said:**
> but why can't we mix licenses? like using GPL'd code in BSD? Just that portion of code would be GPL'd.

What about ReiserFS? Has anyone got any experience with that?

I used to use reisefs, but then I read somewhere, probably wikipedia that he made some negative comments about the linux kernel, saying, pretty much hat his code was the only good code in the kernel, and the rest was crap.

---

### Post by bruce89 on 2008-03-21
> **djbsteart1 said:**
> I used to use reisefs, but then I read somewhere, probably wikipedia that he made some negative comments about the linux kernel, saying, pretty much hat his code was the only good code in the kernel, and the rest was crap.

He's now on trial for allegedly murdering his wife.

---

### Post by el mariachi on 2008-03-21
humm yeah I also read that. How unfortunate. Still, it seems that ReiserFS is more small-file oriented (stuff like Usenet and small servers)

---

### Post by Eclipse. on 2008-03-21
I know they have added ext4 support in fedora 9 but for a LTS release ext4 would have just been out of the question.My guess would be 8.10.

---

### Post by AusIV4 on 2008-03-21
> **el mariachi said:**
> always faster? there must be some weird disadvantage lol (when using jfs)
I use JFS for my MythTV recordings. I tried using ext3 for a while, but I was getting full system crashes fairly regularly. Switching to JFS fixed that. JFS seems to read and write faster than ext3, and delete times are immensely faster. 

There are a couple of disadvantages. First, ext2 is available for most platforms (sometimes requiring extra drivers). Since ext3 can be used as ext2 under certain circumstances, this makes it much more cross platform than JFS, which is only available on OS/2, AIX, and Linux.

The second point is that JFS can only be grown, never reduced. On my laptop, I use LVM and shuffle partitions around all the time. Since JFS can't be reduced, I stick to ext3. JFS is only practical in places like my Desktop, which I expand occasionally, but I never reduce it.

---

### Post by el mariachi on 2008-03-21
a good benchmark/comparison would be great, because all this talk has made me curious about the other filesystems. 

Reducing or growing partitions isn't a drawback for me, because I rarely do those. Ext4 is just around the corner, let's do some serious testing then :D

---

### Post by djbsteart1 on 2008-03-22
> **bruce89 said:**
> He's now on trial for allegedly murdering his wife.

Thats  different story, and even if he did, and his filesystem was great I would use it, it was the remarks on the kernel that stopped me. I was hoping that that wasn't gong to be brought in as it wasn't an issue for me when it comes to his filesystem.

---

### Post by djbsteart1 on 2008-03-22
> **el mariachi said:**
> a good benchmark/comparison would be great, because all this talk has made me curious about the other filesystems. 

Reducing or growing partitions isn't a drawback for me, because I rarely do those. Ext4 is just around the corner, let's do some serious testing then :D

The problem with benchmarks of these sorts is that the results are still quite variable, as you have said, many of the filesystems are better for some things than others, and i am sure will perform differently with different OS's and hardware. Here is a thread i started purely for filesystems, it doesn't go into it that much, but still might be of interest. [Link.]("http://ubuntuforums.org/showthread.php?t=707165")

---

### Post by argie on 2008-03-22
> **djbsteart1 said:**
> The problem with benchmarks of these sorts is that the results are still quite variable, as you have said, many of the filesystems are better for some things than others, and i am sure will perform differently with different OS's and hardware. Here is a thread i started purely for filesystems, it doesn't go into it that much, but still might be of interest. [Link.]("http://ubuntuforums.org/showthread.php?t=707165")

What I'd be interested in is a benchmarking tool. Is there a set of scripts that creates, moves, archives, extracts, deletes files of different sizes and then returns the time taken for each of those operations as output? Then we could just create our own partitions and see what the performance is on our own computers.

---

### Post by djbsteart1 on 2008-03-22
> **argie said:**
> What I'd be interested in is a benchmarking tool. Is there a set of scripts that creates, moves, archives, extracts, deletes files of different sizes and then returns the time taken for each of those operations as output? Then we could just create our own partitions and see what the performance is on our own computers.

This would be vry useful and probably ive the best results. However I don't know of such a tool, but i ma sure that one will exist somewhere.

---

### Post by Rhapsody on 2008-03-22
I'm sure Ubuntu will use ext4 as the default file system at some point in the future, but that will only be after ext4 has been classified as 'stable' by the developers (it's currently marked as 'developmental').

I'll be quite happy to use it when that happens. New features, improved performance, creation timestamps (minor thing, but I missed them after having them for years on FAT16/32 and NTFS) and an online defragmenter will certainly be welcome. Until then, I'll still be using ext3.

---

