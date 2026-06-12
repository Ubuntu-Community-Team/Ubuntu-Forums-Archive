---
title: "Ubuntu 20.04 Server makes my machine scream with Long continuous beeping sound alarm"
date: 2021-05-15
forum: Server Platforms
---

### Post by mortalkorona on 2021-05-15
Hi,

**Description**
I just finished building my Server a couple of weeks ago and installed Ubuntu 20.04 Server edition on it. The machine was running ok 24/7 for about 5 days until it started to scream with a **Long continuous beeping** sound alarm one very early morning.

I shutdown the server by pressing the OFF button to turn off the alarms.

A few days later I turned ON the server again. But now I'm getting this Long continuous screaming sound alarm from my machine several times within 30 minutes or so.

.

**Question 1**
How can I troubleshoot and pinpoint what the issue is?
I ran ```
$ dmesg
``` but don't really know what to look for, it's just a bunch of technical data with no apparent Warning or Error labels.

.

[B]Question 2
[/B]During the 5 days that I ran my machine 24/7 I checked the temperatures for my CPU, SSD and HDD disks several times each day. And I didn't see any critical overheating issues. Is there something from my BIOS menu I can check to find what hardware is causing this screaming beep sound alarms and server shutdowns?

---

### Post by LHammonds on 2021-05-15
Beeps are sounds the BIOS on the motherboard makes when it detects errors with the hardware which are usually VERY bad and need to be addressed.

