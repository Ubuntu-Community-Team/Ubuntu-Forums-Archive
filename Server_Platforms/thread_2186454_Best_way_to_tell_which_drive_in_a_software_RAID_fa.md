---
title: "Best way to tell which drive in a software RAID failed?"
date: 2013-11-07
forum: Server Platforms
---

### Post by Roasted on 2013-11-07
I have a home server running Ubuntu Server 12.04 along with a software RAID (mdadm) with two 3TB WD Reds. I plan on adding two more to the mix and making it a RAID 6. I got to wondering, what's the best way to identify which drive died? My thinking is via smartmontools to grab the serial number and then check each drive. Is that the best way or is there a more predictable way for me to easily identify the drive without checking serial numbers? Just wanted to check - thanks!

---

### Post by SeijiSensei on 2013-11-07
"sudo mdadm --detail /dev/mdX" will tell you the status of the array /dev/mdX and its components.

---

### Post by Roasted on 2013-11-07
> **SeijiSensei said:**
> "sudo mdadm --detail /dev/mdX" will tell you the status of the array /dev/mdX and its components.

I'm aware of that. But what if I'm running a 4 drive array and one drive dies? I know I'll see 3/4 is running, but how can I identify that the 2nd drive in the stack of 4 physical drives within my server tower is *the* drive that is toast? Besides checking serial numbers, or using a hot-swap bay type of situation that has lights on the front of each bay to indicate which drive it is, I'm not sure how else I would. But hey, figured I'd ask and be sure instead of not ask and miss a better solution that I wasn't aware of.

---

### Post by SeijiSensei on 2013-11-08
Create the array using UUIDs as identifiers perhaps?  The UUIDs are based on the devices physical signatures so they remain fixed regardless of which /dev/sdX designations they have.

---

### Post by coldraven on 2013-11-08
> **SeijiSensei said:**
> Create the array using UUIDs as identifiers perhaps?  The UUIDs are based on the devices physical signatures so they remain fixed regardless of which /dev/sdX designations they have.

Would that work using labels?
If you labelled the drives Alice, Bob, Charlie and Dave and also physically wrote the name on the drive with a marker pen.

---

### Post by SaturnusDJ on 2013-11-13
Edit: Didn't read all of the topic. Already posted.

Anyways: Yes use UUID, then be sure to know with physical drive matches with that.

By the way: why RAID6 with the minimum amount of drives? Guys are crazy if they are running RAID5 with like 8 drives, but 4 for RAID6 seems a bit overprotective at one aspect of data conservation.

---

