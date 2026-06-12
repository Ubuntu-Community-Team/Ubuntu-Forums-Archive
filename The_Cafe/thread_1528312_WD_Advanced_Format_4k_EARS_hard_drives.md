---
title: "WD Advanced Format 4k EARS hard drives"
date: 2010-07-10
forum: The Cafe
---

### Post by rjwaldren on 2010-07-10
If you have one of the AF Western Digital drives you know what a pain](*,)they are to use under non-Windows systems.  This is because of a compatibility layer that reports the drive as a 512b disk to work with older OS's (XP and before).  A Solaris user has opened a request in the ideas forum over at WDC.com to release a proper 4k firmware.  Please vote and make some noise over there.

Please report the problems to WD.  They are likely expecting to cash in on people buying another when proper 4k takes over, I doubt I'll buy WD personally, but more noise that gets made the more like they are to listen. So open bugs at WDC and annoy the crap out of them.

[http://community.wdc.com/t5/Other-Ideas/Release-non-512-byte-sector-emulated-firmware-for-WD-EARS/idi-p/21347](http://community.wdc.com/t5/Other-Ideas/Release-non-512-byte-sector-emulated-firmware-for-WD-EARS/idi-p/21347)

---

### Post by RJARRRPCGP on 2010-07-10
4 KB is the same as the typical cluster size of NTFS. 

But I dunno about Ext4. Sorry. :(

---

### Post by cariboo on 2010-07-10
I have a WDC WD10EARS in my server, I didn't have to do anything special to partition and format it. According to the installation instructions that came with the drive, the only OS that needed special consideration was XP.

---

### Post by rjwaldren on 2010-07-10
The FS format really isn't the issue - it's partitioning.  The drive reports itself to the OS as having 512b sectors.  Parted, fdisk, gpt and other partitioning tools use this information to choose the start/end sectors when creating partition.  They align to 512b sector boundaries rather than the actual 4k boundaries that really exists on the drive.  This causes huge performance hits as the 4k disk sectors bridge two adjacent sectors when partitioned with a 512b scheme.

It is possible to manually set the start/end points through these tools to align the partitions to proper boundaries and it's fairly easy for a single partition.  But get's complicated in more advanced setups - multipartition, RAID, BTRFS, ZFS, etc.  If the drive properly reported 4k sectors the tools would do the right thing in the first place.  Any work arounds would likely only apply to these first gen WD AF drives, as second gen (and first gen from other manufacturers) will like properly report 4k to begin with.

My hope is that WDC can be encouraged to release an firmware that properly reports the drives for the droves of us that aren't using legacy windows.  Check the forums and google for a glimpse of the problems and workarounds necessary to use these drives with any kind of decent performance.

---

### Post by rjwaldren on 2010-07-10
cariboo907 - 

If it's MBR partition that starts at sector 63 then it's not aligned correctly.  You would see a notable improvement in manually repartitioning to start at 64 and setting the size to be an even multiple of 4096.

gpt starts partition 1 at sector 2048 (in 512b terms) which is a 4096 boundary but there is no guarantee that the partiton will end on a 4096 boundary or that any following partitions will start/end on one.  So it still requires manual setup.  Win7 also starts at sector 2048 for it's default installation.

See
[http://ubuntuforums.org/showthread.php?t=1407098](http://ubuntuforums.org/showthread.php?t=1407098)
for a break down of how the drive "lies", and
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=drs-#gpt_solution](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=drs-#gpt_solution)
for some pointers on how to align it, there are also various HOWTO threads on this forum.

When you format set the blocksize in mkfs to a multiple of 4096.  I'm using a bs of 32768 right now as 8:1 (block:sector) is the ratio recommended for UFS, since I'm testing on BSD for the moment.

BTW - ext4 looks to default to a 4k BS which is a 8:1 ratio in 512b terms.  I'm not sure how much that ratio matters though.

---

### Post by frostschutz on 2010-07-10
Every storage layer you put on the drive (partitions, encryption, lvm, raid, filesystems, ...) has to respect the 4k boundaries of the drive. Any layer does not respect that and wham you get a huge performance penalty.

Don't get WD EARS drives if you do not know how to partition and format and set other storage layers up manually, because it is not done automatically right for you, as the drive is not detected as 4k.

I don't use multiple of 4k for filesystem sectors. I just use 4k. Anything larger would be inconvenient for me. I don't think it helps performance much either to use larger blocks, but YMMV.

---

### Post by cariboo on 2010-07-10
So how much faster than this:

```
sudo hdparm -tT /dev/sdf
[sudo] password for me: 

/dev/sdf:
 Timing cached reads:   2438 MB in  2.00 seconds = 1219.14 MB/sec
 Timing buffered disk reads:  326 MB in  3.01 seconds = 108.30 MB/sec
```

will I get if I repartition?

BTW this is a file server, so transfer speeds are really limited to network speed, no matter how fast the raw data transfer rates are.

---

### Post by cascade9 on 2010-07-10
> **cariboo907 said:**
> So how much faster than this:

```
sudo hdparm -tT /dev/sdf
[sudo] password for me: 

/dev/sdf:
 Timing cached reads:   2438 MB in  2.00 seconds = 1219.14 MB/sec
 Timing buffered disk reads:  326 MB in  3.01 seconds = 108.30 MB/sec
```will I get if I repartition?

BTW this is a file server, so transfer speeds are really limited to network speed, no matter how fast the raw data transfer rates are.

Depends. This person went from 92MB/sec to 106MB/sec (EXT4)-

[http://www.linuxconfig.org/linux-wd-ears-advanced-format](http://www.linuxconfig.org/linux-wd-ears-advanced-format)

BTW, its not just a speed issue. I forget what the nasty that happens if your drive isnt aligned is called now, but it could shorten the life of the drive a considerable amount.....

---

### Post by rjwaldren on 2010-07-10
True, using a larger BS can waste space if you if have lots small files.  My purpose is large files so I'm using a recommended and test config that covers the 4k scenario.  I kinda think the 8:1 ratio recommendation is based on drive that are truely 512b sectors to match the 4k expectations of the OS (page size, etc).  Last time I really worried about tuning anything similar was for stripe sizes in RAID0, which again depends greatly on the average file size.

So I'll change that to read, when formatting ensure that the BS is 4096 _**OR**_ a multiple thereof.

---

### Post by cariboo on 2010-07-10
Actually everything I read before setting up the drive concerned low data transfer rates. I tried a small partition starting at 63 and then wiped it and started one at 64, there was no discernible difference in transfer speeds. The drive is all one partition, though I can't see that making any difference. The smallest file on the drive is 1.2Gb.

Also this drive has been in constant usage with no reboot since March 30/2010 with zero problems.

---

### Post by rjwaldren on 2010-07-10
> **cariboo907 said:**
> So how much faster than this:

Will I get if I repartition?

BTW this is a file server, so transfer speeds are really limited to network speed, no matter how fast the raw data transfer rates are.

hdparm doesn't really tell the story - I believe it is working properly with the 512b emulation and reading RAW as the firmware directs it to and not concerned about the partitioning.

A better test is to cd to the mount point and use dd.
Write test:
  dd if=/dev/zero of=/mnt/X?X?/test.file bs=4096
Let it run for a bit and CTRL-c. Then read the created file:
  dd if=/mnt/X?X?/test.file of=/dev/null bs=4096

I've seen 22MB/s improvements on writes and 10+MB/s to off the scale improvements on reads.

For misaligned drive it references 2 adjacent sectors for every 1 needed.  Since they are sequential it doesn't amount to a 50% loss but writes are more affected.  As as stated causes the drive to have to work a lot harder than it should.

Most people seem to be using these in file server as am I. It does make a difference in smb perf over a 1g link.  It probably wouldn't be noticeable over a 100 link but it's still overworking the drive.

---

### Post by cariboo on 2010-07-10
I decided to repartition the drive starting at 64, then formating as ext4.

These are the before results:

```
dd if=/dev/zero of=/media/green/test.file bs=4096
^C1166367+0 records in
1166367+0 records out
4777439232 bytes (4.8 GB) copied, 42.0281 s, 114 MB/s

dd if=/media/green/test.file of=/dev/null bs=4096
1166367+0 records in
1166367+0 records out
4777439232 bytes (4.8 GB) copied, 42.6126 s, 112 MB/s
```

These are the results after:

```
dd if=/dev/zero of=/media/green/test.file bs=4096
^C891512+0 records in
891512+0 records out
3651633152 bytes (3.7 GB) copied, 29.6443 s, 123 MB/s

dd if=/media/green/test.file of=/dev/null bs=4096
891512+0 records in
891512+0 records out
3651633152 bytes (3.7 GB) copied, 32.2934 s, 113 MB/s
```

So I gained about 9MB/s on writes, and 1MB/s on reads

Now to move the 480GB of data back on to the drive.

---

### Post by rjwaldren on 2010-07-10
Cool,not as big as some have seen but an improvement, and definitely better for your drive in the long run... If only it was so easy in a RAID config.

That's why I started the thread, for every 1 of us that realize the problem there are probably 10 that don't.  If only people would start voting and making noise over at the WDC link I posted. 

160 views in a few hours but not one has bothered to hit WDC about it.  Numbers, that's the only way to get their attention.

---

### Post by cascade9 on 2010-07-11
I would have posted there except for 2 things- 

1- I dont like the contnet of the link to the WDC forums, its a bit to RAID heavy IMO. If it was purely about issues with linux/bsd/solaris and the 'advanced format' drives I would liek it more.  

2- > You must be a registered user to add a comment on this idea. If you've already registered, please log in. If you haven't registered yet, please register and log in.

That is just not happening. I vowed I would never 'register' with another hardware manufacturer after last time.....

---

### Post by rjwaldren on 2010-07-11
I understand the registration issue, it kept me from voting for a bit.  The actual registration is simply creating a username/password - it does require an email address but I've never received anything from WDC.

Your free to leave your own comment - There is only one comment specific to BSD/Solaris that even mentions RAID the rest are *nix specific.

---

### Post by rjwaldren on 2010-07-12
I thought there would be more support for this.  Oh well, the WD hit craigslist shortly, and I buy some new samsungs or seagates.

---

### Post by cascade9 on 2010-07-14
I'd go for samsung myself (or a WD caviar blacks given the choice).....IMO seagates hasnt really made great SATA drives.

---

### Post by rjwaldren on 2010-07-14
> **cascade9 said:**
> I'd go for samsung myself (or a WD caviar blacks given the choice).....IMO seagates hasnt really made great SATA drives.

Sad thing is, this is the first time since 1.6G was the norm that I've purchased a WD drive.  I had several die without warning and without the possibility of recovery.  My last employer only used WD on workstations and we where replacing them constantly.  Not to say other drives don't fail.  Over the past 15? years, I've only had one Seagate that I couldn't at least get the majority of data off of before it went.  I even still have some 15G IBM's from the heart of the "Deskstar/DeathStar" era that worked for ~3 years in a RAID0 without a blink - Still perfect.  I recently had a 40G samsung 2.5 die of old age, but I saw that coming.  I have never had a Samsung/Hitachi fail for anything other than age.  It's mainly the stigma that keeps me from buy Hitachi.

I have 2 of the EARS drives and one has already replaced RMA'd for mechanical problems. So after 15 years I gave them another chance, yet they still retain there position of 2nd only to Maxtor in crappy drives, at least IMO.  I have never had a Samsung/Hitachi fail for anything other that age.

My list in order of preference/reliability:
Samsung, Seagate, Hitachi, fujitsu, WD, Maxtor

Samsung is the king, IMO.  Though I must admit I haven't used many - I haven't had to;)

---

### Post by cariboo on 2010-07-14
Hard drives can be funny things, I have had absolute no luck at all with Hitachi/IBM, Samsung, Maxtor and especially Fujitsu.

WD and Seagate have always been reliable for me. 

I don't know if you can equate the quality of the drive with falling prices, but hard drive reliability seems to have dropped along with the prices.

---

### Post by rjwaldren on 2010-07-14
Yeah, HD manufacturer can be a touchy area amoung us geeks;).  

When it comes to finding a good one, the recent addition of "For RAID/Not For RAID" to the consumer segment of the market doesn't help, especially when even the lowest end boards support some sort of fake raid for the other OS and don't need it for *nux.  A 1TB+ drive that can't be used in a RAID config makes absolutely no sense to me.  Last years model was fine in either case, now we have to have a special and more expensive feature or it might not work.  It used to just be figuring out the controller drivers.  Remember when you could just grab a drive out of a pile and it just worked?

Reminds me of a Epson Inkjet I RMA'd once, they shipped me a new one and told me to throw away the original - Made for the dumpster.  I believe the engineers want to design the best, but the money guys scale it back to remain far enough on this side of a recall, while still requiring replacement/upgrades.

I think WDC made a lot of money and press off of being the first with 4k drives.  Even though the next wave will be where the true benefit will be seen and matter.  Or will WDC release a 3TB drive with a compatibility layer that can't be bypassed.  (Honestly, I haven't done the math there)

---

### Post by CharlesA on 2010-07-14
Heh, I remember someone telling me that a "desktop" drive won't work on a RAID array, cuz it'll drop out of the array if there are errors it has it repair and that you need special "made for RAID" drives that were about twice the cost of a normal drive.

I've been running an array with three 2TB desktop-class drives for close to a year without any problems. I guess time will tell if I have problems when one of the drives fails and everything hits the fan.

Good thing I have backups. :-)

