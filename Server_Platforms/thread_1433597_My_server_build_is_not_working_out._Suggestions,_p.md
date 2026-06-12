---
title: "My server build is not working out. Suggestions, please?"
date: 2010-03-19
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-19
I started building my server with the following goals:
[LIST=1]
[*]Quiet - it will live in a cabinet in my living room, so it should be as quiet as possible
[*]Low power consumption - not just to keep the heat (ergo cooling demands, ergo noise) down, but also to save money since it will be on 24/7
[*]High reliability
[*]Support for 8 IDE and 2 SATA drives. (Toward this end, I have two 2-port IDE PCI controller cards and one 2-port SATA IDE controller card.)
[*]Spend as little as possible. (Money is VERY tight for me right now.)
[/LIST]

I started with a mini-itx board I had lying around. It's fanless, with a Via Epia 700MHz CPU in it. A little anemic, but it draws very little power and is dead silent. ***The problem*** with this board is that it has 2 IDE ports on board, no SATA ports, and only one PCI slot, so I have to choose between my SATA card and my IDE card. I need - but can't have - both. I tried buying a 2-slot PCI riser card, but apparently it's incompatible (or DOA) - none of my PCI cards work when connected via this riser card. 

I've looked for PCI cards that have 2 x IDE + 2 x SATA ports, but anything that fits that bill is very expensive.

Now I'm thinking new motherboard & CPU - preferably something older that can be had cheaply on ebay. If it uses DDR memory (rather than DDR2), I can use the RAM I have, which saves me $25. A newer Atom-based board would be OK, but they all seem to have one PCI slot -- and not enough IDE/SATA ports to get the job done with just one PCI slot.

If you can recommend a motherboard that meets all the criteria above, please post it. (Or, if you have any other ideas for handling this very cheaply, let's hear it!)

Thanks for your time and consideration! :)

---

### Post by jrssystemsnet on 2010-03-19
Not what you want to hear, but these:

> # Low power consumption
# High reliability
# Support for 8 IDE and 2 SATA drives.

just don't go together.  You also REALLY don't want to have a ton of IDE hard drives operating Master/Slave on the same channels; that causes both performance AND reliability problems in the long run.

Maybe instead you should tell us why you need 10 drives connected to this thing, and we could see if we could find a cheap way around THAT.

---

### Post by Dayofswords on 2010-03-19
yes, tell us your needs


also, cabinet, unless there is a hole, your going to need ventilation

---

### Post by tgalati4 on 2010-03-19
Agreed.  Create a USB or Live CD boot disk, put in the largest IDE drives you can find.  Get a 4-port SATA pci card and populate with "green" drives.  Check your power supply-it's probably 60 watts max.

---

### Post by spynappels on 2010-03-19
In previous threads the OP said he wanted to use drives he already had to build his server hence the mixture of IDE and SATA. 

I have to agree though that 2 or 4 decent sized SATA drives on a SATA PCI card would be better, especially if you want to RAID them as per the other thread.

Couple this with a USB boot device on an internal MOBO header and you'd have a decent fileserver, which I think you were trying to build? Might get away with a relatively low power box too then.

---

### Post by sv87411 on 2010-03-19
I doesn't keep the cost down, but to satisfy the drive mix and single PCI slot you could always use IDE to SATA converters. 

I've struggled trying to build servers from old kit that I have, but ultimately you have to compromise somewhere - especially with old IDE drives. It is annoying to have to shelve large capacity IDEs that still have some life in them.

I tend to agree with jrssystemsnet though that your requirements are contradictory - low power/cost plus 10 drives just doesn't add up.

Edit: And 10 drives won't be very quiet or cool either.

---

### Post by jrssystemsnet on 2010-03-19
> **spynappels said:**
> In previous threads the OP said he wanted to use drives he already had to build his server hence the mixture of IDE and SATA.

Yeah, I pretty much figured that, I just wanted to hear it for sure from the OP.

