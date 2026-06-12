---
title: "SSD with Linux, encrypted"
date: 2010-05-11
forum: Security
---

### Post by buntville on 2010-05-11
I run Linux.  I have a new SSD (80GB Postville).  I want to put an encrypted partition on it.  Questions:  - Is there any encryption software available other than dm-crypt?  It does not seem to use more than 1 CPU core at a time. Truecrypt would use all, but does not boot Linux.  - Does it work for SSDs like for hard disks?  I mean dm-crypt -> LVM -> ext3.  - how much space should I leave unpartitioned? 10%? 20%?  Because trimming does not work when encrypted (Intel's trim tool would not work with Linux anyway.)

---

### Post by HermanAB on 2010-05-11
Howdy,

dmcrypt (LUKS) is pretty much the Linux standard.

The amount of CPU used by LUKS during normal operation is negligible.

You can encrypt the whole disk if you want.

---

### Post by buntville on 2010-05-18
> **HermanAB said:**
> Howdy,

dmcrypt (LUKS) is pretty much the Linux standard.

The amount of CPU used by LUKS during normal operation is negligible.

You can encrypt the whole disk if you want.

But [ here]("http://blog.wpkg.org/2009/04/23/cipher-benchmark-for-dm-crypt-luks/") someone posts benchmarks for LUKS, and they are all much slower than his hard disk.  So on a SSD the CPU will be the bottleneck.  If the benchmarks in that article are correct, the CPU reqirement will be at least 400% of what's available. :-(

---

### Post by cariboo on 2010-05-18
This is really anecdotal, but I really don't really see any difference in the speed for example when Thunderbird opens with either an encrypted home or without, I have about 2Gb of email stored in ~/.thunderbird mirrored between the two systems.

---

### Post by buntville on 2010-05-20
> **cariboo907 said:**
> This is really anecdotal, but I really don't really see any difference in the speed for example when Thunderbird opens with either an encrypted home or without, I have about 2Gb of email stored in ~/.thunderbird mirrored between the two systems.

Thanks.  Good to know.  But do you have a SSD?

---

### Post by cariboo on 2010-05-20
No I don't have an ssd yet, but a slow down if any would be more noticeable with a mechanical drive.

---

### Post by HermanAB on 2010-05-21
The overhead due to encryption is about 3%.  I got to that number a few years ago, by timing kernel compiles on a pair of identical servers.  

So, go ahead, do your encryption and don't worry about the CPU usage.  You won't notice it.

---

### Post by buntville on 2010-05-21
> **cariboo907 said:**
> No I don't have an ssd yet, but a slow down if any would be more noticeable with a mechanical drive.

Sorry to correct you, but I think it's the opposite.  A SSD is faster than a mechanical drive, so it is less of a bottleneck.  Which means that other things, in particular CPU, become *more* of a bottleneck.  It will of course still be faster than a mechanical drive, but if it's not noticeably faster, than the (expensive) SSD wasn't worth paying so much for.

---

### Post by buntville on 2010-05-21
> **HermanAB said:**
> The overhead due to encryption is about 3%.  I got to that number a few years ago, by timing kernel compiles on a pair of identical servers.  

So, go ahead, do your encryption and don't worry about the CPU usage.  You won't notice it.

Good to know.  What exactly are you using (AES? CBC? essiv?)?  I tried some combinations (default, as well as XTS) and the speed went down from 250MB/s unencrypted to about 100MB/s encrypted or worse.  CPU usage is about 25% on a quad core, which  I guess means one CPU fully used and not catching up.

---

### Post by cariboo on 2010-05-21
If you see constant 25% cpu usage, you've got something else going on there.

---

### Post by HermanAB on 2010-05-22
The default LUKS encryption is AES256, ESSIV, SHA256.

As everybody so far has said - don't worry about the CPU load.  It is negligible.  People won't use it on servers and laptops if it wasn't.

Your problem is likely with how you measure the load.  The CPU load of anything is 100% if the measurement time period is short enough.

---

### Post by buntville on 2010-06-05
> **HermanAB said:**
> The default LUKS encryption is AES256, ESSIV, SHA256.  As everybody so far has said - don't worry about the CPU load.  It is negligible.  People won't use it on servers and laptops if it wasn't. A laptop is not comparable.  It has a hard disk, which is much slower than a SSD, and laptop hard disks may be even slower than desktop hard disks.  If the disk is slow, it is easier for the CPU to keep up with the data transfer.  The faster the disk, the faster the data comes, and the higher the CPU requirements are.  E.g. if the disk is now 3 times as fast, then the CPU needs to be 3 times as fast also to achieve the goal with the same %load.  In the past, I would also have told everyone not to worry about CPU load with disk encryption, but in my own recent measurements with a SSD it always came out high, and the transfer from/to SSD was much lower (several times) than without encryption.  I wonder why.  In the past, I used it with hard disks, and the CPU was fast enough for that.  >  Your problem is likely with how you measure the load.  True.  But I used several methods: top, htop, and the CPU load measurement in dd_rescue.  All show high loads.  Even if all of them are wrong, the problem that remains is that the total I/O is several times slower than without encryption.  This is of course the problem I want to solve, otherwise a high CPU load wouldn't bother me.

---

### Post by rookcifer on 2010-06-06
I don't have an SSD yet either, but you would probably be better off if you buy a Core i7 Intel, as they have built-in AES hardware acceleration (I don't think any AMD chip does at this current time).

---

### Post by Paradoxfox93 on 2011-07-19
How did you set up buntville?  Because I do not share your experience.  Did you properly apply all tweaks to the SSD?

Mine is under dm-crypt with LVM with no noticeable preformance hits. (Laptop in sig)

Also, did you partition off reserve space for the wear leveling controller?  %20 is what' I've read to be the mimnimum so 8 GB for me and 16 for you.  Which matches what intel preprovisions.  Yours was probably 64.  As most 64's are 80.  Intel advertizes the full amount whereas other vendors tend to advertize the available amount because intel controllers do not prevent access.

You can reserve less if you write less because write will suffer more than read in a full disk.  If you run encryption. The drive is kind of full in a way.  DOn't create a partition, just leave empty space when partitioning.

I got the same benches I get now you see but actual performance was horrible.  If you run encryption you have ot reserve something to use wear leveling.

Note: The reserved space does not have to be a contiguous it's irrelavant to the end location of the actual data.  Technically, because no matter what software and data allocation scheme you come up with, intel's controller will be handling the *actual* assignment location which is why the only real performance killer spoken of is alignment.  Most SSD manufacturers force reservation which is why this issue isn't commonly spoke of. Arbitrarily limiting yourself to use less will further extend the life of your now rediculously long lasting (beyond some HDDs) flash drives.  Intel got it right.  You know what to do. (NO?  Should I write a tutorial?>  I"m taking screenshots).  SO fragmentation is high but it just doesn't really matter.

---

### Post by DZ* on 2011-07-19
> **buntville said:**
> Is there any encryption software available other than dm-crypt?  It does not seem to use more than 1 CPU core at a time.

Linux 2 6 38 [dm-crypt: scale to multiple cpus]("http://kernelnewbies.org/Linux_2_6_38#head-49f5f735853f8cc7c4d89e5c266fe07316b49f4c")

---

### Post by Paradoxfox93 on 2011-07-19
oh thank you thank you thank!!!

---

