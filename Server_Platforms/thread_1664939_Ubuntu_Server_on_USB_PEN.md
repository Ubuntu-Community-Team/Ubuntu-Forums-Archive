---
title: "Ubuntu Server on USB PEN"
date: 2011-01-11
forum: Server Platforms
---

### Post by syncmasterpt on 2011-01-11
I'm thinking on build my own home server, probably based on the very low consumption Intel board D945GSEJT, and run the OS from flash.

This boards supports it's own ZIF solid disk, but 2GB is quite expensive.

So I'm thinking in running the Ubuntu Server from an USB flash pen. I know it will be slow, but any better ideas?

---

### Post by arrrghhh on 2011-01-11
Well slow is only one problem.  You'll probably also kill the flash disk, as most flash memory uses cheap chips, which don't have any write-levelling protection.

What I've seen some guys do is setup an array of flash disks, the theory being that no one will get hammered I think.  Never done it myself tho.

---

### Post by C.S.Cameron on 2011-01-11
> **arrrghhh said:**
> Well slow is only one problem.  You'll probably also kill the flash disk, as most flash memory uses cheap chips, which don't have any write-levelling protection.

What I've seen some guys do is setup an array of flash disks, the theory being that no one will get hammered I think.  Never done it myself tho.

After a lot of searching I have only heard of one person bricking a pendrive running Ubuntu from it:

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

### Post by arrrghhh on 2011-01-11
There's only a limited number of writes per region.  Feel free to do it, I'm just warning him of the potential consequences.

---

### Post by C.S.Cameron on 2011-01-11
> **arrrghhh said:**
> There's only a limited number of writes per region.  Feel free to do it, I'm just warning him of the potential consequences.

A flash drive is good for a minimum of 10000 writes, (Unlimited reads).
At 3MB/s it takes 16GB/4MB/s = 4000s = 67m = 1hr to do one complete write to the drive, Thus it takes 465 days full time to do 10000 writes.
That is about five years of 40 hour work weeks.
What me worry.

Edit:
I've never had a mechanical hard drive last me that long.

---

### Post by arrrghhh on 2011-01-11
> **C.S.Cameron said:**
> A flash drive is good for a minimum of 10000 writes, (Unlimited reads).
At 3MB/s it takes 16GB/4MB/s = 4000s = 67m = 1hr to do one complete write to the drive, Thus it takes 465 days full time to do 10000 writes.
That is about five years of 40 hour work weeks.
What me worry.

Edit:
I've never had a mechanical hard drive last me that long.

So you've never had a mechanical hdd last longer than 5 years...?  All my hdd's are warrantied to 5 years.

Plus, what if the server is running 24/7?  What if it is doing more intensive writes?

Either way, it'll work - just be prepared to blow up that disk.

For the record, I have hard disks that are 10+ years old that still work just fine.

---

### Post by syncmasterpt on 2011-01-12
I do believe that on write intensive tasks it will probably shorten the lifespan of the drive very quickly. But for only booting the operating system and having minimal writes, I think it will have minimal impact.

Another blog entry [http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One](http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One) refers that probably the PEN/SDHC aproach makes sense for low usage 24/7 home servers...

---

### Post by arrrghhh on 2011-01-12
> **syncmasterpt said:**
> I do believe that on write intensive tasks it will probably shorten the lifespan of the drive very quickly. But for only booting the operating system and having minimal writes, I think it will have minimal impact.

Probably true - go for it if you wish, assuming you know the risk ;)

---

### Post by C.S.Cameron on 2011-01-12
arrrghhh
Please provide some backup for you claim that running Ubuntu from a flash drive will actually brick it in an amount of time to be concerned with.
Just 2 or 3 examples from the internet.

---

### Post by arrrghhh on 2011-01-12
> **C.S.Cameron said:**
> arrrghhh
Please provide some backup for you claim that running Ubuntu from a flash drive will actually brick it in an amount of time to be concerned with.
Just 2 or 3 examples from the internet.

I don't need to post any more articles, the one you posted was just fine - [http://www.bress.net/blog/archives/1...rive-Last.html](http://www.bress.net/blog/archives/1...rive-Last.html).

The point is, you have a limited number of writes.  Obviously mechanical hard disks fail; sometimes quite badly without warning - but my point being is you can damage a flash disk from repeated writes to the same section of the flash.

It probably won't happen for some time, I just want the OP to be aware - I would want the same if I asked this question.  I'd want to know all the risks, I wouldn't want someone just saying "oh yea, it'll work fine" - without any caveats or warnings when there is potential for damage?  No thanks.

