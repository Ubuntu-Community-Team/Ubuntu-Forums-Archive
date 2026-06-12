---
title: "Recovering SoftRaid after losing OS"
date: 2011-04-06
forum: Server Platforms
---

### Post by cmcnulty on 2011-04-06
Hey all, I have a Softraid setup that is used exclusively for media storage on my home server. The OS is *not* installed on the Raid.  What I'm worried about is if the single hard drive that's actually running the OS (10.04) dies on me, will I lose the information needed in order to mount the raid once I've rebuilt the OS.  

Should I be mirroring the OS in order to not lose the SoftRaid, or is there just some files or a directory that I should be backing up?  Basically I need to know how "system-critical" the OS is to a SoftRaid when the OS isn't actually installed *on* the SoftRaid itself.

TIA, Charles

---

### Post by psusi on 2011-04-06
No, you can recover the array without the system drive.  Why have a separate system drive though?  If all 3 drives are the same size, you should just turn them into a raid-5 and install the whole system with media storage there.

---

### Post by cmcnulty on 2011-04-06
Good question.  My Raid is made up of 4 drives that are in an external SATA enclosure, and they're in a raid 5.  I don't know why I did it that way.  Somehow my thought process was:

1) Build Ubuntu on spare computer
2) Add external SoftRAID for more storage.

Regarding recovering the array without the system drive, can you point me at any resources along those lines?  Would it be good enough if I just backed up the fstab and mdadm conf files (or printed them out for that matter), and then upon reinstalling the OS, recreating the config?

---

### Post by psusi on 2011-04-06
You can back up the mdadm.conf file, but it can be recreated by running mdadm --scan.

---

