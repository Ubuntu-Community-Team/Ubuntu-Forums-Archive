---
title: "/ on SATA or IDE?"
date: 2006-11-01
forum: The Cafe
---

### Post by maniacmusician on 2006-11-01
So, here's the situation. I just bought a 300GB SATA hard drive. My plan was to put my /home on there and leave my 80GB IDE drive for / (for when I do clean installs of edgy, feisty, etc). Then, I realized, that my SATA drive was way faster than the IDE. Would it give me a significant speed boost if I used a partition on the SATA drive as / ? 

So in summation, here are my choices:

> / on IDE, /home on SATA

/ on SATA, /home on SATA, extra storage space on IDE. 

I'd really only do it if there was a speed boost to be had. any opinions?

---

### Post by po0f on 2006-11-01
maniacmusician,

Everything on SATA.  Make the slowpoke IDE drive a backup dump.

---

### Post by prizrak on 2006-11-01
SATA1 is the same speed as IDE (ATA-133). The only reason for SATA1 was native RAID. 2 actually has speed advantages.

---

### Post by maniacmusician on 2006-11-01
SATA 1? I'm pretty sure I have whatever the newest one is (SATA 2?). the transfer rate at least is 3.0 Gb/s not 1.5.

I know the actual hard drive is faster, but my question is, will my system operate any faster if I put / on the SATA?


Also, does / have to be the first partition? because I put about 38 Gigs on the first partition earlier today, and it'd be easier if I could use the second as /. 


and on a totally unrelated note, what is the difference between Primary, Logical, and Extended? please don't go to any trouble (like googling) to answer this one, I'll look it up myself if no one knows off the top of their head.

---

### Post by Parkotron on 2006-11-01
I had the same question awhile ago. I didn't find any hard numbers to support significant performance gains from putting / on SATA, but I did it anyway. It's been working great for me, but I can't give you any hard numbers. 

Definitely put your swap partition on the faster drive as swapping out is when that speed increase is most needed.

As far as primary, extended, and logical partitions go, it's not really that complicated. Primary partitions are the "regular" kind. Most drives contain only a single primary partition. Some operating systems (Windows) can only boot from primary partitions. The first partition on your drive should almost always be a primary one. You can have up to four primary partitions on a single disc.

If you need more than four partitions (or think you might ever) you should create an extended partition. Inside of an extended partition you can create as many logical partitions as you want. Other than some complicated BIOS/bootstrapping differences, logical partitions behave exactly the same as primary partition. Most Linuxes can even boot from a logical partition.

When you put that all together, I recommend the following: (This is how I partition my 250GB drive. Your needs may vary or you may disagree.)

10GB Primary partition for Ubuntu /
240GB Extended partition taking up the rest of the drive which contains:
 238GB Logical partition for /home
 2GB Logical partition for swap

Oh, and for all your partitioning needs, I highly, highly recommend the GParted LiveCd ([http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)). Even if you prefer KDE/QT, GParted is way ahead of QtParted and running it from a simple live CD makes me feel so much safer.

---

### Post by Bloodfen Razormaw on 2006-11-01
There is no reason to put / on SATA.  SATA offers no significant performance benefits over IDE.  The bottleneck on both is the drive, not the interface.  On a typical 7200 RPM drive typical read speed will likely never even hit 40 MBps, and even in the best case you will be lucky to sustain 80 MBps.  If you are lucky NCQ will give the SATA drive a tiny benefit, but nothing like the serious queuing you would get from SCSI.  If you really want a fast root partition put down for a 30GB or so 10000 RPM drive.  You don't need anything remotely close to 80GB for root.

---

### Post by maniacmusician on 2006-11-01
hmm I know I don't need 80 GB for root, It's just that I will probably not use that drive for anything else! and with 80 GB of space, I can feel free to get as many distros on there as I want without worrying about it. I actually have two 80GB IDE drives in there. Giving one of them to a friend who could use it. But thanks for the info on the drive speeds, I just need some people to concur with you now on those facts

@Parkotron: Does your system feel any faster being on a SATA drive than an IDE? From what Bloodfen said, it seems like it wouldn't and that's kind of what I was thinking as well. 

I don't really need or use swap, I have 1.5 GBs of RAM, so I'm all set in that department. 

If I were going to put / on the SATA drive, I would give it my 96GB partition just so I can mess around with installing a lot of different things. 

