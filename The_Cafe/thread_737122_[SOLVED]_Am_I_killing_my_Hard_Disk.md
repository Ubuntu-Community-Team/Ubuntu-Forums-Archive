---
title: "[SOLVED] Am I killing my Hard Disk ?"
date: 2008-03-27
forum: The Cafe
---

### Post by Google Spider on 2008-03-27
Hi:)

Will I ultimately kill my hard disk if I kept formatting my disk again and again ( to try different distros)? Is this true? I remember formatting the disk 5 times in December to get the right partitioning.:-|(Trying to set up a dual boot for the first time)

How many times can we format a disk before it dies and should I stop doing this? How often do you format ?

I was going to install open suse on another partition but now I'm scared :(

---

### Post by Kimm on 2008-03-27
I had an old 60 Gb in my old computer that started making strange noise after I had reformated it several times (I cant know for sure how many times... I lost count).

I quickly replaced it though, so it didn't have time to break down. So, this is not a definitive answer, but I think repeated formating can damage the drive.

---

### Post by eddietop on 2008-03-27
Formatting a hard drive is just writing bits of information to the disk with the file structure information, your at no more risk then if you were using your hard disk store any other kind of information.

---

### Post by aaaantoine on 2008-03-27
I heard at one point that the partition table could break or become corrupt if changed too often, though I'm sure at this point you'd have to change your partitions hundreds of times for that to happen.

---

### Post by karellen on 2008-03-27
37289675 times (joking :D)

---

### Post by solitaire on 2008-03-27
Technically your probably doing more good than bad with all the reformatting.

Every disk get's bad sectors over time. When you reformat it the software usually checks for bad sectors and skips them ( so no data errors due to bad sectors!).

So the older the Disk the more life you'll give it if you do a full reformat every now and again...

---

### Post by mips on 2008-03-27
Amazing the amount of FUD out there.

Formatting a drive or partition actually involves less writing to the disk than normal everyday usage does. Formatting is nothing but writing to a disk so I honestly can't see how the hell it is bad for the hd.

---

### Post by jrharvey on 2008-03-27
There are limits to the amount of time that a hard disk can ultimately be reformated. My older 80G hard drive eventually became unusable because i reformatted windows sooooo many times (around 30+) because of studpid viruses. It was also my first time using linux and i must have reformated that about 10 times. Eventually my computer lost the ability to even write to the hard disk.

---

### Post by jrharvey on 2008-03-27
its possible it just got old but i believe its because i overwrote it sooo much

---

### Post by Wobedraggled on 2008-03-27
Anytime you write to the disk, you are stressing it, and all drives willl die eventually but formatting does no more than the usual writing to disk, and like it was said before, bad areas will be avoided.

If it's got moving parts, it'll break eventually, just a general rule of life :)

---

### Post by init1 on 2008-03-27
I wouldn't worry about it too much. Hard drives do die after a while, but I don't think that reformating it is going to do much harm. It's no different than heavy computer use, because it's just writing to the disk.

---

### Post by erginemr on 2008-03-27
> **karellen said:**
> 37289675 times (joking :D)
:lolflag:

---

### Post by FuturePilot on 2008-03-27
> **jrharvey said:**
> There are limits to the amount of time that a hard disk can ultimately be reformated. My older 80G hard drive eventually became unusable because i reformatted windows sooooo many times (around 30+) because of studpid viruses. It was also my first time using linux and i must have reformated that about 10 times. Eventually my computer lost the ability to even write to the hard disk.

