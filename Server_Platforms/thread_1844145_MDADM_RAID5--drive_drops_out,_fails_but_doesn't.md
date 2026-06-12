---
title: "MDADM RAID5--drive drops out, fails but doesn't"
date: 2011-09-14
forum: Server Platforms
---

### Post by greyday on 2011-09-14
Ok, this is weird.  I have a RAID5 running 4 1TB hdds.  I had a complete drive failure a couple months ago so I replaced it (and RMAed it, which was great of the manufacturer) with another drive i had laying around.  So about a month ago that drive had dropped out of the RAID and marked "failed".  I ran some diagnostics on it and couldn't find anything wrong with it so I added it back and everything worked fine.

This morning, it is showing up as failed again under cat /proc/mdstat.  However, running mdadm --examine shows it not only not failed (and lists zero failed drives in the RAID), but has it listed as a "spare" drive.  Which is just weird; should I pull it and test it again?  Reformat it and add it back in instead of just adding back in?  Swap it out with the RMA replacement (which I'm currently using in another system)?

---

### Post by rubylaser on 2011-09-14
I've found that once drives get kicked out more than once, it's a good indicator that either something is wrong with the drive or the SATA cable (You should be able to see this via smartctl in the UDMA error count).  First, I'd replace the cable and re-add the drive to the array.  If it happens again, I'd swap the drive.

---

### Post by greyday on 2011-09-15
Well, it's in a 12 drive rack, so if the cable was bad the other four drives on that line would probably be playing higgledy-piggledy as well.  ;)

I swapped it out with another drive, let's see if the problem persists.  In the meantime, THOROUGH testing of it on my main compy, probably put it in a cache R0 and run some (already completed and saved, of course) animation rendering overnight or something.

I just thought it was weird that it failed it but didn't drop it, it kept it as a spare.  Haven't come across that before...

---