To know what those beep codes are, you need your motherboard manual.  If it is a commercial-built machine, you might be able to get the codes from places that list them by vendor.  [url=https://www.ionos.com/digitalguide/server/know-how/bios-beep-codes/]Example[/code].  But I would go based on the manual for that exact motherboard to be 100% certain.

LHammonds

---

### Post by CharlesA on 2021-05-15
Are you using server grade gear or desktop grade gear for this server? Both should have settings in the BIOS for alarms on CPU temperature as well as fan speed.

Check the bios to see what these are set for and work from there.

---

### Post by mortalkorona on 2021-05-16
I think I know what's causing these _Long continuous beeping alarms_. It's my HBA expansion card for my 18x HDD disks home server build.

**ADAPTEC - RAID Adaptec 71605 16-Ports SAS/SATA RAID Controller**
[https://www.amazon.com/ADAPTEC-16-Ports-Controller-Plug-Supported/dp/B00BEY17NK](https://www.amazon.com/ADAPTEC-16-Ports-Controller-Plug-Supported/dp/B00BEY17NK)

I got this hint from someone, but don't really know what it means for my home server since I only have one HDD disk connected to the RAID card. I just disabled my RAID card alarm from my BIOS menu, didn't know that I could do that before I learnt about it. I will have to monitor today if that alarm comes back again like before.

> Raid cards beep on raid degrade

---

### Post by CharlesA on 2021-05-16
> **mortalkorona said:**
> I think I know what's causing these _Long continuous beeping alarms_. It's my HBA expansion card for my 18x HDD disks home server build.

**ADAPTEC - RAID Adaptec 71605 16-Ports SAS/SATA RAID Controller**
[https://www.amazon.com/ADAPTEC-16-Ports-Controller-Plug-Supported/dp/B00BEY17NK](https://www.amazon.com/ADAPTEC-16-Ports-Controller-Plug-Supported/dp/B00BEY17NK)

I got this hint from someone, but don't really know what it means for my home server since I only have one HDD disk connected to the RAID card. I just disabled my RAID card alarm from my BIOS menu, didn't know that I could do that before I learnt about it. I will have to monitor today if that alarm comes back again like before.


Whether the card triggers an alarm if a drive has failed depends on how it's set up, and it's usually a toggle in the card's BIOS or management software.

Do you only have 1 drive populated on this card, or are you running 16 drives on it? It looks to be a true RAID card, rather than an HBA since it's got onboard cache, but if you haven't configured the drive on the card, it might just be passing it through to the OS.

The next time the alarm sounds, take the panel off the server and try to figure out where it's coming from. That will tell you what you should focus on.

---

### Post by mortalkorona on 2021-05-17
> **CharlesA said:**
> 
Do you only have 1 drive populated on this card, or are you running 16 drives on it? It looks to be a true RAID card, rather than an HBA since it's got onboard cache, but if you haven't configured the drive on the card, it might just be passing it through to the OS.


Hey @CharlesA I disabled my RAID card alarm from my BIOS menu. And ran my server doing nothing for 8 hours yesterday without any annoying alarms so things are looking good.

Today I will try to run my Chia plotting-calculations to see if the heightened burden will make my server create smoke and fire.

.....................................................................

I only have 1 HDD drive connected to this HBA RAID card. With the plan to expand it to 18 drives in the future when my wallet allows for it. Here's a better link description of what hardware I have bought with better screenshots.

**Adaptec ASR 71605 1GB 16Port HBA RAID PCIe Controller Card w/ Battery 4x Cables**
[https://www.ebay.com/itm/Adaptec-ASR-71605-1GB-16Port-HBA-RAID-PCIe-Controller-Card-w-Battery-4x-Cables/353020685999](https://www.ebay.com/itm/Adaptec-ASR-71605-1GB-16Port-HBA-RAID-PCIe-Controller-Card-w-Battery-4x-Cables/353020685999)

I got a tip from another thread that I posted in with manuals I can read for better understanding.
[https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-71605/](https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-71605/)

.....................................................................

This is the YouTube build tutorial I'm roughly following using very similar hardware.

YouTuber: Coin Breakthrough, Caleb Curry
** COMPLETE Build for Chia Farming (360TB Capacity Hard Drive Mining)** - TimeIndex 31 minutes
[https://youtu.be/BQ6zM1izXQs?t=1861](https://youtu.be/BQ6zM1izXQs?t=1861)

.....................................................................

.

---

### Post by LHammonds on 2021-05-17
> **mortalkorona said:**
> I only have 1 HDD drive connected to this HBA RAID card. With the plan to expand it to 18 drives in the future when my wallet allows for it. 
Since you are using hardware RAID, think about what happens when the RAID card itself fails.  The only way you can fix access to your data (unless you have backups outside the RAID) is another RAID card "just like the one you have now"

I would have a 2nd RAID card on-hand at the exact same firmware revision level and make sure you can swap it for a dead card...at least practice one time.

LHammonds

---

### Post by CharlesA on 2021-05-17
> **mortalkorona said:**
> Hey @CharlesA I disabled my RAID card alarm from my BIOS menu. And ran my server doing nothing for 8 hours yesterday without any annoying alarms so things are looking good.

Today I will try to run my Chia plotting-calculations to see if the heightened burden will make my server create smoke and fire.


Good luck! It still sounds strange that it would trigger an alarm with only one drive.


> **LHammonds said:**
> Since you are using hardware RAID, think about what happens when the RAID card itself fails.  The only way you can fix access to your data (unless you have backups outside the RAID) is another RAID card "just like the one you have now"

I would have a 2nd RAID card on-hand at the exact same firmware revision level and make sure you can swap it for a dead card...at least practice one time.

LHammonds

Agreed. I had to do the same when My LSI 9260-8i took a dump on me. I could have restored from backups, but both methods would have taken about the same amount of time since I had to order a replacement card.

That was many years ago - I moved to mdadm after I had the second card fry on me (probably due to overheating, or other issues) with a regular HBA card that doesn't do RAID.

Nowaways I've been running ZFS with RAIDZ2 and I've been happy with it. It's more complicated than mdadm or hardware raid.

---

### Post by mortalkorona on 2021-05-18
> **LHammonds said:**
> Since you are using hardware RAID, think about what happens when the RAID card itself fails.  The only way you can fix access to your data (unless you have backups outside the RAID) is another RAID card "just like the one you have now"

I would have a 2nd RAID card on-hand at the exact same firmware revision level and make sure you can swap it for a dead card...at least practice one time.

LHammonds
Good thinking!

......................................................

> **CharlesA said:**
> Good luck! It still sounds strange that it would trigger an alarm with only one drive.
Second day of high load observation of my server went well too.

Not having read all the Adaptec 71605 HBA RAID manuals yet. My guess why I could run my server 24/7 for 5 days of **Chia plotting** (blockchain calculations) without any sound alarms. Is that my 1 HDD disk reached around 13TB of the available 16TB on the 6th day so the RAID card sounded the alarm every time I rebooted the server.

......................................................

**@LHammonds, @CharlesA**
If my HBA RAID card self-destructs, will I be able to physically move my 1 HDD disk to a NAS or a JBOD machine and still access the data in my HDD disk?

I might consider expanding my Chia mom & pop operation and purchase an enterprise grade rack and put it in my small apartment to house all the HDD disks that I fill up. Since according to the Chia Network team **plotting** (blockchain calculations) and **farming** (blockchain sharing) should be done on 2 separate machines and not all in one if I want 24/7/365 uptime with my operation.

......................................................

.

---

### Post by LHammonds on 2021-05-18
> **mortalkorona said:**
> 
**@LHammonds, @CharlesA**
If my HBA RAID card self-destructs, will I be able to physically move my 1 HDD disk to a NAS or a JBOD machine and still access the data in my HDD disk?

My understanding of RAID may be dated but from what I know, ONLY software RAID is capable of being portable to different hardware.  When using hardware RAID, you are bound to that RAID hardware so taking a RAID'd HD from that machine and sticking it into something else will require re-formatting the disk and losing whatever data is on it.

References:
* [JBOD vs RAID - Differences](https://www.trentonsystems.com/blog/jbod-vs-raid-what-are-the-differences)
* [Adaptec RAID 71605](https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-71605/) (noticed Ubuntu support up to 14 but did mention driver source code)

LHammonds

---

### Post by CharlesA on 2021-05-18
> **mortalkorona said:**
> 
**@LHammonds, @CharlesA**
If my HBA RAID card self-destructs, will I be able to physically move my 1 HDD disk to a NAS or a JBOD machine and still access the data in my HDD disk?

I might consider expanding my Chia mom & pop operation and purchase an enterprise grade rack and put it in my small apartment to house all the HDD disks that I fill up. Since according to the Chia Network team **plotting** (blockchain calculations) and **farming** (blockchain sharing) should be done on 2 separate machines and not all in one if I want 24/7/365 uptime with my operation.

......................................................

.

It depends on the implimentation. Normally, if it's a hardware RAID card and you use another one from the same vendor or the same family, it *might* work, but it also might not work.

With that said, there are some implementations of intel fakeraid (which is just a crappy version of software RAID) that mdadm can read, but I wouldn't count on that happening for most hardware RAID cards.

That's also another reason why I moved off of hardware RAID - when I bought my LSI 9260-8i, it cost me about 200 dollars. The replacement was about the same cost.. three or four years later.

Now I'm using pure HBA cards (LSI 9201-8i), which are dirt cheap and adding an SAS expander ([HP 32-port SAS]("https://forums.servethehome.com/index.php?threads/hp-sas-expander-wiki.146/")) if I need it. I'm only running 8 drives currently, but I've had up to 16 connected when I was moving data to a new array. I like the fact that I can move a mdadm or ZFS array to new hardware without having to also keep the RAID card/HBA the same. That means I can go buy any HBA off ebay or whatever and be back up and running instead of having to search for a specific card and pay out the nose for it because it's a "RAID card."

Now with all that said - My server sucks down about 200-300W depending on load with the 3 SSDs, and 8 + 3 hard drives. It's nowhere near energy efficient, but I just have to deal with it. Please keep the cost of energy in mind before you go all out with Chia farming.

> **LHammonds said:**
> My understanding of RAID may be dated but from what I know, ONLY software RAID is capable of being portable to different hardware.  When using hardware RAID, you are bound to that RAID hardware so taking a RAID'd HD from that machine and sticking it into something else will require re-formatting the disk and losing whatever data is on it.

References:
* [JBOD vs RAID - Differences](https://www.trentonsystems.com/blog/jbod-vs-raid-what-are-the-differences)
* [Adaptec RAID 71605](https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-71605/) (noticed Ubuntu support up to 14 but did mention driver source code)

LHammonds

I don't really have much to add to this, but I just wanted to say that both links are pretty good.

This is also a good article - it's oldish.. but still valid:
[https://www.servethehome.com/difference-hardware-raid-hbas-software-raid/](https://www.servethehome.com/difference-hardware-raid-hbas-software-raid/)

Serve The Home has a ton of good info and reviews of different hardware too.

---

