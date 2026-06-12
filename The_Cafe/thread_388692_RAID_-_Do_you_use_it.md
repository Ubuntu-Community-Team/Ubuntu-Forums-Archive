---
title: "RAID - Do you use it?"
date: 2007-03-19
forum: The Cafe
---

### Post by ixus_123 on 2007-03-19
I've had my trusty PC for 3 years now & think I shall treat myself to an complete upgrade.

I plan to get one of the new Nvidia 680 chipset mother boards & a cheap core 2 duo to tide me over until next year when the quad cores are cheaper.

This mobo chipset supports RAID5 which is something I've wanted for a while.

I plan to have a 3 x 500gb array using either Western Digital or Seagate drives all the same make & model.

I plan to buy spares too but was wondering for those of you out there that use raid & keep spares, how many spares do you keep?

I'm thinking about getting 2 bringing up the drive total to 5 but would welcome any tips / advice / experience you have.

I'd also like to hear if you use RAID & what your setup is like.

---

### Post by slimdog360 on 2007-03-19
what are you going to do with 1.5 Terabytes of room?

---

### Post by mysticrider92 on 2007-03-19
Unless you are building a server, there is pretty much no reason to have three 500 gb drives in RAID 5. That capacity and safety is a bit over the top. Having 2 extra drives is pretty much a waste of money (unless, like I said, it is a server with 6 or so 15k rpm hot-swap drives). If you do serious (commercial) video editing, that might be a different story, then you could use that capacity. I would save some money and go with at the most 2 320gb drives.

[edit] I just remembered RAID 5 won't work with only 2 drives, but RAID 1 would be better if you want the security or 0 for the speed.

---

### Post by RandomJoe on 2007-03-19
Yes, I use RAID.  Everywhere I can! ;)  I have four 300GB drives in a RAID5 config on my file server, and two 300GB in RAID1 on my desktop. Plus various setups for playing around here and there...  Drives are cheap, redundancy is nice.

But I don't use hardware (or worse - "fake") RAID.  I use regular 'ol (and much cheaper) drive controllers and use Linux's software RAID.  Peforms very well, and isn't vulnerable to obsolete hardware.  What happens if you use a particular mobo's RAID setup and then the mobo dies?  If you can't find (preferably) that exact mobo, or at least something that uses the right chipset, you may be hosed.  Whereas I've moved my four-drive RAID5 between a couple of different machines and several Linux distros and it just gets picked up and run without issue.  Nice...

I especially don't like the "fake RAID" stuff - not only are you depending on some features of the chipset, you _still_ have to have a software driver to make it work!  Many mobo RAID offerings are this sort, few actually have true hardware RAID.  (I don't know about yours, I didn't check...)

---

### Post by RandomJoe on 2007-03-19
> **slimdog360 said:**
> what are you going to do with 1.5 Terabytes of room?
It will actually be 1TB, since one of the three drives will be parity for the other two.

I can't say for the OP, but I use my 900GB of storage for the following:

 - All my music in FLAC, as well as MP3 versions for portable use.
 - All my movies encoded at high bitrate to keep the quality up.
 - Anytime I download a file, I store it there for future use on any machine.
 - I back up all my other machines to it via 'rsync'.

So far I'm up around 600-700GB used...

---

### Post by Crashmaxx on 2007-03-19
> **mysticrider92 said:**
> 
[edit] I just remembered RAID 5 won't work with only 2 drives, but RAID 1 would be better if you want the security or 0 for the speed.

Eww, don't go with 0. I honestly can't understand why anyone would run RAID 0. Its worse then just the two drives being separate partitions. I mean with 0 if anything goes wrong with either drive, ALL your data is toast. Not something I'd recommend for the average user.

RAID 1 is ok, but you only get half your storage capacity and it gives you no safety against breaking or deleting things. I think having a backup drive somewhere on your network and doing automatic daily backups is a much better idea. then if a drive fails you have only lost a days worth of data at worst. And you have protection against a lot of other things that can happen to your data then just drive failure.

