---
title: "You guys notice how we get ripped off on Hard drives, i hate it."
date: 2007-11-20
forum: The Cafe
---

### Post by teryowen on 2007-11-20
You ever realize that when you buy a 160GB hard drive its actually 149GB or so because the companies rip you off. Instead of using the 1024 number system to count the size they do it by 1000's

So then they say 
you get 160GB but by that they mean you actually get 160000000000Bytes
which then becomes in the 1024 system 156250000KB
and then becomes in the 1024 system 152587MB
which then becomes in the 1024 system 149GB

Dont you guys think we're getting ripped off when in reality we should actually be getting 171798691800Bytes for a 160GB HD?

Any one else ever realize this?

Last note for a 250GB hard drive your actually getting 233GB
and for a 500GB hard drive your actually getting 466GB

Thought this might be interesting to some.

---

### Post by Nano Geek on 2007-11-20
I've noticed, but it's not that big of a deal to me. They all do that, and you just get used to it.

---

### Post by p_quarles on 2007-11-20
It's not a ripoff, it's just different measures. The labels use GB = 1 billion bytes. Different architectures and filesystems will use that space differently, so having a standard for labels actually prevents the vendors from fudging.

---

### Post by Lostincyberspace on 2007-11-20
Technically that is right. Now if it was GiB (gibibyte) then I would agree. :lol:

---

### Post by TBOL3 on 2007-11-20
I felt ripped of my first go around, but what would you rather see, 160 gigs, or 149.48392.... (not the actual size, but you get the point).

But if they do that, why do they have 512 MB thumb drives, why not 500 MB?

---

### Post by ~LoKe on 2007-11-20
You're not being ripped off Blame Microsoft for screwing everything up.

GiB = 1000 has been a standard a lot longer than 1024.

---

### Post by Lostincyberspace on 2007-11-20
> **~LoKe said:**
> 

GiB = 1000 has been a standard a lot longer than 1024.

GB not GiB

---

### Post by Het Irv on 2007-11-20
> **~LoKe said:**
> You're not being ripped off Blame Microsoft for screwing everything up.

GiB = 1000 has been a standard a lot longer than 1024.

Plus... Its Prettyer.  Not that It matters much.

---

### Post by ~LoKe on 2007-11-20
> **Lostincyberspace said:**
> GB not GiB

I have them backwards.

Gib (Gibibyte) = 1024
GB (Gigabyte) = 1000

A 250GB (Gigabyte) hard drive is 250,000,000,000 bytes.

---

### Post by n3tfury on 2007-11-20
as cheap as storage is nowadays, who really gives a flying crap?

---

### Post by LaRoza on 2007-11-20
> **n3tfury said:**
> as cheap as storage is nowadays, who really gives a flying crap?

Interesting, but true.

You get used to the size differences from the advertised and the actual. It has to do with many things, including individual drives and how the size is measured.

---

### Post by -grubby on 2007-11-20
you can always precalculate to find the actual measurement. But really, they are not ripping you off because they display in gigabytes and your filesystem displays in gibibytes

---

### Post by teryowen on 2007-11-20
You're all right I just thought it was intresting, as for putting on the label GB and seeing Gib on your computer, it makes a differance for the everyday customer, and they might not understand or know about this.

---

### Post by Compucore on 2007-11-20
I have always thought of it this way. I may be wrong in the assumption here. but I thought it was always due to the master boot record. Because of the second MBR that it tends to hide when it uses the main one for your actual usable of the hard drive something in the range of 5-10% of the total  hard drive space itself. Minds you I go far back as seeing hard drive running RLL, MFM, IDE, EDSI to make the space up for the hard drives themselves. There was a book I had somewhere where they gave the names of these things for the hard drive themselves. I do not rmemeber where I had seen it thought.

Compucore

---

### Post by yatt on 2007-11-20
> **teryowen said:**
> You ever realize that when you buy a 160GB hard drive its actually 149GB or so because the companies rip you off. Instead of using the 1024 number system to count the size they do it by 1000's

So then they say 
you get 160GB but by that they mean you actually get 160000000000Bytes
which then becomes in the 1024 system 156250000KB
and then becomes in the 1024 system 152587MB
which then becomes in the 1024 system 149GB

