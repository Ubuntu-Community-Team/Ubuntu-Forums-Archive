---
title: "RAID 10 - Advice please?"
date: 2019-02-19
forum: Server Platforms
---

### Post by undefined86 on 2019-02-19
Hi All,

I'm looking for some advice about how best to setup my server (Predominantly going to be used as a next cloud server hosting precious pictures and videos of our little one).  It's my first foray into setting up RAID and I'm concerned there's likely to be a lot that I don't yet know/understand which will probably come back to haunt me when I least expect it.

I love the idea of using RAID to quickly recover from a drive failure but I worry about how I would realistically go about recovering from a drive failure and whether it adds a level of complication that maybe I could do without.

I have 4 x 1TB drives that I planned to use in a RAID 10 (mdadm) setup to give me approx 2GB of useable space.

Right now, I'm torn between two potential setups:

1) RAID 10, with some "extra" partitions on the 1 TB drives for /boot /swap etc[INDENT]- If I later have a problem with the OS, is it possible/easy to perform a clean install of the OS back onto the "extra" partitions, without compromising/risking the data in the RAID?
- Is there any way of including the OS "as part" of the RAID (i.e. to reduce the likely hood that I need to reconfigure the server as a result of a disk failure)? 

[/INDENT]
2) RAID 10 the 4 disks, with the os installed on completely separate 5th (laptop) disk, independent of the RAID setup.[INDENT]- Is there any advantages/disadvantages to this?  I believe that running the OS from a laptop disk might save power, because the larger drives can spin down (I'm not massively concerned about that though).  And it feels simpler and easier to manage (to me anyway).[/INDENT]
[INDENT]- If I completely break the OS, e.g. through a bad upgrade, is my data safe? Presumably I can still get at data via a Ubuntu Live CD/clean reinstall and "assembling" or "building" the array? [/INDENT]

I hope I've given enough information to allow someone to advise.  The majority of documentation/discussion I read online relates to older versions of Ubuntu that don't offer RAID 10, during it's install (in 18.04 it does!).  

I'd appreciate any tips/pointers/warnings/general advice that any one has to offer!

Thanks in Advance

Ian

---

### Post by LHammonds on 2019-02-19
Are you using software for the RAID setup?  Or a RAID hardware controller?  Hopefully you won't be using a [FakeRAID]("https://help.ubuntu.com/community/FakeRaidHowto") hardware controller.

If using a hardware RAID controller, know that if that controller dies, you will need a 2nd (and identical) controller to get access to those drives.

If using software RAID, it can be portable from machine to machine.

If the purpose of using RAID is to ensure the server remains online "when" a drive fails, be sure you have a spare hard drive handy so you can quickly replace it...because performance is affected when a drive is offline and if a 2nd fails beside it in the RAID array, it will go down.  So it is best to correct the failed drive situation ASAP.

Make sure your "precious data" has a backup...preferably to an offsite location or at the very least, different media (another HD in a separate machine or external USB that is not connected except when backing up)

When setting up this system, you most-certainly want to test and document how to handle the outage.  You do NOT want to try and "figure things out" when under pressure.  As soon as you get your OS installed...pull out a drive to simulate a failed drive.  Then replace the drive with a new one and learn how the re-build process works and how long it takes for hardware you have...and document it.  Make sure your documentation for this is printed out and stuck to the side of the machine because storing it "on" the HD would not be a wise idea...especially if you could not get to it.

I have not done bare-metal server installs in quite some time.  I create servers as virtual machines which sit on top of RAID5.  I mainly use RAID5 for everything but have experimented with RAID10 for better write performance but ultimately, the performance gains were not enough to justify the TCO of maintaining different RAID systems and ended up using RAID5 for all servers.

LHammonds

---

### Post by undefined86 on 2019-02-19
Thanks for the response, much appreciated.  Lots in there for me to consider.  

I'm running on a hand me down HP ProLiant Microserver.  I believe it does have built in RAID controller, but I ruled out using it for reasons you mentioned (I might be wrong.

The main purpose for using RAID is to allow me to easily recover from a drive failure.  I don't want to be manually fiddling with backups if I can help it.  

[COLOR=#000080]"If using software RAID, it can be portable from machine to machine."
[/COLOR]That was exactly what I wanted to hear.  I was concerned that underneath the covers something would be "securing" the array and leave me locked out in the event of a broken OS. I think my main concern was with an OS reinstall.  Could I recover from it.  It seems I should be able to!

Re: Backups - I plan to rent some cloud storage to store my backups (I've still to come up with an exact plan for this, so if anyone wants to recommend their favourite provider, I'm all ears)!

I like your suggestion of simulating the various failures - it'll give me the confidence that I can detect and recover the situation.  I think that's my next step!

---

### Post by SeijiSensei on 2019-02-19
I suggest buying an external USB drive for backups.  You can get [4 TB for $100 or so]("https://www.newegg.com/Product/ProductList.aspx?Description=4tb%20external%20hard%20drive&Submit=ENE") these days.

The old adage still applies: RAID is not a substitute for backups.

One alternative is to use one drive for the OS, and put the other three in a RAID 5 array.  You'll still end up with 2 GB of space in the array, and you don't have to deal with allocating space for /boot, /, etc., on the drives that will be in the array.  If you have yet another drive (the "laptop drive"), you could use that instead.  On a server, most all the processes in use are in active memory.  Writing to and from the OS drive isn't that common, mostly things like log entries in /var.

---

### Post by darkod on 2019-02-19
About the OS install and redundancy that you mentioned. The beauty of mdadm is that it works on partition level (not disk).

That allows you to have smaller partition for OS on each disk, regardless what design for the data array you choose.

For example, you can have 32GB partition on each disk (that is enough for OS not holding any major data or databases), and configure raid1 with all 4 partitions for the OS. That way, you OS can survive even 3 disk failures. Of course, your data won't survive that. :) Being on raid10 you would loose part of data if 3 disks fail. But the OS will continue working.

I have a similar but not identical setup. 4 disks, the OS is on raid1 x4 partitions. Then from the large data partitions I have two separate raid1 x2 arrays (two members each) and I use LVM to join them in one big storage space.

---

### Post by undefined86 on 2019-02-20
> **darkod said:**
> About the OS install and redundancy that you mentioned. The beauty of mdadm is that it works on partition level (not disk).


Ah! I hadn't fully appreciated that. So, I can have as many software raids as I like. One of which I can use as for the OS. That sounds like my ideal setup. 

I'll try it out, simulate some failures and if I'm confident I can recover from it, it's a goer! 

Thanks!

---