The thing is, to meet the stated goals - low power consumption, reliability, and low cost - it almost certainly makes more sense to chuck the random collection of aging drives and just go get one or two 2TB Western Digital green drives.

At newegg right now 1TB WD drives go for $80, 1.5 TB WD drives for $110, and 2TB WD drives for $160.  While he hasn't explicitly stated the total capacity of the drives, I'd bet that his 8 IDE drives put together don't add up to 2TB... and they might very well not even add up to 1TB.

OP's already said he's willing to buy a new motherboard, which certainly puts him in the same price range as a 1TB drive... and once you realize he's almost certainly going to need $70 or more for a beefy enough power supply to reliably power all those drives, you're firmly into "buy a 2TB drive" territory without spending a single dime more.

There's just no way that the motley collection of ancient drives is a good idea, even *with* the understanding that budget is limited.

---

### Post by Donny Bahama on 2010-03-19
Thanks for the responses, everyone. I'll respond to your comments and suggestions in a moment, but first let me clarify a few things...

1. PSU is a 550W ThermalTake, purchased with reliability and number of drive connectors (8 x IDE and 4 x SATA) in mind
2. Case is a rack-mount server case with 3 fans and excellent flow-through ventilation.  Case fans aren't loud at all. Even with all 3 fans running, the drives are louder than the fans (with the top panel off).  
3. Drive racks all use vibration isolators. With the top on, it's extremely quiet. When it's in my cabinet with the doors closed (cabinet is open-backed) it's nearly inaudible.

---

### Post by Donny Bahama on 2010-03-19
I should also clarify that when I say, "low power consumption", I mean "as much as possible for a computer with 10 drives!"

---

### Post by bpalone on 2010-03-19
Do you really need all the capacity of the ten HDs? 

As for you MB delima, how about checking the local goodwills, etc. to find an old computer for a few sheckles?  If it works, it could very well serve your needs and be cheap.  Just a thought.

The ten HDs makes it tough for figuring a cheap solution.

Good luck.

---

### Post by Donny Bahama on 2010-03-19
> **jrssystemsnet said:**
> You also REALLY don't want to have a ton of IDE hard drives operating Master/Slave on the same channels; that causes both performance AND reliability problems in the long run.I suppose I could use IDE-to-SATA converters to circumvent this, but it seems to me that this adds complexity and additional failure points. Master/slave configuration seems the lesser of the two evils to me.
> Maybe instead you should tell us why you need 10 drives connected to this thing, and we could see if we could find a cheap way around THAT.Because I *have* 10 drives and I want as much capacity as I can get. This project has three primary goals:
[list=1][*]Serve music, photos and movies to my (XBMC) HTPC over the LAN. (I own over 400 DVDs, a few dozen Blu-Rays, and 800+ CDs. I want on-demand access to as many of them as possible.)
[*]Automated backup system for three other PCs in the house.
[*]Teach myself about building, maintaining and administering a GNU/Linux server.[/list]
> **Dayofswords said:**
> also, cabinet, unless there is a hole, your going to need ventilationEntire back is open.
> **tgalati4 said:**
> Agreed.  Create a USB or Live CD boot diskWhy do this instead of having a boot drive? With a boot drive, I can not only boot and run the system, but also use the leftover space for additional media storage.
> Get a 4-port SATA pci card and populate with "green" drives.I wish I could afford to do that, but I can't.
> Check your power supply-it's probably 60 watts max.LOL!
> **spynappels said:**
> In previous threads the OP said he wanted to use drives he already had to build his server hence the mixture of IDE and SATA. 

I have to agree though that 2 or 4 decent sized SATA drives on a SATA PCI card would be better, especially if you want to RAID them as per the other thread.In my OP, I said that money is *really* tight. By that I mean I have no regular, steady income, no health insurance, and a wife with a significant health condition. Most months, I wonder if I'm going to be able to pay the basic bills and still have enough left for prescriptions and food.