Dont you guys think we're getting ripped off when in reality we should actually be getting 171798691800Bytes for a 160GB HD?

Any one else ever realize this?

Last note for a 250GB hard drive your actually getting 233GB
and for a 500GB hard drive your actually getting 466GB

Thought this might be interesting to some.Technically, everyone else is wrong when they say a Gigabyte is 1024*1024*1024 = 1073741824 bytes. It is actually 1000*1000*1000 = 1000000000 bytes. Gibibyte is 1073741824 bytes.

---

### Post by stinger30au on 2007-11-21
doesnt a computer work in base 2 not base 10. so a gigabyte is 1024 megabytes

---

### Post by Dimitriid on 2007-11-21
Well numbers sell, ask Intel back in the day when they were trying to sell just clockspeed.

---

### Post by jpkotta on 2007-11-21
> **Compucore said:**
> I have always thought of it this way. I may be wrong in the assumption here. but I thought it was always due to the master boot record. Because of the second MBR that it tends to hide when it uses the main one for your actual usable of the hard drive something in the range of 5-10% of the total  hard drive space itself. Minds you I go far back as seeing hard drive running RLL, MFM, IDE, EDSI to make the space up for the hard drives themselves. There was a book I had somewhere where they gave the names of these things for the hard drive themselves. I do not rmemeber where I had seen it thought.

Compucore

No.  The MBR is tiny compared to the rest of the drive.  Some filesystems (ext3fs included) default to reserving 5% or so "unusable" space to protect against filling the fs completely full (the root user can still fill it).  The MBR is much, much less than 1% of the drive and the overhead of the filesystem is almost certainly less than 3%.

My take on this thing (GiB vs. GB) is that it's all OK. Sometimes I wish everyone used base-2 systems because in some ways they're simpler than base-10 systems, but base-10 is what everyone uses, so...  

Anyway I agree with the guy who said that storage is so cheap it doesn't matter.  If you NEED 160 GiB, rather than 160 GB, you also know enough to do your homework.

---

### Post by LaRoza on 2007-11-21
> **jpkotta said:**
> 
Anyway I agree with the guiy who said that storage is so cheap it doesn't matter.  If you NEED 160 GiB, rather than 160 GB, you also know enough to do your homework.

If it is that close, one should a get a bigger drive.

---

### Post by sloggerkhan on 2007-11-21
I think there's a class action lawsuit against seagate about this right now.

---

### Post by popch on 2007-11-21
Since all manufacturer use the same metrics for their drives, you can compare drive sizes easily.

Reckoning the number of bytes and files you can actually store on the thing depends on so many factors that the metric used to express the capacity does not make any marked difference.

As someone else already has mentioned: at this price, I can not see that it matters.

---

### Post by zekopeko on 2007-11-21
> **jpkotta said:**
> No.  The MBR is tiny compared to the rest of the drive.  Some filesystems (ext3fs included) default to reserving 5% or so "unusable" space to protect against filling the fs completely full (the root user can still fill it).  The MBR is much, much less than 1% of the drive and the overhead of the filesystem is almost certainly less than 3%.


then explain please why when you format (in my case) 320GB drive with ext3, kill root reserved space it still takes 5GB. Thats with an empty drive. the journal can't be that big. that's why i use ntfs on my storage drives because it has far less overhead than ext3

---

### Post by adam.tropics on 2007-11-21
> **teryowen said:**
> You're all right I just thought it was intresting, as for putting on the label GB and seeing Gib on your computer, it makes a differance for the everyday customer, and they might not understand or know about this.

True. And yet they nearly all know how big a hard drive is in terms of how many tracks Apple says their iPod can hold!

---

### Post by n3tfury on 2007-11-21
> **sloggerkhan said:**
> I think there's a class action lawsuit against seagate about this right now.

let me guess:  the lawsuit is being brought on by an american.

---

### Post by mridkash on 2007-11-21
I bought a rewriteable CD which said 700 Mb on the label.

Tried burning ubuntu 7.10 Live CD on it, error. Please insert a disk of higher capacity!!! :confused:

Then used K3b to burn it, only then I came to know that the CD RW is only 680 something Mb. Frustrating :mad:

---

### Post by daynah on 2007-11-21
I am so glad someone brought this up. I thought I had like a messed up harddrive or I was bad at math or something. Phew.

---

