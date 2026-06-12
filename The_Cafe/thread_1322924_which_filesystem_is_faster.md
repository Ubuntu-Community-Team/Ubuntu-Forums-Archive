---
title: "which filesystem is faster?"
date: 2009-11-11
forum: The Cafe
---

### Post by pacco on 2009-11-11
just would like to know if i should go with jfs,ext4,xfs or what?, i mean which is the fastest?

---

### Post by gnomeuser on 2009-11-11
if you just want speed.. XFS is awesome, only you will lose data if you lose power. It's also hugely complex and nobody knows how to fix it properly.

I would recommend btrfs, it mounts by default with barriers which provides a good additional data safety assurance. It is featureful, performance is quite good and you have plenty of developer and vendor buy in to the model meaning fixes and testing will be done swiftly.

downsides include being still some what in early adopter state and lacking easily available boot loader support.

---

### Post by ukripper on 2009-11-11
> **pacco said:**
> just would like to know if i should go with jfs,ext4,xfs or what?, i mean which is the fastest?

Depends on what your needs are!

---

### Post by blueshiftoverwatch on 2009-11-11
> **gnomeuser said:**
> if you just want speed.. XFS is awesome, only you will lose data if you lose power. It's also hugely complex and nobody knows how to fix it properly.
I have my virtual machines on an XFS partition because it's good at handling large files and the multi-gigabyte virtial hard drives are each represented as one file.

---

### Post by kellemes on 2009-11-11
> **pacco said:**
> just would like to know if i should go with jfs,ext4,xfs or what?, i mean which is the fastest?

Depends on what you're doing.
You really should google benchmarks of filesystems..

---

### Post by jeffus_il on 2009-11-11
I haven't noticed any stunning differences in speed, as a user, which for me is more relevant than a benchmark.

What is a real pain in the rear end is lack of support for resizing and moving.
I recently got stuck with an XFS that the latest version of gparted couldn't move or resize. 

jfs and xfs have no support for moving, shrinking, growing from a livecd which is what you normally need to boot from if you want to mess with partitions.

---

### Post by blueshiftoverwatch on 2009-11-11
> **jeffus_il said:**
> I recently got stuck with an XFS that the latest version of gparted couldn't move or resize.
Can't you just delete the XFS partition and "resize" it by creating a new partition?

---

### Post by chucky chuckaluck on 2009-11-11
i found xfs to be snail-like. reiser is wicked fast for most things, but can be oddly slow in some instances.

---

### Post by pacco on 2009-11-11
Thank you all for your quick reply's
 
I was wanting awsome speed with stability to handle large files. read/write performance.

---

### Post by handy on 2009-11-11
> **gnomeuser said:**
> if you just want speed.. XFS is awesome, only you will lose data if you lose power. It's also hugely complex and nobody knows how to fix it properly.

I would recommend btrfs, it mounts by default with barriers which provides a good additional data safety assurance. It is featureful, performance is quite good and you have plenty of developer and vendor buy in to the model meaning fixes and testing will be done swiftly.

downsides include being still some what in early adopter state and lacking easily available boot loader support.

Are you using btrfs?

I just had a look at the wiki:

*v0.19 Released (June 2009) For 2.6.31-rc*

The time it has taken since that update indicates that (most likely) it has become quite reliable.

On the home front (so to speak), I use JFS, but changed some of my partitions to Ext3, because Ext3 for Mac allows me to very reliably access those partitions.  

On FreeNAS I use UFS.

---

