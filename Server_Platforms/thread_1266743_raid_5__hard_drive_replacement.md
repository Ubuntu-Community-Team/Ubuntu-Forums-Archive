---
title: "raid 5  hard drive replacement"
date: 2009-09-15
forum: Server Platforms
---

### Post by francog on 2009-09-15
I have a server set up with Raid 5 with 3 hard drives. One failed and the others are working fine. Well I went to replace the one hard drive and didn't click it on all the way so when I restarted I went into the bios and hit reconstruct and it changed the two remaining drives to raid 0. Now the new hard drive is installed properlly but it won't automatically reinitialize the raid 5.
 
Question: in bios screen how do i get it to find the replaced drive and reset the raid 5 settings. Options at my bios screen are; (configure, initialize, objects, clear, rebuild, check consistency, reconstruct)

---

### Post by windependence on 2009-09-15
Are you running hardware RAID? If so, your card wouldn't just change it to RAID 0 without asking you. IF that is the case, you may not be able to recover the RAID 5 if it overwrote the data. Is the data still there after you booted up the RAID 0? If so, you ca back up the data, create a fresh RAID 5 array, and restore data to the fresh RAID 5.

-Tim

---

### Post by francog on 2009-09-15
All the data is still there when I start the server. I'm guessing your right and it's still set to Raid 5 because the amber warning light is still on. In the bios screen though I can't find the replaced hard drive to rebuild array. I'm going to try to initialize the new hard drive first.

---

### Post by trundlenut on 2009-09-15
it sounds like hardware raid, is it a perc card by an chance? From the options it sounds the same as one I have.  If it has changed to RAID 0 then you can change it back to RAID 5 through the reconstruct option (I did this exact task last night actually).  You should also be able to see the drive in that option.

Also when you go into the RAID bios there should be a number of options across the bottom of the screen which will include something like "F3 drive information" and this should list the drives that are present inlcuding your replacement drive.

---

