---
title: "No Love for ReiserFS?"
date: 2007-08-20
forum: The Cafe
---

### Post by regomodo on 2007-08-20
`

---

### Post by Steveway on 2007-08-20
The future for the Reiser Filesystem is unclear.
Since Hans Reiser got arrested development has slowed down.

---

### Post by kebes on 2007-08-20
In case you don't already know, the main person in charge of ReiserFS (and Namesys), Hans Reiser, is currently embroiled in legal issues. (Defending himself against murder charges.) Because of this (and because Hans Reiser announced that he was going to sell Namesys to help pay for legal fees), the future of ReiserFS is unknown.

That having been said, the current implementations of ReiserFS are certainly usable (and very good quality). However I'm not aware of any Windows driver that allows access to ReiserFS partitions.

---

### Post by regomodo on 2007-08-20
`

---

### Post by AlbinoButt on 2007-08-20
I had love for ReiserFS until the power went out and I lost all my data :mad:

---

### Post by init1 on 2007-08-20
The reason why there are no windows drivers is because so few people use it. I have used it, but didn't see any reason to switch from ext3. Ext* does waste a lot of space though.

---

### Post by toupeiro on 2007-08-20
RiserFS's speed is shadowed by its ability to crash for the slightest unexpected process..

If you want an alternative to EXT# then go zfs!

---

### Post by WishingWell on 2007-08-20
There are so many other alternatives that ReiserFS isn't really an option, if you need a faster file system (you won't notice any speed changes unless you're on Tera bytes of LVM volumes though) then go with XFS or JFS, both work great but neither was made for the I386 architecture and i wouldn't recommend them unless you have an UPS and two power supplies, an unexpected power out may (read WILL) cause data loss.

Besides EXT2/3 are the only file systems i know of that can be both shrunk and grown.

If you don't have a very special reason to go with anything else then just go for EXT3, wait for EXT4 to come around and then use that.

AFAIK ZFS can only live on FUSE for Linux as of now which means it won't be a system that is easy to use nor will it be a system i would count as particularly reliable. It also has a different license than the rest of the kernel (CDDL vs GPL), apparently this isn't going to be an issue once it's ported, to the best of my knowledge.

---

### Post by blastus on 2007-08-20
[quote=AlbinoButt]I had love for ReiserFS until the power went out and I lost all my data[/quote]

If you lost ALL of your data I'd say it is a hardware failure. ReiserFS is journaled like ext3, so it is extremely unlikely the entire file system would become corrupt after an unexpected shutdown. I've never heard of a journaled file system becoming entirely unusable but the drive still functional.

---

### Post by jrusso2 on 2007-08-20
> **blastus said:**
> If you lost ALL of your data I'd say it is a hardware failure. ReiserFS is journaled like ext3, so it is extremely unlikely the entire file system would become corrupt after an unexpected shutdown. I've never heard of a journaled file system becoming entirely unusable but the drive still functional.
'
Not necessarily there can be events where the journal is not flushed before the file system is written to which can lead to corruption of the file system.

[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)


Some directory operations (including unlink(2)) are not synchronous on ReiserFS, which can result in data corruption with applications relying heavily on file-based locks (such as mail transfer agents qmail[5] and Postfix[6]) if the machine halts before it has synchronized the disk.[7]

---

### Post by toupeiro on 2007-08-20
> **WishingWell said:**
> AFAIK ZFS can only live on FUSE for Linux as of now which means it won't be a system that is easy to use nor will it be a system i would count as particularly reliable. 

I guess I misunderstood the context.  If we were talking about servers or some sort of production environment, then no I wouldn't recommend ZFS on linux from a best practice standpoint because as cool as fuse is, its not really mature enough imho to rely on.  However, it sounded like he was doing this on his home system.  That being said, I've not had a stitch of a problem using zfs/fuse except the obvious fact that its slower than native OpenSolaris/ZFS.  

Eventually, ZFS will be natively supported in Linux, and linux users will be able to take advantages of its robustness, but you're right in that XFS and JFS may be better alternatives right now.

---

### Post by WishingWell on 2007-08-20
> **blastus said:**
> If you lost ALL of your data I'd say it is a hardware failure. ReiserFS is journaled like ext3, so it is extremely unlikely the entire file system would become corrupt after an unexpected shutdown. I've never heard of a journaled file system becoming entirely unusable but the drive still functional.

Actually, XFS and JFS are also journaled file systems but they both share this problem with ReiserFS, an unexpected power out can cause file system corruption to the degree where it is unrecoverable.

This is not the case with EXT3 though, actually it's not the case with EXT2 either and that isn't a journaled file system, i don't think you know what the journal actually does and how it works?

---

### Post by WishingWell on 2007-08-20
> **toupeiro said:**
> I guess I misunderstood the context.  If we were talking about servers or some sort of production environment, then no I wouldn't recommend ZFS on linux from a best practice standpoint because as cool as fuse is, its not really mature enough imho to rely on.  However, it sounded like he was doing this on his home system.  That being said, I've not had a stitch of a problem using zfs/fuse except the obvious fact that its slower than native OpenSolaris/ZFS.  

Eventually, ZFS will be natively supported in Linux, and linux users will be able to take advantages of its robustness, but you're right in that XFS and JFS may be better alternatives right now.

I don't think that ZFS is more robust than XFS and JFS and it's features aren't really going to be used on desktops as you said.

It's nice for really big arrays where you will need on the fly maintnance to be performed but other than that, it's not faster than XFS nor is it more stable.

On servers though, yeah i can see the use there but i'd rather go with FreeBSD which already has it or why not Solaris or any of the OpenSolaris clones that support it like OpenSolaris Express, Nexenta or something like that?

I'm a lot more excited about EXT4 than ZFS on Linux, since it's not a project from the general Linux community (and never will be) it will always be a third party hack while EXT4 is the natural progression of EXT3.

---

### Post by Dragonbite on 2007-08-21
I just did an install using ReiserFS and now I'm wondering how I would go about changing it to something like EXT3 instead?  

Copy/Clone the partition, 
reformat, 
Extract copy onto partition (assuming no change in size)

:confused:

---

### Post by kelvin spratt on 2007-08-21
i use  Reisers3 all the time never had a problem with it and lets face it if the power suddenly went no file system can carry on writing with no power can they. Ubuntu Elive and One guest Distro running with Xp 
with Ntfs3g never lost any data in 9 months

---

### Post by tszanon on 2007-08-21
I use Reiser only in /boot. Would it be a problem?

---

### Post by regomodo on 2007-08-21
`

---

### Post by Anthem on 2007-08-21
I've had great success with Reiser3 in the past.  And by "great success" I mean "Reiser saved my data even though the drive suffered all kinds of disgusting physical damage."

On Ubuntu, though, I use ext just because that's the default.

---

### Post by mips on 2007-08-21
I'm very much looking forward to ZFS. Might not see it in Linux but definately in BSD.

I tried reiserfs once but for some odd reason I still prefer XFS in Linux.

---

