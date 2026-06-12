---
title: "NTFS vs ext4"
date: 2009-02-20
forum: The Cafe
---

### Post by velja27 on 2009-02-20
So can anybody make a pros and cons list of these two?

---

### Post by murman on 2009-02-20
I don't think any comparable benchmarking between the two has been done, Although if there has then the results would be interesting

---

### Post by SunnyRabbiera on 2009-02-20
Well NTFS is older, while ext4 is newer.
But I say hat overall EXT in any form is better then NTFS.
NTFS tends to frag up a lot, EXT2 had some issues with it but EXT3 has no frag issues as does ext4.

---

### Post by thisllub on 2009-02-20
Windows doesn't do ext4?

---

### Post by SunnyRabbiera on 2009-02-20
> **thisllub said:**
> Windows doesn't do ext4?

Not nativly, though you can get XP to see EXT drives, including ext4 due to backwards compatibility modules.

---

### Post by RichardLinx on 2009-02-20
Pretty in depth comparison of file systems: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by velja27 on 2009-02-20
> **myusername said:**
> google

Like i haven't,genius.

> **RichardLinx said:**
> Pretty in depth comparison of file systems: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Thanks alot, wikipedia is the best encyclopedia ever.

---

### Post by h4mx0r on 2009-04-22
yeah so if you want to compact a large amount of data that you will never work with use reiserfs. However if you want performance (memory and cpu considered) and no loss of data if power failure or crash then choose something different? 

Hmm I heard of something called jfs but none seem to use it. Ext4 does look surprisingly better than ext3, what is the big difference though? Is it just ext3 with updates, or any new features?

---

### Post by SunnyRabbiera on 2009-04-22
> **h4mx0r said:**
> Ext4 does look surprisingly better than ext3, what is the big difference though? Is it just ext3 with updates, or any new features?

In a way it is EXT3 with updates, as most of the EXT filesystems have a link to eachother.
But EXT4 does offer its own set of features such as faster boot up and defragment tools as even though EXT filesystems are better then NTFS they still fragment over time.
But I dont suspect EXT4 will be a default anytime soon, its still fresh and not many bugfixes have come out for it so right now if EXT3 works use it as EXT4 is not a critical update, just a optional one.

---

### Post by zugu on 2009-04-23
At least NTFS is highly stable. I can't say that about ext4.

---

### Post by Sef on 2009-04-23
> At least NTFS is highly stable. I can't say that about ext4.


For me, so far, it has been very stable.

---

### Post by go2dell on 2009-04-23
> **h4mx0r said:**
> yeah so if you want to compact a large amount of data that you will never work with use reiserfs. However if you want performance (memory and cpu considered) and no loss of data if power failure or crash then choose something different? 

Hmm I heard of something called jfs but none seem to use it. Ext4 does look surprisingly better than ext3, what is the big difference though? Is it just ext3 with updates, or any new features?

As a longtime Reiser3 user, I can say that it definitely has speed advantages, and it also is more efficient with very small files.  Due to Hans Reiser's current status, I don't know if Reiser4 will ever really live up to its promise.

I stopped using Reiser3 because it's the only system on which I've ever experienced a major data loss that I could directly blame on the filesystem.  In point of fact it was the recovery tools that did the damage, rather than any inherent problem with the filesystem.  In contrast, I've recovered an entire ext3 filesystem in which the files even remained in their proper directories.  Both the reiser issue and the ext3 issue started with the very same intermittently-flaky disk controller, so a hardware problem was the root cause.  The whole point of having recoverable filesystems, though, is that they should retain substantially all of your data even through a hardware failure.

JFS is IBM, and don't forget XFS from SGI.  Both are pretty much industrial-strength and probably overkill for PC or even small server use.  There are reports of XFS having serious issues with truncating files and zeroing files (a la ext4) when the lights go out, but I've actually pulled the plug on an XFS machine as a test and could never make it lose so much as a single byte.

For the record, I notice a difference with ext3 being somewhat slower than reiser, but I haven't bothered to really test it that much.  For my desktop use it isn't enough difference to worry over.  I'm just happy that if the cat eats the backups and the motherboard goes up in flames I at least have a small chance of bringing back some of my data from ext3, and I just can't put the same faith in Reiser.  I don't have enough experience with the others to trust or distrust them, but if I used them I'd probably have multi-level backups in place so it wouldn't matter.

If you really want a good discussion of the pros and cons of pretty much every filesystem available for the GNU/Linux world, check out the Gentoo forums.  There are plenty of people over there who have actual war stories about the positives and negatives of each fs.

---