There's no way that could have been due to formatting. I have an old hard drive that had Windows on it and has been reformatted many times. I now use that drive for distro testing. It's been formatted at least 50 times (it's probably way more counting all the distros I've tried more than once and the ones I've messed up and reinstalled). It still works fine.

---

### Post by Ripfox on 2008-03-27
In short, no. I have reformatted so many drives SO many times and never has it caused one problem.

---

### Post by L473ncy on 2008-03-27
I know people who basically reformat every 2-3 weeks they haven't ended up killing any of their HDD's (well except for one but I think that was a freak occurrence)

---

### Post by bigbrovar on 2008-03-27
I read somewhere that formatting doesnt hurt ur HD.. and am a living testimony to that ... i have formated my sony vaio countless of times and even when i got my first lappy (and i have had 3 after that) .. a compaq  i remembered formating it more than 20 times before i sold it .. the guy i sold it too also did his own fair share of formatiing now he has sold the system.. and the cycle continues .. the idea that too much formating my kill an harddrive is nothing but a myth ..

---

### Post by Twitch6000 on 2008-03-27
Well I might be just that one but,I reformatted my harddrive after having major issues with opensuse and windows and after I did I didn't see my full 120gb again :(.I only seen 116 or 114gb.)I still see the full 120gb in ubuntu but windows and my gparted say 116 or 114gb.

---

### Post by whitefang5412 on 2008-03-27
No way it could hurt it. Ever since I found linux I haven't been able to figure out what distro I want to keep on my pc. But I'm always going back to ubuntu, but I think I've reformated mine at least 40 something times. It runs windows now again, but that will change here in a few days. Probably will run xubuntu 8.04 :)

---

### Post by picopir8 on 2008-03-27
Formatting alone causes no more stress than normal writes.

When you do a quick format, it juts clears the file allocation table.  When you do a full format, it erases (ie writes zeros) every area on the drive.  So all you are doing is writing data.

Each particular location on a hard drive is rated for a limited number of writes, but there are a lot of other operations that are much more demanding and have a greater chance of trashing hard drives.  These include:
1) Defrag programs
2) Swapfiles
3) Harddrive testers that write data to look for bad sectors
4) programs that log large amounts of data such as windows restore feature.
5) Security software that overwrites data with other data (sometimes performed by a format).

However, these are all relatively common applications that are used on a regular basis.  If they are safe for most people, then there is no reason why formatting should be considered dangerous.

---

### Post by O3. on 2008-03-27
> **mips said:**
> Amazing the amount of FUD out there.

Formatting a drive or partition actually involves less writing to the disk than normal everyday usage does. Formatting is nothing but writing to a disk so I honestly can't see how the hell it is bad for the hd.

Thanks for the information, till now I formatted my  WD 80 GB harddisk around 70-80 times within 2 years, still going strong :)

---

### Post by mips on 2008-03-27
> **jrharvey said:**
> There are limits to the amount of time that a hard disk can ultimately be reformated. My older 80G hard drive eventually became unusable because i reformatted windows sooooo many times (around 30+) because of studpid viruses. It was also my first time using linux and i must have reformated that about 10 times. Eventually my computer lost the ability to even write to the hard disk.

Absolute BS is all I can say!

If your drive died then it was because it was failing regardless of whatever you did.

---

### Post by blastus on 2008-03-27
If you are concerned about imminent hard drive failure, then get [SpinRite](http://www.grc.com/sr/spinrite.htm).

---

### Post by iSplicer on 2008-03-27
In a way, it does, in a way, it doesnt;

Formatting writes data to the disc, and puts regular stress onto the hard drive (which eventually will kill it after you format 159191457 times)

However, formatting is just using your hard drive in a normal way, so it shouldnt cause any crazy damage whatsoever

---

### Post by Daveski on 2008-03-27
> **Wobedraggled said:**
> If it's got moving parts, it'll break eventually, just a general rule of life :)

Modern solid-state Flash memory only has a limited number of read/write cycles before it too will fail, so it's not just moving parts. Anyway, as mentioned by others, a format is NOT going to reduce the life of your drive more than any other type of use. Although it is worth remembering that it will workout the mechanics as the head will have to move over the whole drive so if the drive has gone bad, then a format might be the final job which makes it fail.

Anyone remember those drive testing diags which did things like butterfly seeks which cained the head moving mechanics and made the drive sound like it was about to explode?. Any good drive will take all this in its stride.

---

### Post by xArv3nx on 2008-03-27
I always used to think this, until I started formatting my disc 5-6 times every day (OCD, anyone?).

---

### Post by mips on 2008-03-28
When one does a normal quick format the contents of the drive does not actually get erased. For a lack of better terminology all that happens is that the indexes pointing to the data gets 'cleared' so only a bit of writing actually occurs.

I need to find a wiki or online article to explain this better than I can.