### Post by Rhubarb on 2007-11-21
Here's the class action law suit here:
[http://www.engadget.com/2007/10/22/details-on-proposed-seagate-class-action-settlement-revealed/](http://www.engadget.com/2007/10/22/details-on-proposed-seagate-class-action-settlement-revealed/)

---

### Post by red_Marvin on 2007-11-21
Gah! I can't decide which side I'm on, as someone who knows a fair bit of digital electronics and programming I see why it makes perfect senes to count things in power of two whenever possible, but as a supporter of standardisation, and consistency it is clear that the prefixes are meant for base ten, finally KISS says the dual system is not the solution...

---

### Post by ~LoKe on 2007-11-21
> **red_Marvin said:**
> Gah! I can't decide which side I'm on, as someone who knows a fair bit of digital electronics and programming I see why it makes perfect senes to count things in power of two whenever possible, but as a supporter of standardisation, and consistency it is clear that the prefixes are meant for base ten, finally KISS says the dual system is not the solution...

1000*1000*1000 has been used by hard drives long before Windows decided to pull out Gib.  I don't see how they could be at fault here.  Especially since I'm almost positive the box says 1GB = 1000MB.

This standard is being used by every hard drive manufacturer.

---

### Post by mcduck on 2007-11-21
> **~LoKe said:**
> 1000*1000*1000 has been used by hard drives long before Windows decided to pull out Gib.  I don't see how they could be at fault here.  Especially since I'm almost positive the box says 1GB = 1000MB.

This standard is being used by every hard drive manufacturer.
Well, I still happen to have old 256MB hard drive, and it really is 268435456 bytes.. It even says that on the label..

In my opinion it's fine that the naming was corrected to 10-base system like usually. But in that case the disks should be sold using Gibs to tell their size. No matter what, your computer still operates in binary and that's how it will also use the disk. 

So call them what you want, but 1 Gwhatever should be 1024Kwhatevers when it's about computers.

---

### Post by wana10 on 2007-11-21
> **mcduck said:**
> Well, I still happen to have old 256MB hard drive, and it really is 268435456 bytes.. It even says that on the label..

In my opinion it's fine that the naming was corrected to 10-base system like usually. But in that case the disks should be sold using Gibs to tell their size. No matter what, your computer still operates in binary and that's how it will also use the disk. 

So call them what you want, but 1 Gwhatever should be 1024Kwhatevers when it's about computers.

but 1 GiB does equal 1024 KiB...so i'm not seeing the problem. the fact that operating systems mislabel GiB as GB is not the hdd manufacturers problem.

edit* for all those that use conky and have your hdd space displayed note that it is correct in GiB. just realized that today. COOL!:KS

---

### Post by HotShotDJ on 2007-11-21
Two different measuring systems.  Some software (but not all) uses one system while the hardware manufacturers use another.  To say you are being "ripped off" is like buying a freezer that will cool down to 0 degreesCentigrade and then claiming you are being ripped off because the thermometer you have at home shows it only cools to 32 degrees Fahrenheit.  How about you got cheated because your 1 liter bottle of milk won't completely fill the 1 gallon container that you poured it into.  And that 7 centimeters is far smaller than 7 inches.  The list goes on and on!

---

### Post by Kensey on 2007-11-21
The whole MB/MiB thing is silly.  For one thing, outside open-source, who have you ever heard talk about "mibibytes" and "gibibytes"?

Like another poster I am old enough to remember when a 40-MB hard drive had 40 * 1024 * 1024 bytes on it.  The first hard drive makers to switch did so purely because of the commercial advantage of advertising more MB wihout changing anything but the ink on the ads, not because of any desire to use SI prefixes properly

Rather than make up another weird-looking term that no ordinary person is ever going to use and thus serves no purpose other than to start arguments, the right solution would be to just refer to them as "standard/imperial" and "metric".  Everybody (in the US anyway) associates metric units with powers of ten and "standard" or "imperial" units with bases other than ten (usually 12 or 16 but it depends on the measurement).  Or you could say "short MB" and "long MB".

Or we can just leave well enough alone -- at this point everybody knows that the scuzzy hard drive makers use the short measure and everybody else uses the long one, so there's no need to distinguish any more.

---

### Post by ericesque on 2007-11-21
I'm going to go with RTFL: read the ... label.

All HDD boxes break it down for you.  They state that for measurement purposes, 1 GB = 1000MB.  They also state that your milage will vary depending on FS--I don't remember how they phrase that line, but it's there.

The lawsuit is frivolous.  I hope it gets struck down as such.  Yes we need to keep companies honest, but what about the consumer?  As much as it is the company's responsibility to pony up the truth about their products, it's the consumer's responsibility to research and look for that truth before they buy.

---

### Post by inversekinetix on 2007-11-21
are you going to pay cd companies extra money?  it says the disks are only 700MB  but actually there is was more space on them for data correction.

---

### Post by n3tfury on 2007-11-21
> **inversekinetix said:**
> are you going to pay cd companies extra money?  it says the disks are only 700MB  but actually there is was more space on them for data correction.

LOL

---

### Post by thx11381974 on 2007-11-21
I think we beat this horse to death last month.

---

### Post by p_quarles on 2007-11-21
> **thx11381974 said:**
> I think we beat this **horse's corpse to re-death** last month.
Fixed. :)