And I already use GParted. Not always the live CD. for things like this, I just umount the drive and partition it. but if it's the main drive that needs to be partitioned, then of course, I use the gparted livecd. 

so can anyone confirm (or deny) what Bloodfen Razormaw said? 

thanks

---

### Post by kuja on 2006-11-02
If you have multiple drives on one ide cable, the interface can easily become a bottleneck. In this case SATA is faster seeing as it's always a straight shot to the motherboard, because your drives won't be sharing a cable.

---

### Post by sup on 2006-11-02
> I don't really need or use swap, I have 1.5 GBs of RAM, so I'm all set in that department.
If you do not have swap bigger than you RAM, you cannot hibernate. But you may not need this.

---

### Post by prizrak on 2006-11-02
You won't see any performance gains from the / on a SATA drive. The speed differences are insignificant and most of the shared libraries are already in RAM once you boot up. The only thing you should do is put a swap file onto the SATA drive that will have a pretty good benefit. Even putting swap onto a different IDE controller makes it noticeably faster. Also the / doesn't have to be the first partition, it actually doesn't matter at all. On my machines /boot is the first partition ;) So keep / where it is just dump /home on SATA.

---

### Post by klerfayt on 2006-11-02
> **sup said:**
> If you do not have swap bigger than you RAM, you cannot hibernate. But you may not need this.
:confused: is that true?

---

### Post by kuja on 2006-11-02
Yes, that should be true, hibernate, if I remember right, copies everything to swap and then shuts down, and then when you go back, it restores things to their prior state from swap.

---

### Post by kuja on 2006-11-02
If you don't want to repartition your drive just to get swap, add a  swapfile:
```

sudo dd if=/dev/zero of=/swapfile bs=1024 count=3145728
sudo mkswap /swapfile
sudo swapon /swapfile
sudo -s

echo "/swapfile               swap                    swap    defaults        0 0" >> /etc/fstab

```

---

### Post by klerfayt on 2006-11-02
I have suspended to disk with less swap size than <512MB memory (in dapper)

---

### Post by sup on 2006-11-02
> I have suspended to disk with less swap size than <512MB memory (in dapper)
suspension is something different than hibernation(one shuts down about everything besides RAM, the other shuts down everything so it needs to copy content of RAM to somewhere).
Although I cannot say it is impossible, for me, enlarging swap enabled me to hibernate.

---

### Post by klerfayt on 2006-11-02
> **sup said:**
> suspension is something different than hibernation(one shuts down about everything besides RAM, the other shuts down everything so it needs to copy content of RAM to somewhere).
Although I cannot say it is impossible, for me, enlarging swap enabled me to hibernate.
hibernate=suspend to disk

---

### Post by maniacmusician on 2006-11-02
suspend to disk (aka hibernate) doesn't sound that great...suspend to RAM however sounds more intriguing. 

I guess I might just make a swap partition on the sata drive then. How big does it need to be?

thanks for all the input guys.

---

### Post by kuja on 2006-11-02
Twice as much as you have RAM is generally a good number.

---

### Post by Polygon on 2006-11-02
of course i have a gig of ram, a 2 gig swap partiton and i still cant hibernate. it always freezes when i start up again and i have to either kill x or restart my computer... which means i lost whatever i was working on ( luckily it was just a test)

---

### Post by klerfayt on 2006-11-03
> **maniacmusician said:**
> suspend to disk (aka hibernate) doesn't sound that great...suspend to RAM however sounds more intriguing. 

I guess I might just make a swap partition on the sata drive then. How big does it need to be?

thanks for all the input guys.
you don't need swap for suspend to ram

---

### Post by jhenager on 2006-11-10
> **maniacmusician said:**
> So, here's the situation. I just 
I'd really only do it if there was a speed boost to be had. any opinions?

Even with a 10,000 rpm SATA drive, the performance boost is only going to be noticable pulling and putting data on the drive.
I'd say you would improve performance more with less effort with hdparm.
[http://justlinux.com/forum/archive/index.php/t-112346.html](http://justlinux.com/forum/archive/index.php/t-112346.html)
Section 3.1

---

### Post by maniacmusician on 2006-11-10
I'll look into it, thanks. 

BTW, for anyone that cares, I did indeed go ahead and install edgy. made a 20 GB partition on the IDE drive for /, a 200GB partition on the SATA drive representing /home/maniacmusician, and a 100 GB partition for my music.

---

