---
title: "Strange 3ware behaviour"
date: 2010-03-18
forum: System76 Support
---

### Post by Skaperen on 2010-03-18
Has anyone seen this happen with the 3ware RAID card in System76 servers?  I reconfigured the RAID controller (in a Jackal Pro 2U) to make each of the 5 (1TB) drives just be individual drives.  I saved the configuration and rebooted from my USB memory stick flash drive (has Ubuntu Desktop on it).  Then I noticed that the RAID controller was running a verify on the first 3 drives.  The last 2 were idle.  What's to verify with just a bunch of disks?  Is it just checking that each block has no errors?  If so, why just 3 drives and not all 5 drives?

---

### Post by thomasaaron on 2010-03-18
We don't get a lot of server-related questions on the forums.

My best guess is that it already verified the other drives and is still working on those three.

---

### Post by Skaperen on 2010-03-18
Servers are usually ordered, installed, and administered by more people who only have to ask around for the really tough questions.  And they often have more than one.

That was on a Jackal Pro 2U.

It was ordered with Ubuntu 9.10 64-bit.  But I am reconfiguring the RAID because we decided to change some things around on which machines have how much space, due to purpose changes.  I will be installing 9.10 64-bit again.

The prior configuration was RAID 5 on 5 drives for 4TB.  I'm changing that to RAID 5 on 4 drives for 3TB.  In the interim I changed it to 5 individual drives.  That's when I noticed it was doing the verify.  It was not doing that in the original RAID configuration when I ran a memory test over the weekend.  But even more strange was it doing the verify only on the first three drives and not on the last 2.  If it had done so on all 5 drives, I'd be less surprised, although still surprised some because I'm not sure what verification means for JBOD (guessing just to verify drives won't give read errors).  Verification of RAID 5 could check that the parity is consistent, and that is what I would hope it would do.  Another machine that had RAID 10, which I may change to RAID 5, did do a verify on all 4 drives which got done in about 3 hours.

---

### Post by Skaperen on 2010-03-22
I let it finish the verify of the 3 drives.  It took a few hours.  I don't have the exact time.  But when it got done, it started verifying the other 2 drives and that similarly took a few hours.

I reconfigured back to Raid 5.  Now it started clearing the drives.  Based on the rate the percentage was going up, it looked like it would take around 12 to 16 hours.  I canceled that.  I booted the Ubuntu 9.10 desktop ISO and ran a dd command to erase the first 4GB like this:  dd if=/dev/zero bs=1048576 count=4096 oflag=direct of=/dev/sda

It took about 18 minutes and dd reported a speed of 4.0 MB/s

On another machine also with Raid 5 but only 3 drives, the same command reported a speed of 77.1 MB/s.

In both cases, it was Raid 5, write cache disabled, 256K striping.  Could DMA be bad on the slow one?

---

### Post by Skaperen on 2010-03-23
It wants to clear the drives if I make a configuration with 5 drives, whether RAID 0 or RAID 5.  But if I make a configuration with just 3 drives (same machine, but just the first 3 drives used in the array unit), then it does not want to clear them.  Back to 5 drives and it wants to clear them again.

---

### Post by thomasaaron on 2010-03-24
***NOTE: This is from the email I sent you, for the benefit of anyone else who might happen across this thread in the future.***

Initial searching isn't really revealing expected performance for 5-drive, RAID 5 arrays with various stripe sizes.

I just called 3-ware and posed your question to them. They said the actual drives that you are using, the firmware of the drives and the firmware of the RAID card all come into play, and that exact performance information may not be possible.

However, they said if you wanted to call them directly they would be happy to provide you as much information as they can. A human picked up a phone on the first ring. Their number is...

888-646-4566

Your RAID card is a 3Ware 9650SE-8LPML.
The model of your hard drives is Seagate ST31000340NS.

---