Either way, I think this thread is 'done'.  The OP has his answer, and can proceed accordingly - there's nothing wrong with running an OS from a flash key, just be prepared one day to not be able to write to the disk any longer!

---

### Post by arrrghhh on 2011-01-12
Repeat post... Sorry guys.

---

### Post by arrrghhh on 2011-01-12
Sorry... last multipost.  Forums were having some issues evidently!

---

### Post by C.S.Cameron on 2011-01-12
From the article I posted:
"It took 90593104 writes for the drive to die. That's 90.5 million"

I think better to warn people that their mechanical hard drives will eventually die.

---

### Post by arrrghhh on 2011-01-12
> **C.S.Cameron said:**
> From the article I posted:
"It took 90593104 writes for the drive to die. That's 90.5 million"

I think better to warn people that their mechanical hard drives will eventually die.

I'm pretty sure people know that mechanical hard drives will eventually die... However, with flash memory there's no moving parts and there isn't any good indicators of a failing flash drive (AFAIK).

However, failing hard disks usually give several warnings that it's going to die, and you can typically recover your data.  I guess that point is moot, as the issue we're discussing with flash memory is purely write-based, and you should be able to re-read that data.

With that said, the article you posted also had a drive with write-leveling.  Not all drives have this, as I understand it most don't.  So I'd be curious to see that same test, with a drive that doesn't write-level.  Either way, I'm just answering the OP's question how I would want it answered if I asked the same question.

---

### Post by C.S.Cameron on 2011-01-12
> **arrrghhh said:**
> I'm pretty sure people know that mechanical hard drives will eventually die... However, with flash memory there's no moving parts and there isn't any good indicators of a failing flash drive (AFAIK).

With that said, the article you posted also had a drive with write-leveling.  Not all drives have this, as I understand it most don't.  So I'd be curious to see that same test, with a drive that doesn't write-level.  Either way, I'm just answering the OP's question how I would want it answered if I asked the same question.

Can you specifically name a flash drive manufacturer that does not use wear leveling?
Kingstone does.
Lexar does.
San Disk does.
Corsair does.

---

### Post by arrrghhh on 2011-01-12
> **C.S.Cameron said:**
> Can you specifically name a flash drive manufacturer that does not use wear leveling?
Kingstone does.
Lexar does.
San Disk does.
Corsair does.

Maybe it's changed, but a couple of years ago I *thought* I read something that said only high end SSD's have a wear-leveling schema.

If that's not the case, I apologize.  It was a while ago that I read that, so perhaps things have changed... as they often do.

---

### Post by syncmasterpt on 2011-01-14
Hi guys!

Thanks for your input. The Pen will be used to boot the OS, and no massive writes are expected. Probably I should had tell that the main data would be on an external hard-disk.

---

### Post by roddersg on 2011-02-22
I'm also in the same boat.
I want to install Ubuntu Server on a flash-drive, however, I would like to put /tmp on ram or /tmpfs, since that would be the most used directory.  The flash drive would be used to boot the server, run raid5.  I would expect a fair amount of updates to be done in the process, but this should be in /tmp, any ideas on how to proceed?

Thanks

Rodders

---

### Post by mciverza on 2011-02-22
> **roddersg said:**
> I'm also in the same boat.
I want to install Ubuntu Server on a flash-drive, however, I would like to put /tmp on ram or /tmpfs, since that would be the most used directory.  The flash drive would be used to boot the server, run raid5.  I would expect a fair amount of updates to be done in the process, but this should be in /tmp, any ideas on how to proceed?

Thanks

Rodders

The short answer to your question is to simply insert the flash drive, put the ubuntu CD in the drive and run the install program as usual. Create the partitions on the flash drive that you need, and point your relevant mountpoints to the flash drive and others to the RAID disks as required.  Set your mountpoint options to include "noatime" to reduce the number of writes.

Make sure that grub is installed to the flash drive and you are done.

regarding putting /tmp in tmpfs
after checking that the system boots properly, 
editing /etc/fstab and putting this line in should make /tmp only exist in RAM.
tmpfs  /tmp tmpfs rw,noatime,mode=4777

... be careful of putting package updates in RAM, as you're likely to create more headaches than that is worth. If you don't want them to be saved to flash, create a mountpoint on your RAID array to use for /var/cache/apt. Remember, package management is like a database. If the database of installed files and available packages is no longer available, you will be unable to do ANY installations.

---

