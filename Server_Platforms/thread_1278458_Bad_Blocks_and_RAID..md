---
title: "Bad Blocks and RAID."
date: 2009-09-29
forum: Server Platforms
---

### Post by DBrocks on 2009-09-29
Hey guys,

I am setting up a server at my house with 4x1tb in RAID6, with the possibility of expanding in the future. (Ubuntu software RAID with mdadm).

I know that sometimes RAID rebuilds can fail if, during the rebuild process, a bad block is encountered. This bad block travels up the chain of command, until the RAID controller (mdadm in this case), marks the drive as failed and drops the drive during the rebuild. I am using RAID 6, so I have a bit better security then RAID 5. However, with the rate hard drive capacity is expanding these days, bad blocks are becoming an unfortunate, and usually unpreventable, fact of storage. When I add another 2X1 TB drives in the not-too-distant future, that's 6 TB for bad blocks to be found on. I want to know how, to scan for bad blocks, and repair/remap them in the array, so the array rebuild will not fail due to bad blocks. (I know it can still fail if there is a mechanical failure, but re-mapped bad blocks is another variable removed). The array is separate from my OS, so unmounting it to fix the blocks is not a problem. Give me a hand, I'm stuck on this one!

I dug up some code from a site that said to do this:

Identify bad Block: ```
badblocks /dev/hda1 > badblocks
```
To repair blocks: ```
fsck -t ext3 -| badblocks /dev/hda1
```

How would I do this on RAID? Do I use /dev/hda1 (and all the other drives), or do I do /dev/md0 (the array?)

[COLOR=lime][/COLOR]

---

### Post by Xianath on 2009-09-30
Bad blocks are taken care of by the drive itself. It relocates them to a "safe" area, therefore even if you run a badblocks scan, you won't find anything (unless the drive is so bad that the "safe" area fills up). That's one more case where good intentions pave the road to hell. You need to keep an eye on the SMART logs for relocation or pending relocation events, and act accordingly. Your best bet is to use SMART tests. See the smartctl man page (install smartmontools if you haven't already) and especially the -t option.

Believe it or not, bad blocks are not even your worst enemy. It's unrecoverable bit errors. The average BER (Bit Error Rate) of consumer-grade drives is 1e-14 or 1e-15. That's one bit in 12.5 or 125 TB, respectively. Rebuilding a 12-spindle RAID5 array of 2TB disks therefore gives you a ~20% chance of an error **that you may not even know about**! If you do know about it, that's still a 20% chance of your array getting sunk by a single bit, if you only have single parity. Thankfully, mdadm is smart enough to let you forcefully recover even in that event, but then you're back to square one with a corrupted piece of data somewhere.

I've done a lot of research on RAID recently as my Master's thesis was on Linux software RAID. I've worked up some pretty nasty math on array failures (all theoretical, of course :) ) and was completely scared away from single-parity RAID. There's still some time before dual-parity becomes obsolete but at the current growth rate of disk density, and the fact that it's not being matched by disk reliability, it is just a matter of time.

Cheers,
Peter

---

### Post by u-slayer on 2009-09-30
> **Xianath said:**
> 
Believe it or not, bad blocks are not even your worst enemy. It's unrecoverable bit errors. The average BER (Bit Error Rate) of consumer-grade drives is 1e-14 or 1e-15. That's one bit in 12.5 or 125 TB, respectively. Rebuilding a 12-spindle RAID5 array of 2TB disks therefore gives you a ~20% chance of an error **that you may not even know about**! If you do know about it, that's still a 20% chance of your array getting sunk by a single bit, if you only have single parity. Thankfully, mdadm is smart enough to let you forcefully recover even in that event, but then you're back to square one with a corrupted piece of data somewhere.


Is that really so bad? If you have 125TB of data, chances are losing 1 bit will not be the end of the world.

---

### Post by DBrocks on 2009-09-30
Wow X. Awesome reply. I should like to pick your brain sometime regarding RAID, seeing as you seem to be really knowledgable about this.

---

### Post by Xianath on 2009-10-01
u-slayer: Let's just say Sun considered it important enough to add end-to-end checksums to the ZFS filesystem **in addition to** RAID parity. I've been in the *x world long enough to know better than to doubt Sun's judgement :)

In case of an UBE, almost all drives will report a read/write error, some will just bump up the relocation failure count in SMART logs, and some el cheapo few will return an indeterminate bit value and not report any error. Thus the host may or may not be aware of UBEs, but it's up to the RAID controller to decide what to do about them. Most hardware controllers drop the disk -- and thus a single bit ruins your array. Some will skip that stripe and continue rebuilding the good ones, then let you choose what to do.

mdadm falls in between -- it drops the disk (and stops the rebuild), but does let you re-add it forcefully. It is therefore **very** important that every time you rebuild, you mount your arrays (or your LVs) read-only for the duration of the rebuild. Use snapshot volumes or unionfs/aufs if you really need that data to be writeable for the few hours that you need. It's a minor inconvenience compared to the alternative. 

DBrocks: Thanks, but that's all just Wikipedia and Google being my friend :)

Cheers,
Peter

---

