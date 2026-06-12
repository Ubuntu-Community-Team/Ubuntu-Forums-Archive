---
title: "favourite flavours of softRAID 0?"
date: 2009-06-04
forum: Server Platforms
---

### Post by Polaris96 on 2009-06-04
Please comment on these three questions.  I'm trying to decide how to implement a softRAID0 array on two seagate cheetah SCSI U320 15k drives.  I haven't seen any hard numbers regarding the questions I'm about to ask.  I just want a "gut feeling" response from some 'heads, if possible.

1.  RAID0 via mdadm or lvm2?  both will do it.  is there a good reason for picking one above the other?  Would it be good to layer both (seems like a waste of function calls, there)?

2.  Reiser4?  Does anyone like it better than ext4?  Why or why not?

3.  is it possible to transfer an existing system to another partition without whacking it? (for example:  "dd if=/* of=/tmp/somenewdisk" and then alter fstab and maybe the bootfile?)

---

### Post by fjgaude on 2009-06-07
> **Polaris96 said:**
> 
1.  RAID0 via mdadm or lvm2?  both will do it.  is there a good reason for picking one above the other?  Would it be good to layer both (seems like a waste of function calls, there)?

2.  Reiser4?  Does anyone like it better than ext4?  Why or why not?

3.  is it possible to transfer an existing system to another partition without whacking it? (for example:  "dd if=/* of=/tmp/somenewdisk" and then alter fstab and maybe the bootfile?)

1. Well, raid0 doubles the read speed you'd get from just one drive. LVM doesn't. If you lose one drive all data is lost, period.

2. I like ext3 for its maturity.

3. An **mdadm** array can be moved to other Ubuntu systems without difficulty. Move the whole drives, physically. I've never used **dd** to go to other drives or arrays.

Good luck with whatever you do.

---

### Post by Polaris96 on 2009-06-08
Thanks very much for answering.  There's lots of read, here, but nobody wants to weigh in, it seems.  I'm thinking this is a good opportunity to do a bit research for the cause.

One question, though, if I might.  Why wouldn't striping in LVM2 double (or, more precisely, almost double) the access time like mdadm does?  After all, we're talking about striping two physical drives, here, not just combining two physical units into one logical volume.

Also, it seems to me that RAID0 offers no options for recovery even if one does use mdadm.  RAID0 protocol, as I understand it, offers only increased speed with no redundancy.  Thanks again.

---

### Post by fjgaude on 2009-06-09
I have not been keeping up with how LVM works... so I can't comment on if it strips or not. I didn't think it did.

Well, raid0 is for speed not reliability, as you thought. I would never use it for data that is important.

---

### Post by Polaris96 on 2009-06-10
thanks, Frank.

I'm going to try setting up and experiment to measuer the access time with both topologies.  Does anybody know of good software tools for measuring hdd access times?

---

### Post by fjgaude on 2009-06-11
I usually use **hdparm**:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec

```

Or use can use **dd** for direct drive speed:

```
time dd bs=1M count=1000 if=/dev/zero of=1000M.bin
```

Let us know what you decide. Thanks!

---

### Post by Polaris96 on 2009-06-11
Awesome!!  thanks again.  I'll try and set it all up over the weekend - will definitely post the results.

---

### Post by Polaris96 on 2009-06-30
just wanted to let everybody know I'm still running the experimetn.  Seems like there's always another parameter that needs evaluation.

I just heard that mdadm likes chunks of 256k or more.  Since my dataset is now {4k <= x <= 64k | K@ K0 + 2^n}, it looks like I'll need to run another couple of trials.

I'm also adding bonnie++ evals to the performance tests.

More to come...

---

