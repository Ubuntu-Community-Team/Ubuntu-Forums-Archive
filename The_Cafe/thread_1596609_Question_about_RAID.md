---
title: "Question about RAID"
date: 2010-10-14
forum: The Cafe
---

### Post by sim-value on 2010-10-14
Hi,

I currently have a 160 + 250 GB Harddrive in my PC and now i read up about RAID and felt like its something i need.

I have all my Operating Systems installed on the 160 GB Drive, so I Obviously dont want to touch that.

No would it be Possible to install another 250 GB drive and set it up as RAID with the other one, leaving the 160 GB as it is?

---

### Post by juancarlospaco on 2010-10-14
160 OS
250+250 RAID *(data?)*

Yes.

---

### Post by endotherm on 2010-10-14
RAID actually describes a number of completely differant hardware configurations, each with it's own boons and caveats. what exactly are you trying to do? provide fault tolerance and improve read performance with a mirror (RAID1), or just to bond volumes on two disks together (so-called RAID0)? the higher RAID configurations require more than 2-3 disks so I assume you are just looking at the lower levels

[https://secure.wikimedia.org/wikipedia/en/wiki/Standard_RAID_levels](https://secure.wikimedia.org/wikipedia/en/wiki/Standard_RAID_levels)

---

### Post by sim-value on 2010-10-14
RAID0 i what i want to do.

> 160 OS
250+250 RAID (data?)
Great :)

---

### Post by CharlesA on 2010-10-14
Keep in mind that if one drive goes down, you lose all your data.

---

### Post by cascade9 on 2010-10-14
> **sim-value said:**
> RAID0 i what i want to do.

Great :)

RAID0 on a data drive isnt going to give you any real benefits in most cases, and like CharlesA....lose one drive, you've lost everything.

---

### Post by futz on 2010-10-14
> **sim-value said:**
> RAID0 i what i want to do.
The thing about RAID-0 is that, while it does make drive reads/writes much faster (not twice as fast, but lots), it cuts safety in half at the same time. If either of those two drives has any problem at all it's very likely you will lose ALL your data. I used to do RAID-0 on all my machines, but drives got faster and I didn't like the high risk.

If you want HIGH speed, spend your money on a big SSD to use as your boot/main drive. They're stupid-fast. Once you've had one you can't ever tolerate a hard drive for a boot drive again. You still run HDs for archive/data storage, but for the OS and programs SSD eliminates that nasty slow HD bottleneck. The OS boots super fast and all programs load pretty much instantly. Updates and drive checks go super fast too. And all that comes with VASTLY less risk than RAID-0.

---

### Post by BrokenKingpin on 2010-10-14
As others have stated, raid-0 has no redundancy. You should look into raid-5, you would get performance and redundancy, but requires more disks.

---

### Post by CharlesA on 2010-10-14
If you are only working with 250GB of data, RAID 5 is a bit of a waste. Backups > RAID.

---

### Post by sim-value on 2010-10-14
I also just came to think about that i actually wanted to speed up my System, which isnt going to happen when i Raid the Data Drive ...

@SSD Insanly Fast, insanly expensive (250 GB HDD: 35€)
@Data Loss, i couldn't relly care less ...

---

### Post by BrokenKingpin on 2010-10-14
> **CharlesA said:**
> If you are only working with 250GB of data, RAID 5 is a bit of a waste. Backups > RAID.
I agree that with only 250GB it is a bit of a waste. In general though, both RAID and backups have their place. RAID manages itself, where backups do not. With RAID, if one disk fails you lose no data, but if you were just using backups of that one disk, you would lose everything since the last backup. On the other hand if you are using just RAID, and the whole system is destroyed (power surge, gets stolen, fire, etc.), then you have lost everything. So using both is a good idea.

---

### Post by CharlesA on 2010-10-14
> **BrokenKingpin said:**
> I agree that with only 250GB it is a bit of a waste. In general though, both RAID and backups have their place. RAID manages itself, where backups do not.

You still need to do maintenance on a RAID array to make sure the drives are healthy.

Same goes for backups, since you need to make sure whatever media you are using is healthy.

---

### Post by cascade9 on 2010-10-14
> **sim-value said:**
> I also just came to think about that i actually wanted to speed up my System, which isnt going to happen when i Raid the Data Drive ...

