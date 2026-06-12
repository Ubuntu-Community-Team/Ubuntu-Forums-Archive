---
title: "RAID advice"
date: 2009-03-23
forum: Server Platforms
---

### Post by pzs on 2009-03-23
I work in bioinformatics and regularly have to read and write large text files. My current project involves 28 CSV files, each of which is around 130MB. My boss has offered to buy some extra kit to make this easier. I'm already looking to buy some extra memory, but I wondered whether it was also worthwhile to look into some RAID.

My machine is a Dell Precision T5400 with a quad core Xeon, 8GB of fully buffered RAM and a 7200rpm 750GB hard drive. My plan would be to buy another 1 or 2 750GB drives and use RAID 0, probably in software. 

- Will I be able to incorporate the new drives without reinstalling?

- Will this give me a noticeable and worthwhile performance boost on this kind of work?

- Am I incurring a much higher risk of losing all my data? I have some backup support but it would certainly be a pain in the **** to lose the local copies.

- How easy is all this to install in Ubuntu? I'm using 8.10.

Cheers,

---

### Post by hyper_ch on 2009-03-23
well, if one disk of raid 0 fails then all data is gone.. I'd rather use raid 10 - that should give redundance and speed improvement.

Also I'd do a cleaqn install, simplest way. I think there a ways to installe a raid later on but I've never done that.

Setting up a raid at installation from the alternate/server cd is simple.

---

### Post by Bachstelze on 2009-03-23
> **hyper_ch said:**
> well, if one disk of raid 0 fails then all data is gone.. I'd rather use raid 10 - that should give redundance and speed improvement.

But will require four drives instead of two. If important files are backed up correctly, failure shouldn't be a major problem.

> Also I'd do a cleaqn install, simplest way. I think there a ways to installe a raid later on but I've never done that.

Only for RAID-1 and RAID-5. For RAID-0, a reinstall is unavoidable.

---

### Post by pzs on 2009-03-23
Thanks for the replies. Reinstalling probably isn't a big problem but I still need to know whether it will be worthwhile. Do you know of any benchmarking for single 7,200 against multiples running in software RAID?

---

### Post by fjgaude on 2009-03-23
> **pzs said:**
> Thanks for the replies. Reinstalling probably isn't a big problem but I still need to know whether it will be worthwhile. Do you know of any benchmarking for single 7,200 against multiples running in software RAID?

Well, in raid5 we get n-1 speed where n is the number of drives in the array and their individual speed. Here's my four-drive mdadm raid5:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

The individual drives show 70MB/sec thruput.

---

### Post by obscure_detour on 2009-03-24
I can tell you what I've learned from *fjgaude* and others on the forums.  I'm about to upgrade my server to 4 drives and a new cpu, but here are my current speeds.

RAID 5, 3x 750GB Samsung.  AMD Athlon X2 4400+, 2GB DDR2 800 RAM

**One drive:**
```

jms@server:~$ hdparm -tT /dev/sda1
/dev/md0:
 Timing cached reads:   1706 MB in  2.00 seconds = 853.26 MB/sec
 Timing buffered disk reads:  420 MB in  3.01 seconds = 139.68 MB/sec

```

**Software RAID5:**
```

jms@server:~$ sudo hdparm -tT /dev/md0
/dev/md0:
 Timing cached reads:   2007 MB in  2.00 seconds = 1003.59 MB/sec
 Timing buffered disk reads:  516 MB in  3.00 seconds = 171.91 MB/sec

```

Now, with your 8GB of RAM, and an Xeon processor, I'd say you'll be off to much better speeds.  :)  Exactly why I'm upgrading mine.  Let us know how the speeds turn out, I'd like to see if how that quad will effect performance.

Cheers.

---

### Post by pzs on 2009-03-24
I might be tempted by another three 750GB drives and then going to RAID 5 or RAID 10. This has a redundancy advantage as well as meaning I don't have to reinstall. Unfortunately it looks like my case won't accommodate them:

[http://www.dell.com/content/products/productdetails.aspx/precn_t5400?c=us&cs=555&l=en&s=biz&~tab=specstab](http://www.dell.com/content/products/productdetails.aspx/precn_t5400?c=us&cs=555&l=en&s=biz&~tab=specstab)

I'm not sure about the power supply either - it's 875W. Any thoughts?

---

### Post by fjgaude on 2009-03-24
I would think 875W is good enough, as drives only take a few watts, 12 or less.

How many drives slots are available in your box?

---

### Post by pzs on 2009-03-24
The web page says 3. Can I do RAID 5 with that? RAID 10?

---

### Post by fjgaude on 2009-03-24
Well, with raid5, yes, and you would get twice one drive's thruput. For raid10 you need four drives. Raid1 would need only two, but the thruput would equal that of one drive.

---