---

### Post by rjwaldren on 2010-07-14
> **CharlesA said:**
> you need special "made for RAID" drives that were about twice the cost of a normal drive.

:-)

Take a look at the WDC forums.  They've actually built the consumer drives to do just that.  In fact some model numbers that used to work don't with newer firmware rev's.  The RAID versions have a TLER feature that prevents it from dropping out of the RAID.  When you ask  what the problem is over there, they say buy the "RAID" version and pin it on you for trying to do something the hardware wasn't designed for.  Then they point you to an obscure document buried in the FAQ's where they tell why a "desktop" drive can't work in a RAID.  It's oddly not on the box and I doubt in the retail literature.

Funny thing is the FAQ is written as though it always happened and the new RAID drives solve it.  Truth is by making it happen they created a market for a "consumer RAID drive".  Personally I wouldn't be suprised to find the difference is no more than a single enable/disable bit in the firmware.  Enterprise class is a different story.

---

### Post by CharlesA on 2010-07-14
Yeah, I read a bit of stuff over at WD about it, but I don't feel like spending 500 bucks per drive for a home server. I think it was the Long-term recovery or some such crap that RE drives don't have.

Granted the drives I have in there are Hitatchi brand ones that cost me almost 200 bucks each (2TB drives were (and still are) bloody expensive when I bought them), they haven't given me any problems (yet) *knock on wood*

