---
title: "Testing RAID 5 troubles"
date: 2011-10-02
forum: Server Platforms
---

### Post by FirstTimeLinuxGuy on 2011-10-02
So, this is my first time actually "Using" Ubuntu, this is my official switch (kinda).  So i decided to build a file server for every computer on my network to store data on, and since im waiting for my hard drives to come in, i decided to toss a copy of Ubuntu server in there and force myself to learn all these new non-windows commands.  So far i have been doing pretty well, i learned how to use vi and edit my network settings.  However this is a data server, and that means RAID.  Now since im waiting for my hard drives to come in, i decided to learn how to use the software RAID.  I have 1  500GB HDD, and i partitioned 100GB for my OS, the rest i saved for 4 separate partitions that i will practice RAID on. now my problem, i have built the array, specifically telling it to use 4 drives, but after that it tells me that 3 /4 drives are being used and 1 is a spare (im doing RAID 5).  so i was really confused, i decided to stop the RAID, and run a command to add the remaining partition, because when i typed in blkid, i got my OS partition, 1 other partition, and 3 partitions in RAID.  after i added it, i re enabled the array, and then i run blkid to find 4 partitions in RAID.  now i run cat /proc/mdstat and i get

md_d0 : inactive sda7[2](s) sda8[4](s) sda[1](s)
        292965184 blocks
unused devices: <none>

now this is confusing, i was supposed to have 4 drives in RAID, which blkid tells me is true, and what does it mean by inactive?

---

### Post by Vegan on 2011-10-02
RAID uses physical disks, not partitions

---

### Post by FirstTimeLinuxGuy on 2011-10-02
Yeh but you can do soft raid with partitions, so in a sense they are "virtual drives" right?

---