---

### Post by n3tfury on 2007-11-21
> **thx11381974 said:**
> I think we beat this horse to death last month.

k.

---

### Post by inversekinetix on 2007-11-22
thats not a horse its a burrito

---

### Post by jpkotta on 2007-11-22
> **zekopeko said:**
> then explain please why when you format (in my case) 320GB drive with ext3, kill root reserved space it still takes 5GB. Thats with an empty drive. the journal can't be that big. that's why i use ntfs on my storage drives because it has far less overhead than ext3

But 5/320 ~ 1.5% < 3%.  How much overhead does ntfs use?  All file systems have overhead, and ext3 is not a winner in that category, but I'd say 1.5% is acceptable.

---

### Post by ericesque on 2007-11-22
"I love Butterstuff"
"Buttercup!"
"Butternuts"
"BUTTERCUP!"
"Cup!"

---

### Post by jespdj on 2007-11-22
Pfff, what a boring discussion.

No, you are **not** ripped off when you buy a 160 gigabyte harddisk and it contains 160,000,000,000 bytes. "Giga" is a standard [SI prefix]("http://en.wikipedia.org/wiki/SI_prefixes") which means 1,000,000,000.

Unfortunately, in the computer world the SI prefixes have been misused for decades to match the closest power of 2. There is now a new system of [binary prefixes]("http://en.wikipedia.org/wiki/Binary_prefix"), which hasn't been generally accepted yet:

1 kibibyte (KiB) = 1024 bytes
1 mebibyte (MiB) = 1024 KiB = 1024 * 1024 bytes
1 gibibyte (GiB) = 1024 MiB = 1024 * 1024 * 1024 bytes

As long as harddrive manufacturers are using the standard SI prefixes, they are completely right when they sell a 160 GB harddisk with 160,000,000,000 bytes. That class action lawsuit has no chance.

---

### Post by rliegh on 2007-11-22
I noticed. Pretty depressing to lookforward to 320g of space only to find out it's really 280. :(

---

### Post by Dale61 on 2007-11-22
The same can be said for blank DVD media.

They are advertised at 4.7GB, but I have never been able to get more than 4.35GB on a blank disc.

---

### Post by Wiebelhaus on 2007-11-22
Dude , does it really matter now?

With affordable 500Gig drives and 250Gigs so cheap? in a year or two Terabyte drives will be standard if you have THAT much data , I'd hate to see what your garage or closet looks like - lol 


Understand what I'm saying? Seriously it's crazy , I can recall not to long ago using [COLOR="Red"]256mb[/COLOR] of drive space.

---

### Post by inversekinetix on 2007-11-23
i dont think most people know GB and GiB nor the structure of disks.

---

### Post by argie on 2007-11-24
> **jespdj said:**
> Pfff, what a boring discussion.

No, you are **not** ripped off when you buy a 160 gigabyte harddisk and it contains 160,000,000,000 bytes. "Giga" is a standard [SI prefix]("http://en.wikipedia.org/wiki/SI_prefixes") which means 1,000,000,000.

Unfortunately, in the computer world the SI prefixes have been misused for decades to match....