But regular backups aside, though it is always a good idea. RAID 5 is really quite a nice setup. You get 2/3 of your total drive space. So in this case, buying 3 drivers instead of two allows him to have a TB of space and the safety of RAID 1. Its also very fast and all, but none of that is really relevant for a desktop machine. It might be overkill, but it is sweet and he can put a TB of data on it and feel very secure it won't just disappear. If a drive were to fail (or maybe when) he can just buy another and be on his way with not only no data loss, but no downtime, pretty sweet. And drives are cheap nowadays, so if you have that much data, why not?

But I'm sorry to say that you chipset is very likely useless when it comes to RAID. It is likely a BIOS software RAID that you might be able to get to work with Linux, but will surely be a pain. I recommend just using the RAID support built into Ubuntu, its a lot easier to setup and manage.

I recently setup a server for my office with a RAID 5 setup, so let me share how I got it to work. As I mentioned, I tried to use the built-in RAID, but this was very difficult and it was much easier just to use the installer. You can also get a hardware RAID, but that is expensive so I wouldn't bother.

Now doing a RAID 5 is a little harder then a RAID 1 because GRUB doesn't support RAID 5. And with 3 disks you first have to make a partition on each that is a RAID partition, then use the RAID tools to make them one partition. This gets tiresome quickly even if you just want a simple setup. So the best way I found was to first make a 50MB RAID partition on each drive and then go into RAID setup and say you want 3 active drives in a RAID 1 array. And then format it as ext3 and mount it to /boot. You don't want to have any spare drives because they won't get written to, and you don't know which drive may fail. Now use the rest of the space on each drive to make a RAID partition and this time make them a RAID 5 array, with no spares. Now I use LVM so I wouldn't have to remake each partition 3 times and I can't mess I would have to deal with if I wanted to change them. So just make your RAID 5 array a LVM partition. then go into LVM config and make the RAID 5 array your physical volume group. Then make your logical volumes and use them like normal partitions.

I even then setup a network drive the same size as my array and used simplebackup to do a nightly backup. And I just have all the important files on the server and backup the workstations to it. Works pretty good. but maybe a little much for home.

But for home, I think i will just put a RAID 1 on my home server and backup everything to that.

Anyway, sorry to ramble on like that, but I'm sure there was some useful stuff in there.

---

### Post by ixus_123 on 2007-03-19
RandomJoe: Good point about the software RAID.

I totally forgot to check what type the mobo uses.

As for the mobo dying, that's another thing I also didn't consider. The main reason I want it is for storage with a bit of redundancy.

I don't think I'll have any trouble filling 1TB. I live in a small house & my DVD collection is taking up valuable space so it's getting moved into the attic box by box as I transcode the DVD's to my hard disk. I did think about putting the DVDs in a case but I like having them all on the hard drive.

I also wouldn't mind getting mythTV on it too.

Any spare drives might well be used as an external usb backup rather than sitting idle - I don't know really.

I have a load of cmputers (4) now & would like to consolidate them with the new tower, maybe having that as the main workhorse / backup / media server & then getting a couple of cheap laptops for web browsing & email before clearing out the old PCs

One thing for sure is I really can't see myself parting with upwards of £200 for a decent RAID card.

I might have to check out the Nvidia site & see what their chipset does offer.
This is the mobo I was thinking of
[http://www.cluboverclocker.com/reviews/motherboards/evga/680i_sli/index.htm]("http://www.cluboverclocker.com/reviews/motherboards/evga/680i_sli/index.htm")

---

### Post by ixus_123 on 2007-03-19
Thanks Crashmaxx :)

It's interesting to know what others are doing.

I'm a bit sad the chipset only uses a software RAID but thankfull for the tips on setting it up.

I have a while yet before I get this new kit as it's probably going to have to wait till next payday - at least that will give me time to ponder

---

