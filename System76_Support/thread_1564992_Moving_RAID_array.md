---
title: "Moving RAID array"
date: 2010-08-31
forum: System76 Support
---

### Post by Skaperen on 2010-08-31
We have some System76 Jackal Pro 2U machines with the 9650SE RAID card.  Having gone through the process of reconfiguring the RAID before, I have discovered that when doing so, the drive data is effectively erased ... or at least enough of it to force loss of existing data.

Now I need to move an existing RAID array from one of these machines to another one (difference in CPU and RAM).  I would like to just take all 5 drives from the 1st machine and put them in the 2nd machine.  The concern is that this might lose all the data.

Anyone know where the 9650SE stores its RAID configuration?  If on the drive, then in theory, the configuration should simply follow the move.  But, if on the card (in flash?), then it would be necessary to reconfigure, and that would lose data.

Anyone know what is going on with these RAID cards, and how to do such a move with absolute safety of data and minimal (5 minutes max) downtime?

---

### Post by isantop on 2010-08-31
The actual RAID configuration is stored on the RAID card. 

So, I believe, apprehensively, that if you move the card, then put each drive back in exactly the same place, you should be okay. You'll need to make sure you put the wires from each drive back in the exact same places on the RAID card, and back in the same disks.

I'll do some additional googling and see what I can learn. If you haven't heard from me by Thursday, go ahead and bump this thread.

---

### Post by zaphod777 on 2010-09-01
I would also say the raid configuration is stored in the card also. But I would backup your data just in case. You can never be too careful.

---

### Post by Skaperen on 2010-09-01
Having to move the card with the drives defeats the intended purpose, which is to be able to quickly move data from one machine to another.

I am definitely going to need to have future machines configured with an extra drive that is not connected via the RAID card at all, to hold the OS.  A RAID card that can be configured w/o erasing existing data would be very highly desired.  If the RAID card dies, you just lost all your data.  I wonder how 3ware would answer that issue.

---

### Post by houstonbofh on 2010-09-01
> **Skaperen said:**
> Having to move the card with the drives defeats the intended purpose, which is to be able to quickly move data from one machine to another.

I am definitely going to need to have future machines configured with an extra drive that is not connected via the RAID card at all, to hold the OS.  A RAID card that can be configured w/o erasing existing data would be very highly desired.  If the RAID card dies, you just lost all your data.  I wonder how 3ware would answer that issue.
With backups...  Without those, you will always have a single point of failure somewhere.  (The building if the backup is not off site)  And as far as disk portability, I would recommend e-sata disk enclosures or e-sata jbods.

Remember that RAID is just designed to make drives more reliable, faster, or both.  Generally, drives fail more often than controllers.

---

### Post by Skaperen on 2010-09-02
I asked LSI/3ware about this and got an answer.  The configuration data is stored on the drives, not the controller.  Even the drive's index/position within a RAID set is stored, so moving the drives around should work.  It was recommended to keep the drives in the original order ... perhaps that is due to scheduling optimizations in the controller hardware or firmware design.  Additionally, more than one RAID set that was previously on separate controllers can be moved to a common controller with more ports to host both RAID sets.

So, here is a scenario:

Machine A is running at the data center and has a RAID array with 5 drives of 2TB each, yielding an set size of 8TB using RAID 5.  At an offsite location machine B has the same setup.  Data from machine A is synchronized to machine B by whatever means is appropriate for the data.  A big tree of files can be synchronized with rsync.  A database with network replication ability can do its own thing.

Machine A fails entirely or has a multi-drive failure.  The offsite backup does not have the network capacity to conduct the intended service.  Machine C is installed in the main center if machine A is not re-usable.  The drives from machine B are pulled, instead of the whole machine B, and brought back to the main center.  These drives are put in machine C or machine A.  Boot up and be back in business.

FYI, I have found those external drive enclosures, whether USB, Firewire, or e-SATA, to be rather unreliable.  And ironically, it is the enclosure controller, not the drive, that tends to fail more often.  But aside from that, I do agree that drives tend to be the biggest computer failure point, with power supplies a close 2nd.  That's why I now try to get "hot" swap power supplies, even if just one P/S (can't "hot" just one), for the ease of swapping, even if it is a cold swap.  It hate having to pull machines out of the rack or shelf, opening them, and swapping screwed in power supplies which in some cases require removing other parts (like the CPU+FAN assembly in some machines I have).  Internal hard drives are easier than power supplies in most cases.  But even they are trouble, so having hot-swap, even if used cold, helps.

---