I agree that it's not a rip-off because most adverts I've seen say ' 1GB = 1,000,000,000 bytes' at the bottom and not extremely small either. But the SI argument is kind of funny, I mean, I don't think a byte is an SI unit, so that wouldn't apply. It's like saying Megaman is a million men.

---

### Post by kopinux on 2007-11-24
you can blame marketing.

how about internet speed, they only say 1mbps.
an average consumer would think its 1 mega bytes per second.
since we dont use bits always bytes.

so what the consumers think they are running 1 mega bytes per sec is actually just running 125 kilo bytes per sec

---

### Post by popch on 2007-11-24
> **kopinux said:**
> you can blame marketing.

how about internet speed, they only say 1mbps.
an average consumer would think its 1 mega bytes per second.
since we dont use bits always bytes.

so what the consumers think they are running 1 mega bytes per sec is actually just running 125 kilo bytes per sec

Yes. Just as some think that the mileage of their cars is measured in miles per Gill.

There are technical reasons for measuring the transmission speed of a serial line in bits per unit of time. Nothing to do with marketing at all.

---

### Post by Endolith on 2008-04-13
> **red_Marvin said:**
> as someone who knows a fair bit of digital electronics and programming I see why it makes perfect senes to count things in power of two whenever possible

What does use of binary for computations have to do with the size of a hard drive?  Or the size of a file?  There's really no connection at all.  If hard drives stored data in trinary, there would be no connection to powers of 3, either.  The only thing that has a natural connection to powers of 2 is memory, due to the binary addressing.

> **Kensey said:**
> Like another poster I am old enough to remember when a 40-MB hard drive had 40 * 1024 * 1024 bytes on it.

Which hard drive was that?  I've heard this before but no one has ever shown an actual hard drive measured in powers of two.  As far as I can tell (reading through old computer manuals on bitsavers.org), hard drives have been consistently measured in powers of 10 since the 50s.

> The first hard drive makers to switch did so purely because of the commercial advantage of advertising more MB wihout changing anything but the ink on the ads, not because of any desire to use SI prefixes properly

I highly doubt that.  The first hard drives stored things like "1,000,000 characters".  There is no reason this would or should be measured in powers of two.

> at this point everybody knows that the scuzzy hard drive makers use the short measure and everybody else uses the long one, so there's no need to distinguish any more.

The huge number of threads on Ubuntu Forums asking about missing space on hard drives, DVDs, and Flash drives says otherwise.

