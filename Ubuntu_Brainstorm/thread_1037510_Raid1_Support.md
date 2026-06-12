---
title: "Raid1 Support"
date: 2009-01-11
forum: Ubuntu Brainstorm
---

### Post by uknowho008 on 2009-01-11
Not really a new idea, I'm just wondering if this is in the works, if I'm not the only person who wants it, or if nobody really cares. I personally would like it to happen so I can install linux on my video and music editing machine. I have raid1 configured for better performance. But anyway, does anybody else want this or am I alone? I don't know much about programming, just a little php, so I wouldn't be able to work on it myself at this point. I'm taking C++ this semster, but I'm sure it takes more than that for something like raid1. I wouldn't even know where to start.

---

### Post by smartboyathome on 2009-01-11
I don't use RAID, so I wouldn't know. Would LVM do a similar thing to what RAID would?

---

### Post by uknowho008 on 2009-01-12
Perhaps, I'm not sure. I know you can install a sofware that does it for you. But I'd be dual booting windows, So I need it to work with windows too. Since most motherboards support configuring raid via hardware I think that linux should support this too.

---

### Post by Cracauer on 2009-01-12
Using raid-1 (mirroring for data safety, speedup only for certain access patterns) on that onboard SATA RAID junk is a really bad idea.

I'd raid Linux in it's partitions. Did you really configure Windows to access Linux filesystems?

---

### Post by uknowho008 on 2009-01-12
why is it a bad idea?

No I didn't configure windows to access linux file systems. I meant I have windows installed on a raid1 configured hd and I would like to install linux to another partition on that raid1 configuration.

---

### Post by smartboyathome on 2009-01-12
Well, after [some research]("http://www.coderchris.com/2008/02/10/how-to-mount-a-linux-lvm2-partition-in-windows"), there is [a tool which allows Windows to access LVM2 partitions]("http://www.chrysocome.net/explore2fs"). LVM2 is a cheap version of raid which is more flexible, as it is located on the partition level.

---

### Post by Cracauer on 2009-01-12
> **uknowho008 said:**
> why is it a bad idea?


Using that onboard SATA stuff for safety (raid-1 or god forbid raid-5) is a bad idea because the web is full of reports of reconstruction of arrays not working when replacing disks. There is a big dependency chain between BIOS and runtime drivers and they don't seem to always agree on what to do with what disk. Most noticeably, people have lost arrays when a reboot happened after a temporary disk malfunction and the BIOS decided to write the bad disk's data over the good one.

I wouldn't touch this with a 10 foot pole. 

Linux md is rock-solid.

---

### Post by uknowho008 on 2009-01-12
> **smartboyathome said:**
> Well, after [some research]("http://www.coderchris.com/2008/02/10/how-to-mount-a-linux-lvm2-partition-in-windows"), there is [a tool which allows Windows to access LVM2 partitions]("http://www.chrysocome.net/explore2fs"). LVM2 is a cheap version of raid which is more flexible, as it is located on the partition level.

But then my xp install wouldn't be raid.

---

### Post by uknowho008 on 2009-01-12
> **Cracauer said:**
> Using that onboard SATA stuff for safety (raid-1 or god forbid raid-5) is a bad idea because the web is full of reports of reconstruction of arrays not working when replacing disks. There is a big dependency chain between BIOS and runtime drivers and they don't seem to always agree on what to do with what disk. Most noticeably, people have lost arrays when a reboot happened after a temporary disk malfunction and the BIOS decided to write the bad disk's data over the good one.

I wouldn't touch this with a 10 foot pole. 

Linux md is rock-solid.

I see, I'm not using raid for backup, it's only for the read performance. I keep my files backup on a separate drive so I'm not worried about losing anything.

---

### Post by Cracauer on 2009-01-13
Raid-1 only gives a speedup for some access patterns, and only if the RAID software is smart enough about which disk to use when.

The onboard SATA raid stuff as implemented by NVidia at least is not smart enough and doesn't even give that speedup for raid-1.

---

### Post by witoff on 2009-01-17
running a software RAID1 in multiple OSs would probably keep your files pretty safe but I'd be concerned with partition table corruptions that can take forever to fix.

Shouldn't any hardware controller abstract this away from the OS?

I've been using mount.cifs to mount a LAN shared RAID drive.  Super easy to configure and no dual booting worries!

---

