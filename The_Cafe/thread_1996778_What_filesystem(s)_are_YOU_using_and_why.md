---
title: "What filesystem(s) are YOU using and why?"
date: 2012-06-04
forum: The Cafe
---

### Post by AnotherMuggle on 2012-06-04
I couldn't find a similar thread so thought I would start one.

What filesystem(s) are you using on your machines and why?

**Filesystem:** ext4 
**Reason:** It was the filesystem I encountered when I first started using Linux, I got comfortable with it and stuck with it :D

TK

---

### Post by Bachstelze on 2012-06-04
Since I don't have any special needs, I always stick with the default of the OS, so for Ubuntu this means ext4 right now. I have experimented with various filesystems over the years (reiser, XFS, JFS...) and have never found a significant difference (once again, I have no special needs).

---

### Post by Bandit on 2012-06-04
I have used every file system under the sun. Currently I am running Ext4 because it performs good and is reliable.

---

### Post by MisterGaribaldi on 2012-06-04
ext3 on my server. HFS+ Journaled on my laptop.

---

### Post by pissedoffdude on 2012-06-04
I'm using ext4 because it's the default on most distros and I haven't had any problems with it.  I have also used ext2 and ext3 in the past without any issues.  I gave reiserfs a go once, and it would get corrupted when I'd have to power down manually when something would go wrong (mostly my fault though)

---

### Post by drawkcab on 2012-06-04
Ext4 on most stuff.  Sometimes I go ext3 on dual boot systems so windows can access those partitions.  Ext2 on netbook's ssd.

---

### Post by MisterGaribaldi on 2012-06-05
I really used to love reiserFS until the dude got arrested for murdering his wife. It was FAAAAAAST!!!

---

### Post by zombifier25 on 2012-06-05
> **MisterGaribaldi said:**
> I really used to love reiserFS until the dude got arrested for murdering his wife. It was FAAAAAAST!!!

They don't have computers in prison? :lolflag:


ext4, since I don't really see a reason to switch to other filesystems

---

### Post by MisterGaribaldi on 2012-06-05
> **zombifier25 said:**
> They don't have computers in prison? :lolflag:

Not sure if they do in Germany.

---

### Post by ads2996 on 2012-06-15
ext4 as is has permissions which work well with ubunutu

ntfs for my data, as it can also be read by windows as well as ubunutu

---

### Post by ExSuSEusr on 2012-06-15
EXT4 here - no reason to use anything else at the moment....

---

### Post by linuxyogi on 2012-06-15
EXT4 coz its the default. In the past I have tried the other filesystems.

---

### Post by Mikeb85 on 2012-06-16
Btrfs because I was curious to see if there would be any noticeable differences.  So far so good, everything is fast and stable.

---

### Post by Shadius on 2012-06-16
The default Ubuntu Linux filesystem, ext4, because I don't know any better. I'm fairly new to Ubuntu Linux and its filesystems. I don't really know the differences between them so I stuck with the default.

---

### Post by Artemis3 on 2012-06-16
Ext4. Waiting for btrfs to have a proper fsck and be mature enough.

---

### Post by szymon_g on 2012-06-16
ext4 + lvm
provides me everything i want.

---

### Post by sujoy on 2012-06-16
ext3 since that seemed fine back in 2008 when i setup the filesystems.

---

### Post by odiseo77 on 2012-06-16
ext4 for my Debian install and NTFS for my data partition (needs to be accesible from windows too). I once used JFS to test and it got messed up pretty bad, so I switched back to ext4, which I've found to be reliable and fast.

---

### Post by Primefalcon on 2012-06-16
ext4 since it's the latest and greatest ext filesystem

looking forward to btrfs though, though I'll probally stick to ext4 until I have to do a complete reinstall from scratch.... All my data across all my drives are stored via encfs as well so transferring all of it might be a pain

---

### Post by HansKisaragi on 2012-06-16
**Filesystem:** ext4 
**Reason:** I like it :)

---

### Post by MadmanRB on 2012-06-16
EXT4, but EXT3 is pretty good too though and is still good on systems that use it

---

### Post by AlanR8 on 2012-06-16
Ext 4 but I really don't understand why you wouldn't just accept the defaults......

---

### Post by meathdeath on 2012-06-16
Personally im using the default file system because when i tried to install on the other ones it failed miserably and i was too lazy to bother with it:) ubuntu works fine on default.

---

### Post by Primefalcon on 2012-06-16
> **AlanR8 said:**
> Ext 4 but I really don't understand why you wouldn't just accept the defaults......
well btrfs one is has proper fsck ability will have some very very cool features such as built in rollback Among a whole bunch of other very very cool features

---

### Post by Shadius on 2012-06-16
I had no idea there were so many different filesystems! Where can one go, besides, Google, to learn the differences between each?

---

### Post by insane_alien on 2012-06-16
ext2 for /boot because, well, i've always done used it for /boot since i understood partitioning
ext4 for / and /home i don't need anything fancy.
ZFS on my NAS because its kinda cool

---