### Post by Polygon on 2009-04-23
> **SunnyRabbiera said:**
> Not nativly, though you can get XP to see EXT drives, including ext4 due to backwards compatibility modules.

no you cant. the windows driver only sees ext2 drives, so therefore it will not be able to read ext4 drives. It also messed up ext3 drives sometimes as well.

and ext4 isnt unstable, its the programs's that RUN on the computer that are at fault, they are not properly calling fsync() to make sure that any saved data is properly saved to the filesystem, and instead just relying on the now non-existant 5 second auto sync or something that was present in ext3.

---

### Post by Darkhack on 2009-04-23
> **SunnyRabbiera said:**
> EXT2 had some issues with it but EXT3 has no frag issues as does ext4.

Ext3 is basically ext2 with journaling which would have no bearing on fragmentation.  The amount of fragmentation that occurs under both file systems is identical.

However ext4 really does improve upon it's previous two predecessors with dynamic allocation, extents, and an online defragmenter.

---

### Post by Supersquirrel on 2009-06-12
Ext4 still has static inodes and is still a pig with them too. Ext2/3/4 still suffer with directorys. It does what fat32 does and store them in a linked list. Well ext3/4 use HTrees but they dont rebalance them so over time it will get slow. 

 SO the winner here is NTFS. NTFS has had extents since it was born in 1993. Ext2 is just getting them. NTFS also has journalling which ext2 got 10 years ago. I say ext2 because ext3/4 is just ext2 with extents and a journal.

But HFS+ is a beast and blows them both away.

---

### Post by Supersquirrel on 2009-06-12
so in 10 years i guess when ext5 comes out it will have B+ trees which all modern Filesystems use like NTFS and JFS.

---

### Post by FuturePilot on 2009-06-12
> **Supersquirrel said:**
> so in 10 years i guess when ext5 comes out it will have B+ trees which all modern Filesystems use like NTFS and JFS.

Ext4 is the end of the line for the Ext file system. There will be no Ext5. Next up is Btrfs.

---

### Post by milanlin on 2009-06-20
Because of mount.ntfs-3g is eating up to 50% of my 4200+ CPU I formatted data HDD WD 500GB to ext4. **And here is my surprise :)**

WD 500GB ntfs-3g to Spinpoint 1TB ntfs-3g write speed **20 MB/sec**
Spinpoint ntfs-3g to  WD 500GB ext4 write speed up to **62MB/sec**

In the same time: WD My Book 500GB ntfs-3g to Corsair 8GB FAT 32 **2.5 MB/sec**

See the picture :D

---

### Post by Eisenwinter on 2009-06-20
> **zugu said:**
> At least NTFS is highly stable. I can't say that about ext4.
I haven't had a single crash with Ext4, and I've been using it for around 4 months now.

---

### Post by juancarlospaco on 2009-06-20
Sabayon is using EXT4 since few years works fine, EXT4 is faster than NTFS,
and dont get locked if you reboot, and takes more care about data integrity than NTFS.

---

### Post by froggyswamp on 2009-06-20
> **juancarlospaco said:**
> Sabayon is using EXT4 since few years works fine, EXT4 is faster than NTFS,
and dont get locked if you reboot, and takes more care about data integrity than NTFS.

and (EXT4) checks the file system so fast that seems to me it's just pretending to be checking. Seriously. Ext3 took like 10-20 times longer. Also when I installed Fedora 11 the other day it reported bad blocks on /dev/sda3 but Ext4 found nothing..

I'm also somewhat worried about Btrfs - Oracle started and pioneered its development but now since they buy Sun they will also have ZFS and hence might question Btrfs's relevance, since they're leading the development - without them the development would (considerably) slow down.

---

### Post by filip007 on 2010-07-10
NTFS is crap...i have noticed slack on files, EXT4 don't have that.

Files are actually bigger on NTFS and Windows have a lot of dll's with slack, now i know why some need quad cores and 16GB RAM+.

---

### Post by Xianath on 2010-07-10
Are we talking filesystems or the Linux implementations thereof? NTFS has a lot of features not implemented in Linux, and what does work consumes an unnatural amount of resources. A real benchmark would have to be Windows Server 2008 NTFS vs. Linux EXT4 on the same box. On a hunch, I'd say EXT4 would outperform NTFS by a small margin, but NTFS significantly outshines EXT4 in terms of features.

Given that EXT4 is practically unusable on Windows, and NTFS is practically unusable on Linux (works well enough to swap files around with Windows, that's about it), there's no real choice to be made. Whatever your OS is, use its native filesystem.

Oh, and JFS is dead :)

---

### Post by cariboo on 2010-07-10
@filip007

You resurrected a year old thread for that comment?

Closed.

---

