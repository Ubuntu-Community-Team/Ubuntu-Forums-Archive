---
title: "Ubuntu Server Will not Boot"
date: 2009-09-06
forum: Server Platforms
---

### Post by jd8001 on 2009-09-06
All,
    I left my personal server running Ubuntu 8.04 (server) running over the weekend. When I came to log in this morning I came to realize that during the night the system had crashed. During boot, the system hangs on this error:

kinit: No resume image, doing normal boot...

Sometimes it can get past that error and give an error about DRDY and ATA errors. I ran through memtest for about 3 hours with no problems. I can't even get the machine to boot from a live CD (it hangs after I go into the live mode) or into recovery mode.  

My thought is that there are several bad sectors, but the sectors holding GRUB are still intact. However that seems mysteriously lucky, but it is the only thing that makes sense to me at the moment. This is a rather old system, so hardware failures would not surprise me. Any thoughts?


-JD

---

### Post by cholericfun on 2009-09-06
well, GRUB isnt all that big so bad sectors are rather unlikely i would think

since your liveCD doesnt boot it really sounds like a hardware issue  
Did you use that LiveCD before? maybe theres "just" a problem with your CD?

---

### Post by jd8001 on 2009-09-07
Hmm... I have used the LiveCD before, just not with that computer. Also, since GRUB is small, wouldn't that make bad sectors more likely (i.e. there is less of a chance of GRUB being on a bad sector?)?. 

What I would really like is a recovery CD that can run entirely in memory. Is there any way to get just the badblocks (or equivalent) utility on a LiveCD? 

Maybe it would help if I list off the things I think it could be:
1. A key component of the OS is on a bad sector, and there are plenty of bad sectors on the disk. The HDD going out would make sense since it happened randomly when I wasn't messing with it.

2. A wayward process deleted some key system file. This seems unlikely, but possible. Yet it does not explain why the LiveCD fails. 

3. Failed Motherboard. More specifically the IDE controller has gone out. Seems unlikely since BIOS recognizes the Drive correctly. 


Thoughts?

Update: 
I ran two different Hard Drive Diagnostic Scans from the Ultimate Boot CD Project. Both have reported 6 Errors on the Disk in the first 1% of the scan. That Doesn't strike me as catastrophic, but I've never dealt with a failing HDD

---

### Post by hessiess on 2009-09-07
> **jd8001 said:**
> Hmm... I have used the LiveCD before, just not with that computer. Also, since GRUB is small, wouldn't that make bad sectors more likely (i.e. there is less of a chance of GRUB being on a bad sector?)?. 

What I would really like is a recovery CD that can run entirely in memory. Is there any way to get just the badblocks (or equivalent) utility on a LiveCD? 

Maybe it would help if I list off the things I think it could be:
1. A key component of the OS is on a bad sector, and there are plenty of bad sectors on the disk. The HDD going out would make sense since it happened randomly when I wasn't messing with it.

2. A wayward process deleted some key system file. This seems unlikely, but possible. Yet it does not explain why the LiveCD fails. 

3. Failed Motherboard. More specifically the IDE controller has gone out. Seems unlikely since BIOS recognizes the Drive correctly. 


Thoughts?

Update: 
I ran two different Hard Drive Diagnostic Scans from the Ultimate Boot CD Project. Both have reported 6 Errors on the Disk in the first 1% of the scan. That Doesn't strike me as catastrophic, but I've never dealt with a failing HDD

If they are IDE (PATA) drives, try replacing the cables, and if you suspect the drives are failing, replace them ASAP.

---

### Post by jd8001 on 2009-09-07
Got it to boot. It was the 6 bad sectors. This tells me that the drive is going out, but I've just bought myself some time.

---

