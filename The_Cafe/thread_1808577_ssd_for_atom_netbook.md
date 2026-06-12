---
title: "ssd for atom netbook"
date: 2011-07-20
forum: The Cafe
---

### Post by ssam on 2011-07-20
i have a lenovo s12 (atom N270, 2GB ram(maxed)). it currently has a 5400rpm 160gb 2.5inch drive. i am considering upgrading to an SSD (maybe 120GB), which should give me a big increase in access time and read/write (disk utility says, max read 71MB/s, av read 55MB/s, av access 18ms).

i suspect that i would not get the full benefits from a super fast ssd due to the slow CPU, but I guess i should get some improvement.

I am also hoping to get some power saving benefit.

Most reviews seem focused on speed (which is fair enough). Any tips on finding a low power SSD? any experience with SSD in similar netbooks?

---

### Post by Paqman on 2011-07-20
I swapped out the nasty slow 5400rpm hard drive in my Eee PC for an Intel X25-V, and it was a good upgrade. I find with an SD slot you don't need much space, I've got a 32GB SSD and it's more than enough. I wouldn't bother spending lots on extra space for storage, as most storage doesn't need to be fast, and you could easily end up with the drive costing more than the whole netbook if you went for over 100GB.

---

### Post by Copper Bezel on 2011-07-20
Yeah, I just want to echo that, yes, the difference is as noticeable as it is on any machine, just all the more necessary in light of the other limitations, and I've also made do with 32 gig drives (including the one in my Eee now,) although a 64 would be more reasonable today.

No idea on finding lower-power drives. I doubt if there's that much variance in power consumption.

---

### Post by wizard10000 on 2011-07-20
I have a 60gb OCZ Agility 2 in an HP Mini 110 netbook.

*Most* (all?) netbooks will only do 1.5 Gbps SATA so that pretty much limits your disk speed to 125MB/sec give or take.  

I *think* in addition to crippling Intel 945 video chipsets they also cripple the I/O controller to save power as the Intel 82801GBM/GHM  I/O controller in my netbook will do 3.0 Gbps SATA, it just won't do it in my netbook  :(

A friend of mine and I both have Atom N270 netbooks from different manufacturers - we both have SSDs that should talk > 250 MB/sec.  Partitions are aligned correctly, I/O scheduler is set to noop, both machines have noatime set in fstab and both of them hit a brick wall at 125 MB/sec, which is better than 80% of capacity for a SATA 1 interface.

Unfortunately an ICH7 controller won't tell you which version of SATA it supports, so it's kind of a tough call, but we think that the SATA controllers have been throttled back to conserve power the same way the video chipsets are.

I have a 500gb Samsung hard drive that used to live in this netbook that'd sustain 100 MB/sec reads and writes but the faster seek time of the SSD makes it seem a fair bit faster than the mechanical hard drive.

My netbook will boot from grub to desktop in ~29 seconds, which is about five seconds quicker than it would with the 500gb 7200 rpm drive.

Can't tell you which is better for you, seat of the pants the SSD feels a lot quicker than the mechanical hard drive did.  If you want more than about 60 GB of storage I wouldn't consider an SSD - get a fast mechanical hard drive instead.

cheers -

---

### Post by Paqman on 2011-07-20
Probably also worth mentioning that for a portable computer, having a shock-proof drive is a very nice feature.

---

### Post by wolfen69 on 2011-07-20
I have a 60gb SSD in my netbook. It's noticably faster, but not the "instantaneous" quickness I expected. I guess the netbook's bottlenecks keep it from it's full potential. It's not game changing, but I guess it's an *OK* upgrade.

---

### Post by ssam on 2011-07-20
thanks for replies.

yes, not expecting to get the full quoted speeds. but even 125MB/s would be reasonable speed up.

maybe 60GB will be enough, i'll need to trim down a bit.

---