[http://ubuntuforums.org/showthread.php?t=101855#10](http://ubuntuforums.org/showthread.php?t=101855#10)
[https://bugs.launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/14422](https://bugs.launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/14422)
[http://ubuntuforums.org/showthread.php?t=300184](http://ubuntuforums.org/showthread.php?t=300184)
[http://ubuntuforums.org/showthread.php?t=49698](http://ubuntuforums.org/showthread.php?t=49698)
[http://ubuntuforums.org/showthread.php?t=322529#2](http://ubuntuforums.org/showthread.php?t=322529#2)
[http://ubuntuforums.org/showthread.php?t=420126](http://ubuntuforums.org/showthread.php?t=420126)
[http://ubuntuforums.org/showthread.php?t=113207](http://ubuntuforums.org/showthread.php?t=113207)
[http://ubuntuforums.org/showthread.php?t=241141](http://ubuntuforums.org/showthread.php?t=241141)
[http://ubuntuforums.org/showthread.php?t=471018](http://ubuntuforums.org/showthread.php?t=471018)
[http://ubuntuforums.org/showthread.php?t=52501](http://ubuntuforums.org/showthread.php?t=52501)
[http://ubuntuforums.org/showthread.php?t=450225](http://ubuntuforums.org/showthread.php?t=450225)
[http://ubuntuforums.org/showthread.php?t=704932](http://ubuntuforums.org/showthread.php?t=704932)
[http://ubuntuforums.org/showthread.php?t=385468](http://ubuntuforums.org/showthread.php?t=385468)
[http://ubuntuforums.org/showthread.php?t=73306](http://ubuntuforums.org/showthread.php?t=73306)
[http://ubuntuforums.org/showthread.php?t=696000](http://ubuntuforums.org/showthread.php?t=696000)
[http://ubuntuforums.org/showthread.php?t=229552](http://ubuntuforums.org/showthread.php?t=229552) 
...

This causes real confusion, and we should fix it if we can.

---

### Post by aaaantoine on 2008-04-14
> **argie said:**
> I agree that it's not a rip-off because most adverts I've seen say ' 1GB = 1,000,000,000 bytes' at the bottom and not extremely small either. But the SI argument is kind of funny, I mean, I don't think a byte is an SI unit, so that wouldn't apply. It's like saying Megaman is a million men.

But Megaman *IS* a million men!  Condensed into a single robot.  Actually, if you consider the premise of the game is that you absorb the powers of the robot masters you defeat, the name... kinda... makes sense.

The byte may not be an SI unit, but it is the universally recognized method of measuring computer data quantity.  And there are a lot of bytes.  Therefore, kilo, mega, giga, tera, etc. have been adapted from the SI system to measure large quantities of bytes.  The only problem being, someone decided that 1 kilobyte can also mean 1024 bytes,.  Because this is different from the SI standard of "1 kilosomething = 1000 somethings", the IEC officially began calling this a Kilo Binary Byte, or Kibibyte.

---

### Post by Endolith on 2008-04-14
> **aaaantoine said:**
> The only problem being, someone at some point decided that 1 kilobyte = 1024 bytes.  Because this is different from the SI standard, the powers that be made an SI unit calling this a kibibyte.

[LIST=1]
[*]There seems to be this misconception that K = 1024 was some kind of standard in the past, and that it's only the evil hard drive manufacturers that corrupted it. But this isn't true.  Look through old documents on bitsavers and most of the instances of "K" are 1000.  It's had multiple definitions from the very beginning.  In fact, in the very beginning, using K for 1000 and K for 1024 were the same.  For instance, writing "16K" for 16,384 is correct whether you divide by 1024 *or* round to the nearest 1000.
[*]"byte" is not an SI unit.  "kibibyte" is not, either.  It's an IEC unit.  The SI standard just says "don't use this for 1024".  It doesn't say what to do instead.
[*]Do you really have to say "kibibyte" for KiB?  It says in the standard that it's an abbreviation for "kilobinary byte".  Can't we just write "KiB" but call it a "binary kilobyte"?
[/LIST]

---

### Post by aaaantoine on 2008-04-14
> **Endolith said:**
> 
1. There seems to be this misconception that K = 1024 was some kind of standard in the past, and that it's only the evil hard drive manufacturers that corrupted it. But this isn't true.  Look through old documents on bitsavers and most of the instances of "K" are 1000.  It's had multiple definitions from the very beginning.  In fact, in the very beginning, using K for 1000 and K for 1024 were the same.  For instance, writing "16K" for 16,384 is correct whether you divide by 1024 *or* round to the nearest 1000.
2. "byte" is not an SI unit.  "kibibyte" is not, either.  It's an IEC unit.  The SI standard just says "don't use this for 1024".  It doesn't say what to do instead.


Thank you for clarifying and correcting.

> **Endolith said:**
> 
3. Do you really have to say "kibibyte" for KiB?  It says in the standard that it's an abbreviation for "kilobinary byte".  Can't we just write "KiB" but call it a "binary kilobyte"?


I guess you could call it either one.  I prefer to go for fewer syllables, myself.

---

### Post by Pogeymanz on 2008-04-14
I like it when some companies advertise with how many photos or mp3s you can fit on their device. That's probably our solution: No GiB or GB, let's measure hard drives in how many mp3s fit! :)

---

### Post by aaaantoine on 2008-04-14
> **EmosSuck777 said:**
> I like it when some companies advertise with how many photos or mp3s you can fit on their device. That's probably our solution: No GiB or GB, let's measure hard drives in how many mp3s fit! :)

I saw one hard drive that explained the size of the drive in such layman's terms.

[quote=Some Hard Drive Manufacturer]
Can store...
[list]
[*]100,000 photos
[*]50,000 songs
[*]20,000 videos
[*]1,000 movies
[*]100 games
[/list][/quote]

Each one had fine print to go along with it.

---

### Post by Kensey on 2008-04-17
I forgot all about this thread...

> **Endolith said:**
> What does use of binary for computations have to do with the size of a hard drive?  Or the size of a file?  There's really no connection at all.

Hard drives operate in bits, just like memory or CPUs.  One would expect data capacity to be measured using the same units in all three.

> ...no one has ever shown an actual hard drive measured in powers of two.  As far as I can tell (reading through old computer manuals on bitsavers.org), hard drives have been consistently measured in powers of 10 since the 50s.

How about [this one]("http://stason.org/TULARC/pc/hard-drives-hdd/western-digital/WD-95048-X-40MB-5-25-HH-IDE-XT.html")?  782 cylinders, 4 heads, 27 sectors/track, 512-byte sectors.  Do the math and that's 43,241,472 bytes = 42228 long K = 41.24 long MB.  That drive is specified as a 40-MB formatted-capacity drive.

> The first hard drives stored things like "1,000,000 characters".  There is no reason this would or should be measured in powers of two.

In those old computer systems, a byte was [often not a power of two]("http://catb.org/jargon/html/B/byte.html") -- it could be any number really (the PDP-7 used an 18-bit byte, many systems used 9-bit bytes, and at least one allowed a byte to be defined as anything from 1 to 36 bits).  Beginning in late 1956, there was a strong push toward an 8-bit byte, reinforcing the idea of measuring things in powers of two.

---

### Post by Xbehave on 2008-04-18
i like it ever since it one me an argument.
Hard drives are physical things so measure it by how many dents you can make
file systems are electronic things so measure it in gi,mi,ki as they make more sense
small mp3 players are chips so it makes more sense to use computing standards.
flash driver are where it gets tricky, does anybody know how they list SSDs?

When they say you can fix x songs on an ipod, its fine aslong as they messure it in led zeppelin mp3s. Hell i wouldnt mind if they messured it in 6:04 songs (all the best songs are around that length anyway), but i bet they use some stupid 3:00 song @128kps (im no audiophile but on good tracks 128 doesnt cut it)

---

### Post by Endolith on 2008-04-18
> **Kensey said:**
> Hard drives operate in bits, just like memory or CPUs.  One would expect data capacity to be measured using the same units in all three.

There is absolutely no connection between powers of 1024 and the number of discrete units (bits, bytes, blocks) you can fit on a given surface area, or the number of discrete events you can send over a wire in a given time, or the number of symbols required to store an arbitrary amount of data (like a 7:32 minute MP3 or a 5 page report).  The only thing that has an inherent power-of-two relationship is memory, because each bit is manufactured individually, and it makes sense to use up all the possible address locations when creating a chip.  If computers used trinary addressing to store binary data, memory would be measured in powers of three.  But even in trinary world, hard drives would still be measured in decimal, because there's no connection between the amount they can store and the base being used.

> How about [this one]("http://stason.org/TULARC/pc/hard-drives-hdd/western-digital/WD-95048-X-40MB-5-25-HH-IDE-XT.html")?  782 cylinders, 4 heads, 27 sectors/track, 512-byte sectors.  Do the math and that's 43,241,472 bytes = 42228 long K = 41.24 long MB.  That drive is specified as a 40-MB formatted-capacity drive.

Maybe.  It's in a series of 20, 30, 40 MB, though, so they could also just be rounding to the nearest ten.  They're rounding down either way.  Pressing the "Prev" button finds a more convincing example:

[WD 95048](http://stason.org/TULARC/pc/hard-drives-hdd/western-digital/WD-95048-A-41MB-5-25-HH-IDE-AT.html)

However, pressing it again finds this:

[WD 95044](http://stason.org/TULARC/pc/hard-drives-hdd/western-digital/WD-95044-X-43MB-5-25-HH-IDE-XT.html)

:)

Keep pressing Prev and see the same (formatted) size drive (21,620,736 bytes) being marketed as 20, 21, and 22 MB.

Anyway, if there were a relationship between drive size and powers of two, the size would be something like 32 MB or 64 MB, not 30 or 43.

> In those old computer systems, a byte was [often not a power of two]("http://catb.org/jargon/html/B/byte.html") -- it could be any number really (the PDP-7 used an 18-bit byte, many systems used 9-bit bytes, and at least one allowed a byte to be defined as anything from 1 to 36 bits).  Beginning in late 1956, there was a strong push toward an 8-bit byte, reinforcing the idea of measuring things in powers of two.

Some of the first computers were decimal throughout, based on the mechanical computers that came before them.

---

### Post by Kensey on 2008-04-18
> **Endolith said:**
> There is absolutely no connection between powers of 1024 and the number of discrete units (bits, bytes, blocks) you can fit on a given surface area, or the number of discrete events you can send over a wire in a given time, or the number of symbols required to store an arbitrary amount of data (like a 7:32 minute MP3 or a 5 page report).  The only thing that has an inherent power-of-two relationship is memory, because each bit is manufactured individually, and it makes sense to use up all the possible address locations when creating a chip.

A bit is a bit is a bit.  It doesn't matter if the physical representation of the bit is which way a magnetic domain points, whether a logic gate is energized, or whether a line is above or below a given voltage -- once you're talking bits, you naturally start talking powers of two.  Also, we're not talking about things in a vacuum here -- eventually the data on that hard drive may be read into memory, and things in memory may be written to a hard drive.  Either use decimal units for everything, or binary units for everything -- the historical expectation in the industry is the latter.

> If computers used trinary addressing to store binary data, memory would be measured in powers of three.  But even in trinary world, hard drives would still be measured in decimal, because there's no connection between the amount they can store and the base being used.

If computers used trinary memory and binary hard drives, then it would make sense on one level to use binary powers for hard drives, and trinary powers for memory, although in practice it would still be better to standardize on one or the other (or something else, as long as everything was measured the same).

There is a very intimate connection between the amount of data you can store and the base used.  Imagine a hard drive where each data element has three states, with the same element density as one that can only express two states.  That hard drive now has an increased capacity in direct relation to the difference between two and three.

---

### Post by Endolith on 2008-04-18
> **Kensey said:**
> A bit is a bit is a bit.  It doesn't matter if the physical representation of the bit is which way a magnetic domain points, whether a logic gate is energized, or whether a line is above or below a given voltage -- once you're talking bits, you naturally start talking powers of two. ...

There is a very intimate connection between the amount of data you can store and the base used.

No there isn't.

Imagine you're a memory manufacturer.  You make a chip that uses binary addressing and stores binary data.  It has 4 address lines and 1 data line, storing a bit in each memory location.  How much data should the chip be made to hold?  16 bits, right?  It makes the most sense to put a storage unit in every memory location that can be accessed.  Having memory addresses that lead to a dead end could certainly be done, but would be a waste of space and materials.

Now imagine you're making a chip that uses binary addressing but stores ternary data (each "trit" stores a -1, 0, or +1).  What's the optimal capacity for the chip?  16 trits.  It's still a power of two, because it's the addressing scheme that sets the optimal size of the chip.

Now imagine you're making a chip that uses ternary addressing (4 address lines) and stores binary data.  So how many bits should the memory chip be made to store?  There are 81 possible memory addresses, so we make it store 81 bits.  Even though you're storing binary data, there's absolutely no relationship between the capacity of the chip and the base of the data being stored.

Now let's imagine you're storing binary data on a wire by reversing magnetic fields as it moves past a magnetic head.  How many bits should you store on it?  The answer is "as many as you can".  There's no connection to binary or ternary or powers of 1024 or anything.  You just fit the maximum density of information on the wire as you reliably can with the technology you have, and the length of the wire on the spool (which can be any arbitrary value) determines the total capacity of the drive.

> Also, we're not talking about things in a vacuum here -- eventually the data on that hard drive may be read into memory, and things in memory may be written to a hard drive.  Either use decimal units for everything, or binary units for everything -- the historical expectation in the industry is the latter.

Memory's the only thing with an inherent relationship to powers of 1024.  Everything else is arbitrary and has traditionally been measured the same way we measure volume, area, length, time, weight, resistance, and power; in decimal.  This is the system that makes the most sense for sizes of storage media, rates, and file sizes.  For memory capacity, we have dedicated power-of-two units that we can use to keep thing simple.

> Imagine a hard drive where each data element has three states, with the same element density as one that can only express two states.  That hard drive now has an increased capacity in direct relation to the difference between two and three.

But there's still no connection to powers of two or powers of three for the total capacity of the drive.  Imagine using the same hard drive in an 8-bit system and a 7-bit system.  The total number of bits you can store is the same, but the number of bytes is different.  There's still no relationship to a power of 2, 7, or 8.

---

### Post by tigerplug on 2008-04-18
I can't forsee myself dying over 11GB

---

