---
title: "[SOLVED] Two RAID 1's combined to a RAID 0"
date: 2008-12-19
forum: Server Platforms
---

### Post by bankg3 on 2008-12-19
Hey everyone,

I really have a few questions ....

First.  I want to upgrade my storage on my server I currently have 2 PATA hard drives (RAID 1 software 500GB) and want to add new SATA drives (RAID 1 hardware 750GB) to the RAID to create a RAID 0.  RAID1(software 500GB)+RAID1(hardware 750GB) = RAID0(~1.2TB) --- is this possible without loosing the data on my software RAID1?

if so, then we can continue to my next questions :)

My current setup is 3 PATA hard drives
/dev/sda
sda1    /       (~74GB)
sda2    swap    (~2GB)

/dev/sdb
sdb1 RAID partition (~459GB)

/dev/sdc
sdc1 RAID partition (~459GB)

/dev/sdb1 and /dev/sdc1 are in a RAID 1 configuration to create my /media/storage directory (software RAID w/ mdadm)

I'm upgrading my motherboard, proc and RAM to give me 4 available sata connections and I'm loosing one PATA, so I am going to move my OS to my new hard drives I can hardware configure these RAIDS so to linux I'm hoping it will just appear as one drive ... here is the desired configuration.

/dev/newSATA
newSATA1     /          (~20GB)
newSATA2     swap       (~4GB)
newSATA3     raid conf  (~726GB)

/dev/sdb and /dev/sdc I want to leave in the current raid configuration above.

Next I wanted to take /dev/newSATA3 and the /dev/md0 (sdb1 and sdc1 RAID1 dev) and combine them together to create a RAID0 dev -- /dev/md1 (~1.2TB) -- and I'm hoping to do all this while maintaining the data on my current RAID1...

Mostly I want to know if this is possible without loosing data, I don't have an extra hard drive to backup too, but I might need to get one just in case.

Any suggestions ... is it possible and am I going to screw my self up trying to do this? or am I safe to move ahead as planned?

Thanks!

---

### Post by bankg3 on 2008-12-22
So I've decided to forgo all the crazy stuff above and just do a RAID 5 with the new 750GB drives.  

Now my question is in a RAID 5 w/ 2 500GB and 2 750GB drives will I get more available room this way than in my RAID 1 + 0 configuration? 

Also will all of the space of my 750GB drive be used or will the RAID shrink them to 500GB drives?  I am using a software RAID..

Thanks!

---

### Post by windependence on 2008-12-23
You will be wasting 250 GB on each of the 750s. I am a big advocate of RAID 5 but this seems a bit of a waste to me. Why not just get one more 750 and then you can RAID5 the 3 750s. Your space on the RAID5 array would be 1.5TB. You could still keep the two 500s as a separate RAID volume for backup.

-Tim

---

### Post by bankg3 on 2008-12-23
Thanks for the advice

---