### Post by andrewabc on 2011-07-20
I have an atom n270 nettop. Swapped out the 160gb hdd for 60gb vertex1 (but put hdd back in when I needed ssd for my main desktop). It did help speed things up, but the processor/chipset definitely limits possible speed increase. You will only get 125mb/s read/write max. Lower access times etc do help.

I would only go with 60gb unless you plan on putting the ssd into another machine in near future (<=3 months).

Here are pics showing what to expect when upgraded. 160gb hdd vs 60gb vertex1.

[http://imageshack.us/photo/my-images/442/screenshot160gbharddisk.png/](http://imageshack.us/photo/my-images/442/screenshot160gbharddisk.png/)

[http://imageshack.us/photo/my-images/175/screenshot64gbsolidstat.png/](http://imageshack.us/photo/my-images/175/screenshot64gbsolidstat.png/)

So you get twice the read speed. Better randoms (good for firefox profile), and low access time.

you sure you have direct access to your HDD on netbook without having to take out keyboard?

If your netbook is primary computer device you have, you should get a 2.5" enclosure so you can hook it up to netbook with usb cable to use for storage.

---

### Post by drawkcab on 2011-07-21
This was a while ago, but I bought a 16gb Super Talent ssd to replace the 4gb ssd in my n270 eeepc

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820609405](http://www.newegg.com/Product/Product.aspx?Item=N82E16820609405)

Spec says:

Sustained Sequential Read
    90 MB/sec

Sustained Sequential Write
    55 MB/sec 

Modest, but for comparison, my eeepc is much snappier than my n450 nettop with 320 gb hdd.

I don't know that I could tease that much more performance out of this thing.  If you have to choose between size and speed, I'd definitely invest in size.  It seems like investing in super speedy ssd for an n270 is going to provide diminishing returns.

---

### Post by wizard10000 on 2011-07-21
> **drawkcab said:**
> I don't know that I could tease that much more performance out of this thing.  If you have to choose between size and speed, I'd definitely invest in size.  It seems like investing in super speedy ssd for an n270 is going to provide diminishing returns.

Yup.

You can also use GMABooster to get your video's clock speed back where it should be.  Intel 945 video chipsets are designed to run at 400MHz but are choked back to 166MHz on netbooks for power savings - I just call GMABooster from /etc/rc.local

If you suspend your machine (I don't) you'll have to re-run it on wakeup but it's pretty cool.

[http://www.gmabooster.com/home.htm](http://www.gmabooster.com/home.htm)

Enjoy!

---

### Post by wizard10000 on 2011-07-21
> **andrewabc said:**
> If your netbook is primary computer device you have, you should get a 2.5" enclosure so you can hook it up to netbook with usb cable to use for storage.

That's what I did - took the 500Gb hard drive I used to have in my netbook and put it in an external enclosure.  I put all my multimedia on the external drive and also use it to back up the netbook now.

---

### Post by BrokenKingpin on 2011-07-21
Putting an SSD in my netbook made it feel like a new machine, the speed increase was more than I expected. I also get a bit better battery life, but not a lot.

For figuring out the power consumption, simply look up the specifications from the manufacturer's website. For example, my drive lists the power consumption here:
[http://www.corsair.com/solid-state-drives/force-series/cssd-f60gb2-brkt.html](http://www.corsair.com/solid-state-drives/force-series/cssd-f60gb2-brkt.html)

You can use these specs to compare the drives to see what would be the best for power consumption.

---

### Post by ssam on 2011-07-24
i got a kingston ssdNow V+ 100, 96GB for £101 :-)

It feels a bit faster, though nothing huge. I guess the CPU is still a big bottleneck.

I measured a few things before and after,
Natty desktop install (from a USB, no network, from the install button on the partition screen to the reboot prompt),
HD 11:17
SSD 9.59

First software update after install. both had 161 MB of updates, which took about a minute to download
HD 12:31
SSD 9.59

boot time (third reboot after install and updates, measured with bootchart)
HD 22.63 s
SSD 14.02 s
boot charts are attached

---