Enterprise level is definitely different, for sure.

---

### Post by rjwaldren on 2010-07-15
Fortunately the problem seems to affect fakeraid and hardware raid.  It seems to work okay with *nix softraid and I had no problem with btrfs either - aside from the 4k issue.

---

### Post by Starks on 2010-07-15
Can't 4K drives that don't report themselves properly still be detected properly.

I had heard that the problem discussed in the original post was alleviated through clever open-source engineering.

---

### Post by rjwaldren on 2010-07-15
It's possible that, for instance that parted, fdisk, etc could maybe the check the devid of the drive and adjust it's math accordingly to align the partitions.  Or maybe the sata driver could catch the 512 reported by the drive and report 4096 to the kernel.  I don't know if it would still require the communication with the drive to be based on 512b or not.

Those would be hacks to work around bad firmware though.  When 4k is in broader production it won't matter as the manufacturer won't lie to the os.  The kernel/utilities would already do the right thing if the firmware was correct.  It's nice that OSS can make the best out of bad designs and work around it, but this is a case where the manufacturer, can and should fix it.

I would guess that even the majority of Win7 users that have these drives with more than one partition, don't know there is a problem that can likely shorten the life of their drives.  Even under Win7 only a full partition or the first partition will be aligned unless you use the WD align tool, which BTW, is a linux based tool from Acronis.  In one test that I did even the tools that start the partition on a 4096 boundary don't necessarily end it on one.