### Post by sloggerkhan on 2009-11-11
Phoronix just did some flash drive filesystem benchmarks:
[http://www.phoronix.com/scan.php?page=article&item=linux_usb_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_usb_fs&num=1)

That said, I've had good experiences with JFS, XFS, ext3, and ext4. Have not tried BTRFs, ZFS, or Reiser. 

One thing that should be noted, is that with ALL of these filesystems, you have control over lots of parameters that can make a big impact on disk performance when you format the drive. When you go to format, look into how you can optimize these parameters for your disk's intended use.

---

### Post by 3rdalbum on 2009-11-11
I wouldn't adopt btrfs yet. I'm sure it's going to be a good filesystem, and initial benchmarks say it's fast; but I wouldn't trust my data to it yet.

Ext4 is excellent as a general-purpose filesystem.

Interestingly, it's possible to store a database just on the raw block device without a filesystem at all - so that would be an option for you if you had a big database.

---

### Post by pacco on 2009-11-12
ok, thank you all,i was using ext4 then i tried jfs,but i didn't see any option for btrfs
maybe i over looked it

---

### Post by SomeGuyDude on 2009-11-12
> **gnomeuser said:**
> if you just want speed.. 

Speed in what sense? Moving giant files or moving huge amounts of small files? XFS was great at the former, but if I opened, say, a folder with a boatload of images and it had to generate thumbs, it took forever.

---

### Post by gnomeuser on 2009-11-12
> **SomeGuyDude said:**
> Speed in what sense? Moving giant files or moving huge amounts of small files? XFS was great at the former, but if I opened, say, a folder with a boatload of images and it had to generate thumbs, it took forever.

It's my experience that people who ask questions like that (pointless questions that imply a lack of research and understanding of ones requirements that is) will accept any answer given to them with authority.. also you can expect them to have a fairly large collection of bad music and teenage comedies - hence the XFS recommendation.

---

### Post by gnomeuser on 2009-11-12
> **handy said:**
> Are you using btrfs?


Indeed, it has served me well for quite some time now, no complaints about stability nor really about performance. I do wish for bootloader support to arrive soon though.

---

### Post by pacco on 2009-11-12
sorry im not a teen,i just wanted other users opinions on the matter.
I did research it on google,everyone so far says ext4 is fastest.
 
Wow i never thought linux community would be rude enough to acttually imply something like this:
"It's my experience that people who ask questions like that (pointless questions that imply a lack of research and understanding of ones requirements that is)"

---

### Post by sloggerkhan on 2009-11-12
The linux community has lots of rude people unfortunately.

---

### Post by gnomeuser on 2009-11-12
> **pacco said:**
> sorry im not a teen,i just wanted other users opinions on the matter.
I did research it on google,everyone so far says ext4 is fastest.
 
Wow i never thought linux community would be rude enough to acttually imply something like this:
"It's my experience that people who ask questions like that (pointless questions that imply a lack of research and understanding of ones requirements that is)"


I apologize for hurting your precious feelings. Please the next time consider asking a question that isn't unanswerable.

---

### Post by blueshiftoverwatch on 2009-11-12
Which would be a better file system to keep Virtualbox's virtual hard drives on, XFS or JFS?

---

### Post by MasterNetra on 2009-11-12
> **pacco said:**
> sorry im not a teen,i just wanted other users opinions on the matter.
I did research it on google,everyone so far says ext4 is fastest.
 
Wow i never thought linux community would be rude enough to acttually imply something like this:
"It's my experience that people who ask questions like that (pointless questions that imply a lack of research and understanding of ones requirements that is)"

Nevermind him, he's just being a troll atm. I personally use and love ext4 its pretty fast, can't say how the others fair from first hand experience but I can say for me EXT4 has been fast and stable.

---

### Post by gnomeuser on 2009-11-12
> **blueshiftoverwatch said:**
> Which would be a better file system to keep Virtualbox's virtual hard drives on, XFS or JFS?

Well XFS is good for large files. However you should be concerned with dataloss. Another thing to be concerned with is how well the source is supported in the kernel, XFS and JFS are both maintained  and used by a considerably smaller set of users and developers. 

This is the strength of something like ext3/4. They are deployed by default, they are tested to death and every vendor has signed on to support it. You can count on it. Btrfs also has good vendor buy in, it is generally seen as the best next generation filesystem and as such will be the naturally next generation pick. Lots of people work on these systems, bugs get fixed, attention is paid.

For the use case you mention I think I would recommend a separate partition in XFS provided you have a UPS or this is a laptop (or if you don't care that it might lose data). If this is a production environment you should consider nothing but ext3 (in a year or so see what has come of ext4 stability wise).

Another question is that pressing soon is what is underneath the filesystem - we can still assume rotating storage but SSDs are becoming contenders though mostly I suspect as some kind of onboard cache (Intel seems keen on this approach) or a hybrid storage device. These devices and setups will have wildly different performance requirements.

---

### Post by pacco on 2009-11-12
didnt hurt my precious feelings,sorry to disapoint you.
;)

---

### Post by blueshiftoverwatch on 2009-11-12
> **gnomeuser said:**
> Btrfs also has good vendor buy in, it is generally seen as the best next generation filesystem and as such will be the naturally next generation pick.
Do you think that Btrfs is going to replace Ext3/4 as default Linux file system for most distros within so many years?
> **gnomeuser said:**
> For the use case you mention I think I would recommend a separate partition in XFS provided you have a UPS or this is a laptop (or if you don't care that it might lose data).
I don't have a UPS. But I have a 750GB external hard drive. So I can just back the virtual hard drives up on that periodically. And even if I did loose my data it wouldn't be a huge loss. Thanks for the recommendation.

---

### Post by gnomeuser on 2009-11-13
> **blueshiftoverwatch said:**
> Do you think that Btrfs is going to replace Ext3/4 as default Linux file system for most distros within so many years?


The lead developer Chris Mason states that kernel 2.6.32 (code backported to Fedora 12 so if you want to play with it try that release) will contain btrfs code he is comfortable giving to early adopters. This is a big step for something as critical as a filesystem. As for it becoming the defacto filesystem soon, vendors from Moblin (Linux Foundation / Intel / ARM), Red Hat and Novell have invested time in developing the codebase. It is very well adopted for the next generation. In fact both the upcoming Fedora and the just released openSUSE both support installing on btrfs. 

I predict that btrfs by this time next year will be the default filesystem for all distros. Moblin has already commented that they want to use it for their post 2.1 release. Also a year from now gives the community distros a lot of time to have tech previews and expand user testing, in the coming year we will likely see enterprise products from Canonical (Lucid), Red Hat (RHEL6) and probably also Novell (SLED 12). They would probably like to ship tech preview btrfs in these but it is not yet ready to be default. However the second after these releases there is likely going to be a strong interest in pushing community releases into defaulting. The code at that point will be fairly solid, the risk is low and it's the beginning of a new enterprise product cycle for everyone. By the time 2 years have gone by and when the next major enterprise products come out they will know if it's truly dependable.

Thus my guess, one year from now you will see all distributions default to btrfs in their releases.

I know that is seemingly quick for a filesystem but btrfs has a good track record so far and the functionality it brings with it is so appealing that most vendors would love to have it as soon as possible. I believe this to be a completely realistic timeframe.

> 
I don't have a UPS. But I have a 750GB external hard drive. So I can just back the virtual hard drives up on that periodically. And even if I did loose my data it wouldn't be a huge loss. Thanks for the recommendation.

If you are running from the external harddrive you shouldn't expect any specific filesystem to really give you a benefit. The cap is likely going to be USB 2.0 transfer speeds - at least that is the case for me.

---

### Post by blueshiftoverwatch on 2009-11-13
> **gnomeuser said:**
> Thus my guess, one year from now you will see all distributions default to btrfs in their releases.
If your right, by the time people start adopting Ext4 all the distros are going to be switching to Btrfs.
> **gnomeuser said:**
> If you are running from the external harddrive you shouldn't expect any specific filesystem to really give you a benefit. The cap is likely going to be USB 2.0 transfer speeds - at least that is the case for me.
I meant that I was running it from a SATA drive but that I have a 750GB external drive that I could use to backup the virtual hard drive files onto.

---

### Post by jaxxstorm on 2009-11-13
> **gnomeuser said:**
> I apologize for hurting your precious feelings. Please the next time consider asking a question that isn't unanswerable.

Congratulations.
You've crossed over from being a bit of a douche to being a massively rude douche.

---

### Post by gnomeuser on 2009-11-13
> **blueshiftoverwatch said:**
> If your right, by the time people start adopting Ext4 all the distros are going to be switching to Btrfs.


Existing products will continue to be supported this is especially true for enterprise products. I don't see a rapid deployment schedule for btrfs as being wasted time on ext4. The companies that bet heavily on enterprise customers need to give them assurances they cannot give them for btrfs now and ext3 is increasingly not an option. Ext4 is though a perfect stepping stone to btrfs, we even have programs to migrate existing ext3/4 partitions to btrfs.

You even have projects like Moblin which clearly stated that they are not going to even look at ext3 since btrfs is already in a state they are comfortable with for their next release (I assume they mean that the code is good now and any bugs can be fixed during their cycle).

I don't think a year is going to be to ambitious to be honest. The demand is there, the code is looking good and every major vendor is investing in btrfs now and have done for a while.

> 
I meant that I was running it from a SATA drive but that I have a 750GB external drive that I could use to backup the virtual hard drive files onto.

Ah.. in that case I would back up to ext4 with barriers enabled on the external drive, keep the images on a separate XFS partition. I think you will find that to be an acceptable solution.

---

### Post by blueshiftoverwatch on 2009-11-13
> **gnomeuser said:**
> Ah.. in that case I would back up to ext4 with barriers enabled on the external drive, keep the images on a separate XFS partition. I think you will find that to be an acceptable solution.
Is there any reason why backing up the virtual hard drive files to a FAT32 partition on my external HD wouldn't be acceptable?

---

### Post by gnomeuser on 2009-11-13
> **blueshiftoverwatch said:**
> Is there any reason why backing up the virtual hard drive files to a FAT32 partition on my external HD wouldn't be acceptable?

Not really.. I was just picking one stable option for the backup, FAT32 will likely be a good option as well - I don't really have much experience with it from a stability pov.

---

### Post by jeffus_il on 2009-11-20
> **blueshiftoverwatch said:**
> Is there any reason why backing up the virtual hard drive files to a FAT32 partition on my external HD wouldn't be acceptable?

FAT won't store Linux ownership and permissions, unless you back up into a tar file

---