[COLOR="Red"]**Please, people, understand that buying 1 or more large SATA drives is not an option for me.**
[/COLOR]
> **sv87411 said:**
> I've struggled trying to build servers from old kit that I have, but ultimately you have to compromise somewhere - especially with old IDE drives. It is annoying to have to shelve large capacity IDEs that still have some life in them.It will be *annoying* when they die and I have to re-rip all the media they store. Until then, though, I can't afford to replace them, so I won't be shelving them. I'll live with the power consumption issues for now.
> **jrssystemsnet said:**
> While he hasn't explicitly stated the total capacity of the drives, I'd bet that his 8 IDE drives put together don't add up to 2TB... and they might very well not even add up to 1TB.Here's how the drives are configured...[list]
[*]6 x 300GB IDE (For RAID5 array)
[*]1 x 1.5TB SATA (JBOD. Purchased with gift money.)
[*]1 x 250MB SATA (JBOD)
[*]1 x 120MB IDE (boot drive)
[*]1 x DVD-ROM (USB doesn't always boot, but a CD always seems to work.)[/list]
> OP's already said he's willing to buy a new motherboard, which certainly puts him in the same price range as a 1TB drive...
No, I'm talking about something older, that I can get off ebay for $40 or so.
> and once you realize he's almost certainly going to need $70 or more for a beefy enough power supply to reliably power all those drives, you're firmly into "buy a 2TB drive" territory without spending a single dime more.But I already *have* the beefy PSU.
> There's just no way that the motley collection of ancient drives is a good idea, even *with* the understanding that budget is limited.OK, it's a bad idea, then. I'm sure that in time, my financial situation will improve. (Significantly, and probably soon.) Until, then, though, this is what it is and I have to operate within the financial constraints I have right now.

One other note... of the 6 300GB drives, the lone Maxtor of the bunch is reporting 200+ relocated sectors. For now, I'll probably use it in JBOD mode and run a 5 x 300GB 1.2TB array with the remaining (rock solid) Seagate 7200.7 drives. 

It occurs to me, though, that if I take the failing Maxtor out of the equation, a single 1.5TB SATA drive could replace my entire array + the 250GB SATA drive. (But then I'd have no RAID array and wouldn't get to learn about setting up and maintaining one.)


Thank you all for your input. :)

---

### Post by Donny Bahama on 2010-03-19
> **bpalone said:**
> Do you really need all the capacity of the ten HDs?Need? No. Want? Yes. :)
> As for you MB delima, how about checking the local goodwills, etc. to find an old computer for a few sheckles?  If it works, it could very well serve your needs and be cheap.  Just a thought.I actually have such a machine. I was planning to sell it on Craigslist to reimburse the household budget for all the nickel-and-dime expenses of building my HTPC and server.

The fan on that motherboard is louder than anything on my server, and even though it's old, it draws a lot more power than the Via-based mini-itx board currently in the server.

In general, though, this is exactly what I had in mind. I was hoping someone would come along and say, *"See if you can find a [brand] motherboard with a [model] CPU. I have one that's underclocked to [spec] and it runs fanless and draws very little power."* As long as such a recommendation has at least 3 PCI slots, I could support all my existing drives.

---

### Post by bpalone on 2010-03-19
> I actually have such a machine. I was planning to sell it on Craigslist to reimburse the household budget for all the nickel-and-dime expenses of building my HTPC and server.

The fan on that motherboard is louder than anything on my server, and even though it's old, it draws a lot more power than the Via-based mini-itx board currently in the server.

Have you thought of changing the fan on the MB?  Or getting creative with some home made ducting to use a larger slower fan (less noise) mounted off the MB?  Just thinking out loud, I know it doesn't cut the power consumption but you have it.

---

### Post by tgalati4 on 2010-03-19
Booting off of USB allows you to remove the CDROM drive.  That frees up an IDE port for another drive.  Yes, you can always partition one of the hard drives to hold a boot partition.  But if you want energy savings, having the entire operating system run in RAM will allow the disks to spin down more often.

