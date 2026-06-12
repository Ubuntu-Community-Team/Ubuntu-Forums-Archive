---
title: "RAID10 questions"
date: 2009-03-27
forum: Server Platforms
---

### Post by vsiege on 2009-03-27
I am unfamiliar with setting up any kind of array under Ubuntu 8.10 Server Edition and was looking for some advice.
I am building a new server and would like to use a RAID10 config. Would it be recommended to use a RAID controller for this? If so, could anyone recommend one?

Would you leave it up to the OS to create a RAID10 or should I stick with a separate RAID controller??

Any kind of recommendations in terms of how much RAM and CPU is greatly appreciated. The server will be used to store files, LAMP and FTP services in a mainly Mac 10.5 environment. the network would have anywhere from 5 - 10 users. I'm guessing I would need about 8 to 16 GB of RAM MIN.

---

### Post by kidders on 2009-03-28
Hi there,

The answer to your question mostly depends on the size of the array. The characteristics of RAID10 make it most suited to heavily loaded database servers or hosting very large contiguous blocks of data (eg media files), which tends to make arrays reasonably large. For the sake of example, let's suppose you plan to make a 4TB array out of 8 x 1TB disks + 2 spares. In that case, a controller seems like a good idea, if you're to avoid throwing away the most significant advantage RAID 10 has over, say, RAID 5.

Given that your web server will probably get very little out of sitting on RAID 10, I don't suppose making your array any smaller than that would justify the use of RAID 10 in the first place. Anything bigger would *certainly* warrant a RAID controller.

> **vsiege said:**
> I'm guessing I would need about 8 to 16 GB of RAM MIN.That seems excessive for what is basically just a giant hard disk. Unless your web server is going to be running some pretty heavy-duty applications, 4GB ought to be more than enough, imo.

Anyhow, I hope that helps.

---

### Post by vsiege on 2009-03-28
ThANks so much.
> **kidders said:**
> . In that case, a controller seems like a good idea, if you're to avoid throwing away the most significant advantage RAID 10 has over, say, RAID 5.
If, I one is creating a RAID 5 why don't they just up it to RAID10? I'm assuming that you are talking about using mdadm to create my array since I will not be serving up videos - is that right?

> Given that your web server will probably get very little out of sitting on RAID 10, I don't suppose making your array any smaller than that would justify the use of RAID 10 in the first place. Anything bigger would certainly warrant a RAID controller.
My server will probably not have any higher storage than 2 terabytes. I'm just looking for the machine to be moderately fast and have a means to duplicate (mirror) content without the users having to do that themselves. If getting a higher speed processor makes more sense lemme know.

---

### Post by kidders on 2009-03-28
Hey again,

The main reason for choosing RAID 10 over RAID 5 is usually write performance. The trouble with RAID 10 is that you need more disks, so software-based RAID 10 performance will degrade faster than RAID 5 as capacity/load increases. The point I was (somewhat ineptly!) trying to make is that if you implement a large enough RAID 10 array in software, you might find it performs worse than an equivalent RAID 5 one. The same principle wouldn't apply to a hardware-based array. Basically, if performance is your only reason for choosing RAID 10, getting a hardware controller would probably be best.

Personally, I tend to opt for software-based arrays where possible, because they're cheaper, more compatible, and aren't exposed to the risk of failure of the controller itself. If software isn't practical, then I'd go with hardware-based RAID 1 or 10 every time :-)

> **vsiege said:**
> If, I one is creating a RAID 5 why don't they just up it to RAID10?In general, it's best to build software-controlled arrays out of as small a number of disks as possible, so that a standard motherboard's SATA interface can keep up with the throughput, and doesn't become a bottleneck. SATA is a switched protocol, so parallelism isn't exactly its strong suit!

> **vsiege said:**
> My server will probably not have any higher storage than 2 terabytes.In that case, I would suggest using RAID 1, with 2 x 1TB hard disks, plus 1 spare. That leaves your motherboard's fourth SATA slot free for your OS. RAID 10 seems unnecessary. :-?

> **vsiege said:**
> If getting a higher speed processor makes more sense lemme know.The only situation where processor speed makes a significant difference to RAID array performance is with software-based RAID 5, which is (comparatively, at least) CPU-heavy. If you opt for something else, then all you really need to worry about is the software you'll be running.

---

### Post by fjgaude on 2009-03-28
Kidders is right on... some years ago, based upon his advice, I did extensive testing of **mdadm** software using from two to five drives, all 320GB Seagates, which have a native read thruput of 70MB/second.

I settled on raid5 because of reliability and read thruput, using four drives. I've used the same array for two years now, moving from motherboard to motherboard and OS upgrades from 6.06 to 8.10, ready for 9.10

I had one drive failure during that time and decided to replace all of them. (I always use triple backups, one online, another near-line, and finally, one off-line. My data is all important, notice my signature.)

My setup is a very fast dual-core Intel and CPU loading has never been a bottleneck, while I/O Wait is.

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

The disk write speed in somewhat over that of a single drive, if memory serves. Read speed is three times that of a single drive, as you see.

Your E4400, assuming fast memory, will do just fine from what your load is likely to be.

Have fun!

---

### Post by Brazilian Joe on 2009-04-02
If you are on a server, you should ALWAYS scan toroughly your disks before you put them into production. This is especually true for SATA disks. I had 3 SATA disks developing bad blocks on me, 6 months after the purchase.

on RAID10 you have the performance benefit of raid 0  and the safety of raid 1, but it is still not as good as a RAID 5, because it has no checksumming. According to what I have read before, in raid 10 there was the possibility of writing the bad data over the good one on reconstruction (!!!). But I don't recall where I have read it, or if it still holds true.

on RAID 5 and 6 you have checksumming, which allows for reconstruction of the correct data.

Recent motherboards have 6 disk controllers.

If you RAID say, 5 disks + 1 spare like I did, with 750GB disks, you get around 1.7TB on RAID 10, and a handsome disk performance. This is very good if you have a database or virtual machines. Unfortunately, I had 3 bad blocks at the same time and they crashed my RAID. Fortunately, I had backups. DON'T FORGET TO BACKUP, it has saved my ***, and will save yours someday. RAID does not protect you from everything, it is just an additional level of robustness.

From what I have read, 4 1TB disks are enough to make the statistical probability of having 1 disk read error while your RAID is reconstructing (i.e. it had a defective disk and is momentarily vulnerable, without redundancy) is very high. This means RAID5 is not good anymore at that data volume (given current disk speeds and failure ratios), so you would NEED RAID6 to be actually safe.

That's what i have done with my 6 750GB disks. After the crash, I verified individually the disks. Each run of a badblocks test with destructive read-write (faster than non-destructive) took around 22 hours.

After that I built a RAID6 with 5 disks + 1 spare. That gave me around 2.2TB of useable space, and less performance. But safer.

If you are going to have a RAID, I'd say you should have at least one hot spare disk AND one more disk, shining new and already tested, well stored to be put to use when/if needed.

---

