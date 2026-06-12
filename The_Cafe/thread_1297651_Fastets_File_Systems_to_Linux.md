---
title: "Fastets File Systems to Linux"
date: 2009-10-22
forum: The Cafe
---

### Post by Ravernomina on 2009-10-22
As it is stated above can people tell me what the fastest file system is available to linux. Hence i only Used the EXT file systems i want to know the other filesystems so i can pick the best one to suit me.

---

### Post by SomeGuyDude on 2009-10-22
I think some are fast in different ways. Some can move large files quickly, others LOTS of files quickly.

---

### Post by cascade9 on 2009-10-22
Agree 100% with SomeGuyDude.

BTW, I think you've made a minor typo. BTRS should be BTRFS (unless you mean BFS).

---

### Post by RichardLinx on 2009-10-22
I use Ext4, but I don't think it's the fastest or the most advanced file system out there. I don't know which is though.

---

### Post by cascade9 on 2009-10-22
The 'most advanced' file system is probably BTRFS. Or it will be once its in 'stable' form.

---

### Post by Cope57 on 2009-10-22
> Fastets File Systems to Linux

I would not know how to answer this...  Is this a trick question?

I would guess and say try them all, and you can decide which is the fastest with the hardware that you are currently using.

---

### Post by SomeGuyDude on 2009-10-22
XFS seemed to work really well with large files, but when I had to so something like open my usr/bin folder it draaaaaaaaaagged. Ext4 is a lot better than Ext3, and overall it works as quickly as I could hope for.

---

### Post by handy on 2009-10-22
> **Ravernomina said:**
> As it is stated above can people tell me what the fastest file system is available to linux. Hence i only Used the EXT file systems i want to know the other filesystems so i can pick the best one to suit me.

Votes made up from people's personal preferences that are based on whatever foundation; some valid others invalid is really not the way to choose which is actually the file system that suits you.

The following link is to a results posted here by a person who's name I don't recall.

That person worked hard to both test & collate the results for our benefit.  His thread still exists here for anyone willing to try & search it out.

I had to post this link over in ostalk.org as the size of attachments must have been reduced here since this .pdf was posted here?

[http://www.ostalk.org/showthread.php?tid=634](http://www.ostalk.org/showthread.php?tid=634)

It only does 5 file systems, but it should give you an idea of what kind of data you are looking for when wanting to make a choice.

There is a great page on the Debian forums on file systems also.

---

### Post by cascade9 on 2009-10-22
Heh, if I try to d/l that file from OS Talk I get the good old "You are either not logged in or do not have permission to view this page" msg. 

BTW SomeGuyDude,the EXT3/EXT4/BTRFS developer (Theodore Ts'o) has started that EXt4 is just a stopgap  and BTRFS is the way forward-
[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

---

### Post by hoppipolla on 2009-10-22
What WAS Reiser4 like? o.O

---

### Post by tubasoldier on 2009-10-22
> **hoppipolla said:**
> What WAS Reiser4 like? o.O

Slow, unstable, and constantly needing to be recovered on boot.
I lost a lot of data while using it.

---

### Post by Xbehave on 2009-10-22
!ext , the others are fastest in different workloads, ext is the turtle its slow and steady and well designed. I think for everyday loads reiserfs is fastest (but uses more CPU), alternatively if you don't mind using the latest FS (more likely to lose data) then btrfs is the way to go.

Oh ted tso only does ext not btrfs (that's oracle's baby)

---

### Post by ssam on 2009-10-22
google use ext4 with journalling turned off (they dont care for recovering machines after a crash, they just re-image). before they used ext2. (mentioned [http://lwn.net/Articles/313514/](http://lwn.net/Articles/313514/) you have to hunt for the original post).

---

### Post by ukripper on 2009-10-22
EXT4 all the way unless you have to run distributed/enterprise level servers, in that case XFS. In all other cases EXT4

BTRFS ain't out yet and also not in stable state, so I won't consider that in poll.

---

### Post by handy on 2009-10-22
> **cascade9 said:**
> Heh, if I try to d/l that file from OS Talk I get the good old "You are either not logged in or do not have permission to view this page" msg. 

BTW SomeGuyDude,the EXT3/EXT4/BTRFS developer (Theodore Ts'o) has started that EXt4 is just a stopgap  and BTRFS is the way forward-
[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

Bummer, you must have to register to get at the attachment.

Sorry about that, it hadn't occurred to me that, that would be a problem...

As previously stated I would attach it here, but the file is now larger than what the UF will accept, though it used to accept them at that size, because I got it from here originally.

---

### Post by samjh on 2009-10-22
There is no single file system which is "fastest".  They each have strengths and weaknesses.

ext4, xfs, and jfs are all considered to be generally fast, but one's experience will vary.  I'm personally fond of JFS for its performance, maturity, and safety.

---

### Post by khelben1979 on 2009-10-22
I voted for [ReiserFS]("http://en.wikipedia.org/wiki/Reiserfs") because that's my guess.

---

### Post by handy on 2009-10-23
> **samjh said:**
> There is no single file system which is "fastest".  They each have strengths and weaknesses.

ext4, xfs, and jfs are all considered to be generally fast, but one's experience will vary.  I'm personally fond of JFS for its performance, maturity, and safety.

I too like JFS, though I have converted a storage partition on my dual booting iMac, that I had created for Arch, from JFS to ext3. As I can now use software under OS X, that makes ext3 fully accessible, which I find very convenient.

---

### Post by cascade9 on 2009-10-23
Just in case anyone is interested, this is actually a neat set of benchmarks- 

[http://t2-project.org/zine/1/](http://t2-project.org/zine/1/)

There is also this, but its a fair way down the page, follow the 'Benchmarking filesystems' link at the top. 

[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

---

### Post by SomeGuyDude on 2009-10-23
If there were a way to change filesystems without losing all your data, maybe I'd have tried more, but feh. I've used ext3, XFS, and ext4, and ext4 is my favorite of those three.

---

### Post by cascade9 on 2009-10-23
EXT4 is still bit too new for my liking. It would probably be OK for the root partition (data loss? bah, reinstall!) but I'm not trusting my media files to it, yet.

---

### Post by Stan_1936 on 2009-10-23
> **SomeGuyDude said:**
> XFS seemed to work really well with large files, but when I had to so something like open my usr/bin folder it draaaaaaaaaagged. **Ext4** is a lot better than Ext3, and **overall it works as quickly as I could hope for.**

Yay, yay!!! Me too, Me too!!!

For me, ext4 is faster than ext3, so I use it and call it the "fastest".

---

### Post by handy on 2009-10-23
I've read somewhere in the past, (sorry don't remember where) that there are changes in the .31 kernel which will actually speed up the ext3 file system.

I have been using the .31 kernel for a week or so (since it came out of testing in Arch) & can't say I've noticed any speed difference.  Though really, I don't actually do much with my machine, so I could be totally missing the fact that it is faster under certain working conditions...?

---

