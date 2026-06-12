---
title: "ReiserFS or EXT3, which do YOU prefer?"
date: 2008-07-25
forum: The Cafe
---

### Post by uberlube on 2008-07-25
I am curious to know how many people out there are using reiserFS and how it stacks for a desktop users needs. After voting leave a note as to your experience with it and if you recommend it. Also let us know if you are using a single or dual-core.

---

### Post by diwas on 2008-07-25
[http://ubuntuforums.org/showthread.php?t=854129](http://ubuntuforums.org/showthread.php?t=854129)

I think this will help u out.

---

### Post by YaroMan86 on 2008-07-25
I use reiserfs for the main partition for Ubunt... and ext3 for my home partition.

Do I need to say what I use for my swap partition? :P

---

### Post by uberlube on 2008-07-25
> **diwas said:**
> [http://ubuntuforums.org/showthread.php?t=854129](http://ubuntuforums.org/showthread.php?t=854129)

I think this will help u out.

Crap I didnt see that when I searched the forum, lol. O well, id still like to see the results from this as its just reiser Im interested in.

---

### Post by Koori23 on 2008-07-25
Uh.. I tend not to use things that were the brainchild of a murderer.

---

### Post by madjr on 2008-07-25
> **Koori23 said:**
> Uh.. I tend not to use things that were the brainchild of a murderer.

Well at least he will have enough time in prison to perfect "*ReiserFS 2 - the vengeance*"

---

### Post by Barrucadu on 2008-07-25
I prefer ReiserFS, I use it for my /var partition as it is great with lots of small files. I don't actually use Ext3, my favourite filesystem is JFS, though I use Ext2 for /boot.

> **Koori23 said:**
> Uh.. I tend not to use things that were the brainchild of a murderer.
That's a silly reason not to use something. If he created the cure for the common cold would you boycott that?

---

### Post by InfinityCircuit on 2008-07-25
Reiser eats data.  Plain and simple.  Use ext3.

ext4 is also far better than reiser4.  Reiser4 works well for 2 weeks and then fragments to hell.

---

### Post by samwyse on 2008-07-25
ReiserFS takes a long time to mount large partitions. EXT3 takes a looong time to do the periodical check on large partitions.

---

### Post by tubezninja on 2008-07-25
I've had bad luck with ReiserFS volumes.  Corrupted data, files not reporting their correct sizes, and yet fsck says everything is fine.

Never had an issue with ext3.

---

### Post by bsharp on 2008-07-26
ext3 cause it's the default and I've never had any probs with it....the reverse would be true for me if reiserfs was default.

---

### Post by stimpack on 2008-07-26
ReiserFS simply because I hate ext3 fsck'ing every 30 boots or whatever.

Both are well proven and any personal experience is statistically irrelevant.

---

### Post by damis648 on 2008-07-26
> **stimpack said:**
> ReiserFS simply because I hate ext3 fsck'ing every 30 boots or whatever.

Both are well proven and any personal experience is statistically irrelevant.

This can be disabled with an override, and is just a check to help keep you safe from lost or corrupted data. I myself have never had any problems with Ext3... I only used ReiserFS once, not that my experience was bad, I just didn't care for it.

---

### Post by Canis familiaris on 2008-07-26
This really should have been a multiple choice poll.

I use both.

My / is ReiserFS
My /home is ext3

---

### Post by billgoldberg on 2008-07-26
I'm using reiserfs on my desktop, and ext3 on my laptop.

The only change I notice is that the reiserfs pc doesn't ask to check the disk for errors every 30 or so boots.

So I prefer reiserfs.

---

### Post by billgoldberg on 2008-07-26
> **Anurag_panda said:**
> This really should have been a multiple choice poll.

I use both.

My / is ReiserFS
My /home is ext3

The question isn't what do you use, but what do you prefer.

---

### Post by Canis familiaris on 2008-07-26
> **billgoldberg said:**
> The question isn't what do you use, but what do you prefer.

The poll question asks what do you use? :)

---

### Post by smartboyathome on 2008-07-26
I don't prefer one over the other, one is just better in some situations than the other. I use ReiserFS for / and Ext3 for /home, due to ReiserFS's superior handling of small files and Ext3's stable track record. What I hate about Ext3, though, is that it takes very long just to format a partition.

---

### Post by Peyton on 2008-07-26
> **stimpack said:**
> ReiserFS simply because I hate ext3 fsck'ing every 30 boots or whatever.

Both are well proven and any personal experience is statistically irrelevant.

As damis648 noted, you can change that:

[http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

---

### Post by david_lynch on 2008-07-26
I've been using reiser everywhere for the past 4 years or so. It's the default filesystem on suse linux enterprise, which we use in the datacenter at a fortune 100 company.

I use reiser on my own desktops and laptops, and when I build servers for consulting clients, they are reiserfs. 

Why? performance. I just don't want the performance hit that ext3 imposes, but I do want a journalling filesystem, and I want something mainstream.

In every performance comparison I've done, reiser beats the hell out of ext3. xfs also performs well, but it is apparently enough out of the mainstream that it has issues e.g. grub has problems booting from an xfs disk. jfs has some virtues, but speed is not one of them.

Eventually reiserfs in our environment will be superceded, since reiser4 looks to be dead in the water, due to various factors. Maybe the next killer linux fs will be ext4, or it could be btrfs, a filesystem sponsored by oracle and developed by Chris Mason, and which looks quite promising.

---

### Post by insane_alien on 2008-07-26
i use ext3 for my root partition but XFS for my data partitions, it handles massive files very well.

---

### Post by bobbocanfly on 2008-07-26
> **david_lynch said:**
> 
In every performance comparison I've done, reiser **beats the hell out of** ext3. xfs also performs well, but it is apparently enough out of the mainstream that it has issues e.g. grub has problems booting from an xfs disk. jfs has some virtues, but speed is not one of them.

Eventually reiserfs in our environment will be superceded, since reiser4 looks to be **dead in the water**, due to various factors. Maybe the next **killer** linux fs will be ext4, or it could be btrfs, a filesystem sponsored by oracle and developed by Chris Mason, and which looks quite promising.

Was that intentional? :P

---

### Post by steveneddy on 2008-07-26
> **Koori23 said:**
> Uh.. I tend not to use things that were the brainchild of a murderer.

My thoughts exactly.

---

### Post by uberlube on 2008-07-26
I never knew that he killed his wife, ouch. I do have to say that knowing this will have an effect on my decision to give it a try but it will not be the only deciding factor. What a douchebag.

---

### Post by david_lynch on 2008-07-29
You guys crack me up. reiserfs 3 was developed several years before Mr Reisers unfortunate crime of passion. In any event, usage of reiserfs does not constitute support for murder. In a few years the choices will be different, but right now reiserfs is the best I can find, regardless of what depths the original filesystem designer eventually sank to.

---

### Post by ModelM on 2008-07-29
I've used Reiser FS since I first used Suse linux - this was back in the day when they included a little chameleon pin in the box. It's never given me any problems & I like the fact that the file system check is so fast it checks at every boot. Unless the laptop is on battery power - it senses that & skips the fsck in that case.

---

### Post by SupaSonic on 2008-07-29
Well for me reiserFS is a 'killer' FS. Oops, that came out wrong.

On a serious note, i've had two corrupted drives with ext3 after power failures. None with reiserFS. And I don't care who made it. It's a filesystem, it didn't kill anyone. And never will.

---

### Post by srvm on 2008-07-29
Nice thread. I was of the opinion that ReiserFS performs well only with small files. I've used it for /tmp and /var partitions for a few months now. I guess I should try out Reiser on root as well.

---

### Post by Saint Angeles on 2008-07-29
i used reiserFS until i started having homicidal visions about my wife... now i use ext3 and the visions are gone!

just kidding... i've never used reiserFS but i have no issues with ext3 at all.

man these jokes will never get old

---

### Post by Archmage on 2008-07-29
> **david_lynch said:**
> You guys crack me up. reiserfs 3 was developed several years before Mr Reisers unfortunate crime of passion. In any event, usage of reiserfs does not constitute support for murder. In a few years the choices will be different, but right now reiserfs is the best I can find, regardless of what depths the original filesystem designer eventually sank to.

The problem is, that there are not many people that will do bugfixing and devloping the new version, since the main devloper has other things on his mind right now.

---

### Post by blazemore on 2008-07-29
Reiser is ever so slightly faster for multiple small-file operations. However, its very nature means that, in the case of hard drive failure, data are almost impossible to recover.

---

### Post by articpenguin on 2008-07-29
I perfer JFS.

One-It uses B+ trees to scale with large directorys that ext3 is slow on.

second- It dynamically allocates Inodes. ext3 is a HUGE PIG with inodes. I lost 9GB because of its inodes on my 500GB partition.

---

### Post by Blibit42 on 2009-04-13
We have two large servers, both with 11 terabytes holding just over 15 million files with an average (median) file size about 700K each.
We set up ext3 on the first server, but read that resier was good with many small files, and also good with larger numbers of files. 
*Now for the BIG SURPRISE: ***When we copied all of the data over from the ext3 disks to the resiers (1 for 1), we had 45 to 50 gigs left free on every reiser drive!** We thought maybe we messed up the partitions, or that we had some settings screwed up, but no, reiser is simply that much more efficient with its file storage scheme (allocation of sectors to files). 
When we first set it up using ext3, we were also unlucky enough to find out how long it takes to fsck 11 full one terbayte ext3 drives. It took all day long (and then some). That sucked... (we are thankful that we still had our old Windoze server running). 
We had been using the ext3 server for a few months before THAT happened. We thought it would be a couple of hours at most.

The file manager also responds MUCH faster when listing the directories under reiser. So needless to say, we are sold on resier, at least for our data storage needs. We still use ext3 to boot from because that is the default installation (so why mess with it).
When manually checking the reiser disks with reiserfsck it takes about 1 hour on each of our disks if we watch it (with the log going to stdout) - but if you minimize it so it doesn't have to waste time writing to the console, it goes MUCH faster - about half the time (you wouldn't think so, but GUI consoles showing character based data slow it down a bit). We should have shut down X to do it, but "whooda thunk it?"

Cheers,
  Blibit42

---

### Post by sekinto on 2009-04-13
i personally like XFS, I've had good experiences with JFS to. Although I am currently using EXT3.

---