Edit:
[http://en.wikipedia.org/wiki/Disk_formatting](http://en.wikipedia.org/wiki/Disk_formatting)
> Recovery of data from a formatted disk
As with regular deletion, data on a disk is not fully destroyed during a high-level format. Instead, the area on the disk containing the data is merely marked as available (in whatever file system structure the format uses), and retains the old data until it's overwritten. If the reformatting is done with a different file system than previously existed in the partition, some data may be overwritten that wouldn't be if the same file system had been used. However, under some file systems (e.g., NTFS; but not FAT), the file indexes (such as $MFTs under NTFS, "inodes" under ext2/3, etc.) may not be written to the same exact locations. And if the partition size is increased, even FAT file systems will overwrite more data at the beginning of that new partition.
From the perspective of preventing the recovery of sensitive data through recovery tools, the data must either be completely overwritten (every sector) with random data before the format, or the format program itself must perform this overwriting; as the DOS FORMAT command did with floppy diskettes, filling every data sector with the byte value F6h.

---

### Post by mips on 2008-03-28
[http://en.wikipedia.org/wiki/Hard_drive#Disk_failures_and_their_metrics](http://en.wikipedia.org/wiki/Hard_drive#Disk_failures_and_their_metrics)
[http://computer.howstuffworks.com/hard-disk.htm](http://computer.howstuffworks.com/hard-disk.htm)
[http://www.cf-intl.com/evidence_recovery_basics.htm](http://www.cf-intl.com/evidence_recovery_basics.htm)
[http://www.cf-intl.com/evDeleted.htm](http://www.cf-intl.com/evDeleted.htm)

For those that want to do a bit of reading.

---

### Post by Google Spider on 2008-03-28
Thanks Everyone!

---

### Post by regomodo on 2008-03-28
> **Daveski said:**
> Modern solid-state Flash memory only has a limited number of read/write cycles before it too will fail, so it's not just moving parts.

Please research this "fact" (myth) before you state it as negative point. Sorry, its my only pet hate as i did a masters dissertation on flash technology.

---

### Post by Daveski on 2008-03-28
> **regomodo said:**
> Please research this "fact" (myth) before you state it as negative point. Sorry, its my only pet hate as i did a masters dissertation on flash technology.

Sure - I was not saying that flash was bad, just that there is a finite life span for this type of solid-state technology, not just mechanical devices.  
I do realise that the endurance rating is so high on most modern flash devices that they will probably out-live traditional hard drives.

---

### Post by sumguy231 on 2008-03-28
Formatting my disk isn't what I'm worried about, it's running headfirst into the load cycle problem with my laptop hard disk. I won't rant about it here, but it is frustrating.

---

### Post by hessiess on 2008-03-28
you should avoid excess writing on SSD's though, as they only lave a limited number of reed/right cycles.

---

### Post by mips on 2008-03-28
lol, oh the irony. My second (I have two) 160GB Western Digital hd just gave up on me today, it's not dead but full of errors which I cannot recover from. Weird thing is I first saw errors on it over a year ago and thought to myself that i should just return it while it was under warranty but I never did. I found XFS to hande the errors better than Ext3 so that is how I lived with it :)

I had LVM on my two 160GB drives with a /home partition spanning both drives for more size. Recently the boot process moaned about errors wich I tried to repair with fsck but no go as much I tried. I could not even delete or create new partitions on the drive. I thought I might try and write zeroes to the drive with dd but that did not even work as it bombed out at 33MB. So the drive is toast.

This has nothing to do with formatting the drive though or excesive usage. It's just one of those things in life. Fortunately I had all my data backed up to a 500GB external drive, phew :)

I have never had a WD drive fail on me in all my life so this is a first for me. But you know what, I will be buying another WD drive to replace it with tomorrow.

Such is life :)

---

### Post by piratesmack on 2008-04-01
> **xArv3nx said:**
> I always used to think this, until I started formatting my disc 5-6 times every day (OCD, anyone?).

lol I'm the same way. I've formatted at least 20 times in the past 2 days. If I mess up one little thing, even if it's completely fixable I'll format and reinstall. OCD.....

Formatting is basically just changing the filesystem on your hd right? And the data isn't actually deleted until it's overwritten, right?

So I'd assume the actual process of installing an OS would be more harmful than the formatting. 

I hope it doesn't affect my hds life too much, I format A LOT :lolflag:

---