@SSD Insanly Fast, insanly expensive (250 GB HDD: 35&#8364;)
@Data Loss, i couldn't relly care less ...

You should be able to get a 32GB SSD for about 60-70 quid. You could even go lower on price, but then you would be getting a SSD thats not much faster than a (fast) mechanical HDD. 32GB is not huge, but run the OS from there you'd notice the speed difference much more than RAID0ing a couple of 250s.

---

### Post by BrokenKingpin on 2010-10-14
> **CharlesA said:**
> You still need to do maintenance on a RAID array to make sure the drives are healthy.

Same goes for backups, since you need to make sure whatever media you are using is healthy.
With backups you have to do the backups yourself, by plugging in the media and doing the backup and all that fun stuff, where RAID backs up to the other disks in the raid automatically on write. And once the RAID is setup there is really no maintenance until the RAID reports a failure.

As stated in my updated post above, both methods have their pros and cons, so both methods can be used together.

EDIT:
Also, doing raid-0 on data drives is almost pointless. raid-0 on the OS drive itself is a good idea in terms of performance, as long as you backup that os drive (or go with something like raid-1+0, but that is getting a bit crazy lol).

---

### Post by futz on 2010-10-14
> **sim-value said:**
> I also just came to think about that i actually wanted to speed up my System, which isnt going to happen when i Raid the Data Drive ...

@SSD Insanly Fast, insanly expensive (250 GB HDD: 35&#8364;)
@Data Loss, i couldn't relly care less ...
I really don't think SSD is "insanely" expensive. I run Ubuntu on a [128GB G.Skill Falcon II]("http://ncix.com/products/index.php?sku=46520&vpn=FM-25S2I-128GBF2&manufacture=G.Skill") $365. 128GB is plenty for the OS and your program files as long as you keep your data on HDs. I bought it on sale for something like $300 - can't remember exactly. But it's many thousands of times faster than RAID-0 and much, much safer. Totally worth spending the money if you're looking for a **VERY** noticeable speed increase (RAID-0 speed increase isn't really noticeable, in my experience - it shows up in benchmarks, but daily use is really almost same as single drive). An SSD is the best bang for the buck you can do for a computer these days IMHO.

If I had bought two tiny (let's say) 250GB HDs to use in RAID-0 instead at $60ish each then that's almost half the cost of the SSD, it's still pretty slow and it's still terribly risky.

Fancier, safer RAID methods cost more (more drives) and are still dog-slow compared to SSD.

---

### Post by sim-value on 2010-10-15
> **cascade9 said:**
> You should be able to get a 32GB SSD for about 60-70 quid. You could even go lower on price, but then you would be getting a SSD thats not much faster than a (fast) mechanical HDD. 32GB is not huge, but run the OS from there you'd notice the speed difference much more than RAID0ing a couple of 250s.

That sounds nice, i think i just looked at the Wrong Shops til now ... (now what about two SSDs in RAID ? :P)

Thanks for your advice everybody!

---

### Post by futz on 2010-10-15
> **sim-value said:**
> That sounds nice, i think i just looked at the Wrong Shops til now ... (now what about two SSDs in RAID ? :P)
Sure, that would work fine. My buddy has a big quad-drive RAID-0 SSD on a PCI board from (I think) OCZ. It's horribly expensive, but silly-fast. And he's had a failure and had to RMA it at least once, as well as firmware trouble early on.

---

### Post by cascade9 on 2010-10-15
I've heard that soem of the SSD, early ones in particular have isues with RAID, nd problems like futzs buddy can happen (firmware problems, etc). As time goees on SSDs just get better and faster though, I'm sure that those problems will be mostly a thing of the past soon. 

Still, I dont know if I'd run a SSD in RAID...they run fast enough as a single drive that you notice the difference over a mechanical HDD. 

> **sim-value said:**
> That sounds nice, i think i just looked at the Wrong Shops til now ... (now what about two SSDs in RAID ? :P)

Thanks for your advice everybody!

I dont even live in the UK, I got that price from a great website- staticice. See here- 

[http://www.staticice.co.uk/](http://www.staticice.co.uk/)

Just type in what yout after, eg 32GB SSD, and you'll geta list of places selling them, from cheapest to most expensive. BTW, from experience, sometimes the 'cheapest' shop isnt, because they charge excessive postage and handling (and quite oftn the 'cheapest' is online only).

---