On freenas, they have added a 4k check box to their WebUI that passes correct parameters when creating/formatting under UFS or ZFS.  It still must be done manually for other formats and doesn't work for softRAID setups.  FreeBSD also has a tool that allows you to create a virtual device over your drive and specify it as 4096.  It works to some extent, but results in having to go through 2 emulation layers to get to the truth.

It all comes down to there are many ways to skin this cat, but if we speak up to WDC maybe it wouldn't be needed at all, it shouldn't have been needed at all.  It would rather have seen "must have support in os" or "Not compatible with XP" than needing special handling in all OS's.

[http://community.wdc.com/t5/Other-Ideas/Release-non-512-byte-sector-emulated-firmware-for-WD-EARS/idi-p/21347](http://community.wdc.com/t5/Other-Ideas/Release-non-512-byte-sector-emulated-firmware-for-WD-EARS/idi-p/21347)

---

### Post by cascade9 on 2010-07-16
> **cariboo907 said:**
> Hard drives can be funny things, I have had absolute no luck at all with Hitachi/IBM, Samsung, Maxtor and especially Fujitsu.

WD and Seagate have always been reliable for me. 

For me, the big problem was always quantum. Maxtor would be the 2nd worst, and generally WD, Seagate, Fujitsu and Hitachi/IBM pretty good. I've had issues with all of them though :| 

> **cariboo907 said:**
> I don't know if you can equate the quality of the drive with falling prices, but hard drive reliability seems to have dropped along with the prices.

+1. IMO they are built 'down to a price point'. 

BTW, link to a forum posting with some info on the possible long term reliability problem- 
 
[http://www.readynas.com/forum/viewtopic.php?f=24&t=40828](http://www.readynas.com/forum/viewtopic.php?f=24&t=40828)

> **CharlesA said:**
> Yeah, I read a bit of stuff over at WD about it, but I don't feel like spending 500 bucks per drive for a home server. I think it was the Long-term recovery or some such crap that RE drives don't have.

*blinks* show how much I know,  thought that the RE drivers were the RAID drives. :|

---

### Post by rjwaldren on 2010-07-16
> **cascade9 said:**
> For me, the big problem was always quantum. Maxtor would be the 2nd worst, and generally WD, Seagate, Fujitsu and Hitachi/IBM pretty good. I've had issues with all of them though :| 

Hah, see what I mean, I loved quantum and mourned the day they were swallowed by Maxtor.  I've had multiple Maxtors smoke on me, not fail, literally burn up there controller boards with smoke and smd's popping off (Yes the P/S was fine and a another brand lasted the remaining life of the PC's they were used in.)  One Maxtor failed and when I called tech supp they said - a 100Mhz FSB with a 3 divider = 33.33Mhz.  Their drives are only spec'd for 33 therefor I had overclocked it and voided the warranty.  Hmmm, industry wide default settings at the time were over spec and would void your warranty:mad:. This response came from their tier-3 support BTW.

I must admit for quantum, I mainly used their Atlas scsi drives.

---