---

### Post by jrssystemsnet on 2010-03-19
> **Donny Bahama said:**
> [list]
[*]6 x 300GB IDE (For RAID5 array)
[*]1 x 1.5TB SATA (JBOD. Purchased with gift money.)
[*]1 x 250MB SATA (JBOD)
[*]1 x 120MB IDE (boot drive)
[*]1 x DVD-ROM (USB doesn't always boot, but a CD always seems to work.)[/list]

Try to craigslist, ebay, overclockers.com, or whatever your random collection of old drives.  If you can get $110 out of the lot (and you probably can, particularly if you get any bites on craigslist), you just got yourself another 1.5TB SATA drive for free.

To move them fairly quickly, I'd try getting $20 a drive for the 120GB, 250GB and 300GB drives.  It's a fair cop - you could probably get a little more, if you weren't in a hurry, but hey, you want to do this soon right?  At the end of it, you'll be in MUCH better shape with 2 1.5TB SATA drives that you can JBOD or RAID0 together, and you'll have just as much storage as you would have with your motley collection of older stuff, with probably a tenth of the power consumption, FAR better reliability, FAR better performance, MUCH quieter...

---

### Post by Donny Bahama on 2010-03-19
> **tgalati4 said:**
> Booting off of USB allows you to remove the CDROM drive.  That frees up an IDE port for another drive.  Yes, you can always partition one of the hard drives to hold a boot partition.  But if you want energy savings, having the entire operating system run in RAM will allow the disks to spin down more often.Makes sense. I think I'll do this. The only part I'm not sure about is losing the CD-ROM drive. Booting from flash drives has been less than reliable for me. (Could just be this motherboard/BIOS, though - I find that it won't boot from the CD unless I go into BIOS and temporarily disable all other boot devices. Come to think of it, maybe that would have resolved my USB boot troubles... In any case, I'm inlined to keep the CD drive.)

---

### Post by Donny Bahama on 2010-03-19
> **jrssystemsnet said:**
> Try to craigslist, ebay, overclockers.com, or whatever your random collection of old drives.  If you can get $110 out of the lot (and you probably can, particularly if you get any bites on craigslist), you just got yourself another 1.5TB SATA drive for free.

To move them fairly quickly, I'd try getting $20 a drive for the 120GB, 250GB and 300GB drives.  It's a fair cop - you could probably get a little more, if you weren't in a hurry, but hey, you want to do this soon right?  At the end of it, you'll be in MUCH better shape with 2 1.5TB SATA drives that you can JBOD or RAID0 together, and you'll have just as much storage as you would have with your motley collection of older stuff, with probably a tenth of the power consumption, FAR better reliability, FAR better performance, MUCH quieter...Your logic is persuasive, but...

1. I really do want to learn to work with RAID arrays, and I can't afford to go RAID0 and give up all that capacity, so I'd need three of these drives at a minimum.
2. My Seagate 300GB IDE drives have always been rock-solid reliable, but when it comes to TB drives, I've heard a lot of nightmare stories about drives failing after a few months (or less!) In fact, my first one started failing within the first few weeks! I just wouldn't be comfortable going with big drives unless they were in a RAID array.

I think for now, I'm going to live with my motley crew of drives, play around with RAID5 on the 5 x 300GB Seagate drives, and use an SATA to IDE adapter on the 1.5TB drive. Later, when I can afford at least a couple more 1.5TB drives, I'll get a 4-port SATA PCI card and replace all the IDE drives at that time. (Maybe then I'll sell them and use the proceeds to buy a 4th TB drive.)

---

### Post by jrssystemsnet on 2010-03-19
I've had about thirty WD 1TB drives in the field for over a year now, spread out over quite a few machines in quite a few environments, some in big RAID arrays, some deployed as single drives.  No problems.

RAID0 doesn't give up any capacity, RAID0 gives up *redundancy* - RAID0 is striping without parity.  2 1.5 TB drives in a RAID0 = 3TB capacity.  Which I wouldn't normally recommend to anybody, but you've made it pretty clear that budget is "low as possible", capacity is "as much as possible", and you really aren't *that* concerned about reliability, when it comes right down to it.

And 2 1.5TB WD drives in a RAID0 almost certainly still have a MUCH lower mtbf than your 10-drive motley crew.

I'd advise you to stay the heck away from Seagate at this point; the Barracuda line was great back in the 80GB to 160GB days, but everything they've made including and since the 200GB drives has sucked BADLY for both performance and reliability.

---

### Post by Donny Bahama on 2010-03-19
> **jrssystemsnet said:**
> I've had about thirty WD 1TB drives in the field for over a year now, spread out over quite a few machines in quite a few environments, some in big RAID arrays, some deployed as single drives.  No problems.Wow. Really good to know!
> RAID0 doesn't give up any capacity, RAID0 gives up *redundancy* - RAID0 is striping without parity.OK. My bad. I don't normally pay much attention to anything except RAID5. So what's the point of having a RAID if there's no redundancy?! (And technically, wouldn't that make it an AID? ;))
> 2 1.5 TB drives in a RAID0 = 3TB capacity.  Which I wouldn't normally recommend to anybody, but you've made it pretty clear that budget is "low as possible", capacity is "as much as possible", and you really aren't *that* concerned about reliability, when it comes right down to it.But see, I kind of am. For the media, no big deal. I own the discs and can always re-rip. But I /was/ planning to use this as a backup system, too, so having no redundancy concerns me.
> I'd advise you to stay the heck away from Seagate at this point; the Barracuda line was great back in the 80GB to 160GB days, but everything they've made including and since the 200GB drives has sucked BADLY for both performance and reliability.Wow. I didn't know that. I've had excellent luck with 200 and 300GB Seagate drives. This complicates things even further, because my lone 1.5TB drive is a Seagate. :cry:

---

### Post by jrssystemsnet on 2010-03-19
> **Donny Bahama said:**
> Wow. Really good to know!
OK. My bad. I don't normally pay much attention to anything except RAID5. So what's the point of having a RAID if there's no redundancy?!Concatenation of capacity into a single filesystem, and performance boost.

> But see, I kind of am (concerned with reliability).

Well, you're going about it the wrong way - the odds of you losing data to a 10-drive array of odds and sods that are largely five years or more old is VERY high, parity or no parity.

RAID5 will - maybe - protect you from a *single* drive that *completely fails all at once*.  RAID5 will *not* protect you from *corruption* on even a single drive, much less multiple drives - it will know that there was a parity failure if you read a file that spans across corrupted blocks, but it has no way of knowing *which* blocks were corrupted, and therefore has no way of reconstructing from parity and giving you the real data, even if the corruption *was* only on a single member.  It won't have any way of knowing which member the corruption was on - heck, it could even have *been* the parity blocks themselves that got corrupted... who knows?

You can lose an entire filesystem all at once if this happens to exactly the wrong blocks on the RAID5.  And guess what... most drive failures *don't* consist of "work absolutely great until one moment you suddenly don't work at all, whatsoever".  ESPECIALLY on consumer gear.  Most drive failures - especially on elderly Seagates - manifest as "whoops, here are some bad blocks... now here are some MORE bad blocks... well, crap, now here's some blocks that confuse my controller so badly that it locks up entirely until you reboot the system.  But hey, then I'll keep working again until... well, until you try to read that block again."

RAID5 isn't going to help with that.

And you want to spread your data out across a LOT of these elderly drives... not good.

Sorry, I don't wanna rain on your parade, and learning about RAID is great, and Linux mdraid is really nice but... even a 2-disk RAID0 of *new* drives is going to be a LOT more reliable than your proposed setup. :)

---

### Post by Donny Bahama on 2010-03-19
> **jrssystemsnet said:**
> Sorry, I don't wanna rain on your paradeThat's OK! I may be getting wet, but I'm learning A LOT. Thank you so much for your time and knowledge.

I assume the same holds true for RAID1?

Do you avoid RAID5, then? Or does it have its place given the right circumstances?

---

### Post by Donny Bahama on 2010-03-19
> **jrssystemsnet said:**
> RAID5 isn't going to help with that.If not RAID5, then what? If I'm going to 86 my motley crew and add a 2nd 1.5TB drive -- given that my existing TB drive is a Seagate, what measures can I take to guard against data loss? (Besides regularly backing up to hundreds of DVD-Rs?)

---

### Post by jrssystemsnet on 2010-03-20
> **Donny Bahama said:**
> I assume the same holds true for RAID1?

Yep... if you get corrupt data on blocks on a RAID1 array, the system will usually know that it *is* corrupt - because the data on the corresponding blocks on the other member is different - but it really has no way of knowing which one is *right*.  In real-world practice, the controller will all too frequently keep kicking out the GOOD drive, and leaving the BAD drive in the array... and also all too frequently, it will immediately add the good drive back into the array *and synch it with the bad drive*, thus ensuring that your data is screwed up before you ever get the chance to look at it and try to figure out for yourself which drive was actually failing.

> Do you avoid RAID5, then? Or does it have its place given the right circumstances?

RAID5 has its place.  When you need a relatively efficient (in terms of total capacity : usable capacity) storage volume larger than a single disk can provide, RAID5 is your go-to from the traditional RAID types.  You just have to remember, "RAID is not backup", and understand that there are more than a few potential drawbacks - read performance and *large* write performance will generally be enhanced, and the parity blocks give you protection against losing the entire array due to a single drive's *complete failure*... but you may see not only no performance boost, but even a significant performance DROP in small random writes (because it has to do a "read-modify-write" fandango), you aren't protected against data corruption at all, and something called the "RAID5 write hole" (google it) can hurt you bad in the event of a power failure.

When performance and redundancy is more important than storage efficiency, you usually want RAID10: a stripe of mirrors.  You get much better performance, you don't have read-modify-rewrite problems, you can lose more drives before the array goes down entirely... but you get about half the total storage for the same number of drives, and you still aren't protected against data corruption.

If you really want the most protection for your data that an array can provide, you have to leave the Linux world and head into FreeBSD or Solaris, where they've got ZFS.  ZFS has its own array type called RAIDZ, which is basically a RAID5 with a variable stripe width, and parity checksums *on each individual member* as well as on the stripe as a whole.  This means that in the event of data corruption, as long as the corruption only occurs on a single member for that stripe, ZFS will not only be able to detect the corruption, but detect *which member* had the corruption, AND reconstruct the data correctly from the parity member for that stripe.  (If two or more members have corruption on a single stripe, of course, ZFS will know about it but won't have any way of reconstructing the data.)

This is, in a single word, FREAKING AWESOME, and it's why I run some FreeBSD servers where I need very large arrays with very low tolerance for data problems.  I've actually tested the "data healing" by dropping the array, booting into single user mode, and hex editing the data on a single member... and just like it says on the tin, when I booted the system back up and read the file, ZFS immediately caught the error, silently fixed it and handed me the correct data, and wrote an entry in the logs warning me that the member whose data I'd hex-edited had a corrupt block.

Unfortunately, you're not going to get ZFS on Linux, because Sun's CDDL license is incompatible with the Linux kernel's GPL license.  Boo.  So, right now, we're hoping that BTRFS will incorporate this (and more) of the features ZFS has and nothing else does, whenever BTRFS finally gets finished and released... but that'll be quite a few years from now.

---

### Post by jrssystemsnet on 2010-03-20
> **Donny Bahama said:**
> If not RAID5, then what? If I'm going to 86 my motley crew and add a 2nd 1.5TB drive -- given that my existing TB drive is a Seagate, what measures can I take to guard against data loss? (Besides regularly backing up to hundreds of DVD-Rs?)You need more backup storage space than you have "live" storage space, if you really care about your data - unpleasant fact, but true.  Practically speaking, these days, that generally means more hard drives.  (I have a 5TB RAIDZ on a server that acts as a dedicated backup server for my network, which has about 2TB of "live" capacity all told.)

Unpleasant, I know.

Which is why the vast, vast majority of people (and far too many businesses!) just don't back up at all.

---

### Post by brian mcgee on 2010-03-20
> **Donny Bahama said:**
> If not RAID5, then what? If I'm going to 86 my motley crew and add a 2nd 1.5TB drive -- given that my existing TB drive is a Seagate, what measures can I take to guard against data loss? (Besides regularly backing up to hundreds of DVD-Rs?)

Yeah, RAID is definitely not a substitute for good backups. Personally, I'd buy more disks if I had to, or reuse existing disks. DVD-Rs would be a pain. 

Maybe ditch RAID altogether. I know you want high availability, but sometimes an hour of downtime is worth it for good backups... In other words, instead of using a disk for parity in a RAID array, maybe use it for backups and forget RAID... also, did I see JBOD and RAID0? I would recommend against both!

---

### Post by Donny Bahama on 2010-03-20
> **jrssystemsnet said:**
> ZFS has its own array type called RAIDZ, which is basically a RAID5 with a variable stripe width, and parity checksums *on each individual member* as well as on the stripe as a whole.  This means that in the event of data corruption, as long as the corruption only occurs on a single member for that stripe, ZFS will not only be able to detect the corruption, but detect *which member* had the corruption, AND reconstruct the data correctly from the parity member for that stripe.  (If two or more members have corruption on a single stripe, of course, ZFS will know about it but won't have any way of reconstructing the data.)

This is, in a single word, FREAKING AWESOME, and it's why I run some FreeBSD servers where I need very large arrays with very low tolerance for data problems.  I've actually tested the "data healing" by dropping the array, booting into single user mode, and hex editing the data on a single member... and just like it says on the tin, when I booted the system back up and read the file, ZFS immediately caught the error, silently fixed it and handed me the correct data, and wrote an entry in the logs warning me that the member whose data I'd hex-edited had a corrupt block.Very cool. This must be the safety net below DropBox, Mozy, CrashPlan, etc.

Is there something along the lines of FreeNAS or OpenFiler, etc. that offers RAIDZ support - but makes it easy for hobbyists?

---

### Post by Donny Bahama on 2010-03-20
> **brian mcgee said:**
> Maybe ditch RAID altogether.
. . .
also, did I see JBOD and RAID0? I would recommend against both!No RAID *and* no JBOD? Um, what exactly does that leave me?!

---

### Post by jrssystemsnet on 2010-03-20
> **Donny Bahama said:**
> Very cool. This must be the safety net below DropBox, Mozy, CrashPlan, etc. Probably not - the really big sites and orgs are generally using purpose built SANs which offer much of the same functionality, but at several orders of magnitude higher cost.

> Is there something along the lines of FreeNAS or OpenFiler, etc. that offers RAIDZ support - but makes it easy for hobbyists?Ah, I'm not really sure - but honestly, it's not THAT hard to use FreeBSD; and ZFS itself is ridiculously simple.  Basically you just need to do things the same way you would with Ubuntu Server - ie operate from the shell, install Samba and whatever else from repositories, then go about your business.

The biggest pain in using FreeBSD vs Ubuntu *as a server* is that FreeBSD's binary package management system is frankly inferior to Ubuntu's in every conceivable way; in some consolation, FreeBSD has a "ports" system that makes compiling software from source RIDICULOUSLY easy, and in most cases, that's what you use rather than ports.  Which isn't that big a deal; installing software from ports means "cd /usr/ports/net/samba && make install clean" rather than "apt-get install samba"... but installing *updates and upgrades* is more of a pain, and compiling the software takes some time when you actually do it.

I like FreeBSD a lot, and I've been using it a lot longer than Ubuntu, but if it weren't for ZFS, I wouldn't have any reason to keep up with it.  But, there *is* ZFS... so I have to pick and choose what I need more in any given case, ZFS's filesystem features, or Ubuntu's package management.

---

### Post by jrssystemsnet on 2010-03-20
> **Donny Bahama said:**
> No RAID *and* no JBOD? Um, what exactly does that leave me?!Reading *books*, you impertinent whippersnapper - it was good enough for your dad, and it's good enough for you!

---

### Post by Donny Bahama on 2010-03-20
> **jrssystemsnet said:**
> Reading *books*, you impertinent whippersnapper - it was good enough for your dad, and it's good enough for you!LMAO!!! Classic.

I'll have you know that my Dad was at Intel during the microprocessor's nascence! I still remember him showing me a prototype of the first digital watches.

P.S. I'm probably older than you! :P

---

### Post by Donny Bahama on 2010-03-20
> **jrssystemsnet said:**
> in some consolation, FreeBSD has a "ports" system that makes compiling software from source RIDICULOUSLY easyI wonder if there's an official psychiatric nomenclature for "fear of compiling from source code".

I have C-phobia...

---

### Post by jrssystemsnet on 2010-03-20
> **Donny Bahama said:**
> P.S. I'm probably older than you! :PMaybe, maybe not.  My first computer was a TRS-80 Model I.  With 4K of RAM.  (Yes, *K*.)

---

### Post by jrssystemsnet on 2010-03-20
> **Donny Bahama said:**
> I wonder if there's an official psychiatric nomenclature for "fear of compiling from source code".[compilar](http://en.wiktionary.org/wiki/compilare#Latin)ophobia, presumably. :popcorn:

---

### Post by Donny Bahama on 2010-03-20
> **jrssystemsnet said:**
> Maybe, maybe not.  My first computer was a TRS-80 Model I.  With 4K of RAM.  (Yes, *K*.)You may have me there. [Mine]("http://carlstrom.com/machines/Zx81-timex.jpg") had 16K. (Yes, *K*.) AND a cassette tape drive! :D

---

### Post by jrssystemsnet on 2010-03-20
> **Donny Bahama said:**
> You may have me there. [Mine]("http://carlstrom.com/machines/Zx81-timex.jpg") had 16K. (Yes, *K*.) AND a cassette tape drive! :DUGH, those things *sucked*!  Those were the ones with the chiclet keyboard, and the power supply port that was prone to wiggling just a little bit and immediately power-cycling the machine, right?

My stepdad got one of those things.  He kept it for about a week before his cheap butt gave up, returned it to the store, and spent a little bit more for a TI99-4/A, which of course was still a ludicrous toy but at least was a reasonably *entertaining* toy that wouldn't drive you absolutely insane in under 5 minutes. :)

---

### Post by Donny Bahama on 2010-03-20
> **jrssystemsnet said:**
> UGH, those things *sucked*!  Those were the ones with the chiclet keyboard, and the power supply port that was prone to wiggling just a little bit and immediately power-cycling the machine, right?I don't recall any power cycling issues, but holy cow did that keyboard SUCK! lol!

The strange thing is, I remember having this when I was like, 16... but Wikipedia says they were introduced in 1983. (3 years after I graduated high school.) I don't know how I managed that! Must have the model mixed up or something.

---

### Post by jrssystemsnet on 2010-03-20
> **Donny Bahama said:**
> 1983. (3 years after I graduated high school.)  Looks like you're the old man after all - class of '89, here.

---

### Post by Donny Bahama on 2010-03-20
> **jrssystemsnet said:**
> Looks like you're the old man after all - class of '89, here.Whippersnapper, indeed! ;)

---

